---
title: "wine and wow problem - fresh install of 8.04"
date: 2008-04-30
forum: Wine
---

### Post by adt41287 on 2008-04-30
i just backed up my home folder and placed it into my fresh install of 8.04 and apt-get install wine ... and try to run wow .. but i am get this error: ```
adam@adam-desktop:~$ wine /media/storage/World\ of\ Warcraft/Wow.exe -opengl
fixme:spoolsv:serv_main (0 (nil))
err:module:attach_process_dlls "DivxDecoder.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"K:\\World of Warcraft\\Wow.exe" failed, status c0000005
```

ive looked this up and am unable to find any solutions, thanks for the hlep

---

### Post by thisismalhotra on 2008-05-01
> **adt41287 said:**
> i just backed up my home folder and placed it into my fresh install of 8.04 and apt-get install wine ... and try to run wow .. but i am get this error: ```
adam@adam-desktop:~$ wine /media/storage/World\ of\ Warcraft/Wow.exe -opengl
fixme:spoolsv:serv_main (0 (nil))
err:module:attach_process_dlls "DivxDecoder.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"K:\\World of Warcraft\\Wow.exe" failed, status c0000005
```

ive looked this up and am unable to find any solutions, thanks for the hlep

Did you setup wine after install by running winecfg first.

I think your problem is since you backed up your home directory it already has hidden folder .wine with your old configuration and so there are compatibility issue.

I would copy my WoW directory out of it and delete the whole .wine directory, remove wine and install it again.

Try this and post back the result please GL

FTW

---

### Post by adt41287 on 2008-05-01
> **thisismalhotra said:**
> Did you setup wine after install by running winecfg first.

I think your problem is since you backed up your home directory it already has hidden folder .wine with your old configuration and so there are compatibility issue.

I would copy my WoW directory out of it and delete the whole .wine directory, remove wine and install it again.

Try this and post back the result please GL

FTW

ok i removed the .wine folder and reinstalled, ran winecfg everything was set up right.. now i am just getting those last two lines of errors. 
```
adam@adam-desktop:~$ wine /media/storage/World\ of\ Warcraft/Wow.exe -opengl
err:module:attach_process_dlls "DivxDecoder.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\storage\\World of Warcraft\\Wow.exe" failed, status c0000005
```

---

### Post by adt41287 on 2008-05-01
i should probably mention also i am running on amd64 ... i keep coming across posts that people are deleting the .dll file but just made more problems so i replaced it

---

### Post by thisismalhotra on 2008-05-02
> **adt41287 said:**
> ok i removed the .wine folder and reinstalled, ran winecfg everything was set up right.. now i am just getting those last two lines of errors. 
```
adam@adam-desktop:~$ wine /media/storage/World\ of\ Warcraft/Wow.exe -opengl
err:module:attach_process_dlls "DivxDecoder.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\storage\\World of Warcraft\\Wow.exe" failed, status c0000005
```

Don't know if it matters but why is you WoW not in .wine/drive_c/Program Files but in some other directory??

Also,

1. What wine version you r using?? run ```
wine --version
```
2. How did you install wine??

---

### Post by adt41287 on 2008-05-02
> **thisismalhotra said:**
> Don't know if it matters but why is you WoW not in .wine/drive_c/Program Files but in some other directory??

im running it from a different partition... ive always done this, its always worked

> **thisismalhotra said:**
> Also,

1. What wine version you r using?? run ```
wine --version
```
2. How did you install wine??

wine --version
wine-0.9.60

and i installed it with apt-get

---

### Post by scottynou on 2008-05-02
double post

---

### Post by scottynou on 2008-05-02
Hi adt41287,

i have the same error on debian amd64... i try as you to delete the dlls divxdecoder.dll and fmd.dll and to move them in system32 directory then i got this error:

```
jonathan@SCOTTY:/media/sata1/Jeux/World of Warcraft$ wine WoW.exe -opengl
wine: Unhandled page fault on execute access to 0x00401000 at address 0x401000 (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x00401000 in 32-bit code (0x00401000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00401000 ESP:0032ff0c EBP:0032ffe8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7ee76884 ECX:e008af03 EDX:00000000
 ESI:00401000 EDI:7ffdf000
Stack dump:
0x0032ff0c:  7ee3bf58 7ffdf000 00000000 00000000
0x0032ff1c:  00000000 00000000 00000000 00000000
0x0032ff2c:  ffffffff 7ee3bfe0 7ee072e0 7ee76884
0x0032ff3c:  ffe04016 ffe04664 0032ffe8 71fe21fe
0x0032ff4c:  d37e0b03 00000000 00000000 00000000
0x0032ff5c:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x00401000 EntryPoint() in wow (0x0032ffe8)
  2 0xf7dedb47 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00401000 EntryPoint in wow: call      0x0063c8c0
Modules:
Module  Address                 Debug info      Name (84 modules)
PE        330000-  3c0000       Deferred        fmod
PE        400000-  cf9000       Export          wow
PE      10000000-10069000       Deferred        divxdecoder
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d17e000-7d192000       Deferred        midimap<elf>
  \-PE  7d180000-7d192000       \               midimap
ELF     7d192000-7d1aa000       Deferred        msacm32<elf>
  \-PE  7d1a0000-7d1aa000       \               msacm32
ELF     7d530000-7d562000       Deferred        uxtheme<elf>
  \-PE  7d540000-7d562000       \               uxtheme
ELF     7d562000-7d56b000       Deferred        libxcursor.so.1
ELF     7d56b000-7d570000       Deferred        libxfixes.so.3
ELF     7d570000-7d573000       Deferred        libxcomposite.so.1
ELF     7d573000-7d57b000       Deferred        libxrender.so.1
ELF     7d593000-7d62c000       Deferred        winex11<elf>
  \-PE  7d5a0000-7d62c000       \               winex11
ELF     7d639000-7d659000       Deferred        libexpat.so.1
ELF     7d659000-7d682000       Deferred        libfontconfig.so.1
ELF     7d682000-7d697000       Deferred        libz.so.1
ELF     7d697000-7d706000       Deferred        libfreetype.so.6
ELF     7d706000-7d70c000       Deferred        libxrandr.so.2
ELF     7d71e000-7d73f000       Deferred        mpr<elf>
  \-PE  7d720000-7d73f000       \               mpr
ELF     7d73f000-7d78d000       Deferred        wininet<elf>
  \-PE  7d750000-7d78d000       \               wininet
ELF     7d78d000-7d7f8000       Deferred        msvcrt<elf>
  \-PE  7d7a0000-7d7f8000       \               msvcrt
ELF     7d7f8000-7d81f000       Deferred        msacm32<elf>
  \-PE  7d800000-7d81f000       \               msacm32
ELF     7d81f000-7d881000       Deferred        rpcrt4<elf>
  \-PE  7d830000-7d881000       \               rpcrt4
ELF     7d881000-7d924000       Deferred        ole32<elf>
  \-PE  7d890000-7d924000       \               ole32
ELF     7d924000-7d9b3000       Deferred        winmm<elf>
  \-PE  7d930000-7d9b3000       \               winmm
ELF     7d9d1000-7d9f1000       Deferred        imm32<elf>
  \-PE  7d9e0000-7d9f1000       \               imm32
ELF     7da55000-7e56a000       Deferred        libglcore.so.1
ELF     7e56a000-7e56f000       Deferred        libxdmcp.so.6
ELF     7e56f000-7e572000       Deferred        libxau.so.6
ELF     7e572000-7e616000       Deferred        libgl.so.1
ELF     7e616000-7e702000       Deferred        libx11.so.6
ELF     7e702000-7e710000       Deferred        libxext.so.6
ELF     7e710000-7e727000       Deferred        libice.so.6
ELF     7e727000-7e72f000       Deferred        libsm.so.6
ELF     7e72f000-7e7b0000       Deferred        opengl32<elf>
  \-PE  7e740000-7e7b0000       \               opengl32
ELF     7e7b0000-7e7c3000       Deferred        libresolv.so.2
ELF     7e7c3000-7e7e1000       Deferred        iphlpapi<elf>
  \-PE  7e7d0000-7e7e1000       \               iphlpapi
ELF     7e7e1000-7e80d000       Deferred        ws2_32<elf>
  \-PE  7e7f0000-7e80d000       \               ws2_32
ELF     7e80d000-7e827000       Deferred        wsock32<elf>
  \-PE  7e810000-7e827000       \               wsock32
ELF     7e827000-7e881000       Deferred        shlwapi<elf>
  \-PE  7e830000-7e881000       \               shlwapi
ELF     7e881000-7e98d000       Deferred        shell32<elf>
  \-PE  7e890000-7e98d000       \               shell32
ELF     7e98d000-7ea29000       Deferred        gdi32<elf>
  \-PE  7e9a0000-7ea29000       \               gdi32
ELF     7ea29000-7eb73000       Deferred        user32<elf>
  \-PE  7ea40000-7eb73000       \               user32
ELF     7eb73000-7ec36000       Deferred        comctl32<elf>
  \-PE  7eb80000-7ec36000       \               comctl32
ELF     7ec36000-7ec88000       Deferred        advapi32<elf>
  \-PE  7ec40000-7ec88000       \               advapi32
ELF     7edc2000-7eef0000       Deferred        kernel32<elf>
  \-PE  7ede0000-7eef0000       \               kernel32
ELF     7eef0000-7eefb000       Deferred        libnss_files.so.2
ELF     7eefb000-7ef05000       Deferred        libnss_nis.so.2
ELF     7ef05000-7ef1d000       Deferred        libnsl.so.1
ELF     7ef1d000-7ef42000       Deferred        libm.so.6
ELF     7ef44000-7ef47000       Deferred        libxinerama.so.1
ELF     7ef55000-7ef58000       Deferred        iso8859-1.so
ELF     7ef5a000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef70000-7f000000       \               ntdll
ELF     f7c61000-f7c6a000       Deferred        libnss_compat.so.2
ELF     f7c6b000-f7c6f000       Deferred        libdl.so.2
ELF     f7c70000-f7db7000       Deferred        libc.so.6
ELF     f7db7000-f7dce000       Deferred        libpthread.so.0
ELF     f7dce000-f7dd0000       Deferred        libnvidia-tls.so.1
ELF     f7de1000-f7de6000       Deferred        libxxf86vm.so.1
ELF     f7de6000-f7f1c000       Dwarf           libwine.so.1
ELF     f7f1f000-f7f3d000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) F:\Jeux\World of Warcraft\WoW.exe
        00000009    0 <==
0000000c
        00000014    0
        00000013    0
        0000000e    0
        0000000d    0
0000000f
        00000015    0
        00000012    0
        00000011    0
        00000010    0
00000016
        00000017    0
Backtrace:
=>1 0x00401000 EntryPoint() in wow (0x0032ffe8)
  2 0xf7dedb47 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

I got this error "libwine.so.1" with many apps

---

### Post by thisismalhotra on 2008-05-05
Try the 64 bit instructions here 

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by adt41287 on 2008-05-05
work great with wine-0.9.61 now :)

---

### Post by thisismalhotra on 2008-05-05
> **adt41287 said:**
> work great with wine-0.9.61 now :)

GREAT can you make the thread solved pls so that other user can benefit...

THANKS

---

### Post by adt41287 on 2008-05-05
i dont see how to mark a thread as solved... it used to be in thread tools.. did they change it?

---

### Post by thisismalhotra on 2008-05-06
> **adt41287 said:**
> i dont see how to mark a thread as solved... it used to be in thread tools.. did they change it?

guess they did ... anyways enjoy .. 

For the Horde ... :lolflag:

---

### Post by Kemon on 2009-03-04
> **adt41287 said:**
> i just backed up my home folder and placed it into my fresh install of 8.04 and apt-get install wine ... and try to run wow .. but i am get this error: ```
adam@adam-desktop:~$ wine /media/storage/World\ of\ Warcraft/Wow.exe -opengl
fixme:spoolsv:serv_main (0 (nil))
err:module:attach_process_dlls "DivxDecoder.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"K:\\World of Warcraft\\Wow.exe" failed, status c0000005
```

ive looked this up and am unable to find any solutions, thanks for the hlep

Hi, I just got the same problem. I have this code to add my secound disk(1TB)

If it's your secound disk, you can do this =)

```
UUID=0B23878508C97937 /data ntfs auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0
```
But I tryed to edit it to what I had before I got the error.
```
UUID=0B23878508C97937 /data ntfs rw 0 0
```
You can also use: /dev/x, but you can also get the UUID.
```
vol_id -u /dev/sdb1
```

---

