---
title: "Error running program with wine"
date: 2007-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by atomicdad on 2007-09-17
I am getting errors trying to a program under wine. A little backgound:
I'm pretty new to this.
Running Ubuntu 7.04 64 bit (***.16.... kernel) on a new Dell Inspirion 1520 laptop. I loaded/installed the 64 bit version of wine last Friday so I assume it is the latest version. I am trying to run a 32bit windows program lsprepost, which is the pre and post processing gui interface for the LSDyna finite element code.

The following is the printout from terminal window after I try to fire up the program:

> dan@dan:~$ wine lspre
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No litGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
16:53:50: my malloc allocated =      8000000 bytes @x a570040, with message = DB_MemDataAlloc-ScratchInit
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
16:53:50: Debug: C:\wx\src\msw\glcanvas.cpp(573): 'ChoosePixelFormat' failed with error 0x00000000 (success).
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:get_fbconfig_from_visualid glXChooseFBConfig returns NULL
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:X11DRV_GetPixelFormat Unable to find a WineGLPixelFormat for iPixelFormat=0
err:wgl:X11DRV_DescribePixelFormat No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglCreateContext No libGL on this box - disabling OpenGL support !
16:53:50: Debug: C:\wx\src\msw\glcanvas.cpp(199): assert "wxAssertFailure" failed: Couldn't create OpenGL context
 OpenGL version Version not found
wine: Unhandled page fault on read access to 0x00000000 at address 0x149d09e (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0149d09e).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0149d09e ESP:09fcfc1c EBP:09fcfc38 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000000 EBX:7b8b0888 ECX:0155ac18 EDX:00004c47
 ESI:00000000 EDI:00000000
Stack dump:
0x09fcfc1c:  09fcfc30 7b8b0888 09fcfd3c 004121e4
0x09fcfc2c:  00000000 0155ac18 09fcfc40 09fcfc48
0x09fcfc3c:  00620fcd 09fcfda8 015a8710 09fcfd3c
0x09fcfc4c:  006218d0 09fcfd94 09fcfda8 09ff7a80
0x09fcfc5c:  09ff7950 cccccccc cccccccc 00000000
0x09fcfc6c:  00000000 00000064 00000064 00020000
Backtrace:
=>1 0x0149d09e in lspre (+0x109d09e) (0x09fcfc38)
  2 0x00620fcd in lspre (+0x220fcd) (0x09fcfc48)
  3 0x006218d0 in lspre (+0x2218d0) (0x09fcfd3c)
  4 0x00401331 in lspre (+0x1331) (0x09fcfd48)
  5 0x0043e5ab in lspre (+0x3e5ab) (0x09fcfda0)
  6 0x0043f3ac in lspre (+0x3f3ac) (0x09fcfdb0)
  7 0x00577136 in lspre (+0x177136) (0x09fcfddc)
  8 0x00520b93 in lspre (+0x120b93) (0x09fcfe18)
  9 0x00520d1c in lspre (+0x120d1c) (0x09fcfe60)
  10 0x0043e856 in lspre (+0x3e856) (0x09fcfe78)
  11 0x01499796 in lspre (+0x1099796) (0x09fcff08)
  12 0x7b87546e in kernel32 (+0x5546e) (0x09fcffe8)
  13 0xf7ecd9e7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0149d09e: movb        0x0(%edi),%al
Modules:
Module  Address                 Debug info      Name (69 modules)
PE        400000- 8fb5000       Export          lspre
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d9e8000-7da1a000       Deferred        uxtheme<elf>
  \-PE  7d9f0000-7da1a000       \               uxtheme
ELF     7da1a000-7da37000       Deferred        imm32<elf>
  \-PE  7da20000-7da37000       \               imm32
ELF     7da37000-7da3d000       Deferred        libxrandr.so.2
ELF     7da3d000-7da45000       Deferred        libxrender.so.1
ELF     7da45000-7da48000       Deferred        libxinerama.so.1
ELF     7da55000-7dae5000       Deferred        winex11<elf>
  \-PE  7da60000-7dae5000       \               winex11
ELF     7db50000-7db70000       Deferred        libexpat.so.1
ELF     7db70000-7db9b000       Deferred        libfontconfig.so.1
ELF     7db9b000-7dbaf000       Deferred        libz.so.1
ELF     7dbaf000-7dc19000       Deferred        libfreetype.so.6
ELF     7dc26000-7dc3c000       Deferred        glu32<elf>
  \-PE  7dc30000-7dc3c000       \               glu32
ELF     7dc9f000-7dcab000       Deferred        libgcc_s.so.1
ELF     7dd95000-7e61b000       Deferred        libglcore.so.1
ELF     7e61b000-7e620000       Deferred        libxdmcp.so.6
ELF     7e620000-7e6a0000       Deferred        libglu.so.1
ELF     7e6a0000-7e72c000       Deferred        libgl.so.1
ELF     7e72c000-7e81d000       Deferred        libx11.so.6
ELF     7e81d000-7e82b000       Deferred        libxext.so.6
ELF     7e82b000-7e8ac000       Deferred        opengl32<elf>
  \-PE  7e840000-7e8ac000       \               opengl32
ELF     7e8ac000-7e8d9000       Deferred        ws2_32<elf>
  \-PE  7e8c0000-7e8d9000       \               ws2_32
ELF     7e8d9000-7e976000       Deferred        oleaut32<elf>
  \-PE  7e8f0000-7e976000       \               oleaut32
ELF     7e976000-7e989000       Deferred        libresolv.so.2
ELF     7e989000-7e9a7000       Deferred        iphlpapi<elf>
  \-PE  7e990000-7e9a7000       \               iphlpapi
ELF     7e9a7000-7ea00000       Deferred        rpcrt4<elf>
  \-PE  7e9b0000-7ea00000       \               rpcrt4
ELF     7ea00000-7ea9f000       Deferred        ole32<elf>
  \-PE  7ea10000-7ea9f000       \               ole32
ELF     7ea9f000-7ead2000       Deferred        winspool<elf>
  \-PE  7eab0000-7ead2000       \               winspool
ELF     7ead2000-7eb8f000       Deferred        comctl32<elf>
  \-PE  7eae0000-7eb8f000       \               comctl32
ELF     7eb8f000-7ebe8000       Deferred        shlwapi<elf>
  \-PE  7eba0000-7ebe8000       \               shlwapi
ELF     7ebe8000-7eceb000       Deferred        shell32<elf>
  \-PE  7ec00000-7eceb000       \               shell32
ELF     7eceb000-7ed8c000       Deferred        comdlg32<elf>
  \-PE  7ecf0000-7ed8c000       \               comdlg32
ELF     7ed8c000-7edd4000       Deferred        advapi32<elf>
  \-PE  7eda0000-7edd4000       \               advapi32
ELF     7edd4000-7ee6c000       Deferred        gdi32<elf>
  \-PE  7edf0000-7ee6c000       \               gdi32
ELF     7ee6c000-7efaa000       Deferred        user32<elf>
  \-PE  7ee90000-7efaa000       \               user32
ELF     7efaa000-7efb5000       Deferred        libnss_files.so.2
ELF     7efb5000-7efcc000       Deferred        libnsl.so.1
ELF     7efcc000-7eff3000       Deferred        libm.so.6
ELF     7eff3000-7eff6000       Deferred        libxau.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     f7d50000-f7d52000       Deferred        libnvidia-tls.so.1
ELF     f7d52000-f7d5b000       Deferred        libnss_compat.so.2
ELF     f7d5c000-f7d60000       Deferred        libdl.so.2
ELF     f7d60000-f7ea1000       Deferred        libc.so.6
ELF     f7ea2000-f7eb9000       Deferred        libpthread.so.0
ELF     f7ec6000-f7fda000       Export          libwine.so.1
ELF     f7fdc000-f7ffa000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
00000008 (D) C:\windows\system32\lspre.exe
        00000009    0 <==


Right off the bat I noticed the GLX extension missing message and all the OpenGL messages.  What i'm not sure about is whether my wine installation went bad, or if I need to install some additional items, or if this is just an indication that the program i'm trying to run is not going to work within wine. I looked through the Synaptic Package Manager and it looks as if there is plenty of libGL related items installed and I don't want to start messing around with that stuff randomly. Like I said, i'm fairly new to this so I would appreciate any possible insight or direction, I assume i've provided enough info to help debug, but if there is anything else you might need let me know.

One more thing that might or might not be of interest. My laptop has the NVidia 8600GT graphics card. During the Ubuntu install I changed the device driver to "vesa" in the /etc/X11/xorg.conf to get it to work initially, and have not done anything since to try to update the graphics driver.

Thanks

---

### Post by Kilz on 2007-09-18
> **atomicdad said:**
> I am getting errors trying to a program under wine. A little backgound:
I'm pretty new to this.
Running Ubuntu 7.04 64 bit (***.16.... kernel) on a new Dell Inspirion 1520 laptop. I loaded/installed the 64 bit version of wine last Friday so I assume it is the latest version. I am trying to run a 32bit windows program lsprepost, which is the pre and post processing gui interface for the LSDyna finite element code.

The following is the printout from terminal window after I try to fire up the program:



Right off the bat I noticed the GLX extension missing message and all the OpenGL messages.  What i'm not sure about is whether my wine installation went bad, or if I need to install some additional items, or if this is just an indication that the program i'm trying to run is not going to work within wine. I looked through the Synaptic Package Manager and it looks as if there is plenty of libGL related items installed and I don't want to start messing around with that stuff randomly. Like I said, i'm fairly new to this so I would appreciate any possible insight or direction, I assume i've provided enough info to help debug, but if there is anything else you might need let me know.

One more thing that might or might not be of interest. My laptop has the NVidia 8600GT graphics card. During the Ubuntu install I changed the device driver to "vesa" in the /etc/X11/xorg.conf to get it to work initially, and have not done anything since to try to update the graphics driver.

Thanks

You need a accelerated graphics driver.

---

### Post by bigtom2 on 2007-09-18
Go To Nivida An Download The Missing Drivers That
Should Be All You Need . But Always Remeber Not
All Programs Work With All Computers.
I Have Been Hacking For 20 Years I Dont No It All
This Board Has A Lot Of Great Support.
Hope It Helps.

---

### Post by atomicdad on 2007-09-18
Thanks, I suspected the openGL and libGL stuff was related to the graphics board/drivers. Previously I had the 32 bit version up and I tried to run ENVY and it crashed and burned so I didn't mess with it further. Since then I put the 64bit version on and didn't go back to ENVY, I was trying some different procedures I found with little success ( I put in a different thread). I went back and downloaded ENVY last night and it appeared to succesfully update my NVidia drivers.

When I tried wine again last night it still crashed but the amount of messages was greatly reduced and I did not see any of the openGL and libGL warnings/errors. I will dig around a little more before I send out another cry for help. I do understand that the program i'm running just might not work under wine. 

Thanks

---

