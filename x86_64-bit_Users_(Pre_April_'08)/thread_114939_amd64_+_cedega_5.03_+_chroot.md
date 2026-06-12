---
title: "amd64 + cedega 5.03 + chroot"
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by takedown on 2006-01-09
Hi there,
I installed cedega in chroot(use 32 bit chroot howto), updated to 5.03 version and install the game(gta3), but when i load a game its run very slowly before i run the game i make a test in cedega and opengl test failed.
I have a ati radeon 9600 and i have a fgrlx drivers, but how i can do this works in chroot? i try to install a 32 bit version fglrx in chroot, but it dont work. 
takedown@breezy:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)
takedown@breezy:~$ glxinfo |grep direct
direct rendering: Yes

Thanks for any help.
P.S. Sorry for my terrible english.

---

