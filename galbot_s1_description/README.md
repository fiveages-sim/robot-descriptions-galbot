# Galbot S1 Description

This package contains the description files for Galbot S1 humanoid. Source assets are tracked with [Galbot S1 Description](https://github.com/GalaxyGeneralRobotics/galbot_s1_description).

## 1. Build

```bash
cd ~/ros2_ws
colcon build --packages-up-to galbot_s1_description --symlink-install
```

## 2. Visualize the robot

### 2.1. Full robot

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_s1
```

### 2.2. Component modules

* Chassis

  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_s1 type:=chassis
  ```

* Body (no chassis — lifting column + torso / head only)

  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_s1 type:=body
  ```

* Arms

  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_s1 type:=arm
  ```

* Left gripper only (GE103-in)

  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_s1 type:=left_gripper collider:=visual
  ```

* Right gripper only (GE103-in)

  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_s1 type:=right_gripper
  ```

* Notes

  - `robot.xacro` now uses argument `collider` (for example: `collider:=convex_decomposition`)

## 3. Official OCS2 Mobile Manipulator Demo

```bash
source ~/ros2_ws/install/setup.bash

ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_s1
```

### 4. OCS2 Arm Controller Demo

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_s1
```

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_s1 hardware:=isaac
```

### 5. Isaac Navigation

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch navigation_isaac_gt.launch.py robot:=galbot_s1 map:=german_poc nav2_profile:=map_only
```