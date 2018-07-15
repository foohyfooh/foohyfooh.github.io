---
layout: post
title:  "Virtana Week 3"
date:   2018-06-29 -0400
categories: posts
---

This week at [Virtana](https://virtanatech.com/) has been spent attempting to build upon my work from [last week](/posts/2018/06/22/Virtana-Week-2.html). I have started work on a calibration target, refactored the simulation class to make new simpler classes, and dealt with issues.

I have worked on adding a calibration target to a simulation. A calibration target is an image used to determine the intrinsics of the camera. I had originally been given an image and had to determine necessary values for it to calibrate the camera from it, but then was given the image that we were going to actually use. I then needed to generate a mesh for the target and then read in the image as a texture for it. Once that was successful, I had moved to generating the image myself. Then finally it was added to the overall simulation. <br>
![Asymmetric Circle Grid Calibration Target](/images/virtana_posts/Calibration_Target.jpg){:height="194px" width="150px"}

Once the calibration target was included, I had to refactor the simulation code. A refactor was needed since we were using the same pybullet client in multiple threads - which is wrong. This decision caused three refactors thus far.<br>
The first refactor was done to move the robot building and control logic out of the simulation and into its own class. This class was made to be responsible for the creation of its thread, its physics client, and the life cycle of these objects. <br>
Next was the refactor of the camera code. The camera class was made to handle the logic for a stationary and an attached camera.<br>
The last refactor was done to abstract the concept of scene. We needed the ability to switch out the scene for the simulation rather than have to copy over the whole simulation class to make a new scene. <br>
I have also been adding command line arguments so that it is easier to change parameters of the simulation such as the scene.

While making changes to the simulation code I have had some issues. For the first refactor that I did for this week, I had a merge  conflict because  I didn't pull the latest changes and this lead to a bit of a headache as I resolved it. This was troublesome but didn't cause any problems with the simulation. But I apparently introduced an error in my pull request that I mentioned last week. I accidentally called start on a thread again instead of join and this error wasn't noticed until I was doing the refactoring. <br>
I have also started trying to fix the generated calibration target to correct its look, but I have come across some issues with my understanding of mixing texture coordinates and object coordinates.

## Reference Links
- [Wavefront Geometry Format for 3D Models](https://en.wikipedia.org/wiki/Wavefront_.obj_file)

### OpenCV 2.4.13.6 Camera Calibration
- [Camera calibration With OpenCV](https://docs.opencv.org/2.4.13.6/doc/tutorials/calib3d/camera_calibration/camera_calibration.html)
- [calibrateCamera](https://docs.opencv.org/2.4.13.6/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#calibratecamera)

### OpenCV 3.4.1 Camera Calibration
- [Camera Calibration](https://docs.opencv.org/3.4.1/dc/dbb/tutorial_py_calibration.html)
