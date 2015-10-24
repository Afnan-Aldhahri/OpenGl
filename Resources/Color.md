
### Color 

Default is RGB color (Red Green Blue)

R,G,B 0-1 or integer range

● glColor3f(1.0 , 0.0 .0.0); 

● glColor3b(127 , 0 , 0);

● glColor3ub(255 , 0 , 0); 

● glColor3fv(rgbarray);

Color can also contain transparency (alpha)

glColor4f(1.0 , 0.0 . 0.0 , 0.5);

Default alpha=1 (opaque)

lets see some examples :

**Example**
    
    void display()
    {
    //  Clear screen and Z-buffer
    glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
    //  Reset transformations
    glLoadIdentity();
    glBegin(GL_POLYGON);
    glColor3f(1.0,1.0,0.0); glVertex2f( -0.5, -0.5);
    glColor3f(1.0,0.0,1.0); glVertex2f( -0.5,0.5);
    glColor3f(1.0,0.0,1.0); glVertex2f( 0.5,0.5);
    glColor3f(0.0,1.0,1.0); glVertex2f( 0.5,-0.5);
    glEnd();
    //  Flush and swap buffer
    glFlush();
    glutSwapBuffers();
    }

**output**

![ ] (https://cloud.githubusercontent.com/assets/14142983/10709230/d772611c-79e1-11e5-8688-a283da3165d0.jpg)

As you can see , we are seeing these beautiful colors got mixed togother because we are using different color for each vertex in the polygon .
