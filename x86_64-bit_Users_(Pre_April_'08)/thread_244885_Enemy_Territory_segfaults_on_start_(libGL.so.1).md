---
title: "Enemy Territory segfaults on start (libGL.so.1)"
date: 2006-08-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ribs on 2006-08-27
Hi,

I cannot, for the life of me, get Enemy Territory to run on this machine. I'm running the 64-bit release of Dapper. Enemy Territory installed just fine, but refuses to run. It seems to always segfault where it should be loading up the OpenGL system. Here's the console output:

ribs@aphrodite:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/ribs/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Segmentation fault

Even using linux32 to run et doesn't help at all. It seems et is loading the correct 32-bit version of the library which is installed (I moved the 64-bit version to one side to test this). I want to avoid a chroot if at all possible. Has anyone got this running?

---

### Post by gerbman on 2006-08-27
Did you install the drivers for your video card (which one do you have)?

---

### Post by a-musing amazon on 2006-08-27
Is Enemy Territory 32-bit?

32-bit Programs use the libGL.so.1 (->libGL.so.1.2) in /usr/lib32/, not the 64bit one in /usr/lib/ and /usr/lib64/ so they should not conflict.

However you may be using the 'wrong' LibGL.so.1.2, which can then lead to a variety of wrong behaviours.

I can't speak for Enemy Territory but I did find this with Googleearth which is the only 32-bit GL app I use.

In my case I accidentally overwrote the working libGl.so.1.2 when I had copied some files into /usr/lib32/ in an (ultimately successful) attempt to get my 32-bit mplayer plugin running. This then seg-faulted Googleearth.

I subsequetly tried two different LibGL.so.1.2, including the one that is provided when you compile the latest ATI fglrx driver - ver 8.28.8 - and although Googleearth didn't seg-fault it wouldn't work properly either. With one version of LibGL it just hung after the spash screen (using 100% cpu) and the other started but there was no 3D and Googleearth said it didn't recognise my video driver. The fglrx and glx diagnostics only seem to test the 64-driver and this was always working OK.

I finally fixed the problem by extracting the (usr/lib32/)LibGL.so.1.2 from the Dapper 64-bit xorg-driver-fglrx archives (i.e. I was then using the one I started with when I installed Dapper) and replacing my existing LibGL.so.1.2.  

There seems no obvious way of checking which LibGL.so.1.2 you have apart from how big it is and perhaps its date. My working version in /usr/lib32 is 642476 bytes and dated 2006-07-10. If this matches yours then the your problem is probably something else.

---

### Post by cocteau on 2006-08-27
I had a similar problem with Doom III and my ATI card. In the end I had to give up and now I'm firing my ATI card for an nvidia one.

The best solution I found with ATI 3d problems in Cedega is to install the open source driver and cross your fingers.

---

### Post by Ribs on 2006-08-30
> **a-musing amazon said:**
> Is Enemy Territory 32-bit?

32-bit Programs use the libGL.so.1 (->libGL.so.1.2) in /usr/lib32/, not the 64bit one in /usr/lib/ and /usr/lib64/ so they should not conflict.

However you may be using the 'wrong' LibGL.so.1.2, which can then lead to a variety of wrong behaviours.

I can't speak for Enemy Territory but I did find this with Googleearth which is the only 32-bit GL app I use.

I've not messed with these files at all. I've just checked against the actual files in the nvidia-glx package, and they are identical. I've tested Google Earth, and get the same problem (just 'segmentation fault', no mention of what went wrong, but I think it's safe to assume it's the same issue here).

This may be another case where 64-bit prooves to be more trouble than it's worth. ](*,)

---

