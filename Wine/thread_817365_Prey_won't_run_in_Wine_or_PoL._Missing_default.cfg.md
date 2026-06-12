---
title: "Prey won't run in Wine or PoL. Missing default.cfg"
date: 2008-06-03
forum: Wine
---

### Post by RedMartin on 2008-06-03
As per the title I can't run Prey in Wine.

I get this error (at the bottom) about not being able to load a default.cfg

> 
Prey 1.4.119 win-x86 Nov 20 2007 18:31:35
1200 MHz Intel CPU with MMX & SSE & SSE2 & SSE3 & x64
2016 MB System Memory
64 MB Video Memory
Winsock Initialized
Found interface: eth0 eth0 - 192.168.0.3/255.255.255.0
Sys_InitNetworking: adding loopback interface
prey using MMX & SSE & SSE2 & SSE3 for SIMD processing
enabled Flush-To-Zero mode
enabled Denormals-Are-Zero mode
------ Initializing File System ------
Loaded pk4 C:\Program Files\Prey\base\game00.pk4 with checksum 0xff851bf2
Loaded pk4 C:\Program Files\Prey\base\game01.pk4 with checksum 0xa208af14
Loaded pk4 C:\Program Files\Prey\base\game02.pk4 with checksum 0xaa46eb08
Loaded pk4 C:\Program Files\Prey\base\game03.pk4 with checksum 0x39a5ed9c
Loaded pk4 C:\Program Files\Prey\base\pak005.pk4 with checksum 0xead35190
Loaded pk4 C:\Program Files\Prey\base\pak006.pk4 with checksum 0xed8ce397
Loaded pk4 C:\Program Files\Prey\base\pak020.pk4 with checksum 0x39191193
Loaded pk4 C:\Program Files\Prey\base\pak040.pk4 with checksum 0x40dd9bb5
Current search path:
C:\Program Files\Prey/base
C:\Program Files\Prey\base\pak040.pk4 (468 files)
C:\Program Files\Prey\base\pak020.pk4 (23 files)
C:\Program Files\Prey\base\pak006.pk4 (108 files)
C:\Program Files\Prey\base\pak005.pk4 (10 files)
C:\Program Files\Prey\base\game03.pk4 (2 files)
C:\Program Files\Prey\base\game02.pk4 (10 files)
C:\Program Files\Prey\base\game01.pk4 (2 files)
C:\Program Files\Prey\base\game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Shutting down OpenGL subsystem
...shutting down QGL
Couldn't load default.cfg


Apparently the *.cfg file is created when the game runs but if it won't run then how will it ever be created?

Using PlayOnLinux is worse. I don't even get the error message.

Anyone?

---

### Post by RedMartin on 2008-06-04
It's working now. Re-installed it and it works fine!

---

