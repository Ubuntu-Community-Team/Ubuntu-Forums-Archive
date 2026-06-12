---
title: "Wine apps fail to start - Missing libGL.so.1 (11.10 &amp; !2.04)"
date: 2012-11-11
forum: Wine
---

### Post by Cheifchimp on 2012-11-11
running ubuntu 11.10 or 12.04 64 bit. 
When I try to launch several 32 bit apps in wine I get:

[B]wine /home/mick/.wine/drive_c/Program\ Files/MapInfo/Professional/MAPINFOW.EXE 
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libGL.so.1: cannot open shared object file: No such file or directory[/B]

**sudo find / -iname "libGL.so.1"**
returns
 
[B]/usr/lib32/mesa/libGL.so.1
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1[/B]

I also get the same error when I attempt to run Google Earth

I tried doing 

[B]export LD_LIBRARY_PATH=/usr/lib32
ldconfig[/B]

as advised in some answers to other, similar threads but it made no difference.

These programs worked fine in 64 bit ArchLinux before I switched back to ubuntu.

---

