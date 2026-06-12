---
title: "Is DRI ever going to work on Mach64?!"
date: 2006-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mad Echidna on 2006-05-05
I have a powerbook Lombard and I'm ready to pitch it out the window. What do I have to do in order to get dri?

---

### Post by davygravy on 2006-05-05
Running glxinfo from a terminal and looking for the part with "Renderer:" will also tell you whether you've got 3D acceleration (and are using DRI drivers which probably also have the best 2D performance you can get)

DRI does work.  I don't know if it works on Mach64.

Have you tried opening a terminal and typing 

```

glxinfo 

```

may tell you something.  You could post the output and someone may be able to assist you.

---

### Post by Peter76 on 2006-05-05
Hello, maybe I should post a new thread about this, but I've been noticing already for a while:

agpgart: Putting AGP V2 device at 0000:00:0b.0 into 1x mode

Now when I type :  glxinfo | grep render

I get:

direct rendering: Yes
OpenGL renderer string: Mesa DRI Radeon 20050528 AGP 1x TCL

Does this mean my graphics card is running at 1x while it can be running at 2x?

---

### Post by Mad Echidna on 2006-05-05
I don't even have DRI, I don't know how to install it. Ubuntu doesn't come with a Mach64 module.

---

### Post by slux on 2006-05-06
What would you use your Mach64's 3D acceleration for? The DRI driver might eventually get into Xorg and to Ubuntu I guess but I'm not sure of the status and no-one is probably very eagerly working on it because it's of such a limited use. I can't imagine it satisfiably rendering much more than the screensavers...

---

### Post by deathshadow on 2006-05-06
[QUOTE=Mad Echidna]I have a powerbook Lombard and I'm ready to pitch it out the window. What do I have to do in order to get dri?[/QUOTE]

Why would it? The flat Mach64 doesn't even HAVE openGL support on it... Although given it's a lombard I'm assuming you mean the Mach64LM, which is generally not called a Mach 64 but a Rage Mobility LT... Which in 3d terms is a joke being inferior to a S3 virge (in other words so little you might have things run faster in software mode) 

This is almost like asking for 3d support on a Tseng 4000 or a Trident 9440 :-({|= There's nothing there really TO support. The only real acceleration on the board is for a handful of 2d operations meant for Windows 3.1 (There's a reason it's called a winboost card), and those are primative AT BEST and supported through the base driver, NOT the DRI.

Besides, the last time I think ANYONE spent any time coding support for the Mach64/Rage LT chipset in X would have been over five years ago - the chipset was three years out of date and five years old when Apple started using it (which is typical apple - always a generation behind).

---

