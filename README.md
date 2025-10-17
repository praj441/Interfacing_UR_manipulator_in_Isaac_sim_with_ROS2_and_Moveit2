# 🦾 Interfacing UR Manipulator in Isaac Sim with ROS2 and MoveIt2

This repository demonstrates how to simulate a **UR10e robot** in **Isaac Sim** and interface it with **ROS2 (Humble)** and **MoveIt2**.  
The guidelines will help you simulate your own robot and customize it for your specific needs.

---

## 🧩 System Setup

**Tested Configuration**
- **OS:** Ubuntu 22.04  
- **GPU:** NVIDIA (8 GB VRAM)  
- **RAM:** 32 GB  
- **Isaac Sim:** 5.0.0 (Python 3.11 in a virtual environment)  
- **ROS2:** Humble (system-level, Python 3.10)

---

## ⚙️ Environment Setup

### 1️⃣ Isaac Sim Environment (Python 3.11)

Activate the Isaac Sim virtual environment and set required paths:

```bash
source ~/env_isaaclab/bin/activate
export ROS_DISTRO=humble
export RMW_IMPLEMENTATION=rmw_fastrtps_cpp
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/prem/env_isaaclab/lib/python3.11/site-packages/isaacsim/exts/isaacsim.ros2.bridge/humble/lib
