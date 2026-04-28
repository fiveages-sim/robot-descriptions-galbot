# Galbot G1(foxtrot) Description

This package contains the description files for Galbot G1(foxtrot) humanoid. The origin models could be found at [Galbot IOAI](https://github.com/galbot-ioai/physics_sim_edu).

## 1. Build
```bash
cd ~/ros2_ws
colcon build --packages-up-to galbot_foxtrot_description --symlink-install
```

## 2. Visualize the robot

### 2.1. Full Robot
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

### 2.2. Component

* Wheel
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_foxtrot type:=wheel
  ```

* Chassis
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_foxtrot type:=chassis
  ```

* Head
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_foxtrot type:=head
  ```

* Arms
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_foxtrot type:=arm
  ```

## 3. Official OCS2 Mobile Manipulator Demo

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_foxtrot
```
[Screencast from 2025-08-29 18-01-39.webm](https://github.com/user-attachments/assets/d9c63f0a-4b28-45b2-a046-77b3883a7504)


## 4. OCS2 Arm Controller Demo

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_foxtrot
```

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_foxtrot hardware:=isaac
```

### 5. Isaac Navigation

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch navigation_isaac_gt.launch.py robot:=galbot_foxtrot map:=warehouse_multiple_shelfs nav2_profile:=map_only
```