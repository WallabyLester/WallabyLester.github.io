---
layout: post
---
ROS, MoveIt!, OpenCV, Python

## Overview
The goal of this project was to command a Franka Emika Panda arm to pour pancake batter onto a griddle, flip the pancake, and lift the pancake off the griddle. This process was done completely autonomously; utilizing open-source computer vision and motion planning software packages. See the code in my [GitHub repository](https://github.com/WallabyLester/FlipIt_Pancake_Maker_Robot).

![pancake making](/files/flip-it/pancake_making.gif)

## Actions
### Pour

![Pour](/files/flip-it/pour.gif)

The first step is pouring of batter onto the heated griddle. This part of the service will command the robot to grab the bottle containing the mixed pancake batter, flip the bottle above the griddle, squeeze the bottle, and place the bottle back at its starting location.

### Bubble Detection

![Bubble Detection](/files/flip-it/bubble_detection.gif)

The robot will then wait for a signal to flip the pancake. Flip time is determined by counting the number of contours on the pancake and their rate of change. Once the number of bubbles is no longer increasing, the pancake is ready to be flipped. 

### Flip

![Flip](/files/flip-it/flip.gif)

Next, the robot grabs the spatula, maneuvers it under the pancake, flips the pancake back onto the griddle, and moves the robot to its home position.

### Lift

![Lift](/files/flip-it/lift.gif)

A 20 second wait time is used to ensure that the other side of the pancake is perfectly cooked. Then the robot uses the spatula to get under the pancake and lift it off of the griddle; flipping it onto the user's plate.
