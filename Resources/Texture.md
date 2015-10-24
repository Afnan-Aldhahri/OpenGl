##Texture

####What are texture maps?

Texture maps used to make surfaces appear more realistic.

They are simple in concept, but hardware intensive.

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



#####Creating a Texture 

    glGenTextures(1,&texname);
    
Returns unique texture name

    glBindTexture(GL_TEXTURE_2D,texname);
    
First use – allocates memory and makes current

    glTexImage2D(GL_TEXTURE_2D,0,3,dx,dy, 0,GL_RGB,GL_UNSIGNED_BYTE,image);
    
Copies RGB image to texture memory (size dx xdy) 

Finally,lets see an example :

we will add a texture for the same 3d house that we draw before 

**Example**
    
   

**output**

![ ] (https://cloud.githubusercontent.com/assets/14142983/10709978/9ce11e8a-79ff-11e5-93d9-ee1dd1804d9d.jpg)

