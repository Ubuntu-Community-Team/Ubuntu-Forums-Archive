---
title: "ATi X600XT PCI-E at full power ???"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by bughead on 2005-10-24
Hi friends, how can I make my ATi X600XT work at full power ?
In the xorg.conf file it's recognized, but how can I test if the board is working with accelerations and etc.... ?

Thanks,

---

### Post by Pablo_Escobar on 2005-10-24
You can try typing in the terminal "fgl_glxgears".
Wait for a couple of seconds, close the window which poped out, and for a comparison You can paste here how many FPS did You manage :)

---

### Post by bughead on 2005-10-25
I follow the fglrx drivers install howto and .... tadadada ....

... great !!!

root@ubuntu:~# **glxgears -printfps**
7998 frames in 5.4 seconds = 1476.282 FPS
8438 frames in 5.0 seconds = 1687.436 FPS
8125 frames in 5.5 seconds = 1483.641 FPS
8231 frames in 5.0 seconds = 1646.174 FPS
root@ubuntu:~# **fgl_glxgears**
Using GLX_SGIX_pbuffer
2254 frames in 5.0 seconds = 450.800 FPS
2952 frames in 5.0 seconds = 590.400 FPS
2545 frames in 5.0 seconds = 509.000 FPS
2991 frames in 5.0 seconds = 598.200 FPS
root@ubuntu:~# **fglrxinfo**
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600/X550 Series Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)
root@ubuntu:~#

But now my 2D is lagging ... 3 sec. lag .. 3 sec. lag ... 3sec. lag ....
When I run any video file (not just in this case, my mouse is lagging too) ... I have slowdowns ...

What can I do now ? :confused:

---

### Post by bughead on 2005-10-26
One more question ...

When I run fgl_glgears or glgears, the main processor stay at 100% of use ... it's normal ?

Who would have to take care of this would not have to be the video board ?

[ ]'s
Juliano

---

