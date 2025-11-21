# Turtlebot4 — Pick & Place Item with Buzzer Indicator  
### Mid-Semester Exam – RE702 Localization and Mapping  
**Case Study:** Autonomous Delivery Robot (From Room 203 → Lobby BRAIL)

---

## Project Overview
This project involves programming a Turtlebot4 robot to autonomously go to pick up point at **Room 203** and going back to **Lobby BRAIL**.  
The system uses:

- **ROS2 Navigation (Nav2)**
- **SLAM Toolbox (Mapping)**
- **AMCL (Localization)**
- **Autonomous multi-waypoint navigation**
- **Buzzer/Speaker as notification**

### Buzzer Logic
- **1 beep** → Robot reaches **Pick Point (Room 203)**  
- **2 beeps** → Robot reaches **Place Point (Lobby BRAIL)**  

---

# 1. Connect to Turtlebot4
Ensure your laptop is connected to the Turtlebot4 using a **LAN cable**.

SSH into the robot:

ssh ubuntu@192.168.185.3

# 2. Build Workspace & Install Dependencies
2.1 Create ws

2.2 mkdir -p kelompok1/src

2.3 cd kelompok1

2.2 Clone repo
git clone https://github.com/Rusaven/turtlebot4_pickAndPlace.git

2.3 Install Dependencies
cd ../
rosdep install --from-paths src --ignore-src -r -y

2.4 Build ws
colcon build

# 3. Load map + AMCL
ros2 launch turtlebot4_navigation localization.launch.py map:=Mapping_Kelompok1APagiUTS.yaml params:=localization.yaml

# 4 Launch nav
ros2 launch turtlebot4_pick_place uts_nav.launch.py

# 5. Open RViz
ros2 launch turtlebot4_viz view_navigation.launch.py

# 6. Run pick and place program
6.1 cd kelompok1
6.2 source install/setup.bash
6.3 ros2 run uts uts

---

Demo : https://youtu.be/H8caqi7VKDY 
