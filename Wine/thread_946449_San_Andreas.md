---
title: "San Andreas"
date: 2008-10-13
forum: Wine
---

### Post by xblackxphoenix on 2008-10-13
Hey guys, I'm using hardy 8.04 and wine 1.1.6
thinkpad t61
1gig ram
Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
(vice city runs beautifully but gta 3 runs like crap because the mouse keeps leaving the virtual desktop)



San Andreas installed and launches to the menu with the mouse as a white box and menu items as blue boxes, but when i try to start a new game it plays the sound it makes when you start a new game, then freezes, and then crashes. the sound is no problem, it plays perfectly in the Audio Option menu. i tried in cedega, too, but it didn't even start in cedega. 
anybody know whats up?





```
blackphoenix@Phoenix:~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas$ wine "gta_sa.exe"
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:win:EnumDisplayDevicesW ((null),0,0x177f74c,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x12e008) : stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
fixme:wave:DSD_CreateSecondaryBuffer (0x1e2058,0x177fcc4,8014,0,0x1e5dc0,0x1e5ecc,0x1e5da0): stub
Initialised SoundManager
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(800,600)
wine: Unhandled page fault on write access to 0x00000050 at address 0x5dd97c (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000050 in 32-bit code (0x005dd97c).
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 088d8601 in module L"gta_sa"
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:005dd97c ESP:0177fd00 EBP:7ed461e0 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:00000000 ECX:00000158 EDX:020e4468
 ESI:00000010 EDI:00000001
Stack dump:
0x0177fd00:  0086c074 00000000 00000000 00000010
0x0177fd10:  00000010 0086c080 00000000 0000000f
0x0177fd20:  02ca2240 0177fef8 0083cc4b 00000000
0x0177fd30:  005bf8ef 00863b10 0053bc8b 00863b10
0x0177fd40:  0000000a 0053e593 00863b10 00748d00
0x0177fd50:  7b8670b0 00000000 0177ff08 7b8b4f68
Backtrace:
=>1 0x005dd97c in gta_sa (+0x1dd97c) (0x7ed461e0)
  2 0x000248ec (0x81e58955)
0x005dd97c: movb	$0x2,0x50(%eax)
Modules:
Module	Address			Debug info	Name (107 modules)
PE	  230000-  239000	Deferred        ogg
PE	  240000-  348000	Deferred        vorbis
PE	  350000-  380000	Deferred        eax
PE	  400000- 1577000	Export          gta_sa
PE	10000000-10011000	Deferred        vorbisfile
ELF	791d0000-792b7000	Deferred        oleaut32<elf>
  \-PE	791f0000-792b7000	\               oleaut32
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7b995000-7b9ef000	Deferred        shlwapi<elf>
  \-PE	7b9a0000-7b9ef000	\               shlwapi
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7bf0b000-7bf1f000	Deferred        avicap32<elf>
  \-PE	7bf10000-7bf1f000	\               avicap32
ELF	7bf1f000-7bf3f000	Deferred        devenum<elf>
  \-PE	7bf20000-7bf3f000	\               devenum
ELF	7bf3f000-7c000000	Deferred        comctl32<elf>
  \-PE	7bf50000-7c000000	\               comctl32
ELF	7c455000-7c488000	Deferred        uxtheme<elf>
  \-PE	7c460000-7c488000	\               uxtheme
ELF	7c488000-7c49c000	Deferred        lz32<elf>
  \-PE	7c490000-7c49c000	\               lz32
ELF	7c49c000-7c4b5000	Deferred        version<elf>
  \-PE	7c4a0000-7c4b5000	\               version
ELF	7c4b5000-7c4de000	Deferred        msvfw32<elf>
  \-PE	7c4c0000-7c4de000	\               msvfw32
ELF	7c4de000-7c54d000	Deferred        quartz<elf>
  \-PE	7c4f0000-7c54d000	\               quartz
ELF	7c54d000-7c57d000	Deferred        d3d9<elf>
  \-PE	7c550000-7c57d000	\               d3d9
ELF	7c57d000-7c5b5000	Deferred        dinput<elf>
  \-PE	7c590000-7c5b5000	\               dinput
ELF	7c5b5000-7c5cd000	Deferred        dinput8<elf>
  \-PE	7c5c0000-7c5cd000	\               dinput8
ELF	7c5cd000-7c617000	Deferred        dsound<elf>
  \-PE	7c5d0000-7c617000	\               dsound
ELF	7df17000-7e14e000	Deferred        i965_dri.so
ELF	7e14e000-7e158000	Deferred        libdrm.so.2
ELF	7e158000-7e15b000	Deferred        libxdamage.so.1
ELF	7e15b000-7e1bd000	Deferred        libgl.so.1
ELF	7e1c6000-7e1d1000	Deferred        libgcc_s.so.1
ELF	7e1d3000-7e268000	Deferred        opengl32<elf>
  \-PE	7e1f0000-7e268000	\               opengl32
ELF	7e290000-7e3a1000	Deferred        wined3d<elf>
  \-PE	7e2a0000-7e3a1000	\               wined3d
ELF	7e3a1000-7e3fa000	Deferred        ddraw<elf>
  \-PE	7e3b0000-7e3fa000	\               ddraw
ELF	7e60b000-7e632000	Deferred        msacm32<elf>
  \-PE	7e610000-7e632000	\               msacm32
ELF	7e632000-7e649000	Deferred        msacm32<elf>
  \-PE	7e640000-7e649000	\               msacm32
ELF	7e649000-7e684000	Deferred        wineoss<elf>
  \-PE	7e650000-7e684000	\               wineoss
ELF	7e684000-7e68d000	Deferred        libxcursor.so.1
ELF	7e68d000-7e692000	Deferred        libxfixes.so.3
ELF	7e692000-7e695000	Deferred        libxcomposite.so.1
ELF	7e695000-7e69b000	Deferred        libxrandr.so.2
ELF	7e69b000-7e6a3000	Deferred        libxrender.so.1
ELF	7e6a3000-7e6a8000	Deferred        libxxf86vm.so.1
ELF	7e6a8000-7e6ab000	Deferred        libxinerama.so.1
ELF	7e6ab000-7e6cb000	Deferred        imm32<elf>
  \-PE	7e6b0000-7e6cb000	\               imm32
ELF	7e6cb000-7e6d0000	Deferred        libxdmcp.so.6
ELF	7e6d0000-7e6e8000	Deferred        libxcb.so.1
ELF	7e6e8000-7e6ea000	Deferred        libxcb-xlib.so.0
ELF	7e6ea000-7e7d1000	Deferred        libx11.so.6
ELF	7e7d1000-7e7df000	Deferred        libxext.so.6
ELF	7e7df000-7e7f7000	Deferred        libice.so.6
ELF	7e7f7000-7e7ff000	Deferred        libsm.so.6
ELF	7e7ff000-7e813000	Deferred        midimap<elf>
  \-PE	7e800000-7e813000	\               midimap
ELF	7e815000-7e8ad000	Deferred        winex11<elf>
  \-PE	7e820000-7e8ad000	\               winex11
ELF	7e8f3000-7e914000	Deferred        libexpat.so.1
ELF	7e914000-7e93e000	Deferred        libfontconfig.so.1
ELF	7e93e000-7e953000	Deferred        libz.so.1
ELF	7e953000-7e9c0000	Deferred        libfreetype.so.6
ELF	7e9c0000-7e9d3000	Deferred        libresolv.so.2
ELF	7e9d3000-7e9d6000	Deferred        libxau.so.6
ELF	7e9e9000-7ea08000	Deferred        iphlpapi<elf>
  \-PE	7e9f0000-7ea08000	\               iphlpapi
ELF	7ea08000-7ea6d000	Deferred        rpcrt4<elf>
  \-PE	7ea10000-7ea6d000	\               rpcrt4
ELF	7ea6d000-7eb76000	Deferred        ole32<elf>
  \-PE	7ea90000-7eb76000	\               ole32
ELF	7eb76000-7eba2000	Deferred        ws2_32<elf>
  \-PE	7eb80000-7eba2000	\               ws2_32
ELF	7eba2000-7ebf6000	Deferred        advapi32<elf>
  \-PE	7ebb0000-7ebf6000	\               advapi32
ELF	7ebf6000-7ec94000	Deferred        gdi32<elf>
  \-PE	7ec10000-7ec94000	\               gdi32
ELF	7ec94000-7eddd000	Deferred        user32<elf>
  \-PE	7ecb0000-7eddd000	\               user32
ELF	7eddd000-7ee6f000	Deferred        winmm<elf>
  \-PE	7edf0000-7ee6f000	\               winmm
ELF	7ef8f000-7ef9a000	Deferred        libnss_files.so.2
ELF	7ef9a000-7efa4000	Deferred        libnss_nis.so.2
ELF	7efa4000-7efbc000	Deferred        libnsl.so.1
ELF	7efbc000-7efc5000	Deferred        libnss_compat.so.2
ELF	7efc5000-7efea000	Deferred        libm.so.6
ELF	b7cf3000-b7cf7000	Deferred        libdl.so.2
ELF	b7cf7000-b7e46000	Deferred        libc.so.6
ELF	b7e47000-b7e5f000	Deferred        libpthread.so.0
ELF	b7e75000-b7fab000	Deferred        libwine.so.1
ELF	b7fad000-b7fc9000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Rockstar Games\GTA San Andreas\gta_sa.exe
	00000022    0
	00000021    0
	00000020   15
	0000001c    0
	0000001b   15
	00000017    0
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000018 
	00000019    0
Backtrace:
=>1 0x005dd97c in gta_sa (+0x1dd97c) (0x7ed461e0)
  2 0x000248ec (0x81e58955)
fixme:winmm:MMDRV_Exit Closing while ll-driver open
blackphoenix@Phoenix:~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas$ 
```

---

### Post by homemadejam on 2008-10-13
Have you tried emulating a virtual desktop in winecfg ?
I remember I had problems with getting it to run fine when I first installed it onto my old computer.

Jam

---

### Post by xblackxphoenix on 2008-10-13
> **homemadejam said:**
> Have you tried emulating a virtual desktop in winecfg ?
I remember I had problems with getting it to run fine when I first installed it onto my old computer.

Jam

yea i use a virtual desktop

---

### Post by RealG187 on 2008-10-13
Does this game work with Wine?

Do I need to configure anything fancy other than use a virtual desktop?

---

### Post by RuleMaker on 2008-11-30
Try replacing the compiz with metacity.

---

### Post by wirate on 2009-08-23
same problem
tried metacity and emulating virtual desktop. no difference. this is the output when i run san andreas in terminal

fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8c5, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)

---

### Post by hikaricore on 2009-08-24
ffs don't bump a year old thread.

---

### Post by wirate on 2009-08-24
start a new thread instead?

---

