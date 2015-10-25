
##Drawing in 2D

Now , lets see how to draw a 2d scene by combining the objects that we have just cover .

**Example**
    
    void display()
    {
    //  Erase the window and the depth buffer
    glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
    //  Enable Z-buffering in OpenGL
    glEnable(GL_DEPTH_TEST);
    //  Undo previous transformations
    glLoadIdentity();
    
    
    //  Undo previous transformations
    glLoadIdentity();
    
    //  Orthogonal - set world orientation
    
    glRotatef(ph,1,0,0);
    glRotatef(th,0,1,0);
    
    // draw the house
    house(0,-1,0 , 0.6,0.6,0.6 , 0,1);
    
  
    //  Five pixels from the lower left corner of the window
    glWindowPos2i(5,5);
    //  Print the text string
    Print("Angle=%d,%d",th,ph);
    //  Render the scene
    glFlush();
    //  Make the rendered scene visible

    }


This was the display function, and as you can see ,the only thing new here is the **house function**.

In house() function , we will draw a **2d house** by using combination of *Polygons*.

static void house(double x,double y,double z,
                  double dx,double dy,double dz,
                  double th,int color)
    {
    
    //  Save transformation
    glPushMatrix();
    //  Offset
    glTranslated(x,y,z);
    glRotated(th,0,1,0);
    glScaled(dx,dy,dz);
    
    //  structure of the house
    glBegin(GL_QUADS);
    glVertex3f( -1,  0,  1 );
    glVertex3f( -1,  2,  1 );
    glVertex3f(  1,  2,  1 );
    glVertex3f(  1,  0,  1 );
    
    
    glEnd();
    
    
    //Now the window
    // left Window
    
    glBegin(GL_QUADS);
    
    glColor3f( 0.72 , 0.45 , 0.20);
    glVertex3f( -0.8,  1,  1.01 );
    glVertex3f( -0.8,  1.5,  1.01 );
    glVertex3f(  -0.4,  1.5,  1.01 );
    glVertex3f(  -0.4,  1,  1.01 );
    glEnd();
    
    glBegin(GL_LINES);
    glColor3f( 0, 0, 0 );
    glVertex3f( -0.81,  1.01,  1.02 );
    glVertex3f( -0.81,  1.51,  1.02 );
    
    glVertex3f( -0.81,  1.51,  1.02 );
    glVertex3f(  -0.41,  1.51,  1.02 );
    
    glVertex3f(  -0.41,  1.51,  1.02 );
    glVertex3f(  -0.41,  1.01,  1.02 );
    
    glVertex3f(  -0.41,  1.01,  1.02 );
    glVertex3f( -0.81,  1.01,  1.02 );
    
    glVertex3f( -0.81,  1.51,  1.02 );
    glVertex3f(  -0.41,  1.01,  1.02 );
    
    glVertex3f(  -0.41,  1.51,  1.02 );
    glVertex3f( -0.81,  1.01,  1.02 );
    
    glEnd();
    
    // right window
    glPushMatrix();
    glTranslated(1,0,0);
    
    glBegin(GL_QUADS);
    glColor3f( 0.72 , 0.45 , 0.20 );
    glVertex3f( -0.8,  1,  1.01 );
    glVertex3f( -0.8,  1.5,  1.01 );
    glVertex3f(  -0.4,  1.5,  1.01 );
    glVertex3f(  -0.4,  1,  1.01 );
    
    glEnd();
    
    glBegin(GL_LINES);
    glColor3f( 0, 0, 0 );
    glVertex3f( -0.81,  1.01,  1.02 );
    glVertex3f( -0.81,  1.51,  1.02 );
    
    glVertex3f( -0.81,  1.51,  1.02 );
    glVertex3f(  -0.41,  1.51,  1.02 );
    
    glVertex3f(  -0.41,  1.51,  1.02 );
    glVertex3f(  -0.41,  1.01,  1.02 );
    
    glVertex3f(  -0.41,  1.01,  1.02 );
    glVertex3f( -0.81,  1.01,  1.02 );
    
    glVertex3f( -0.81,  1.51,  1.02 );
    glVertex3f(  -0.41,  1.01,  1.02 );
    
    glVertex3f(  -0.41,  1.51,  1.02 );
    glVertex3f( -0.81,  1.01,  1.02 );
    
    glEnd();
    glPopMatrix();
    
    
    //Now the door
    glBegin(GL_QUADS);
    glColor3f( 0.80 , 0.81 , 0.10 );
    glVertex3f( -0.3,  0,  1.01 );
    glVertex3f( -0.3,  0.8,  1.01 );
    glVertex3f(  0.3,  0.8,  1.01 );
    glVertex3f(  0.3,  0,  1.01 );
    glEnd();
    
    glBegin(GL_QUADS);
    glColor3f( 0, 0, 0 );
    glVertex3f( 0.23,  0.4,  1.02 );
    glVertex3f( 0.23,  0.44,  1.02 );
    glVertex3f( 0.37,  0.44,  1.02 );
    glVertex3f( 0.37,  0.4,  1.02 );
    glEnd();
    
    
    // Now the roof
    glBegin(GL_TRIANGLES);
    glVertex3f( -1,  2,  1 );
    glVertex3f(  -1,  4,  1);
    glVertex3f(  1,  2,  1 );
    

    glEnd();
    
    //  Undo transformations
    glPopMatrix();
    
    }
  
**output**

![ ] (https://cloud.githubusercontent.com/assets/14142983/10709851/89fc3e6c-79fa-11e5-86f2-388c063aff80.jpg)

[Home] (https://github.com/Afnan-Aldhahri/OpenGl/blob/master/README.md)
