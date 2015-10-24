##Types of objects



####Points

    glBegin(type) 

    GL_POINTS points
    
Points are represented by a single vertex. 

The vertex represents a point in four-dimensional homogeneous coordinates.

When rendering points, OpenGL determines which pixels are covered by the point using a set of rules called rasterization rules.

The default point size is 1.0. 

Thus, when points are rendered, each vertex essentially becomes a single pixel on the screen (unless it’s clipped, of course). 

    void glPointSize(GLfloat size);
    
Sets the fixed size, in pixels, that will be used for points when
GL_PROGRAM_POINT_SIZE is not enabled.


    
####Point Sprites
When you render points with OpenGL, the fragment shader is run for every fragment in the point.

Each point is essentially a square area of the screen and each pixel can be shaded a different color.

You can calculate that color analytically in the fragment shader or use a texture to shade the point. 

To assist in this, OpenGL fragment shaders include a special built-in variable called gl_PointCoord which contains the coordinate within the point where the current fragment is located. 

####Lines, Strips, and Loops

    GL_LINES lines between pairs of points
    GL_LINE_STRIP series of line segments
    GL_LINE_LOOP closed GL_LINE_STRIP

In OpenGL, the term line refers to a line segment, not the mathematician’s version that extends to infinity in both directions.

Individual lines are therefore represented by pairs of vertices, one for each endpoint of the line.

Lines can also be joined together to represent a connected series of line segments, and optionally closed. 

The closed sequence is known as a line loop, whereas the open sequence (one that is not closed) is known
as a line strip.

As with points, lines technically have no area, and so special rasterization rules are used to determine which pixels should be lit when a line segment is rasterized.

The rule for line rasterization is known as the diamond exit rule. It is covered in some detail in the OpenGL specification.

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
    //  Red triangle
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

When separate triangles are rendered, each triangle is independent of all others.

A triangle is rendered by projecting each of the three vertices into screen space and forming three edges running between the edges.

A sample is considered covered if it lies on the positive side of all of the half spaces formed by the lines between the vertices. 

If two triangles share an edge (and therefore a pair of vertices), no single sample can be considered inside both triangles. 

This is important because, although some variation in rasterization algorithm is allowed by the OpenGL specification, the rules governing pixels that lie along a shared edge are quite strict:
• No pixel on a shared edge between two triangles that together would cover the pixel should be left unlit.
• No pixel on a shared edge between two triangles should be lit by more than one of them.
This means that OpenGL will reliably rasterize meshes with shared edges without gaps between the triangles, and without overdraw.2 This is important when rasterizing triangle strips or fans.

When a triangle strip is rendered, the first three vertices form the first triangle, then each subsequent vertex forms another triangle along with the last two vertices of the previous triangle.

When rendering a triangle fan, the first vertex forms a shared point that is
included in each subsequent triangle. Triangles are then formed using that



####Rendering Polygons As Points, Outlines, or Solids

    GL_POLYGON simple polygon

A polygon has two sides---front and back---and might be rendered differently depending on which side is facing the viewer. 

This allows you to have cutaway views of solid objects in which there is an obvious distinction between the parts that are inside and those that are outside. 

By default, both front and back faces are drawn in the same way. To change this, or to draw only outlines or vertices, use glPolygonMode().

    ￼void glPolygonMode(GLenum face, GLenum mode);
Controls the drawing mode for a polygon’s front and back faces. 

The parameter face must be GL_FRONT_AND_BACK; while mode can be GL_POINT, GL_LINE, GL_FILL to indicate whether the polygon should be drawn as points, outlined, or filled. 

By default, both the front and back faces are drawn filled.

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

![ ](https://cloud.githubusercontent.com/assets/14142983/10709210/fe15c9a4-79e0-11e5-9f2f-c4a59145b717.jpg)
