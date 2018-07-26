---
layout: post
title:  "Virtana Week 6"
date:   2018-07-20 -0400
categories: posts
---

This week at [Virtana](https://virtanatech.com/) has been spent attempting to build upon my work from [last week](/posts/2018/07/13/Virtana-Week-5.html). My week was spent finishing the WebRTC additions that I had started last week, working on simplifying the communication process to update robot joints and attempting to fix a bug in the simulation output for WebRTC.

I finished the WebRTC stuff that I had started last week. Now all the cameras in the simulation should be able to send data to a remote viewer using WebRTC.

For most of this week I have been trying to simplify communication between a user and the simulation robot. This is has not gone the best as I am not understanding the data flow for the system and I have temporarily moved onto fixing a bug.

I have moved to fixing a bug in the simulation output that is being used by WebRTC. It involved adding a lock to the the output statement so that multiple camera don't output data at the same time thus causing malformed data to be output.
