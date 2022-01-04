---
layout: post
mathjax: true
---
Manipulation, Motion Planning, Trajectory Generation, Omnidirectional Robot

## Overview
The goal of this project was to perform mobile manipulation using Python code which: generates a trajectory, calculates odometry, and performs feedback control with a PI controller. The code outputs a csv file for use with CoppeliaSim in order to simulate the results. See the code in my [GitHub repository](https://github.com/WallabyLester/Mobile_Manipulation).

![mobile manipulation](/files/mobile-manipulation/mobile-manipulation.gif)

## Components
The code can contains three main segments:
- [Trajectory Generation](#trajectory-generation)
- [Kinematics Model](#kinematics-model)
- [Feedback Control](#feedback-control)

### [Trajectory Generation](#trajectory-generation)

![trajectory generation](/files/mobile-manipulation/trajectory-generation.gif)

This segment outputs a reference trajectory needed for the end effector to pick and place the cube. The TrajectoryGenerator function takes in the initial end-effector configuration, initial cube configuration, desired cube configuration, end-effector grasping configuration, and the number of trajectory reference configurations per second.

### [Kinematics Model](#kinematics-model)

The robot kinematics are attained using NextState, which takes the current configuration of the robot, arm joint and wheel speeds, timestep, and max speed of the joints and wheels. The function returns the new configuration of the robot using first-order Euler Integration and hte chassis configuration based on odometry. 

### [Feedback Control](#feedback-control)
The last step is to implement feedforward plus feedback control law:

$$V(t) = [Ad_{X^{-1}-X_d}]V_d(t) + K_pX_{err} + Ki{\int\limits_0^t}X_{err}(t)dt$$

$V$ - end-effector twist\
$X_{err}$ - error between the current end-effector configuration and the reference trajectory\
$K_{p}$ - the proportional gain\
$K_{i}$ - the integral gain

The pseudoinverse of the jacobian is then used to calculate the wheel and arm joint speeds. 

$$\left[ {u \atop {\dot{\theta}}} \right] = {J^{\dagger}}_e(\theta)V$$

### Example of Badly Tuned Controller
![overshoot](/files/mobile-manipulation/overshoot.gif)

### Example of Different Cube Position
![new task](/files/mobile-manipulation/new-task.gif)