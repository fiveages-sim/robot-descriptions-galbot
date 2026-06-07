# Galbot Zero Description

This package contains the description files for Galbot Zero humanoid. The origin models could be found at [RoboHanger_code](https://github.com/chen01yx/RoboHanger_code)

Robot models are defined under **`xacro/`** only (no static `urdf/`). `robot_common_launch` and OCS2 expand `xacro/robot.xacro` at runtime.

![galbot_zero.png](../.images/galbot_zero.png)

## 1. Build

```bash
cd ~/ros2_ws
colcon build --packages-up-to galbot_zero_description --symlink-install
```

## 2. Visualize the robot

### 2.1. Full robot

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_zero
```

* Without End Effector:
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_zero type:=none
  ```

### 2.2. Component modules

* Chassis
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_zero type:=chassis
  ```

* Body
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_zero type:=body
  ```

## 3. OCS2 Arm Controller Demo

### 3.1. Mock Component

* Full body
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_zero
  ```

* Split body
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch ocs2_arm_controller split_body.launch.py robot:=galbot_zero
  ```

### 3.2. Isaac Sim

* Full body
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_zero hardware:=isaac
  ```

* Split body
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch ocs2_arm_controller split_body.launch.py robot:=galbot_zero hardware:=isaac
  ```

## 4. Navigation

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch navigation_isaac_gt.launch.py robot:=galbot_zero map:=warehouse_multiple_shelfs nav2_profile:=map_only
```
