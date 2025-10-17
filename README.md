🦾 Interfacing UR Manipulator in Isaac Sim with ROS2 and MoveIt2

This repository demonstrates how to simulate a UR10e robot in Isaac Sim and interface it with ROS2 (Humble) and MoveIt2.
The guidelines will help you simulate your own robot and customize it for your specific needs.

🧩 System Setup

Tested Configuration

OS: Ubuntu 22.04

GPU: NVIDIA (8 GB VRAM)

RAM: 32 GB

Isaac Sim: 5.0.0 (Python 3.11 in a virtual environment)

ROS2: Humble (system-level, Python 3.10)

⚙️ Environment Setup
1️⃣ Isaac Sim Environment (Python 3.11)

Activate the Isaac Sim virtual environment and set required paths:

source ~/env_isaaclab/bin/activate
export ROS_DISTRO=humble
export RMW_IMPLEMENTATION=rmw_fastrtps_cpp
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/prem/env_isaaclab/lib/python3.11/site-packages/isaacsim/exts/isaacsim.ros2.bridge/humble/lib


💡 Tip:
Save the above commands in a file (e.g., isaac_env.sh) and source it whenever needed:

source isaac_env.sh

2️⃣ ROS2 Environment (Python 3.10)
source /opt/ros/humble/setup.bash

🔗 ROS2 and Isaac Sim Bridging

Official documentation:
👉 Isaac Sim ROS Bridge Installation Guide

🧱 Isaac ROS2 Workspace Setup

Download the official Isaac ROS2 workspace and use the humble_ws folder as your working ROS2 workspace (since we’re using Humble):

🔗 Isaac Sim ROS Workspaces (IsaacSim-5.0.0)

Isaac Sim (running in Python 3.11) and ROS 2 (Python 3.10) communicate using the
topic_based_ros2_control
 package.

🤖 UR ROS2 Description and Driver

Download the official Universal Robots packages for ROS2:

Universal Robots ROS2 Description

Universal Robots ROS2 Driver

You’ll need to make a few modifications to integrate them with Isaac Sim — examples are provided in this repository.

🏗️ Building the Workspace
cd humble_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
source install/setup.bash


⚠️ You must source install/setup.bash each time you open a new terminal.

🚀 Overall Workflow

Run Isaac Sim and load the UR10e robot:

Top-Left → Create → Robots → Asset Browser → UR10.usd

Create an Action Graph and configure the ROS2 bridge nodes.

(Follow this helpful tutorial: YouTube Video
)

Run the simulation in Isaac Sim and verify that appropriate ROS2 topics are being published:

ros2 topic list


Launch MoveIt2 along with RViz, ros2_control, and topic_based_ros2_control.

🧠 MoveIt2 Configuration

Refer to this repository’s example configuration.
You’ll need to edit the following file to match your robot and controller setup:

src/Universal_Robots_ROS2_Driver-humble/ur_moveit_config/ur_moveit_isaac.launch.py


Example snippets and explanations are included in comments within the file.

🚧 In Progress

Work in progress...
Stay tuned for full launch scripts, parameter files, and detailed setup instructions!

Authored by Prem Raj Kala
🧠 Robotics | Computer Vision | ROS 2 | Isaac Sim
