---
layout: post
title:  "Virtana Week 5"
date:   2018-07-13 -0400
categories: posts
---

This week at [Virtana](https://virtanatech.com/) has been spent attempting to build upon my work from [last week](/posts/2018/07/06/Virtana-Week-4.html). I have been working on textured boxes, adding a UVC camera to the simulation, and started working with WebRTC to send camera images.

I had to make textured boxes for the simulation from a set of images which involved joining images and making meshes. I had to join images together and determine the texture coordinates for them in the new image. This should have been easy as it was just to get the coordinates of each original image in the new image and divide by the size of the new image, but I was having trouble displaying the images correctly. The problem was that the image coordinates in numpy start from the the top as (0, 0) where as texture vertices start at the bottom with (0, 0). Once I realised this all I had to do was the reverse the order of the images when determining the texture coordinates. <br>
The next thing that caused me problems with making the box mesh was the ordering of the vertices when making the faces for the box. I knew that the order the vertices was specified for the texture was important but I didn't know how exactly it was supposed to be until I read up on the winding order of the vertices that make up the triangle. This determines which side of the triangle is visible. <br>

**Winding Order Example**:<br>
![Winding Order Example](/images/virtana_posts/Winding_Order.png){:height="100px" width="110px"} <br>
If I wanted the following triange to appear visible when looking at it fron the front, then I would have to specify the points in counter-clockwise order: 1-> 2 -> 3 <br>
If I wanted the following triange to appear visible when looking at it fron the  back, then I would have to specify the points in clockwise order: 1 -> 3 -> 2 <br>

A UVC (or USB Video Class) Camera had to be added to the simulation. For this camera, I had didn't have intrinsics for it so I had to make them up for now , and unlike the previous camera that I added doesn't send depth data. Also in the sending of the images to a remote viewer, I had to use OpenCV methods to convert the image from RGB to BGR and to encode the image as this is what the client was expecting.

**Colour Spaces Example**:<br>

|RGB Color Space| BGR Color Space|
|:---:|:---:|
|![Colour Space RGB](/images/virtana_posts/Colour_Spaces_RGB.png){:height="90px"}|![Colour Space BGR](/images/virtana_posts/Colour_Spaces_BGR.png){:height="90px"}|


Lastly, I have started working to output camera images and other data from the simualtion to be sent using WebRTC to a remote viewer.


## References
- [Face Culling](https://www.khronos.org/opengl/wiki/Face_Culling)
- [UVC](https://en.wikipedia.org/wiki/USB_video_device_class)

### OpenCV
- [Changing Colorspaces](https://docs.opencv.org/3.2.0/df/d9d/tutorial_py_colorspaces.html)
- [cvtColor](https://docs.opencv.org/3.4.1/d7/d1b/group__imgproc__misc.html#ga397ae87e1288a81d2363b61574eb8cab)
- [imencode](https://docs.opencv.org/3.4.1/d4/da8/group__imgcodecs.html#ga5a0acefe5cbe0a81e904e452ec7ca733)
