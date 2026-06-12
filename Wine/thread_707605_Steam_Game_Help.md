---
title: "Steam Game Help"
date: 2008-02-25
forum: Wine
---

### Post by Malink on 2008-02-25
Hey, I got steam installed and loaded my games up into it manually. Now when I go to start a game I get an errror that looks like this 

```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
```

I'm unsure how to fix this problem. I've looked all over. Can any1 help

Oh and Im using wine 0,9.55 with 64Bit Gusty, and a 7600 Nvidia Card.

---

### Post by Malink on 2008-02-28
Also, if I run it in a vista environment I get an admin error.

---

### Post by naz37 on 2008-03-01
Do you have opengl and 3d acceleration setup correctly? the last line of your error seems to imply this.

---

### Post by Malink on 2008-03-10
how am I to properly set up these tools (opengl and 3d) for my system

---

### Post by doorknob60 on 2008-03-10
Did you install the proprietary Nvidia drivers? If not, I recomend Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You can also try the Restricted Drivers Manager but it has issues on two of my four computers and the drivers are older so I'd use Envy.

---

