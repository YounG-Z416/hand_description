# Stellarobot Models Repository
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Release](https://img.shields.io/github/v/release/YounG-Z416/hand_description.svg)

[简体中文](README.zh.md)

This repository contains **URDF** descriptions of dexterous hands, packaged in a ROS-style layout (`package.xml`, `CMakeLists.txt`, `launch/`, etc.).

**Folder naming:** each package directory uses **model line first**, then **`_left`** or **`_right`** (e.g. `gaiahand20_left`, `pantheonhand_right`). The main **URDF/CSV** files in `urdf/` use the same pattern (**`gaiahand20_right.urdf`**, not `right_gaiahand20.urdf`). Link and joint names inside the file may still use the historical `left_*` / `right_*` prefix for hardware alignment.

## Repository Structure
```
hand_description/                                        # Stellarobot dexterous hand URDF model collection
  ├── gaiahand20_left/                                   # ROS package: gaiahand20_left
  │   ├── config/joint_names_left_gaiahand20.yaml        # Joint name list  
  │   ├── launch/                                        # Launch files  
  │   │   ├── display.launch                             # ROS launch: Start RViz visualization  
  │   │   └── gazebo.launch                              # ROS launch: Start Gazebo physics simulation  
  │   ├── meshes/                                        # STL files  
  │   ├── urdf/                                          # URDF models 
  │   │   ├── gaiahand20_left.csv                        # Joint parameter table 
  │   │   └── gaiahand20_left.urdf                       # Main URDF robot description 
  │   ├── CMakeLists.txt                                 # CMake build script 
  │   ├── README.md                                      # English documentation
  │   ├── README.zh.md                                   # Chinese documentation
  │   ├── gaiahand20_left.png                            # Gaiahand20_left preview image 
  │   └── package.xml                                    # ROS package manifest 
  ├── gaiahand20_right/                                  # ROS package: gaiahand20_right 
  │   ├── config/joint_names_right_gaiahand20.yaml       # joint name list 
  │   ├── launch/                                        # Launch files 
  │   │   ├── display.launch                             # ROS launch: Start RViz visualization
  │   │   └── gazebo.launch                              # ROS launch: Start Gazebo physics simulation
  │   ├── meshes/                                        # STL files
  │   ├── urdf/                                          # URDF models
  │   │   ├── gaiahand20_right.csv                       # Joint parameter table
  │   │   └── gaiahand20_right.urdf                      # Main URDF robot description
  │   ├── CMakeLists.txt
  │   ├── README.md
  │   ├── README.zh.md
  │   ├── gaiahand20_right.png                           # Gaiahand20_right preview image
  │   └── package.xml  
  ├── gaiahand_left/                                     # ROS package: gaiahand_left
  │   ├── config/joint_names_left_gaiahand.yaml          # joint name list
  │   ├── launch/                                        # Launch files
  │   │   ├── display.launch                             # ROS launch: Start RViz visualization
  │   │   └── gazebo.launch                              # ROS launch: Start Gazebo physics simulation
  │   ├── meshes/                                        # STL files
  │   ├── urdf/                                          # URDF models 
  │   │   ├── gaiahand_left.csv                          # Joint parameter table
  │   │   └── gaiahand_left.urdf                         # Main URDF robot description
  │   ├── CMakeLists.txt  
  │   ├── README.md
  │   ├── README.zh.md          
  │   └── package.xml 
  ├── gaiahand_right/                                    # ROS package: gaiahand_right
  │   ├── config/joint_names_right_gaiahand.yaml         # joint name list
  │   ├── launch/                                        # Launch files
  │   │   ├── display.launch                             # ROS launch: Start RViz visualization
  │   │   └── gazebo.launch                              # ROS launch: Start Gazebo physics simulation
  │   ├── meshes/                                        # STL files
  │   ├── urdf/                                          # URDF models
  │   │   ├── gaiahand_right.csv                         # Joint parameter table
  │   │   └── gaiahand_right.urdf                        # Main URDF robot description
  │   ├── CMakeLists.txt
  │   ├── README.md
  │   ├── README.zh.md 
  │   └── package.xml    
  ├── pantheonhand_left/                                 # ROS package: pantheonhand_left
  │   ├── config/joint_names_left_pantheonhand.yaml      # joint name list
  │   ├── launch/                                        # Launch files
  │   │   ├── display.launch                             # ROS launch: Start RViz visualization
  │   │   └── gazebo.launch                              # ROS launch: Start Gazebo physics simulation
  │   ├── meshes/                                        # STL files
  │   ├── urdf/                                          # URDF models
  │   │   ├── pantheonhand_left.csv                      # Joint parameter table
  │   │   └── pantheonhand_left.urdf                     # Main URDF robot description
  │   ├── CMakeLists.txt
  │   ├── README.md
  │   ├── README.zh.md
  │   └── package.xml    
  ├── pantheonhand_right/                                # ROS package: pantheonhand_right
  │   ├── config/joint_names_right_pantheonhand.yaml     # joint name list
  │   ├── launch/                                        # Launch files
  │   │   ├── display.launch                             # ROS launch: Start RViz visualization
  │   │   └── gazebo.launch                              # ROS launch: Start Gazebo physics simulation
  │   ├── meshes/                                        # STL files
  │   ├── urdf/                                          # URDF models
  │   │   ├── pantheonhand_right.csv                     # Joint parameter table
  │   │   └── pantheonhand_right.urdf                    # Main URDF robot description
  │   ├── CMakeLists.txt
  │   ├── README.md
  │   ├── README.zh.md     
  │   └── package.xml      
  ├── LICENSE     
  ├── README.md                                          # Repository English overview
  └── README.zh.md                                       # Repository Chinese overview
```
                                                              
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
