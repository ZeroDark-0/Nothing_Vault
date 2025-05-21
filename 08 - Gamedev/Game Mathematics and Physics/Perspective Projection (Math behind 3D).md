---
date: 2025-05-13T19:04
tags: 
link: https://youtu.be/U0_ONQQ5ZNM?si=fJffK6F0MiUyywJW
share_link: https://share.note.sx/jzht20b1#HalgUl+OxlriBg1YFWkZKYivuYobSwZL+srD4dw8Rio
share_updated: 2025-05-20T15:49:56+08:00
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


So the numerator is the Canonical view volume and the denominator is the orthographic view volume.. \ ![[4-Perspective Projection (Math behind 3D).png]]


By applying this method -> the object within the reason occupied by orthographic view volume will be scaled and view in canonical view volume.. 

But the orthographic view volume doesn't apply perspective and so do that we require a viewing volume like a square frustum..

![[5-Perspective Projection (Math behind 3D).png]]

![[6-Perspective Projection (Math behind 3D).png]]

To do this we have to get a 4X4 Matrix for the preceptive matrix. (Ax=B) but the thing arise that the product of the **<code style = "color:red">Ax</code>** matrix have a division by a Z component in X and Y components...  ![[7-Perspective Projection (Math behind 3D).png]]
For that-> we use..\

## <code style = "color:yellow">Homogeneous Vector</code>
![[8-Perspective Projection (Math behind 3D).png]]

We use the "W" as a forth component which set that -> W is always equals to one..
and initially define the "W" as the denominator of X,Y and Z component..\

### Construction of Perspective Transformation

From the knowledge, we can make a perspective transformation matrix-> in which the first two row have the distance of the viewing plane on the main diagonal and zero elsewhere...
the final row will be [0,0,1,0]  to take the Z component from the input vector and move it top the w component of the solution vector...

and the remaining is the third row -> remember that every component is divided by the w component.. meaning "Z" over "Z" is just one and now we lost our depth component..![[9-Perspective Projection (Math behind 3D).png]]

So to do that we can have Z * Z in the final matrix cuz z * z is z itself ..
meaning we got only 2 unknown component for the perspective matrix..
![[10-Perspective Projection (Math behind 3D).png]]
![[11-Perspective Projection (Math behind 3D).png]]

putting this in the z component making Z^2 = ![[12-Perspective Projection (Math behind 3D).png]]

meaning ->
![[13-Perspective Projection (Math behind 3D).png]]

![[14-Perspective Projection (Math behind 3D).png]]

