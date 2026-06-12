---
title: "Enemy Territory on nvidia: libXxf86vm.so.1 not found?"
date: 2005-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by syscrash2k on 2005-09-18
Hi,
I'm trying to get Enemy Territory to work on my AMD64 install of ubuntu.
I've tried a variety of things, and i've tried following the howto.

I have also tried copying the files from the lib32 folder of the nvidia drivers into my /usr/lib32 folder, but it hasn't helped.

When i try to run ET, the following happens:
```

<snip>
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: QGL_Init: dlopen libGL.so.1 failed: libXxf86vm.so.1: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
``` 

It seems that others have had the same problem before, but no one has posted a solution.

Does anyone know what I could do?

---

### Post by adewale on 2007-04-23
i know this is late but could help someone. i ran into a similar problem though i use a 32 bit system the soulution was  sudo ln -s /usr/lib/libXxf86vm.so.1 /usr/lib/libXxf86vm.so and it worked

---

