---
title: "error while linking glfw framework"
date: 2007-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by sajjad on 2007-01-09
Hello,

I am running the 64 bit version Edgy Eft and i am having the following linking error while compiling a program using the glfw framework.

root@sajjad-laptop:/home/sajjad/shade/shader# make shader
g++ -o  shader Camcorder.o glut_teapot.o main_shader.o textfile.o -L/usr/X11R6/lib -lglut -lglfw -lGLU -lGL -lGLEW -lXmu -lX11 -lpthread -lm
/usr/X11R6/lib/libglfw.a(x11_init.o): In function `_glfwPlatformInit':
x11_init.c:(.text+0xd3): undefined reference to `XF86VidModeQueryExtension'
/usr/X11R6/lib/libglfw.a(x11_window.o): In function `_glfwPlatformRefreshWindowParams':
x11_window.c:(.text+0x7f1): undefined reference to `XF86VidModeGetModeLine'
/usr/X11R6/lib/libglfw.a(x11_window.o): In function `_glfwPlatformIconifyWindow':
x11_window.c:(.text+0x88a): undefined reference to `XF86VidModeLockModeSwitch'
x11_window.c:(.text+0x8a1): undefined reference to `XF86VidModeSwitchToMode'
/usr/X11R6/lib/libglfw.a(x11_window.o): In function `_glfwPlatformCloseWindow':
x11_window.c:(.text+0xb3c): undefined reference to `XF86VidModeLockModeSwitch'
x11_window.c:(.text+0xb53): undefined reference to `XF86VidModeSwitchToMode'
/usr/X11R6/lib/libglfw.a(x11_fullscreen.o): In function `_glfwPlatformGetDesktopMode':
x11_fullscreen.c:(.text+0x93): undefined reference to `XF86VidModeGetAllModeLines'
/usr/X11R6/lib/libglfw.a(x11_fullscreen.o): In function `_glfwGetClosestVideoMode':
x11_fullscreen.c:(.text+0x128): undefined reference to `XF86VidModeGetAllModeLines'
/usr/X11R6/lib/libglfw.a(x11_fullscreen.o): In function `_glfwPlatformGetVideoModes':
x11_fullscreen.c:(.text+0x209): undefined reference to `XF86VidModeGetAllModeLines'
/usr/X11R6/lib/libglfw.a(x11_fullscreen.o): In function `_glfwSetVideoModeMODE':
x11_fullscreen.c:(.text+0x485): undefined reference to `XF86VidModeGetAllModeLines'
x11_fullscreen.c:(.text+0x49e): undefined reference to `XF86VidModeLockModeSwitch'
x11_fullscreen.c:(.text+0x4b8): undefined reference to `XF86VidModeSwitchToMode'
x11_fullscreen.c:(.text+0x4ca): undefined reference to `XF86VidModeSetViewPort'
x11_fullscreen.c:(.text+0x4dd): undefined reference to `XF86VidModeLockModeSwitch'
collect2: ld returned 1 exit status
make: *** [shader] Fel 1


any idea?

---

