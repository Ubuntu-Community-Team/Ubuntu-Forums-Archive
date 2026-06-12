---
title: "Problem with wine: seems to stem from error with open GL"
date: 2007-11-21
forum: Wine
---

### Post by Griffiss on 2007-11-21
Hi there

I was just trying to get a program to run with wine in the terminal and got this error:

```
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems

```

After a bit of research I got no solutions but think the following outputs might help:

Command: glxinfo | grep -i opengl

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

and command: glxinfo | grep direct

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

which seems to be the same, and not good.

sudo apt-get install opengl just says that it can't find the package opengl.

Really want to sort this out. Anyone?

---

### Post by hikaricore on 2007-11-21
> glxinfo | grep rendering

??

If this returns a **no**, you need to install/configure your video drivers.

Opengl is not something that's installable, it's a method of processing 2d/3d data through your video hardware.  [http://en.wikipedia.org/wiki/OpenGL](http://en.wikipedia.org/wiki/OpenGL)

---

### Post by Griffiss on 2007-11-22
Yes, thanks, I tracked it down to the video drivers. I enabled nvidia-glx with the restricted drivers manager (don't know why this was disabled), and now things seem ok, except desktop effect can't be enabled.

---

