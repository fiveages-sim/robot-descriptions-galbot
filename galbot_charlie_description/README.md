# Galbot Charlie Description

This package contains the description files for Galbot Charlie humanoid. The origin models could be found at [RoboHanger_code](https://github.com/chen01yx/RoboHanger_code)

Robot models are defined under **`xacro/`** only (no static `urdf/`). `robot_common_launch` and OCS2 expand `xacro/robot.xacro` at runtime.

![galbot_charlie.png](../.images/galbot_charlie.png)

## 1. Build

```bash
cd ~/ros2_ws
colcon build --packages-up-to galbot_charlie_description --symlink-install
```

## 2. Visualize the robot

### 2.1. Full robot

* Without End Effector:
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_charlie type:=none
  ```

* With Hitbot Gripper (Default)
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_charlie type:=hitbot
  ```

* With Galbot Gripper
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_charlie type:=galbot_gripper
  ```

### 2.2. Component modules

* Base
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_charlie type:=base
  ```

* Body
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_charlie type:=body
  ```

* Arms module
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_charlie type:=arm
  ```

### 3. Official OCS2 Mobile Manipulator Demo

* Hitbot Gripper (Default)
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_charlie type:=hitbot
```

* Galbot Gripper
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_charlie type:=galbot_gripper
```

### 4. OCS2 Arm Controller Demo

### 4.1 Mock Component

* Hitbot Gripper (Default)
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py \
  robot:=galbot_charlie
```

* Galbot Gripper
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py \
  robot:=galbot_charlie type:=galbot_gripper
```

* Left Hitbot + Right Suction Cup (mixed end effectors, mock)
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_charlie \
  left_type:=hitbot right_type:=suction_cup
```

### 4.2 Isaac Sim

* Isaac + Hitbot Gripper (Default)
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py \
  robot:=galbot_charlie hardware:=isaac
```

* Isaac + Galbot Gripper
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py \
  robot:=galbot_charlie type:=galbot_gripper hardware:=isaac
```

