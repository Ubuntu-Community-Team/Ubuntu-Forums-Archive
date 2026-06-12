---
title: "[SOLVED] Totem Error - No video output is available"
date: 2007-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by mosestruong on 2007-12-27
I've recently installed the 64bit version of Ubuntu. Now when I try to open Totem, I get an error:
No video output is available. Make sure that the program is correctly installed.

When I tried using gxine, and I get the following error:
gtkvideo: couldn't open video driver
gxine has suffered a fatal internal error.
To get a backtrace, run gxine in a debugger such as gdb.
Then, when the error occurs:
  (gdb) thread apply all bt
gxine: error: Fatal error: Segmentation fault
Segmentation fault (core dumped)

I am using nvidia-glx-new graphics driver. Would anyone know how I can solve this problem. Thanks.

---

### Post by mosestruong on 2007-12-27
Found the solution - after installing libxine1-x package, it seems to be working now. Not sure why that wasn't a dependent package...

---

### Post by zorkerz on 2008-01-07
Thanks this post thread helped me but now im getting a new error.

> There is no input plugin to handle the location of this movie

I am using hardy heron x64

---

