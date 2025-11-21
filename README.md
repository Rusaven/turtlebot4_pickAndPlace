# Turtlebot4 — Pick & Place Item with Buzzer Indicator  
### Mid-Semester Exam – RE702 Localization and Mapping  
**Case Study:** Autonomous Delivery Robot (From Room 203 → Lobby BRAIL)

---

## Project Overview
This project involves programming a Turtlebot4 robot to autonomously pick up an item from **Room 203** and deliver it to **Lobby BRAIL**.  
The system uses:

- **ROS2 Navigation (Nav2)**
- **SLAM Toolbox (Mapping)**
- **AMCL (Localization)**
- **Autonomous multi-waypoint navigation**
- **Buzzer/Speaker notification**

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
