# Galbot G1(golf) Description

This package contains the description files for Galbot G1(golf) humanoid. The origin models could be found at [Galbot Golf Description](https://github.com/GalaxyGeneralRobotics/galbot_one_golf_description).

## 1. Build
```bash
cd ~/ros2_ws
colcon build --packages-up-to galbot_golf_description --symlink-install
```

## 2. Visualize the robot

* Galbot Golf Robot
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_golf
  ```
      
  ![G1](../.images/galbot_golf.png)


### Component

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

## 3. OCS2 Demo

### 3.1 Official OCS2 Mobile Manipulator Demo

```bash
source ~/ros2_ws/install/setup.bash

ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_golf
```
[Screencast from 2025-08-29 17-53-30.webm](https://github.com/user-attachments/assets/f4d60a29-b3e8-4a98-b488-b28d5b3514f0)

### 3.2 OCS2 Arm Controller Demo

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_golf
```

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_golf hardware:=isaac
```
