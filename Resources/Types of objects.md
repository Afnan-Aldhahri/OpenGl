##Types of objects



####Points

    glBegin(type) 

    GL_POINTS points
    
Points are represented by a single vertex. 

The vertex represents a point in four-dimensional homogeneous coordinates.

OpenGL determines which pixels are covered by the point using a set of rules called rasterization rules.

The default point size is 1.0. 

So, when points are rendered, each vertex  becomes a single pixel on the screen. 

    void glPointSize(GLfloat size);
    
Sets the fixed size, in pixels, that will be used for points when
GL_PROGRAM_POINT_SIZE is not enabled.


    
####Point Sprites

When you render points with OpenGL, the fragment shader is run for every fragment in the point.

Each point is essentially a square area of the screen and each pixel can be shaded a different color.

 OpenGL fragment shaders include a special built-in variable called gl_PointCoord which contains the coordinate within the point where the current fragment is located. 

####Lines, Strips, and Loops

    GL_LINES lines between pairs of points
    GL_LINE_STRIP series of line segments
    GL_LINE_LOOP closed GL_LINE_STRIP


Individual lines are  represented by pairs of vertices, one for each endpoint of the line.

The closed sequence is known as a line loop, whereas the open sequence (one that is not closed) is known
as a line strip.

lines  have no area, and so special rasterization rules are used to control and specify which pixels should be lit when a line segment is rasterized.

OpenGL allows you to specify wider sizes for lines using the glLineWidth() function (the equivalent for glPointSize() for lines).

    void glLineWidth(GLfloat width);
Sets the fixed width of lines. The default value is 1.0. width is the new value of line width and must be greater than 0.0, 

otherwise an error is generated.

**Example**

    void display()
    {
    //  Clear screen and Z-buffer
    glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
    //  Reset transformations
    glLoadIdentity();
    //  green lines
    glBegin(GL_LINE_STRIP);
    glColor3f(0.0,1.0,0.0); glVertex2f( 0.0, 0.5);
    glColor3f(0.0,1.0,0.0); glVertex2f( 0.5,-0.5);
    glColor3f(0.0,1.0,0.0); glVertex2f(-0.5,-0.5);
    glEnd();
    //  Flush and swap buffer
    glFlush();
    glutSwapBuffers();
    }

**output:**

![](https://cloud.githubusercontent.com/assets/14142983/10709108/332b1f5c-79de-11e5-817f-16aaa6617e4f.jpg)
-----------------------------------------------------------------------------------------------------------------------------

#### Triangles, Strips, and Fans

    GL_TRIANGLES triangles between triples of points
    GL_TRIANGLE_STRIP series of triangles GL_TRIANGLE_FAN fan of triangles

Triangles are made up of collections of three vertices. 

A triangle is rendered by projecting each of the three vertices into screen space and forming three edges running between the edges.


If two triangles share an edge (and therefore a pair of vertices), no single sample can be considered inside both triangles. 

 the rules control pixels that set on a shared edge are :
 
• No pixel on a shared edge between two triangles that together would cover the pixel should be left unlit.
• No pixel on a shared edge between two triangles should be lit by more than one of them.




####Rendering Polygons As Points, Outlines, or Solids

    GL_POLYGON simple polygon

A polygon has two sides---front and back---.

They could  be rendered in defferent ways according to  which side is facing the viewer. 

This let you  have cutaway views of solid objects in which there is an obvious distinction between the parts that are inside and those that are outside. 

So, both front and back faces are drawn in the same way by default. 

if you want to change this, or to draw only outlines or vertices, use glPolygonMode().

    ￼void glPolygonMode(GLenum face, GLenum mode);
Controls the drawing mode for a polygon’s front and back faces. 



**Example**

    void display()
    {
    //  Clear screen and Z-buffer
    glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
    //  Reset transformations
    glLoadIdentity();
    
    //  Red triangle
    glBegin(GL_TRIANGLES);
    glColor3f(1.0,0.0,0.0); glVertex2f( 0.0, 0.5);
    glColor3f(1.0,0.0,0.0); glVertex2f( 0.5,-0.5);
    glColor3f(1.0,0.0,0.0); glVertex2f(-0.5,-0.5);
    glEnd();
    
    //  Flush and swap buffer
    glFlush();
    glutSwapBuffers();
    }
    
**output:**

![ ](https://cloud.githubusercontent.com/assets/14142983/10709166/5a4fc6cc-79df-11e5-81ef-f58d366cd4dc.jpg)


**Example**

    void display()
    {
    //  Clear screen and Z-buffer
    glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
    //  Reset transformations
    glLoadIdentity();
    
    //  blue squre
    glBegin(GL_TRIANGLES);
    glColor3f(1.0,0.0,0.0); glVertex2f( 0.0, 0.5);
    glColor3f(1.0,0.0,0.0); glVertex2f( 0.5,-0.5);
    glColor3f(1.0,0.0,0.0); glVertex2f(-0.5,-0.5);
    glEnd();
    
    //  Flush and swap buffer
    glFlush();
    glutSwapBuffers();
    }
    
**output:**

![ ](https://cloud.githubusercontent.com/assets/14142983/10709210/fe15c9a4-79e0-11e5-9f2f-c4a59145b717.jpg)


[Home] (https://github.com/Afnan-Aldhahri/OpenGl/blob/master/README.md)
