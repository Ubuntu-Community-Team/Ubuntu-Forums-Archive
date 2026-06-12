---
title: "ATI Radeon 9250 3D acceleration"
date: 2005-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Paul Yard on 2005-04-16
Hello!
I'm new to UBUNTU and not a Linux expert too.
I just installed Hoary on my Athlon 64.
The video card is a Radeon 9250.
X works perfectly but I cannot get the 3D acceleration.
I followed alla the instruction I found on the subject but probably I miss something.
1) I modified xorg.conf replacing "ati" with "fglrx" and setting UseInternalAgpgart=NO but with fglxinfo till I get:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Then I ran fglxconfig and replaced the Device section of xorg.conf but X crashes .

Can anibody help me?

Thanks for support.
p

I passed to Gentoo and I solved the problem.
It was something connected to sis760 cipset and it was necessary to modify the source amd64-agp.c.
Maybe it can be solved in the same way for UBUNTU.

Thanks anyway.

---

