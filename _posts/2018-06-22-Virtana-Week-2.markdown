---
layout: post
title:  "Virtana Week 2"
date:   2018-06-22 -0400
categories: posts
---

This week at [Virtana](https://virtanatech.com/) has been spent attempting to build upon my work from [last week](/posts/2018/06/15/Virtana-Week-1.html). I have continued working with the camera APIs, been attempting to understand meshes, and started making meaningful contributions.

I had installed Blender to modify the meshes of the pybullet samples. I wanted to get the texture to appear on a single side of an object and not on each side of it. I had some partial success but using Blender wasn't the best as it would involve manually making meshes. To avoid that complexity, I searched for a Python library to generate the mesh and found OpenMesh. I tried to use OpenMesh to generate the mesh files to apply textures to, but this was unsuccessful and only produced poor results.

I added an end-effector camera to an existing simulation and sent the camera data to a remote viewer. It involved some refactoring of the existing code for an environment camera. I was originally just going to copy/paste it but it would have been too much trouble to sort out later if more cameras had to be added. The time was invested to refactor the code to work with the different cameras and their individual paramaters, so that there is not unnecessary work in the event more cameras need to be added. But the camera code was not without its challenges. I had encountered a strange error where data is only sending sometimes with sockets and other times it was timing out. <br>
Thanks to some work by my boss, we were able to successfully move from using pybullet camera APIs to generate the view matrix - which wasn't giving the best results anyway - to new generating it ourselves. This involved the use of the transformation matrix discussed last week. A transformation matrix had to generated to properly position the camera in front of the end effector and then another one had to be used to properly orient the camera's direction; along with some other mathematics to finally produce a correct view matrix.

I have finally moved from local files to the hosted repository. I need to get used to committing with git to a repository and then have the code reviewed on Gerrit, rather than using GitHub as a single service to handle the repository and the review. And with Gerrit, I have to either not make separate commits but rather amend to my previous commit or rebasing my commits to squash them into a single one to make a code review and pull request. <br>
I was also able to make a successful pull request even though I had to go through a few review steps due to my mistakes; and I had to review changes for a pull request.

## Reference Links
### Gerrit Code Review
- [Homepage](https://www.gerritcodereview.com/)
- [Wikipedia Page](https://en.wikipedia.org/wiki/Gerrit_(software))
