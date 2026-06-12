---
title: "Little Fighter 2 with Wine or other emulatior"
date: 2006-10-23
forum: Wine
---

### Post by OlaRune on 2006-10-23
This is my first thread in these forums. I just registered but have read threads here for a long time. I've had some problems and found every answer here. This is the first time I didn't find the answer.

I want to play the windows game Little Fighter 2 and have tried using Wine for this.

The game can be found here: [http://lf2.net/download_1.html#](http://lf2.net/download_1.html#)

I downloaded the installation file and installed it using wine. This went well but when i tried to play the game a window popped up but then closed again.

The output in the terminal is:

```

root@Racer:/home/olarune# wine /home/olarune/LF2_v1.9c/lf2.exe
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd46c50)->(0x10022,00000008)fixme:wave:DSD_CreateSecondaryBuffer (0x7fd492a0,0x7fb9fcbc,e0,0,0x7fd69ddc,0x7fd465e4,0x7fd69db8): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x7fd492a0,0x7fb9fcbc,e0,0,0x7fd69f54,0x7fd6a064,0x7fd69f30): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x7fd492a0,0x7fb9fcbc,e0,0,0x7fd6a104,0x7fd6a214,0x7fd6a0e0): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x7fd492a0,0x7fb9fcbc,e0,0,0x7fda25cc,0x7fda26bc,0x7fda25a8): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x7fd492a0,0x7fb9fcbc,e0,0,0x7e1acb84,0x7e1acc74,0x7e1acb60): stub
fixme:ddraw:DIB_DirectDrawSurface_Blt Can't handle DDBLT_WAIT flag right now.
wine: Unhandled page fault on write access to 0x00000004 at address 0x43d038 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
First chance exception: page fault on read access to 0x00000000 in 32-bit code (0x7ff9c26c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7ff9c26c ESP:7fb9edd0 EBP:7fb9ee98 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7ffd51fc ECX:00000000 EDX:00000000
 ESI:00000000 EDI:00000002
Stack dump:
0x7fb9edd0:  7fb9edf0 00000001 7ff9a545 7e1f6df0
0x7fb9ede0:  00000001 7fb9f240 7ff94134 00000001
0x7fb9edf0:  7ffd51fc 00000000 00000002 7fb9ee98
0x7fb9ee00:  7fb9edd0 7ff9c263 00000001 00000000
0x7fb9ee10:  00000000 7fb9ee64 7ff9ae31 7fcf0000
0x7fb9ee20:  00000001 7e150000 7ff8df80 00000001
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ff9c26c RtlImageNtHeader+0x5f in ntdll (0x7ff9c26c)
  2 0x7ff9c390 RtlImageDirectoryEntryToData+0x34 in ntdll (0x7ff9c390)
  3 0x7fc2eedc UnhandledExceptionFilter+0x11b in kernel32 (0x7fc2eedc)
  4 0x7ff94175 __wine_exception_handler+0x41 in ntdll (0x7ff94175)
  5 0x7ffb6829 call_exception_handler+0x29 in ntdll (0x7ffb6829)
  6 0x7ffb67fd EXC_CallHandler+0x1d in ntdll (0x7ffb67fd)
  7 0x7ff948dd in ntdll (+0x148dd) (0x7ff948dd)
  8 0x7ff94991 __regs_RtlRaiseException+0x25 in ntdll (0x7ff94991)
  9 0x7ffb69a7 call_exception_handler+0x1a7 in ntdll (0x7ffb69a7)
  10 0xdeadbabe (0xdeadbabe)
  11 0x0043a711 in lf2 (+0x3a711) (0x0043a711)
  12 0x00000000 (0x00000000)
0x7ff9c26c RtlImageNtHeader+0x5f in ntdll: cmpw $0x5a4d,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (71 modules)
PE      0x00400000-00812000     Export          lf2
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e491000-7e4a5000     Deferred        joystick<elf>
  \-PE  0x7e4a0000-7e4a5000     \               joystick
ELF     0x7f05b000-7f070000     Deferred        midimap<elf>
  \-PE  0x7f060000-7f070000     \               midimap
ELF     0x7f182000-7f1a8000     Deferred        msacm32<elf>
  \-PE  0x7f190000-7f1a8000     \               msacm32
ELF     0x7f1a8000-7f1c0000     Deferred        msacm<elf>
  \-PE  0x7f1b0000-7f1c0000     \               msacm
ELF     0x7f1c0000-7f204000     Deferred        wineoss<elf>
  \-PE  0x7f1d0000-7f204000     \               wineoss
ELF     0x7f222000-7f226000     Deferred        libxfixes.so.3
ELF     0x7f226000-7f22f000     Deferred        libxcursor.so.1
ELF     0x7f22f000-7f24b000     Deferred        imm32<elf>
  \-PE  0x7f240000-7f24b000     \               imm32
ELF     0x7f24b000-7f253000     Deferred        libxrender.so.1
ELF     0x7f253000-7f25a000     Deferred        libdrm.so.2
ELF     0x7f25a000-7f2c0000     Deferred        libgl.so.1
ELF     0x7f2c0000-7f343000     Deferred        winex11<elf>
  \-PE  0x7f2d0000-7f343000     \               winex11
ELF     0x7f343000-7f362000     Deferred        libexpat.so.1
ELF     0x7f362000-7f390000     Deferred        libfontconfig.so.1
ELF     0x7f390000-7f3a4000     Deferred        libz.so.1
ELF     0x7f3a4000-7f40d000     Deferred        libfreetype.so.6
ELF     0x7f40d000-7f438000     Deferred        ws2_32<elf>
  \-PE  0x7f420000-7f438000     \               ws2_32
ELF     0x7f438000-7f452000     Deferred        wsock32<elf>
  \-PE  0x7f440000-7f452000     \               wsock32
ELF     0x7f452000-7f4a4000     Deferred        dsound<elf>
  \-PE  0x7f460000-7f4a4000     \               dsound
ELF     0x7f4a4000-7f52c000     Deferred        winmm<elf>
  \-PE  0x7f4b0000-7f52c000     \               winmm
ELF     0x7f52c000-7f612000     Deferred        libx11.so.6
ELF     0x7f612000-7f62a000     Deferred        libice.so.6
ELF     0x7f62a000-7f6a5000     Deferred        ddraw<elf>
  \-PE  0x7f650000-7f6a5000     \               ddraw
ELF     0x7f6a5000-7f6c4000     Deferred        iphlpapi<elf>
  \-PE  0x7f6b0000-7f6c4000     \               iphlpapi
ELF     0x7f6c4000-7f70d000     Deferred        rpcrt4<elf>
  \-PE  0x7f6d0000-7f70d000     \               rpcrt4
ELF     0x7f70d000-7f79e000     Deferred        ole32<elf>
  \-PE  0x7f720000-7f79e000     \               ole32
ELF     0x7f79e000-7f7de000     Deferred        advapi32<elf>
  \-PE  0x7f7b0000-7f7de000     \               advapi32
ELF     0x7f8b3000-7f964000     Deferred        gdi32<elf>
  \-PE  0x7f8d0000-7f964000     \               gdi32
ELF     0x7f964000-7fa90000     Deferred        user32<elf>
  \-PE  0x7f980000-7fa90000     \               user32
ELF     0x7fba0000-7fba3000     Deferred        libxrandr.so.2
ELF     0x7fba3000-7fbb0000     Deferred        libxext.so.6
ELF     0x7fbb3000-7fbb6000     Deferred        libxau.so.6
ELF     0x7fbb6000-7fbbb000     Deferred        libxxf86vm.so.1
ELF     0x7fbee000-7fcf0000     Export          kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe01000-7fe0b000     Deferred        libgcc_s.so.1
ELF     0x7fe0b000-7fe15000     Deferred        libnss_files.so.2
ELF     0x7fe15000-7fe1e000     Deferred        libnss_nis.so.2
ELF     0x7fe1e000-7fe33000     Deferred        libnsl.so.1
ELF     0x7fe33000-7fe3c000     Deferred        libnss_compat.so.2
ELF     0x7fe3d000-7fe42000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e07000-b7e0a000     Deferred        libdl.so.2
ELF     0xb7e0a000-b7f39000     Deferred        libc.so.6
ELF     0xb7f39000-b7f4b000     Deferred        libpthread.so.0
ELF     0xb7f5a000-b7f74000     Deferred        libwine.so.1
ELF     0xb7f77000-b7f8d000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\olarune\LF2_v1.9c\lf2.exe
        0000000c   15
        0000000b   15
        0000000a    0
        00000009    0 <==

```

When I used the "Run little fighter" option in the install it worked. But otherwise I just got this output and then it crashed.

I don't know what to do from here. I would be very grateful if someone could help me to get this to work.

//OlaRune

Edit: If you can recommend any other emulator that will work i will gladly switch. I would prefer it to be freely available. Thanks once more.

//OlaRune

---

### Post by Salim on 2006-10-31
Hi,
I have a similiar problem. But I knew that that game worked once with linux and wine, although it was a bit slow. With this wine version it doesnt seem to work or its because of ubuntu (I could play it under suse 6 months ago)
I get the following error message:
```
$ wine lf2.exe 
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x16b3b0) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16a748)->(0x10024,00000008)
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_WAIT flag right now.

```
It doesnt crash, I see a black window of lf2, I can hear sound when I click somewhere, but it just doesnt draw anything.
My Wine versoin is 0.9.22

---

### Post by M4C C41N on 2007-02-19
I tried to run it with wine (latest version) but I get a "couldn't create art surface" error message when I launch "game start".

---

### Post by holodila on 2009-02-25
Anybody could overcome this problem? It's been 2 years, but I still get the "couldn't create art surface" error =)

---

### Post by holodila on 2009-03-01
I managed to make it work)) I installed vbox and vboxgtk, installed windows xp on it and everything works as a charm, at full speed on my vaio sz (core 2 duo).

---

### Post by Fernando Hernandez on 2010-01-24
I tried running this in VirtualBox in Windows 7, and it's giving me errors there, too.  Notably, this:

[http://i46.tinypic.com/2urntk0.jpg](http://i46.tinypic.com/2urntk0.jpg)

The window is...quadrupled.  It seems to play fine and everything, but it would be nice if it could be played with proper video output.  Am I missing a VBox plugin or something?  Are there any other emulators that can run the game?

---

### Post by godews on 2010-06-08
HI,

I'm searching for a way to play lf2 on linux too. Would it work with Wine and PLayOnLinux? If someone found a way tell here plz. (Note: I'm using the latest version of Ubuntu, 10.4)

About the error: "couldn't create art surface" it appears because the is a file missing and the loader cannot read it. If I remmember well, there are some versions of LF2 in what that usualy happens with wave files, so thats not critical. Just se the file that is loading when the error appear and create a short wave file with that name in  "...\lf2\data".

---

### Post by cogadh on 2010-06-09
The "couldn't create surface" error is caused by the default settings for video card memory size, not any missing files. Instructions on how to correct it can be found in [Wine's AppDB entry for the game]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14909"). However, the game doesn't really get better than a "garbage" rating from AppDB, so it might still not run.

---

