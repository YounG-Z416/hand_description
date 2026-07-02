# Stellarobot Models Repository

[简体中文](README.zh.md)

This directory contains **URDF** descriptions of dexterous hands, packaged in a ROS-style layout (`package.xml`, `CMakeLists.txt`, `launch/`, etc.).

**Folder naming:** each package directory uses **model line first**, then **`_left`** or **`_right`** (e.g. `gaiahand20_left`, `pantheonhand_right`). The main **URDF/CSV** files in `urdf/` use the same pattern (**`gaiahand20_right.urdf`**, not `right_gaiahand20.urdf`). Link and joint names inside the file may still use the historical `left_*` / `right_*` prefix for hardware alignment.

## Packages

| Folder | Description |
|--------|-------------|
| [gaiahand20_left](gaiahand20_left/README.md) | Left · Gaia Hand 20 (20-DOF) |
| [gaiahand20_right](gaiahand20_right/README.md) | Right · Gaia Hand 20 (20-DOF) |
| [gaiahand_left](gaiahand_left/README.md) | Left · Gaia Hand |
| [gaiahand_right](gaiahand_right/README.md) | Right · Gaia Hand |
| [pantheonhand_left](pantheonhand_left/README.md) | Left · Pantheon Hand |
| [pantheonhand_right](pantheonhand_right/README.md) | Right · Pantheon Hand |

## Typical layout

Each hand package usually includes:

- **`urdf/`** — Primary `.urdf` and optional companion files (e.g. `.csv`).
- **`config/`** — `joint_names_*.yaml` listing controller joint names in order for simulation or toolchain alignment.
- **`launch/`** — `display.launch`, `gazebo.launch`, etc. for RViz / Gazebo workflows (optional).
- **`package.xml` / `CMakeLists.txt`** — Legacy catkin/ROS package metadata for reuse in a ROS workspace.

## Maintenance

- After changing meshes or joints, verify `package://` or relative mesh paths in the URDF still resolve.
- If joints are added or removed, update the matching `config/joint_names_*.yaml` and any upstream control logic.

## Contact

For licensing, models, or technical questions: **support@stellarobotic.com**
