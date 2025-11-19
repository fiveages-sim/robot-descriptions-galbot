# Galbot G1(foxtrot) Description

This package contains the description files for Galbot G1(foxtrot) humanoid. The origin models could be found at [Galbot IOAI](https://github.com/galbot-ioai/physics_sim_edu).

## 1. Build
```bash
cd ~/ros2_ws
colcon build --packages-up-to galbot_foxtrot_description --symlink-install
```

## 2. Visualize the robot

* Galbot Foxtrot Robot
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_foxtrot
  ```
      
  ![G1](../.images/galbot_foxtrot.png)

* Galbot Gripper
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch gripper.launch.py gripper:=galbot_foxtrot
  ```
  ![Gripper](../.images/galbot_gripper.png)

## 3. OCS2 Demo

### 3.1 Official OCS2 Mobile Manipulator Demo

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_foxtrot
```
[Screencast from 2025-08-29 18-01-39.webm](https://github.com/user-attachments/assets/d9c63f0a-4b28-45b2-a046-77b3883a7504)


### 3.2 OCS2 Arm Controller Demo

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller demo.launch.py robot:=agibot_g1
```

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller demo.launch.py robot:=agibot_g1 hardware:=gz
```
