---
layout: post
title:  "Virtana Week 3"
date:   2018-06-29 -0400
categories: posts
---

This week at [Virtana](https://virtanatech.com/) has been spent attempting to build my work from [last week](/posts/2018/06/22/Virtana-Week-2.html). I have started work on a calibration target, refactored the simulation class to make new simpler classes, and dealt with issues.

I have worked on adding a calibration target to a simulation. A calibration target is an image used to determine the intrinsics of the camera. I had originally been given an image and had to determine necessary values for it to calibrate the camera, but then was given the image that was actually going to be used. I then needed to generate a mesh for the target and then read in the image as a texture for it. Once that was successful, I had moved to generating the image myself. Then finally it was added to the overall simulation.

Once the calibration target was included, I had to refactor the simulation code. A refactor was needed since we were using the same pybullet client in multiple threads - which is wrong. This decision caused three refactors thus far.<br>
The first refactor was done to move the robot building and control logic out of the simulation and into its own class. This class was made to be responsible for the creation of its thread, its physics client, and the life cycle of these objects. <br>
Next was the refactor of the camera code. The camera class was made to handle the logic for a stationary and an attached camera.<br>
The last refactor was done to abstract the concept of scene. We needed the ability to switch out the scene for the simulation rather than have to copy over the whole simulation class to make a new scene. <br>
I have also been adding command line arguments so that it is easier to change paramaters of the simulation such as the scene.

While making changes to the simulation code I have had some issues. For the first refactor that I did for this week, I had a merge  conflict because  I didn't pull the latest changes and this lead to a bit of a headache as I resolved it. This was troublesome but didn't cause any problems with the simulation. But I apparently introduced an error in my pull request that I mentioned last week. I accidentally called start on a thread again instead of join and this error wasn't noticed until I was doing the refactoring.
