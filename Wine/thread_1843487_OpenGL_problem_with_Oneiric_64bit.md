---
title: "OpenGL problem with Oneiric 64bit"
date: 2011-09-13
forum: Wine
---

### Post by Lazy123 on 2011-09-13
~/.wine/drive_c/Program Files/Warcraft III$ wine Frozen\ Throne.exe -opengl
err:ole:CoCreateInstance apartment not initialised
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libGL.so.1: cannot open shared object file: No such file or directory
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"C:\\Program Files\\Warcraft III\\Game.dll") failed (error c000007a).

Everything worked fine in 11.04, but now Wine seems to be broken. There is also a bug report I made: [https://bugs.launchpad.net/ubuntu/+source/wine1.3/+bug/849209](https://bugs.launchpad.net/ubuntu/+source/wine1.3/+bug/849209)

---

### Post by Dlambert on 2011-09-15
Try,
> this is a simple tutorial to show a new linux user (such as myself) how to setup freeglut and opengl.

System used ibm t22 thinkpad:
Mobile pentium 3 900mhz
256mb ram
20gb hd
s3 inc. 86c270-294 savage/ix-mv (rev 13) video card

os: Xubuntu 6.10

i  have just recently become a linux user and wanted to install freeglut  to do my graphics assignments on my laptop. Although the install did not  turn out to be very difficult it took me a while to do. So i have  written this tutorial in case another young linux user comes along and  decides he/she wants to install freeglut and opengl.

**this tutorial assumes that you have your operating system installed and you have access to the internet**

steps:

From a terminal

1) sudo apt-get update

-this will update your apt database to the most recent available packages.

2) sudo apt-get install build-essential

- this installs the necessary development tools for building source code.

3) sudo apt-get install freeglut3-dev

- this installs the development libraries and headers for freeglut.

Your  done! Extremely simple! However you must remember that when compiling  you must add a '-lglut' as a comand line argument to gcc. If you don't  it cannot find the library's and you will get undefined reference  errors.

Example command line: Gcc simple.c -lglut

at this  point if your program compiles and runs then you are finished. However  the first time i tried to run mine i received a 'libgl warning: 3d  driver claims to not support visual 0x42'. This error means i cannot  display the required colors to run the program. In my case i had the  most recent drivers for my video card. So i did some research on my  monitor and found out it can display a color depth of 24 instead of the  16 it was set at. To fix this problem you must edit the  /etc/x11/xorg.conf file as root and set the 'defaultdepth 24'. Reboot  and the problem is solved.

This is my first post (and tutorial)  on the ubuntuforums. If people feel that this tutorial is not needed  they can feel free to remove it. If anyone wants to add anything related  to freeglut or opengl please feel free.


---

### Post by jalirious on 2011-09-19
Hi, unfortunately I add to this only my own issues. 

I'm trying to compile something that depends on libGL.so - openGL. Running 11.10 64-bit. The script tries to find the library - and fails. Here's a bit of the log..

Checking in directories /usr/local/Mesa /usr/local/Mesa for  libGLU.so libGLU.sl libGLU.dylib libGLU.dll.a libMesaGLU.so libMesaGLU.sl libMesaGLU.dylib libMesaGLU.dll.a  libGLU.a libGLU.lib libGLU libMesaGLU.a libMesaGLU.lib libMesaGLU Checking in directories /opt/Mesa /opt/Mesa for  libGLU.so libGLU.sl libGLU.dylib libGLU.dll.a libMesaGLU.so libMesaGLU.sl libMesaGLU.dylib libMesaGLU.dll.a  libGLU.a libGLU.lib libGLU libMesaGLU.a libMesaGLU.lib libMesaGLU
 [etc, etc]

Any advice? Is there a replacement libGL.so for 11.10 that I could sym link to?

Cheers!

---

