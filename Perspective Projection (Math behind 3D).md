---
date: 2025-05-13T19:04
tags: 
link: https://youtu.be/U0_ONQQ5ZNM?si=fJffK6F0MiUyywJW
---

Like in real life the observing a object is the light bounce to the object and then hit the eyes.. so to generate an image it's the opposite of that -> if you shot a ray from your eyes hit a color through a window what the color you hit is the pixel of that 2D image and that's how 3D graphic works.. 
![[1-Perspective Projection (Math behind 3D).png]]

The above method where ray are project and collide for that pixel is what ray-tracing is... ray-tracing is an image-order rendering..\
the alternative is an object order rendering which is must faster and efficient then he CPU ray-tracing..
Also we can find the project of every pixel position within the vertex by calculating line-plane intersection....
but a must better way to do that is the matrix transformation ...

### <code style = "color:purple">Orthographic Projection</code>
It is a generalization of the view volume [[Vulkan's Canonical View Volume]] that allows us to specify whatever dimension and whatever location we want, but maintains the overall shape of the volume and keeps the view direction and the orientation fixed.
![[2-Perspective Projection (Math behind 3D).png]]


The orthographic Projection is 6 bounded planes (right and left -> X-axis, the top and bottom -> Y-axis and the near and far ->Z-axis)...\


To construct the orthographic projection matrix we need to solve the problem to ***how to transform the orthographic view volume to Vulkan's Canonical View Volume***
![[3-Perspective Projection (Math behind 3D).png]]


So the numerator is the Canonical view volume and the denominator is the orthographic view volume.. ![[4-Perspective Projection (Math behind 3D).png]]

