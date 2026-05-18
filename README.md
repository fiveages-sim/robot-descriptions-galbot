# Galbot Robots

This directory contains Galbot humanoid robot description packages. Each package provides URDF/Xacro, mesh, RViz, and controller configuration files for one Galbot model.

| Brand  | Model                                      | Repaint | Images                                             |
|--------|--------------------------------------------|---------|----------------------------------------------------|
| Galbot | [Zero](galbot_zero_description/)           | Yes     | <img src=".images/galbot_zero.png" width="200">    |
| Galbot | [One](galbot_one_description/)             | Yes     | <img src="../.images/galbot_one.png" width="200">  |
| Galbot | [Charlie](galbot_charlie_description/)     | Yes     | <img src=".images/galbot_charlie.png" width="200"> |
| Galbot | [G1 Golf](galbot_golf_description/)        | Yes     | <img src=".images/galbot_golf.png" width="200">    |
| Galbot | [G1 Foxtrot](galbot_foxtrot_description/)  | Yes     | <img src=".images/galbot_foxtrot.png" width="200"> |
| Galbot | [S1](galbot_s1_description/)               | Yes     | <img src=".images/galbot_s1.png" width="200">      |

## Usage

Each Galbot description is a ROS2 package that can be built and used independently.

### Build

Build an individual package:

```bash
cd ~/ros2_ws
colcon build --packages-up-to <package_name> --symlink-install
```

For example:

```bash
cd ~/ros2_ws
colcon build --packages-up-to galbot_foxtrot_description --symlink-install
```

### Visualize

Galbot packages are visualized through `robot_common_launch` with the robot name listed above.

Robot name:

```bash
robot:=<robot_argument>
```

Example:

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_foxtrot
```

Some models use `humanoid.launch.py` or expose additional variants such as `type:=hitbot`, `type:=galbot_gripper`, or `type:=none`. See the package README for model-specific launch commands, component modules, OCS2 demos, and navigation examples.


### Official OCS2 Mobile Manipulator Demo

Robot name:

```bash
robot_name:=<robot_argument>
```

Example:

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_foxtrot
```

[Screencast from 2025-08-29 18-01-39.webm](https://github.com/user-attachments/assets/d9c63f0a-4b28-45b2-a046-77b3883a7504)

### OCS2 Arm Controller Demo

#### Mock Component

OCS2 arm controller demos use `robot:=<robot_argument>`.

Example:

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_foxtrot
```

#### Isaac Sim

Example:

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_foxtrot hardware:=isaac
```

###  Gripper Support

Galbot models include several end-effector configurations depending on the robot package:

- `type:=hitbot` for Hitbot gripper variants
- `type:=galbot_gripper` for Galbot gripper variants
- `type:=none` for models that can hide the end effector
- `type:=left_gripper` and `type:=right_gripper` for Galbot S1 GE103-in gripper modules

Standalone gripper visualization is also available for packages that provide gripper components:

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch gripper.launch.py gripper:=<robot_argument>
```

## Package Structure

```
Galbot/
├── .images/                     # Robot and gripper images for documentation
├── galbot_zero_description/     # Galbot Zero robot package
├── galbot_one_description/      # Galbot One robot package
├── galbot_charlie_description/  # Galbot Charlie robot package
├── galbot_golf_description/     # Galbot G1 Golf robot package
├── galbot_foxtrot_description/  # Galbot G1 Foxtrot robot package
└── galbot_s1_description/       # Galbot S1 robot package
```
