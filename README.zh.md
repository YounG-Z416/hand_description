# Stellarobot 模型资源库

[English](README.md)

本目录存放灵巧手的 **URDF 模型** 及相关 ROS 风格包文件（`package.xml`、`CMakeLists.txt`、`launch/` 等）。

**目录命名：** 每个包目录为 **产品系列名在前**，**左右侧在后**，使用 **`_left`** / **`_right`** 后缀（例如 `gaiahand20_left`、`pantheonhand_right`）。`urdf/` 下主 **URDF、CSV** 文件名与目录一致（如 **`gaiahand20_right.urdf`**）。文件内的连杆、关节名仍可为 `left_*` / `right_*`，与硬件与控制器约定对齐。

## 子目录一览

| 子目录 | 说明 |
|--------|------|
| [gaiahand20_left](gaiahand20_left/README.zh.md) | 左手 · Gaia Hand 20（20 关节） |
| [gaiahand20_right](gaiahand20_right/README.zh.md) | 右手 · Gaia Hand 20（20 关节） |
| [gaiahand_left](gaiahand_left/README.zh.md) | 左手 · Gaia Hand |
| [gaiahand_right](gaiahand_right/README.zh.md) | 右手 · Gaia Hand |
| [pantheonhand_left](pantheonhand_left/README.zh.md) | 左手 · Pantheon Hand |
| [pantheonhand_right](pantheonhand_right/README.zh.md) | 右手 · Pantheon Hand |

## 典型目录结构

每个手型包通常包含：

- **`urdf/`**：主 `.urdf` 文件及配套的 `.csv`（若有）等。
- **`config/`**：`joint_names_*.yaml`，列出控制器关节名顺序，供仿真或工具链对齐。
- **`launch/`**：`display.launch`、`gazebo.launch` 等，用于 RViz / Gazebo 调试（可选）。
- **`package.xml` / `CMakeLists.txt`**：历史 ROS/catkin 包布局，便于在 ROS 工作空间中复用。

## 维护建议

- 更新网格或关节后，检查 URDF 中 `package://` 或相对 mesh 路径是否仍有效。
- 若增减关节，请同步更新对应 `config/joint_names_*.yaml` 及上层控制逻辑。

## 联系与支持

如有模型、授权或技术问题，请联系：**support@stellarobotic.com**
