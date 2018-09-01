---
layout: post
title:  "Virtana Internship Week 4"
date:   2018-07-06 -0400
categories: Virtana
---

This week at [Virtana](https://virtanatech.com/) has been spent attempting to build upon my work from [last week](/posts/2018/06/29/Virtana-Internship-Week-3). I have updated my calibration target code, added the initial work for a new scene to the simulation, and made a tool to do a perspective warp for images.

My calibration target was a bit off so it had to be updated. I had to go over the mathematics for coordinate vertices and texture vertices.

I have been working on adding a new scene to the simulation. At first, I was creating collision and visual shapes, and then making individual pybullet multibodies for each part of an object. This meant that after I created the multibodies I had to join then by constraints. I had successfully joined the tables but this apparently wasn't the best way to do things. I didn't realise that the function to create multibodies had parameters for links until my boss pointed it out to me. This meant that I could create the whole object as a single multibody and not have to fiddle around with constraints. This gave better results for my objects.

The last thing I did this week was create a tool to do a perspective warp on images. I originally had tried to determine the bounds of the images and do the perspective warp on that using OpenCV methods but this didn't work out. I moved on to just determining the points myself and just passing that the OpenCV perspective transform method. <br>
Once I made finished the tool, I had to look at a bunch of images and record the points of the main focus of the image to feed into my tool.

## Reference Links
- [Wavefront Geometry Format for 3D Models](https://en.wikipedia.org/wiki/Wavefront_.obj_file)

### OpenCV Methods
- [findContours](https://docs.opencv.org/3.4.1/d3/dc0/group__imgproc__shape.html#ga95f5b48d01abc7c2e0732db24689837b)
- [getPerspectiveTransform](https://docs.opencv.org/3.4.1/da/d54/group__imgproc__transform.html#ga8c1ae0e3589a9d77fffc962c49b22043)
- [warpPerspective](https://docs.opencv.org/3.4.1/da/d54/group__imgproc__transform.html#gaf73673a7e8e18ec6963e3774e6a94b87)

### PyImageSearch Tutorials
- [Perspective Transform](https://www.pyimagesearch.com/2014/08/25/4-point-opencv-getperspective-transform-example/)
- [Finding Shapes](https://www.pyimagesearch.com/2014/10/20/finding-shapes-images-using-python-opencv/)
