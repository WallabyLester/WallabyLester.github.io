---
layout: post
---
Embedded Control, Machine Learning, EMG, Feedback Control, C, Python

## Overview
The goal of this project was to design an EMG controlled hand exoskeleton that would aid stroke patients in playing the piano. 

<div style="text-align:center;">
<video width="640" height="360" controls> <source src="https://user-images.githubusercontent.com/90433630/159782526-b3bb951d-2681-48af-9a75-46fd34234eaf.mp4"> </video>
</div>

Stroke patients are often paralyzed, often on one side of the body or in only the face, an arm, or a leg. The idea behind this project is to allow patients to play the piano using a paralyzed hand, controlled by their other hand (read more about a non-actuated exoskeleton hand - [GQ article](https://www.gq.com/story/pianist-joao-carlos-martins-bionic-gloves)). I designed a 3D printable hand exoskeleton (inspired by Alex Czech's Elysium exoskeleton) which can be controlled using four Myoware EMG sensors and an Arduino Uno. The sensors give readings of the electrical activity of the active muscle fibers during contraction which I used machine learning to classify into an index finger, middle finger, fourth finger, and pinky. See the code in my [GitHub repository](https://github.com/WallabyLester/EMG_Controlled_Hand_Exoskeleton).


## Actions
The exoskeleton is controlled through a Feedback Loop implementing PID control and classified EMG sensor readings. When a user pushes down with any of the four fingers, the signals are classified to the correct finger and the motors move the corresponding finger of the exoskeleton. 
- [Design](#design)
- [Basic Movement](#basic-movement)
- [Thresholding](#thresholding)
- [Finished Product](#finished-product)

### [Design](#design)

![Exoskeleton](/files/EMG-controlled-hand/exoskeleton.png)

The 3D printed exoskeleton without any wiring. The mini DC gearmotors are contained in the box and velcro is used to contain the wrist and fingers.

### [Basic Movement](#basic-movement)

![Basic Movement](/files/EMG-controlled-hand/basic_movement.gif)

An Arduino Uno was used for speed of development. When the signal is received by the controller, the motors are moved. In this stage encoders were not yet implemented so the motors ran forward then backward. 

### [Thresholding](#thresholding)

![Thresholds](/files/EMG-controlled-hand/thresholds.gif)

Prior to machine learning classification, manual thresholds were found in a lookup table format which enabled moderately well predictions of which fingers were being moved. 

### [Finished Product](#finished-product)
<div style="text-align:center;">
<video width="640" height="360" controls> <source src="https://user-images.githubusercontent.com/90433630/159782526-b3bb951d-2681-48af-9a75-46fd34234eaf.mp4"> </video>
</div>
<p style="text-align:center;">Realtime</p>

<div style="text-align:center;">
<video width="640" height="360" controls> <source src="https://user-images.githubusercontent.com/90433630/159781489-9f40ca56-956c-40ad-be2c-83d8e31b5621.mp4"> </video>
</div>
<p style="text-align:center;">Sped up 2x to hear the song</p>


With machine learning classification and position control I am able to play some of You Are My Sunshine, if a little slowly. The hand responds slowly due to the speed at which serial data is being set and classification occurs. These are both areas that can be improved upon. In addition, the Arduino can be replaced with a better controller which would help considerably in the frequency everything can be run. I also hoped to augment the design of the exoskeleton itself to make it more comfortable and add joints for the fingers to enable greater lateral movement.


For the full code see my [GitHub repository](https://github.com/WallabyLester/EMG_Controlled_Hand_Exoskeleton).

See my next project [FlipIt Pancake Maker Robot](https://wallabylester.github.io/flip-it-pancake-maker-robot).
