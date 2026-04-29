# Galbot Charlie Description

## 1. Build

```bash
cd ~/ros2_ws
colcon build --packages-up-to galbot_charlie_description --symlink-install
```

## 2. 可视化机器人

### 2.1 全机器人

* Hitbot 夹爪（默认）
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_charlie type:=hitbot
```

* Galbot 夹爪
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_charlie type:=galbot_gripper
```

* 不挂夹爪
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator.launch.py robot:=galbot_charlie type:=none
```

### 2.2 组件模块

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

* Arm
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch component.launch.py robot:=galbot_charlie type:=arm
```

## 3. OCS2 Mobile Manipulator Demo

* Hitbot 夹爪
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_charlie type:=hitbot
```

* Galbot 夹爪
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=galbot_charlie type:=galbot_gripper
```

## 4. OCS2 Arm Controller Demo

### 4.1 Mock Component

* Hitbot 夹爪
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_charlie 
```

* Galbot 夹爪
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_charlie type:=galbot_gripper
```

### 4.2 Isaac Sim

* Isaac + Hitbot
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_charlie type:=hitbot hardware:=isaac
```

* Isaac + Galbot 夹爪
```bash
source ~/ros2_ws/install/setup.bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_charlie type:=galbot_gripper hardware:=isaac
```

## 5. 复用说明

`galbot_charlie_description` 当前实现为：
- `arm` 使用 Charlie 自定义 `xacro/components/arm.xacro`
- `chassis/body` 复用 `galbot_one_description`
- `ros2_control` 接口层复用 `galbot_one_description`

