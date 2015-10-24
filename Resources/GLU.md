
##GLU: OpenGL Utility

According to [opengl.org] (https://www.opengl.org) ,"

If you think of OpenGL as a low-level 3D graphics library, think of GLU as adding some higher-level functionality not provided by OpenGL. 

**Some of GLU's features include:**

* Scaling of 2D images and creation of mipmap pyramids
* Transformation of object coordinates into device coordinates and vice versa
* Support for NURBS surfaces
* Support for tessellation of concave or bow tie polygonal primitives
* Specialty transformation matrices for creating perspective and orthographic projections, positioning a camera, and selection/picking
* Rendering of disk, cylinder, and sphere primitives
* Interpreting OpenGL error values as ASCII text

GLU provides tessellation routines to let you render concave polygons, self-intersecting polygons, and polygons with holes. 

The tessellation routines break these complex primitives up into (possibly groups of) simpler, convex primitives that can be rendered by the OpenGL API. 

This is done by providing the data of the simpler primitives to your application from callback routines that your application must provide.

Your app can then send the data to OpenGL using normal API calls."


[Home] (https://github.com/Afnan-Aldhahri/OpenGl/blob/master/README.md)
