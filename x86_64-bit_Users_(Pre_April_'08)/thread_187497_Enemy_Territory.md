---
title: "Enemy Territory"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by krak on 2006-06-03
Hello, today after long break with ubuntu i have installed Kubuntu 6.06 x64. I have installed ATI drivers using this how to [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver) 
and they seems to work 
krak@hal:~$ glxgears -printfps
20736 frames in 5.0 seconds = 4147.166 FPS
24406 frames in 5.0 seconds = 4881.111 FPS
24407 frames in 5.0 seconds = 4881.382 FPS

 
When i run ET here whats i get
 
 ET 2.60 linux-i386 Mar 10 2005
 ----- FS_Startup -----
 Current search path:
 /home/krak/.etwolf/etmain
 /home/krak/gry/enemy-territory/etmain/pak2.pk3 (22 files)
 /home/krak/gry/enemy-territory/etmain/pak1.pk3 (10 files)
 /home/krak/gry/enemy-territory/etmain/pak0.pk3 (3725 files)
 /home/krak/gry/enemy-territory/etmain/mp_bin.pk3 (6 files)
 /home/krak/gry/enemy-territory/etmain
 
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
 ...loading libGL.so.1: QGL_Init: dlopen libGL.so.1 failed: libGL.so.1: cannot open shared object file: No such file or directory
 failed
 ----- CL_Shutdown -----
 RE_Shutdown( 1 )
 -----------------------
 ----- CL_Shutdown -----
 -----------------------
 Sys_Error: GLimp_Init() - could not load OpenGL subsystem

i have searched for libGL.so.1 and its in /usr/lib/

---

### Post by Patsoe on 2006-06-03
[QUOTE=krak]Hello, today after long break with ubuntu i have installed Kubuntu 6.06 **x64**. 

[...]
 
When i run ET here whats i get
 
 ET 2.60 linux-**i386** Mar 10 2005

[...] 

i have searched for libGL.so.1 and its in /usr/lib/[/QUOTE]

Could it be that ET is looking for a 32bit library?

---

### Post by kingmob on 2006-06-03
[QUOTE=Patsoe]Could it be that ET is looking for a 32bit library?[/QUOTE]
I think the problem simply is that the libGL isn't linked in the places ET is searching for it. I can remember having these same problems on 32bit. There are ways to solve this problem all over the internet i think. If you can't find it for ET, try Quake3, the problem is identical i believe.

---

### Post by krak on 2006-06-03
still no succes I did search net no succes ;(

i had libGL.so.1  in /usr/lib/ and i have coppy it to lib32 and lib64 created symbolic link in all lib folders but still i get same error.

still need to get some ideas.

---

