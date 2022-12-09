---
layout: post
---
Prosthesis Control, Semi-Supervised, EMG, Pattern Recognition, Virtual Games

## Overview
The goal of this project was to utilize the existing EMG sensor device designed by Coapt in combination with virtual reality (VR) games to improve EMG-based classification. Virtual game data was used from prosthesis users playing two of Coapt's VR games. Data will not be available with this repository. Classification was performed with an adaptive linear discriminant analysis (LDA) model used by Coapt and recreated for this project. (Refer to: Vidovic et al. 2015 Improving the Robustness of Myoelectric Pattern Recognition for Upper Limb Prostheses by Covariate Shift Adaptation)

An LDA is often used for supervised classification problems. It estimates the probability that a new input belongs to every existing class. The output class is the one with the highest probability. However, training an LDA requires overwriting the previous which doesn't account for past history in the case of EMG classification. Adaptation allows for the LDA to be adapted to new data instead of overwriting the previous classifier. Using the previous class means and covariances, the LDA can be updated to account for past history and the new data. Such adaptive algorithms have been employed on myoelectric pattern recognition control systems to improve upper limb prosthesis performance. When training their control system, prosthesis users typically attempt to make consistent and repeatable muscle contractions. However, minimizing input data variation does not always resemble realistic usage scenarios as several factors (muscle fatigue, limb position, electrode shift, etc.) can contribute to changes in the characteristics of the muscle signals that lead to poor controller performance. While it may be difficult to account for all the possible variation, prosthesis users may benefit from training that better mimics real-life prosthesis use. 

Virtual games can be used for this, developed for practicing specific aspects of myoelectric prosthesis control, to adapt a linear discriminant analysis (LDA) model in a semi-supervised manner. Results from offline analysis of virtual game data collected across two weeks show that classification error rates substantially improve for some users using an adapted model compared to a non-adapted model. These results were also compared to an alternative adapted model in which low-level data re-labeling based on the sequence of the predicted model outputs during virtual game play was performed. Virtual games are a promising clinical tool which can be applied to better learn the user’s control preferences under simulated use conditions. Further development of this work could impact daily prosthesis use and performance for those who use myoelectric pattern recognition prosthesis control. See the code in my [GitHub repository](https://github.com/WallabyLester/Semi_Supervised_Adaptation_for_Myoelectric_Prosthesis_Control).

## Contents 
This project encompassed initial data processing and analysis to find the rules to be applied. Classification was then performed with various different methods and finally initially integrated into a cloud based platform.
- [Data Analysis](#data-analysis)
- [Rules](#rules)
- [Classification](#classification)
- [Cloud](#cloud)

### [Data Analysis](#data-analysis)
Data analysis was performed to observe data trends and information for creating rules in classifying EMG data. Virtual game data for In the Zone and Simon Says virtual games from Coapt for all participants was looked at. Involved the speed and consecutive classified motions. Consecutive motions can be used as indicators of user intention. 

### [Rules](#rules)
![Rules_Table](/files/semi-supervised-learning/Rules_Table.png)

Used the data analysis results to find the rules and relabel virtual game data based off of them. The rules were then used in classification comparisons. Used the base rule and augmented rule on all subjects to visualize the number of data points being relabeled by the rules.

![Relabeled_Points](/files/semi-supervised-learning/Relabeled_Points.png)

### [Classification](#classification)
![Model_Performance](/files/semi-supervised-learning/Model_Performance.png)

Applied an adaptive LDA on virtual game data along with comparisons to an unadapted LDA and an adaptive LDA using relabeled data from the applied rules. The augmented rule was the main focus as the base rule is encompassed in it and has less depth. 

![All_Subjects](/files/semi-supervised-learning/All_Subjects.png)

### [Cloud](#cloud)
As a final implementation step, the adaptive algorithm was integrated into a cloud platform. Based in Google cloud it queries an existing database and applied the adaptive LDA and adaptive LDA with rules and sends the updated classifier back to the cloud. 
