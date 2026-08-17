# Galbot Robots

Galbot humanoid robot description packages. Each package contains xacro models, meshes, RViz, and controller configuration. URDF is generated at launch time by `robot_common_launch` from `xacro/robot.xacro` (no static `urdf/` in the package).

These packages are licensed under [Apache-2.0](LICENSE). Third-party model sources and upstream terms are listed in [NOTICE](NOTICE) and each package README.

| | | |
|:---:|:---:|:---:|
| <img src=".images/galbot_zero.png" alt="Galbot Zero" width="300"> | <img src=".images/galbot_one.png" alt="Galbot One" width="300"> | <img src=".images/galbot_charlie.png" alt="Galbot One Charlie" width="300"> |
| **[Zero](galbot_zero_description/)** | **[One](galbot_one_description/)** | **[One Charlie](galbot_charlie_description/)** |
| <img src=".images/galbot_foxtrot.png" alt="Galbot G1 Foxtrot" width="300"> | <img src=".images/galbot_golf.png" alt="Galbot G1 Golf" width="300"> | <img src=".images/galbot_s1.png" alt="Galbot S1" width="300"> |
| **[G1 Foxtrot](galbot_foxtrot_description/)** | **[G1 Golf](galbot_golf_description/)** | **[S1](galbot_s1_description/)** |

## Common Commands

### Build

```bash
cd ~/ros2_ws
colcon build --packages-up-to <package> --symlink-install
source ~/ros2_ws/install/setup.bash
```

### Visualize Full Robot

```bash
ros2 launch robot_common_launch manipulator.launch.py robot:=<robot>
```

Useful arguments:

- `robot:=<robot>` selects the robot, for example `galbot_s1` or `galbot_foxtrot`.
- `type:=none` hides optional end effectors when the model supports it.
- `type:=hitbot`, `type:=galbot_gripper`, or `type:=suction_cup` selects the same end effector on both arms when available.
- Mixed arms: `left_type:=<type>` and `right_type:=<type>` override `type` per arm. Leave a side empty to use `type` on that arm.
- `collider:=simple` is the default on most models and uses simple primitive collision geometry. Some models also support `convex_decomposition` for convex-hull collision meshes.

### Visualize Component

```bash
ros2 launch robot_common_launch component.launch.py robot:=<robot> type:=<component>
```

Common component values include `chassis`, `body`, `head`, `arm`, and gripper-specific entries such as `left_gripper` or `right_gripper`. The exact list is model-specific.

### Run OCS2 Demos

The default hardware is `mock_components`.

```bash
ros2 launch robot_common_launch manipulator_ocs2.launch.py robot_name:=<robot>
ros2 launch ocs2_arm_controller full_body.launch.py robot:=<robot>
ros2 launch ocs2_arm_controller split_body.launch.py robot:=<robot>
```

`manipulator_ocs2.launch.py` is the official mobile manipulator demo. `full_body.launch.py` and `split_body.launch.py` are arm controller demos. Add `hardware:=isaac` for Isaac Sim where supported; otherwise the launch uses mock components. Navigation examples and model-specific OCS2 or gripper commands live in each package README.

Mixed end effectors on left and right arms (`galbot_foxtrot`, `galbot_golf`, `galbot_one`, `galbot_charlie`): pass **`left_type`** and **`right_type`** instead of a single symmetric `type`. Keys: `galbot_gripper`, `hitbot`, `suction_cup`, `none`.

Each arm gets a unified planning frame **`left_eef` / `right_eef`** (fixed joint on arm tip, gripper TCP, or suction TCP). OCS2 planning URDF uses `eef_fixed_joints:=true` automatically via `robot_common_launch`.

```bash
# OCS2 arm controller mock demo — left Hitbot + right suction cup
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_foxtrot \
  left_type:=hitbot right_type:=suction_cup
```

Optional: `enable_suction_rotation:=true` enables the suction-cup rotation joint in the visualization URDF only (no ros2_control interface).

### Robot profile (YAML)

Per-machine defaults use a robot profile YAML. Copy [`config/profile/robot.local.yaml.example`](config/profile/robot.local.yaml.example) and pass:

```bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_foxtrot \
  robot_profile:=/path/to/robot.local.yaml
```

Launch CLI `left_type` / `right_type` override profile `defaults.end_effectors`. Asymmetric setups compose gripper controllers automatically; `suction_cup` is passive (no ros2_control joint).

```bash
# Profile EEF defaults + launch override
ros2 launch ocs2_arm_controller full_body.launch.py robot:=galbot_foxtrot \
  robot_profile:=/path/to/robot.local.yaml left_type:=galbot_gripper
```

## Packages

```text
Galbot/
├── galbot_zero_description/
├── galbot_one_description/
├── galbot_charlie_description/
├── galbot_foxtrot_description/
├── galbot_golf_description/
└── galbot_s1_description/
```
