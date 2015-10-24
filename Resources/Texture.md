##Texture

####What are texture maps?

Texture maps used to make surfaces appear more realistic.

They are simple in concept, but hardware intensive.

--------------------------------

####OpenGL Texture Types

1D, 2D and 3D textures.

2D textures most commonly used

OpenGL Texture Calls 

    glGenTextures
    
Returns unused texture name(s)

    glBindTexture
    
Sets the active (current) texture

    glTexImage*
    
Copies image to texture memory 

    glTexCoord*
    
Sets texture coordinates for vertex 

    glTexEnv*, glTexParameter*
    
Control application of textures

--------------------------------


#####Creating a Texture 

    glGenTextures(1,&texname);
    
Returns unique texture name

    glBindTexture(GL_TEXTURE_2D,texname);
    
First use – allocates memory and makes current

    glTexImage2D(GL_TEXTURE_2D,0,3,dx,dy, 0,GL_RGB,GL_UNSIGNED_BYTE,image);
    
Copies RGB image to texture memory (size dx xdy) 

Finally,lets see an example :

**Example**
   
   we will add a texture for the same 3d house that we draw before 
In display function( ) : 

 We have to add texture for the **base of the house **:

    //  Enable textures
    glEnable(GL_TEXTURE_2D);
    glTexEnvi(GL_TEXTURE_ENV,GL_TEXTURE_ENV_MODE,GL_MODULATE);
    glColor3f(1,1,1);
    glBindTexture(GL_TEXTURE_2D,texture[0]);
    
    //  structure of the house
    glBegin(GL_QUADS);
    // Front
    // glColor3f( 0.647059 , 0.164706 , 0.164706);
    glColor3f(1,1,1);

    glNormal3f( 0, 0, 1);
    
    glTexCoord2f(0,0); glVertex3f( -1,  0,  1 );
    glTexCoord2f(1,0); glVertex3f( -1,  2,  1 );
    glTexCoord2f(1,1); glVertex3f(  1,  2,  1 );
    glTexCoord2f(0,1);  glVertex3f(  1,  0,  1 );
    
    // Back
    // glColor3f( 0.36 , 0.25 , 0.20 );

    glNormal3f( 0, 0,-1);
    
    glTexCoord2f(0,0);  glVertex3f( -1,  0, -1 );
    glTexCoord2f(1,0);  glVertex3f( -1,  2, -1 );
    glTexCoord2f(1,1);  glVertex3f(  1,  2, -1 );
    glTexCoord2f(0,1);  glVertex3f(  1,  0, -1 );
    
    // Left side
    // glColor3f( 0.35 , 0.16 , 0.14 );
    glNormal3f(-1, 0, 0);
    
    glTexCoord2f(0,0); glVertex3f( -1,  0,  1 );
    glTexCoord2f(1,0);glVertex3f( -1,  2,  1 );
    glTexCoord2f(1,1);  glVertex3f( -1,  2, -1 );
    glTexCoord2f(0,1); glVertex3f( -1,  0, -1 );
    
    // Right side
    glNormal3f(+1, 0, 0);
  
    glTexCoord2f(0,1); glVertex3f(  1,  0,  1 );
    glTexCoord2f(0,0); glVertex3f(  1,  0, -1 );
     glTexCoord2f(1,0); glVertex3f(  1,  2, -1 );
     glTexCoord2f(1,1); glVertex3f(  1,  2,  1 );
  
    
    //Bottom
    glNormal3f( 0,-1, 0);
    
    glTexCoord2f(0,0);  glVertex3f(  -1,  0,  1 );
    glTexCoord2f(1,0); glVertex3f(  -1,  0, -1 );
    glTexCoord2f(1,1);   glVertex3f(  1, 0, -1 );
    glTexCoord2f(0,1);  glVertex3f(  1,  0,  1 );
    glEnd();
    
    glDisable(GL_TEXTURE_2D);
 
 Now, we have to add different texture for the **roof of the house **:

      
    // Now the roof
    //  Enable textures
    glEnable(GL_TEXTURE_2D);
    glTexEnvi(GL_TEXTURE_ENV,GL_TEXTURE_ENV_MODE,GL_MODULATE);
    glColor3f(1,1,1);
    glBindTexture(GL_TEXTURE_2D,texture[1]);
    glBegin(GL_TRIANGLES);
    // Front
    glColor3f( 0.91 , 0.76 , 0.65 );
    glNormal3f( 0, 0, 1);
    
    glTexCoord2f(0.0  ,0.0); glVertex3f( -1,  2,  1 );
    glTexCoord2f(1.0  ,0.0); glVertex3f(  1,  2,  1 );
    glTexCoord2f(1/2,1); glVertex3f(  0,  4,  0 );
    
    // Right side
    glColor3f( 0.65 , 0.50 , 0.39 );
    glNormal3f(+1, 0, 0);
    
    glTexCoord2f(0.0  ,0.0); glVertex3f(  1,  2,  1 );
    glTexCoord2f(1.0  ,0.0); glVertex3f(  1,  2, -1 );
    glTexCoord2f(1/2,1);  glVertex3f(  0,  4,  0 );
    // Back
    glColor3f( 0.52 , 0.37 , 0.26 );
    glNormal3f( 0, 0,-1);
    
    glTexCoord2f(0.0  ,0.0);glVertex3f(  1,  2, -1 );
    glTexCoord2f(1.0  ,0.0);glVertex3f( -1,  2, -1 );
    glTexCoord2f(1/2,1);  glVertex3f(  0,  4,  0 );
    // Left side
    glColor3f( 0.42, 0.24, 0.13 );
    glNormal3f(-1, 0, 0);
    
    glTexCoord2f(0.0  ,0.0); glVertex3f( -1,  2,  1 );
    
    glTexCoord2f(1/2,1); glVertex3f(  0,  4,  0 );
    glTexCoord2f(1.0  ,0.0); glVertex3f( -1,  2, -1 );
    glEnd();
    glDisable(GL_TEXTURE_2D);

    //  Undo transformations
    glPopMatrix();
    
 and we will do the samething with the** door , windows and the floor **.
 
 Finally ,We need to **upload these textures** in the main function :
 
    int main(int argc,char* argv[])
    {
    //  Initialize GLUT
    glutInit(&argc,argv);
    //  Request double buffered, true color window with Z buffering at 600x600
    glutInitDisplayMode(GLUT_RGB | GLUT_DEPTH | GLUT_DOUBLE);
    glutInitWindowSize(900,550);
    glutCreateWindow("Afnan Aldhahri");
    //  Set callbacks
    glutDisplayFunc(display);
    glutReshapeFunc(reshape);
    glutSpecialFunc(special);
    glutKeyboardFunc(key);
    glutIdleFunc(idle);
    
    //  Load textures
    texture[0] = LoadTexBMP("c.bmp"); //house
    texture[1] = LoadTexBMP("r.bmp"); //roof
    texture[2] = LoadTexBMP("d.bmp"); //door
    texture[3] = LoadTexBMP("w.bmp"); //window
    texture[4] = LoadTexBMP("g.bmp"); //grass
 
    //  Pass control to GLUT so it can interact with the user
    ErrCheck("init");
    glutMainLoop();
    return 0;
    }
    
You can Find alot of different kind of textures online .

**output**

![ ] (https://cloud.githubusercontent.com/assets/14142983/10709978/9ce11e8a-79ff-11e5-93d9-ee1dd1804d9d.jpg)


[Home] (https://github.com/Afnan-Aldhahri/OpenGl/blob/master/README.md)
