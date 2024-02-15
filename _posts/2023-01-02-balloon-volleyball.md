---
title: Balloon Volleyball with a 7-DOF Robot Arm
tags: [ROS 2, Python, OpenCV, MoveIt]
background: /assets/theme/images/balloon_volleyball.gif
description: Collaborated with four other students to recreate the game "Don't let the balloon touch the ground" with a Franka Emika Panda robot.
---

# Balloon Volleyball with a 7-DOF Robot Arm

## Overview
In this project, I collaborated with four other students to recreate a human-robot version of the game "Don't let the balloon touch the ground." Using the Intel RealSense D435i camera, the Franka Emika Panda robot is able to track the balloon in real space, predict where the balloon will fall, move to that location before the balloon, and push it up. Once the balloon is in the air, the robot waits for it to fall down and hits it up again. The user interacts with the robot by initially tossing the balloon and adjusting it if it goes out of range.

<img src="/assets/theme/images/balloon_volleyball.gif" />

## Group Members
* Rintaroh Shima (Tracking/Computer Vision)
* Dilan Wijesinghe
* Muye Jia
* Hanbing Wu
* Ayush Gaggar

## Computer Vision
My main task was to work with another tracking engineer in the group to design a perception pipeline that can track the balloon in real space. This included calculating the centroid of the balloon and sending it over to the "hit" node, which was responsible for making a prediction of the balloon's falling location and sending a goal request to the robot. Below is a demonstration of the perception pipeline:

<img src="/assets/theme/images/balloon_tracking.gif" />

RealSense D435i camera was used throughout the design process. I first used background substraction, which eliminates the background from an image by extracting the moving foreground from the static background. However, it was not sufficient because the camera also detected random objects. This was a problem since the prediction would only work if the balloon tracking was accurate.

To overcome this problem, we decided to create a frame that detected only the red objects in the scene and then apply background subtraction. This successfully tracked only the moving red balloon and calculated the x, y, and z coordinates of its centroid.

<div style="text-align: center;">
    <a href="https://github.com/r-shima/AirTrafficControl" class="btn btn-outline-primary" role="button">View Project on GitHub</a>
</div>