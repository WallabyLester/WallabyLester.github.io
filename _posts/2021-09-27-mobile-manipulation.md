---
layout: post
---
Manipulation, Motion Planning, Trajectory Generation, Omnidirectional Robot

## Overview
The goal of this project was to perform mobile manipulation using Python code which: generates a trajectory, calculates odometry, and performs feedback control with a PI controller. The code outputs a csv file for use with CoppeliaSim in order to simulate the results. See the code in my [GitHub repository]().

![mobile manipulation](/files/mobile-manipulation/mobile-manipulation.gif)

## Components
The code can contains three main segments:
- [Trajectory Generation](#trajectory-generation)
- [Kinematics Model](#kinematics-model)
- [Feedback Control](#feedback-control)

### [Trajectory Generation](#trajectory-generation)

![trajectory generation](/files/mobile-manipulation/trajectory-generation.gif)

This segment outputs a reference trajectory needed for the end effector to pick and place the cube. The TrajectoryGenerator function takes in the initial end-effector configuration, initial cube configuration, desired cube configuration, end-effector grasping configuration, and the number of trajectory reference configurations per second.
