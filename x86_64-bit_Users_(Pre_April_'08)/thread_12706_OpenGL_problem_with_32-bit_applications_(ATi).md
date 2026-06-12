---
title: "OpenGL problem with 32-bit applications (ATi)"
date: 2005-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by kaspersv on 2005-01-26
hey, I'm running an AMD64 Hoary install with xorg and the new ATi driver.

All 64-bit apps work perfectly and seems to use the OpenGL renderer provided by the ATi driver:

```

glxinfo(64-bit)
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

glxgears(64-bit)
12228 frames in 5.0 seconds = 2445.600 FPS
14233 frames in 5.0 seconds = 2846.600 FPS

```
But for some reason 32-bit apps don't:

```

glxinfo(32-bit)
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

glxgears(32-bit)
1237 frames in 5.0 seconds = 247.400 FPS
1320 frames in 5.0 seconds = 264.000 FPS

```
Is this a problem with my setup, or doesn't the ATi driver support 32-bit OpenGL apps when using the 64-bit driver?

---

