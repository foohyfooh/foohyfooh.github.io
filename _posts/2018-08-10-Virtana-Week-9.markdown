---
layout: post
title:  "Virtana Week 9"
date:   2018-08-10 -0400
categories: Virtana
---

This week at [Virtana](https://virtanatech.com/) has been spent attempting to build upon my work from [last week](/posts/2018/08/03/Virtana-Week-8.html). This week I completed what I started about 2 weeks ago and I have started working on outputting data to inform client programs of the positioning of the robot in the scene.

My changes from the last 2 weeks have been merged into master, and now the simulation can take commands directly to move it from a remote client.

I have moved the mathematics functions that we have accumulated in the simulation into a common file for all the scene components to use.

I have started outputting data for the system so that other programs in the system can understand where the different components in a scene are in relation to each other. This meant getting positions of objects relative to the robot and the cameras, and then outputting it into a file for later use. But my work for outputting the data has been scrapped due to how the implementation of the other programs interpret the ordering of the data. <br>
Since my previous work was scrapped, I am currently trying to run a script that should output the data in the correct format.
