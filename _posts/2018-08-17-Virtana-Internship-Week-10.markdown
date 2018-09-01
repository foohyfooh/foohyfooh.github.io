---
layout: post
title:  "Virtana Internship Week 10"
date:   2018-08-17 -0400
categories: Virtana
---

This week at [Virtana](https://virtanatech.com/) has been spent attempting to build upon my work from [last week](/posts/2018/08/10/Virtana-Internship-Week-9). This week has been spent getting the Unity simulation to feature parity with the pybullet simulation.

I started working on updating the calibration target to a new one, but we have discovered that our simulation is not rendering fast enough to produce good calibration results. Thus I have switch to working on the Unity simulation and I am outputting robot state and taking in commands in the Unity simulation so that web can control the simulated robot over WebRTC.
