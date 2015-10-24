##Drawing in 3D

Now , lets move to drawing in 3d. 

lets see how to draw the same house that we draw in the previouse example , but this time in 3 dimentional.

**Example**

The display function will stay the same ,but we will change the house() function

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
    // Front
    glVertex3f( -1,  0,  1 );
    glVertex3f( -1,  2,  1 );
    glVertex3f(  1,  2,  1 );
    glVertex3f(  1,  0,  1 );
    
    // Back
    glVertex3f( -1,  0, -1 );
    glVertex3f( -1,  2, -1 );
    glVertex3f(  1,  2, -1 );
    glVertex3f(  1,  0, -1 );
    
    // Left side
    glVertex3f( -1,  0,  1 );
    glVertex3f( -1,  2,  1 );
    glVertex3f( -1,  2, -1 );
    glVertex3f( -1,  0, -1 );
    
    // Right side
    glVertex3f(  1,  0,  1 );
    glVertex3f(  1,  0, -1 );
    glVertex3f(  1,  2, -1 );
    glVertex3f(  1,  2,  1 );
    
    //Bottom
    glVertex3f(  -1,  0,  1 );
    glVertex3f(  -1,  0, -1 );
    glVertex3f(  1, 0, -1 );
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
    
    // Front
    glVertex3f( -1,  2,  1 );
    glVertex3f(  0,  4,  0 );
    glVertex3f(  1,  2,  1 );
    
    // Right side
    glVertex3f(  1,  2,  1 );
    glVertex3f(  1,  2, -1 );
    glVertex3f(  0,  4,  0 );
    
    // Back
    glVertex3f(  1,  2, -1 );
    glVertex3f( -1,  2, -1 );
    glVertex3f(  0,  4,  0 );
    
    // Left side
    glVertex3f( -1,  2,  1 );
    glVertex3f(  0,  4,  0 );
    glVertex3f( -1,  2, -1 );
    glEnd();
    
    //  Undo transformations
    glPopMatrix();
    
    }



**output**

![ ] (https://cloud.githubusercontent.com/assets/14142983/10709856/91f9ae7e-79fa-11e5-890f-a0b1682a966b.jpg)
