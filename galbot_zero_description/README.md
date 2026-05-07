# Galbot Zero Description



## Build

```bash
cd ~/ros2_ws
colcon build --packages-up-to galbot_zero_description --symlink-install
```

## Visualize

### Full Robot

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch humanoid.launch.py robot:=galbot_zero
```

Hide grippers (type:=none):

```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch humanoid.launch.py robot:=galbot_zero type:=none
```

### Component

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



## Full-body OCS2 Demo

* Mock Component
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_zero
  ```
* Isaac Sim
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_zero hardware:=isaac
  ```
## Split-body OCS2 Demo

* Mock Component
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch ocs2_arm_controller split_body.launch.py robot:=galbot_zero
  ```

* Isaac Sim
  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch ocs2_arm_controller split_body.launch.py robot:=galbot_zero hardware:=isaac
  ```
## Navigation

  ```bash
  source ~/ros2_ws/install/setup.bash
  ros2 launch robot_common_launch navigation_isaac_gt.launch.py robot:=galbot_zero map:=warehouse_multiple_shelfs nav2_profile:=map_only
  ```

