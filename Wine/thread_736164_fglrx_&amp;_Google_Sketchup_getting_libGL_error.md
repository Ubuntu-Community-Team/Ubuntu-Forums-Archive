---
title: "fglrx &amp; Google Sketchup getting libGL error"
date: 2008-03-26
forum: Wine
---

### Post by bismark on 2008-03-26
I'm try to get Google Sketchup to run under wine.  I've seen posts about people getting it to run successfully however I am not able to. When I try to start it I get it to briefly appear and then it closes.

I'm running Hardy Heron x64 with everything up to date.  The fglrx out of the repositories not manually installed.  DRI is enabled, but AIGLX and compositing are not in my xorg.

When I start SketchUp I get the following and it closes:
libGL error: drmMap of framebuffer failed (Cannot allocate memory)
libGL error: reverting to (slow) indirect rendering

[fglxinfo]
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5250
OpenGL version string: 2.1.7412 FireGL Release

[glxinfo|grep direct]
direct rendering: Yes

---

