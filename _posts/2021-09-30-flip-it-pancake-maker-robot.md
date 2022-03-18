---
layout: post
---
ROS, MoveIt!, OpenCV, Python

## Overview
The goal of this project was to command a Franka Emika Panda arm to pour pancake batter onto a griddle, flip the pancake, and lift the pancake off the griddle. This process was done completely autonomously; utilizing open-source computer vision and motion planning software packages in a team of five: James Avtges, Anna Garverick, Jackson Levine, Sarah Ziselman, and myself. I personally focused on flipping the pancake and working on the manipulation node, while assisting with finding the object locations and computer vision. Manipulation involved calculating trajectories and cartesian paths for use with inverse kinematics to achieve reliable, effective movement. Single joint control was applied with forward kinematics, enabling precise control of the arm for difficult tasks, such as flipping the pancake. Utilizing a RealSense d435i and 3D Vision, we used point clouds, transformations, and AprilTags to find the pose of objects. See the code in my [GitHub repository](https://github.com/WallabyLester/FlipIt_Pancake_Maker_Robot).

![pancake making](/files/flip-it/pancake_making.gif)
<center>NOTE: This video is sped up 2.5x</center>

## Actions
All of the main functionalities of the project are implemented through a single ROS service `make_pancakes`.
- [Pour](#pour)
- [Bubble Detection](#bubble-detection)
- [Flip](#flip)
- [Lift](#lift)

### [Pour](#pour)

![Pour](/files/flip-it/pour.gif)

The first step is pouring of batter onto the heated griddle. This part of the service will command the robot to grab the bottle containing the mixed pancake batter, flip the bottle above the griddle, squeeze the bottle, and place the bottle back at its starting location.

### [Bubble Detection](#bubble-detection)

![Bubble Detection](/files/flip-it/bubble_detection.gif)

The robot will then wait for a signal to flip the pancake. Flip time is determined by counting the number of contours on the pancake and their rate of change. Once the number of bubbles is no longer increasing, the pancake is ready to be flipped. 

### [Flip](#flip)

![Flip](/files/flip-it/flip.gif)

Next, the robot grabs the spatula, maneuvers it under the pancake, flips the pancake back onto the griddle, and moves the robot to its home position.

### [Lift](#lift)

![Lift](/files/flip-it/lift.gif)

A 20 second wait time is used to ensure that the other side of the pancake is perfectly cooked. Then the robot uses the spatula to get under the pancake and lift it off of the griddle; flipping it onto the user's plate.

For the full code see my [GitHub repository](https://github.com/WallabyLester/FlipIt_Pancake_Maker_Robot).

See my next project [Robotic Helping Hand](https://wallabylester.github.io/robotic-helping-hand) or return to [EMG Controlled Hand Exoskeleton](https://wallabylester.github.io/EMG-controlled-hand-exoskeleton).