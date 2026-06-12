---
title: "xmame on amd 64bit"
date: 2005-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by eolo999 on 2005-07-24
Someone has got xmame working on ubu 64bit? i install the package from official repositoryes and when i launch it it says something like "wrong arch"!!!
Help me with your experiences...
eolo

---

### Post by Tamir on 2005-07-25
added to my todo list, but I don't know if it is actually can work on amd64.

---

### Post by nrayever on 2005-07-26
i try it directly for xmame/xmess source code and it work preatty smooth. you only need to do some little changes to install file for make it work on amd64 platform. if you have any 3d card (as i suppouse u have) it will become xmame-x11.

pretty easy to try it from source code. easy to compile no big probs.  :grin:  :grin:

---

### Post by eolo999 on 2005-07-27
[QUOTE=nrayever]i try it directly for xmame/xmess source code and it work preatty smooth. you only need to do some little changes to install file for make it work on amd64 platform. if you have any 3d card (as i suppouse u have) it will become xmame-x11.

pretty easy to try it from source code. easy to compile no big probs.  :grin:  :grin:[/QUOTE]
 Hi nrayever,
wich are the exct change you made to install xmame from source?
Perhaps it's a stupid matter but i cannot make it work on my laptop....

---

### Post by nrayever on 2005-07-27
ok, here it is, a little quote from xmame readme file:

> Q: How do I compile XMAME/XMESS?

A: The documentation (doc/xmame-doc.*) contains detailed instructions, 
    including extra notes specific to particular hardware/OS combinations.
   READ THE DOCUMENTATION FIRST!
   Then edit the Makefile (it contains lots of helpful hints).
   Then run make.
   No, there is no configure script. Feel free to write one yourself and
    contribute it to the project. :)

Q: What platforms can I run XMAME/XMESS on?

A: Lots! :)
   Currently the following CPU bases are explicitly supported in the Makefile:
   i386  /  ia64   /  alpha  /  m68k  /  risc (various flavours)

   The following OSes are also explicitly supported:
   Linux / FreeBSD / NetBSD / OpenBSD / Solaris / NeXT / MacOS-X / IRIX / AIX

   The following display methods are explicitly supported:
   X11(R6) / SVGAlib (Linux only) / GGI (only tested on Linux) / 
   XGL (i.e. X with OpenGL) / XFX (i.e. X with 3Dfx) / 
   SVGAfx (i.e. SVGAlib with 3Dfx) / OpenStep / SDL / Photon2

   If your OS is not listed above, then there is also a "generic unix"
    compilation target that may work for you.
   The display method of choice is X11. If you have an X server on your
    system the xmame/xmess will talk to it. The other display methods are
    aimed at improving the framerate the xmame/xmess runs at, but may not
    be available on your system.

after this little quote, you need to make some corrections on the makefile. now referring to the make file you should find something like this on it:

> ###########################################################################
# Architecture; choose your CPU (only one!!) 
###########################################################################

# i386, GNU asm
 MY_CPU = i386

# i386, no asm -- needed for the Intel C++ compiler, which does not fully
# understand GCC's inline assembly syntax, though you may still enable 
# X86_ASM_68000, etc., which are assembled by NASM.  You may also need to 
# use this for BeOS.
# MY_CPU = i386_noasm

# IA64
# MY_CPU = ia64

# Opteron/Athlon64
#MY_CPU = amd64

# DEC Alpha
# MY_CPU = alpha

# Motorola M68K
# MY_CPU = m68k

# Generic RISC (PowerPC, SPARC, HPPA, IBM)
# MY_CPU = risc

# Generic RISC, LSB-first (RISC (Ultrix machines) & PlayStation2)
# MY_CPU = risc_lsb

# MIPS (generic RISC + SGI compiler bug workarounds)
# MY_CPU = mips


###########################################################################
# Architecture; choose your OS (only one!!) 
###########################################################################

# Linux 
ARCH  = linux

# FreeBSD
# ARCH  = freebsd

# NetBSD
# ARCH  = netbsd

# OpenBSD
# ARCH = openbsd

# Solaris/SunOS
# ARCH  = solaris
# For Solaris, you MIGHT need to add paths where other stuff is; libjpeg and 
# so on...  If so, uncomment the next two lines.
# CFLAGS += -I/usr/local/include -I/usr/sfw/include 
# LDFLAGS += -L/usr/local/lib -L/usr/sfw/lib

# QNX Neutrino (QNX4/QNX6)
# ARCH = nto

# OpenStep on NeXT systems
# ARCH  = next

# OpenStep on Apple systems (Cocoa)
# ARCH  = macosx

# IRIX (with sound using the old AL (version 1) package) (*)
# ARCH  = irix

# IRIX (with sound using the al (IRIX 6.x) package) (*)
# ARCH  = irix_al

# AIX (with sound, you'll need the UMS and SOM lpp's installed (under 
# AIX4))
# ARCH  = aix

# BeOS on Intel
# ARCH = beos

# generic UNIX, no sound
# ARCH  = generic

# (*) For IRIX 6.5 or higher add -DHAVE_SNPRINTF to CFLAGS.irix(_al) in
# src/unix/Makefile

this the original makefile. then some changes need to be make. 

> # Architecture; choose your CPU (only one!!) 
> # i386, GNU asm
 MY_CPU = i386

# i386, no asm -- needed for the Intel C++ compiler, which does not fully
# understand GCC's inline assembly syntax, though you may still enable 
# X86_ASM_68000, etc., which are assembled by NASM.  You may also need to 
# use this for BeOS.
# MY_CPU = i386_noasm

# IA64
# MY_CPU = ia64

# Opteron/Athlon64
#MY_CPU = amd64

change cpu options by adding a # in front of > #MY_CPU = i386  and erasing the # that is in front of > MY_CPU = amd64

and now you have selected the right architecture for your cpu. on the > Architecture; choose your OS (only one!!)  
you should have linux, leave it as it is.  u may check the display metohd options. if u have a 3d accelerator video card you should use X11

those are the basic changes that need to be done with xmame makefile. make sure u have installed all xmame dependencies before compiling it. all dependencies should be in (k)ubuntu  amd64 repositories.

i hope it work for u, any doubt ask me again!! :grin:  :grin:

---

### Post by eolo999 on 2005-07-28
[QUOTE=nrayever]ok, here it is, a little quote from xmame readme file:



after this little quote, you need to make some corrections on the makefile. now referring to the make file you should find something like this on it:



this the original makefile. then some changes need to be make. 




change cpu options by adding a # in front of   and erasing the # that is in front of 

and now you have selected the right architecture for your cpu. on the  
you should have linux, leave it as it is.  u may check the display metohd options. if u have a 3d accelerator video card you should use X11

those are the basic changes that need to be done with xmame makefile. make sure u have installed all xmame dependencies before compiling it. all dependencies should be in (k)ubuntu  amd64 repositories.

i hope it work for u, any doubt ask me again!! :grin:  :grin:[/QUOTE]
 Thanks nrayever,
my xmame works perfectly just changing CPU to amd64 (was easy!!!).
Now i'm triyng to play "fullscreen"...(any suggestion? even if this is not the right place to ask...).

---

### Post by nrayever on 2005-08-07
hi:

sorry for the late answer. i was is summer course at my university. there is a way to play in fullscreen. using ctrl + (one of the six keys of insert, delete, end, etc...). sorry for not giving u the right combination but i don't really remember it. i hope this help u.  :grin:

---

### Post by Tamir on 2005-08-07
So now I can make a .deb package of it! thanks, it will help many.

---

### Post by Tamir on 2005-08-08
I have a problem while compiling, it gives me:
```
[OSDEPEND] Compiling src/unix/video-drivers/xf86_dga1.c ...
src/unix/video-drivers/xf86_dga1.c:13:36: X11/extensions/xf86dga.h: No such file or directory
src/unix/video-drivers/xf86_dga1.c: In function `xf86_dga1_init':
src/unix/video-drivers/xf86_dga1.c:42: warning: implicit declaration of function `XF86DGAQueryDirectVideo'
src/unix/video-drivers/xf86_dga1.c:44: error: `XF86DGADirectPresent' undeclared (first use in this function)
src/unix/video-drivers/xf86_dga1.c:44: error: (Each undeclared identifier is reported only once
src/unix/video-drivers/xf86_dga1.c:44: error: for each function it appears in.)
src/unix/video-drivers/xf86_dga1.c:53: warning: implicit declaration of function `XF86DGAGetVideo'
src/unix/video-drivers/xf86_dga1.c: In function `xf86_dga1_set_mode':
src/unix/video-drivers/xf86_dga1.c:333: warning: implicit declaration of function `XF86DGAForkApp'
src/unix/video-drivers/xf86_dga1.c:341: warning: implicit declaration of function `XF86DGADirectVideo'
src/unix/video-drivers/xf86_dga1.c:342: error: `XF86DGADirectGraphics' undeclared (first use in this function)
src/unix/video-drivers/xf86_dga1.c:342: error: `XF86DGADirectMouse' undeclared (first use in this function)
src/unix/video-drivers/xf86_dga1.c:342: error: `XF86DGADirectKeyb' undeclared (first use in this function)
src/unix/video-drivers/xf86_dga1.c:348: warning: implicit declaration of function `XF86DGASetViewPort'
make[1]: *** [xmame.obj/unix.x11/video-drivers/xf86_dga1.o] Error 1
make[1]: Leaving directory `/home/tamir/tamir/env/xmame/xmame-0.97'
make: *** [build] Error 2
```

ugly  :-|

---

