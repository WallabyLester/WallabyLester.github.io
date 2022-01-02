---
layout: post
mathjax: true
---
Dynamics, Simulation, Lagrangian Mechanics, Python, SymPy, Jupyter Notebook

## Overview
The goal of this project was to use Lagrangian dynamics to model a complex system. The system in this project is a 6 DOF system of a dice inside of a cup; much like many common playing games with dice being shaken inside of a cup. The cup in this instance is rotating in order to show multiple impacts occurring. See the code in my [GitHub repository](TODO).

![dice in cup](/files/dice/dice_in_cup.gif "dice_in_cup.gif")

## System Configuration
The 6 degrees of freedom in the system consist of the x and y coordinates and angle ($\theta$) of the dice and cup. 

### Reference Frames
![frames](/files/dice/frames.png "frames.png")

Using transformation matrices, the position and orientation of all of the frames are related. 

### Equations of Motion
With this, the Euler-Lagrange Equations are solved for:
$$KE = \frac{1}{2} * {V}^TIV$$
$V$ - the velocity of the body\
$I$ - the combined mass and inertia matrix

$$PE = g({m}_c{y}_c + {m}_d{y}_d)$$
$g$ - gravity\
${m}_c$ - mass of the cup\
${m}_d$ - mass of the dice\
${y}_c$ - height of the cup\
${y}_d$ - height of the dice

$$Lagrangian = KE - PE$$

$$\frac{d}{dt}\dot{(\frac{\partial L}{\partial q})} - \frac{\partial L}{\partial q} = F$$
$q$ - matrix of configuration variables\
$F$ - matrix of external forces\
$L$ - Lagrangian previously found

### Constraints
The system has a total of 16 impact constraints: 4 for each wall of the cup impacting a specific vertex of the dice. With the extra frames defined on the cup at each midpoint of every side, the constraints are when the wall of the cup and vertex of the dice are equal.

### Impact Update
Momentum: 
$${\dot{\frac{\partial L}{\partial q}}}^+ - {\dot{\frac{\partial L}{\partial q}}}^- = \lambda\frac{\partial \varphi}{\partial q}$$
$\varphi$ - impact constraints\
$-$ - the configuration variables before impact\
$+$ - the configurations variables after impact

Energy:
$$H = (\dot{\frac{\partial L}{\partial q}})(\frac{dq}{dt}) - L$$
$H$ - Hamiltonian