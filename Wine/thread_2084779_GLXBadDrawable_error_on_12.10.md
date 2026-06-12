---
title: "GLXBadDrawable error on 12.10"
date: 2012-11-16
forum: Wine
---

### Post by kowaz on 2012-11-16
I'm getting the following error output when I try to run GTA IV on Ubuntu 12.10 (64bit) with WINE:

```
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  3817
  Current serial number in output stream:  3817
```I think my system is up-to-date:

```
Ubuntu 12.10
Linux 3.5.0-18-generic
unity 6.10.0
wine-1.5.17
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 304.64

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes
Unity 3D supported:       yes
```Running *export LIBGL_DRIVERS_PATH=/usr/lib32/dri* before the program had no effect.

Suggestions?

---

### Post by Adonn on 2012-11-21
Hey, I'm having the same problem. I tried PlayOnLinux too, but I got the same error you did. I also have a NVidia card (360M, I think), running 12.10.

Here's what I got:
```

X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  5190
  Current serial number in output stream:  5190

```

Any help here would be greatly appreciated

---

### Post by virx on 2012-11-26
Sirs, did you get is solved?
I have nvidia GTX 460 card and drivers 310.14
wine-1.5.17

---

