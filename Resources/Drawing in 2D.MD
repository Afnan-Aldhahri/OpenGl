
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

This was the display function, and as you can see ,the only thing new here is the house function.

In house() function , we will draw a 2d house by using combination of Polygons.

  
**output**

![ ] (https://cloud.githubusercontent.com/assets/14142983/10709230/d772611c-79e1-11e5-8688-a283da3165d0.jpg)
