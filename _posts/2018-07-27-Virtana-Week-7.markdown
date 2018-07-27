---
layout: post
title:  "Virtana Week 7"
date:   2018-07-27 -0400
categories: posts
---

This week at [Virtana](https://virtanatech.com/) has been spent attempting to build upon my work from [last week](/posts/2018/07/20/Virtana-Week-6.html). I refactored camera code and have been working on simplifying the communication process to update robot joints.

Originally, I was supposed to just be  fixing the bug in the simulation cameras' output for WebRTC that I mentioned last week, but instead I decided to refactor the code as well. The  camera code had to logic for image processing and making packets mixed together. This was fine when the cameras only had to send the images as TCP/IP packets, but it became a problem when the simulation needed to output data to be read by another program as input. The code was doing unnecessary work since the packets it was generating would have been ignored. Now the three processes are separate functions and hopefully the bug is fixed.

I continued the simplification of the updating the positioning of the simulation robot that was started last week. This involved getting the removing intermediary programs between the simulation and an operator program, and making the simulation accept the input commands that the intermediary programs translated into joint angles for the robot. <br>
The simulation is working correctly when getting joint angles but when giving a pose it has different results than before due to the different reference points of the robot software that was previously calculating inverse kinematics and the simulation. One of the problems I was getting had to deal with the orientation of the robot pose. I was assuming the rotation vector for the end effector was in Euler Angles but it was actually an Axis-Angle. <br>
The process of getting inverse kinematics working as expected is still ongoing though.


## References

### Mathematics
- [Euler Angles](https://en.wikipedia.org/wiki/Euler_angles)
- [Axis-Angle](https://en.wikipedia.org/wiki/Axis–angle_representation)
- [Quaternion](https://en.wikipedia.org/wiki/Quaternion)
