# Galbot One Description

This package contains the description files for Galbot humanoid. The origin models could be found at [RoboHanger_code](https://github.com/chen01yx/RoboHanger_code)

![galbot_one.png](../.images/galbot_one.png)

## 1. Build

```bash
cd ~/ros2_ws
colcon build --packages-up-to galbot_one_description --symlink-install
```

## 2. Visualize the robot

### 2.1. Full robot

* Without End Effector:
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_one type:=none
  ```

* With Hitbot Gripper (Default)
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_one collider:=simple
  ```

* With Galbot Gripper
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_one collider:=simple type:=galbot_gripper
  ```

### 2.2. Component modules

* Wheel
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_one type:=wheel
  ```

* Chassis
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_one type:=chassis
  ```

* Body
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_one type:=body
  ```

* Arms module
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch component.launch.py robot:=galbot_one type:=arm
  ```

* Gripper Hitbot (Default)
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch gripper.launch.py gripper:=galbot_one
  ```

* Gripper Galbot
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch gripper.launch.py gripper:=galbot_one type:=galbot_gripper
  ```

### 3. Official OCS2 Mobile Manipulator Demo

* Hitbot Gripper (Default)
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_one
```

* Galbot Gripper
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_one type:=galbot_gripper
```

https://github.com/user-attachments/assets/2948099b-ac18-473c-8201-79c42028e2c4

### 4. OCS2 Arm Controller Demo

### 4.1 Mock Component

* Hitbot Gripper (Default)
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py \
  robot:=galbot_one
```

* Galbot Gripper
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py \
  robot:=galbot_one type:=galbot_gripper
```

### 4.2 Isaac Sim

* Isaac (Default)
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py \
  robot:=galbot_one hardware:=isaac
```

* Isaac + Galbot Gripper
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py \
  robot:=galbot_one type:=galbot_gripper hardware:=isaac
```
