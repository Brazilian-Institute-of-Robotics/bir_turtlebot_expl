# bir_turtlebot-expl

This repository contains a **ROS** package to implement navigation with the  **A\*** algorithm on the **turtlebot 3**. A* (pronounced "A-star") is a path search algorithm.

**Keywords**: TurtleBot3, ROS, A*, D*, RRT, PRM

**Author**: [Anderson Lima](https://github.com/aldenpower)<br />
Affiliation: [BIR - Brazilian Institute of Robotics](https://github.comBrazilian-Institute-of-Robotics) <br />
Maintainer: Anderson Lima, eng.andersonfsl@gmail.com

_For more details visit [RASC](https://www.braziliansinrobotics.com/) and [Star navigation](https://www.braziliansinrobotics.com/2021-12-10-turtlebot3-astar-navigation/)_


## Supported Versions
- **ROS Noetic**: Tested under [ROS](https://www.ros.org/) Noetic and Ubuntu 20.04

## Installation base

_Create a workspace folder_

1 - `mkdir -p ~/turtle_ws/src`

_Enter in the source folder of the workspace_

2 - `cd ~/turtle_ws/src`

_Clone the turtlebot3 repositories_

3 - `git clone -b noetic-devel https://github.com/ROBOTIS-GIT/DynamixelSDK.git`

4 - `git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git`

5 - `git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3.git`

_Clone this respository_

6 - `git clone --recurse-submodules https://github.com/Brazilian-Institute-of-Robotics/bir_turtlebot_expl.git`

_Build your workspace_

7 - `cd ~/turtle_ws && catkin_make`

_Source your workspace_

8 - `source ~/turtle_ws/devel/setup.bash`


## A* run

Run the turtlebot 3 house world with: 

1 - `roslaunch turtlebot3_gazebo turtlebot3_house.launch`

### Run the simulation

You can run the navigation with two launchs:

- **Navigation with Gmapping**

    _This launch will run the SLAM Gmapping Node with Move base planning the path with A*_

    2.1 - `roslaunch ttb_astar navigation_a_star.launch`

- **Navigation with AMCL**

    _This launch will run the AMCL with the house map with Move base planning the path with A*. The navigation with AMCL is more precise._

    2.2 - `roslaunch ttb_astar navigation_a_star_amcl.launch`

## RRT run

_Download the image that will be used by docker through the link_

1 - [rrt image link](https://drive.google.com/file/d/19lIg9ob_BZekCTNvuxKBq69jxl-yBjjp/view?usp=sharing)

_Load the image to docker_

2 - `docker load < kineticrrt.tar.gz`

_Run the turtlebot 3 house world with:_

3 - `roslaunch turtlebot3_gazebo turtlebot3_house.launch`

_Run the navigation launch_

4 - `roslaunch ttb_rrt navigation_rrt.launch`

_Create the container through the image_

3 - `docker run -it --privileged --net=host kinetic/rrt`

_Run the rrt exploration launch inside the container_

5 - `roslaunch rrt_exploration simple.launch`