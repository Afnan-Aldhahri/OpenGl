
### Text 

OpenGL provides only hooks for fonts

*Stroked fonts*

Lines and fills write the characters 

*Bitmap (raster) fonts*

Characters are raster images

Orientation, size, etc. treated just like any other drawing elements

#####Text using GLUT

    glutBitmapCharacter(GLUT_FONTTYPE,ch)

Single charcter

Limited font selection

    glRasterPos3d(x,y,z)

Sets position to write text in (x,y,z) coordinates

    glWindowPos2i(x,y)

Sets position to write text in pixels coordinates


**Example**
    
    

    #define LEN 8192  //  Maximum amount of text
    void Print(const char* format , ...)
    {
    char    buf[LEN]; // Text storage
    char*   ch=buf;   // Text pointer
    //  Create text to be display
    va_list args;
    va_start(args,format);
    vsnprintf(buf,LEN,format,args);
    va_end(args);
    //  Display text string
    while (*ch)
        glutBitmapCharacter(GLUT_BITMAP_HELVETICA_18,*ch++);
   }

    
    void display()
    {
    //  Clear screen and Z-buffer
    glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
    
    //  Display rotation angle
    glColor3f(1,1,1);
    glWindowPos2i(5,5);
    Print("Hello there ..Here is the text that we print");
  
    //  Flush and swap buffer
    glFlush();
    glutSwapBuffers();

    }

**output**

![ ] (https://cloud.githubusercontent.com/assets/14142983/10709392/82b088fe-79e9-11e5-9a7c-5be14b728e36.jpg)

