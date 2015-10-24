
###Transformation

* Transformation apply to everything that follows

* Call glLoadIdentity() in display()

* Transformations are cumulative

* Primitive operations :

    glLoadIdentity();
    
    glTranslatef(dx , dy , dz) 
    
    glScalef(Sx , Sy , Sz)
    
    glRotatef(angle , Ux , Uy , Uz)


**glTranslate Example**

    void display()
    {
    //  Clear screen and Z-buffer
    glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
    //  Reset transformations
    glLoadIdentity();
    
    glBegin(GL_POLYGON);
    glColor3f(1.0,0.0,0.0); glVertex2f( -0.3, -0.3);
    glColor3f(0.0,1.0,0.0); glVertex2f( -0.3,0.3);
    glColor3f(0.0,0.0,1.0); glVertex2f( 0.3,0.3);
    glColor3f(0.0,0.0,0.0); glVertex2f( 0.3,-0.3);

    glEnd();

    glTranslatef(0.3 , 0.6, 0) ;
    
    glBegin(GL_POLYGON);
    glColor3f(1.0,0.0,0.0); glVertex2f( -0.5, -0.5);
    glColor3f(0.0,1.0,0.0); glVertex2f( -0.5,0.5);
    glColor3f(0.0,0.0,1.0); glVertex2f( 0.5,0.5);
    glColor3f(0.0,0.0,0.0); glVertex2f( 0.5,-0.5);
    
    glEnd();

    //  Flush and swap buffer
    glFlush();
    glutSwapBuffers();
    }
    
**output:**

![ ](https://cloud.githubusercontent.com/assets/14142983/10709305/c01d1568-79e4-11e5-84aa-74f12fa51a02.jpg)


**glScale & glRotatef Example**

    void display()
    {
    //  Clear screen and Z-buffer
    glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
    //  Reset transformations
    glLoadIdentity();
    
    glBegin(GL_TRIANGLES);
    glColor3f(0.0,0.0,1.0); glVertex2f( -0.3, 0.0);
    glColor3f(1.0,0.0,1.0); glVertex2f(  0.0,0.5);
    glColor3f(0.0,0.0,1.0); glVertex2f( 0.3,0.0);

    glEnd();

    glTranslatef(0.0 , -0.5, 0) ;
    glScalef(2 , 2, 0);
    glRotatef(50 , 1 , 1 , 0);
    
    glBegin(GL_POLYGON);
    glColor3f(0.0,0.0,1.0); glVertex2f( -0.3, 0.0);
    glColor3f(1.0,0.0,1.0); glVertex2f(  0.0,0.5);
    glColor3f(0.0,0.0,1.0); glVertex2f( 0.3,0.0);   glEnd();

    //  Flush and swap buffer
    glFlush();
    glutSwapBuffers();

    }
    
**output:**

![ ](https://cloud.githubusercontent.com/assets/14142983/10709333/3ee34164-79e6-11e5-8da9-031554ce5ddd.jpg)
