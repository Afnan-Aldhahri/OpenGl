    
    int main(int argc,char* argv[]) {
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE);
    glutInitWindowPosition(50, 50);
    glutInitWindowSize(900,600);
    glutCreateWindow("HW2 : Afnan Aldhahri ");
    glutDisplayFunc(display);
    glutReshapeFunc(reshape);
    glutSpecialFunc(special);
    glutKeyboardFunc(key);
    glutIdleFunc(idle);
    glutMainLoop();
    
    return 0;
    }

**Lets explain each function in The main( ) :**

    glutInit(&argc,argv); 
will Initialize GLUT and process user parameters
     
     
    glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE);  
will Request double buffered, true color window with Z buffering
    
    glutInitWindowPosition(50, 50);
will dtermine the position of the window from the left corner 

    glutInitWindowSize(900,600);  
will determine the size of the window to be 900 x 600 pixel window
    
    glutCreateWindow("Hello from our first program");
will Create the window and the name of the window will be :Hello from our first program
    
    
    glutDisplayFunc(display); 
will Tell GLUT to call "display" when the scene should be drawn
    
    glutReshapeFunc(reshape); 
will Tell GLUT to call "reshape" when the window is resized

    glutSpecialFunc(special); 
will Tell GLUT to call "special" when an arrow key is pressed

    
    glutKeyboardFunc(key); 
will Tell GLUT to call "key" when a key is pressed
    
    
    glutIdleFunc(idle); 
will Tell GLUT to call "idle" when there is nothing else to do
    
    glutMainLoop();  
will Pass control to GLUT so it can interact with the user

[Home] (https://github.com/Afnan-Aldhahri/OpenGl/blob/master/README.md)
