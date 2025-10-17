# Interfacing_UR_manipulator_in_Isaac_sim_with_ROS2_and_Moveit2

In this repository, I will let you go through simulating a UR10e robot in Isaac Sim and then go interface with ROS2 (humble) and Moveit2.
The guidelines will help you to simulate your own robot and do customization you needs.

Below steps are tested on a Ubuntu 22.04 system with 8GB Nvidia GPU and 32GB RAM

Installed Isaac-sim 5.0.0 in a virtual environment (with python 3.11) provided by UV

Installed ROS2 humble on system level (python 3.10)

Since you should need different shell environment for isaac sim (python 3.11) and ROS (python 3.10), I am using below commands for each:
Isaac_sim:
source ~/env_isaaclab/bin/activate
export ROS_DISTRO=humble
export RMW_IMPLEMENTATION=rmw_fastrtps_cpp
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/prem/env_isaaclab/lib/python3.11/site-packages/isaacsim/exts/isaacsim.ros2.bridge/humble/lib

you can store these command in a file_name.sh file and do:
source file_name.sh, to prepare the environment for isaac

ROS:
source /opt/ros/humble/setup.bash


Ros2 and issacsim bridging:
https://docs.isaacsim.omniverse.nvidia.com/latest/installation/install_ros.html

Isaac_ros2_workspace:
download the isaac_ros2 workspace from below and use its humble_ws folder as your ROS workspace (since I am using ROS2 humble)
https://github.com/isaac-sim/IsaacSim-ros_workspaces/tree/IsaacSim-5.0.0

Isaac-sim (in virtual env) and ROS (system) communicates using topic_based_ros2_control package


UR_ROS2 description and driver:
Download the original official drivers from below links. You need to modify certain things to work it out with Isaac
https://github.com/UniversalRobots/Universal_Robots_ROS2_Description
https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver


Building the humble_ws workspace:
1) cd to /humble_ws
2) rosdep install --from-paths src --ignore-src -r -y
3) colcon build --symlink-install
4) source install/setup.bash   (you need to run this each time you open a new terminal)

Overall workflow:
1) Run isaac sim and load UR10.usd from (Top-left -> Create -> Robots -> Asset Browser)
2) You need to create an ActionGrasp and configure a few things (I followed this (https://youtu.be/pGje2slp6-s))
3) Run the simulation in Isaac_sim and check if it publish appropiate topics
4) launch moveit2 along with rviz, ros2_control, topi_based_ros2_control 

For moveit part above, refer my code as an example and you need to do following changes:
1) In /src/Universal_Robots_ROS2_Driver-humble/ur_moveit_config/ur_moveit_isaac.launch.py
.
.
.

In progress...
Stay Tuned...
