# Installing OpenGl

I summerize the installations steps from [www.prinmath.com](http://www.prinmath.com/csci5229/misc/install.html) , so if you need more details about how to install OpenGl take a look [here](http://www.prinmath.com/csci5229/misc/install.html) .

You need to install an environment on your hardware where you can compile and run OpenGL programs.

how to compile and link programs varies depends on which operatin system you use .


**Linux**

the libraries and header files are installed using the command

    yum install freeglut-devel
   
For distributions derived from Debian such as Ubuntu, the installation command is

    apt-get install freeglut3-dev
   
To compile and link your program on Ubuntu 14 based distros you need to explicitly grab every library using

    gcc -o foo foo.c -lglut -lGLU -lGL -lm



**OS/X**
To compile and link your program using the Apple SDK requires

    gcc -o foo foo.c -framework GLUT -framework OpenGL
   
Note that under OS/X, the GLUT header files are in the subdirectory GLUT rather than the GL subdirectory. 

The following code works on OSX and Linux

    #ifdef __APPLE__
    #include <GLUT/glut.h>
    #else
    #include <GL/glut.h>
    #endif


**Windows**

To compile and link foo.c under MinGW you need

    gcc -Wall -ofoo foo.c -lglut32cu -lglu32 -lopengl32


To compile and link foo.c using MinGW and GLEW you need

    gcc -DUSEGLEW -Wall -ofoo foo.c -lglew32 -lglut32cu -lglu32 -lopengl32
