# Galbot G1(golf) Description

This package contains the description files for Galbot G1(golf) humanoid. The origin models could be found at [Galbot Golf Description](https://github.com/GalaxyGeneralRobotics/galbot_one_golf_description).

## 1. Build
```bash
cd ~/ros2_ws
colcon build --packages-up-to galbot_golf_description --symlink-install
```

## 2. Visualize the robot

### 2.1. Full robot

* Galbot Golf Robot (Default)
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_golf 
  ```

* Galbot Golf Robot with Hitbot Gripper
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_golf type:=hitbot
  ```
      
  ![G1](../.images/galbot_golf.png)


### 2.2. Component modules

* Body
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_golf type:=body
  ```

* Head
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_golf type:=head
  ```

### 3. Official OCS2 Mobile Manipulator Demo

* Galbot Gripper (Default)
```bash
source ~/ros2_ws/install/setup.bash

ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_golf
```

* Hitbot Gripper
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_golf type:=hitbot
```
[Screencast from 2025-08-29 17-53-30.webm](https://github.com/user-attachments/assets/f4d60a29-b3e8-4a98-b488-b28d5b3514f0)

### 4. OCS2 Arm Controller Demo

### 4.1 Mock Component

* Galbot Gripper (Default)
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_golf
  ```

* Hitbot Gripper
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_golf type:=hitbot
  ```
  
### 4.2 Isaac Sim

* Isaac (Default)
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_golf  hardware:=isaac

```
* Isaac + Hitbot
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_golf type:=hitbot hardware:=isaac

```

### 5. Isaac Navigation

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch navigation_isaac_gt.launch.py robot:=galbot_golf map:=warehouse_multiple_shelfs nav2_profile:=map_only
```