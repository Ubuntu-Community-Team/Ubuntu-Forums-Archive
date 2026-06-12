---
title: "Fifa 08 - Screen turns turquoise"
date: 2008-05-26
forum: Wine
---

### Post by nagao88 on 2008-05-26
Hi guys, here's what happened when I tried to run Fifa 08 on wine:

Installation was fine.
Display, sound, everything was fine.
I could even manage my team, etc. But when I tried to actually play a game, when it goes to the loading screen, the screen just turns turquoise for about 5 seconds, then the game crashes. 

Any idea what to do?

---

### Post by alexzy on 2008-06-06
Hi there .... don't be happy yet because I have the same problem, and no solution to it

I try to run fifa 08 in wine, as everyone says it's possible.With vertex shader on and pixel shader off i am able to enter the game, everything works fine.

However, when I start the actual game, after it loads, it displays nothing but a diagonal line with different shades of gray on each side ... and it eventualy gets to display team arrangements and crashes.

Should I post the output as anyone to help me ?

My machine is a Athlon64 3000 with geforce FX 5200 graphics card, running a 8.04 ubuntu x86_64, wine 1.0 rc3, tried with 9.59 also.

> 
fixme:d3d9:D3DPERF_SetMarker (color 0xffffffff, name L"Binding Vertex Shader: DATexture[0]") : stub
fixme:d3d9:D3DPERF_SetMarker (color 0xffffffff, name L"Binding Vertex Shader: DATexture[0]") : stub
wine: Unhandled page fault on read access to 0x0000002c at address 0x71b0bc (thread 001a), starting debugger...
Unhandled exception: page fault on read access to 0x0000002c in 32-bit code (0x0071b0bc).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0071b0bc ESP:01aafb94 EBP:01e52470 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:0726f400 EBX:00000000 ECX:00000000 EDX:01aafbc0
 ESI:01e52470 EDI:00000ba0
Stack dump:
0x01aafb94:  0726f400 00000000 00000ba0 01aafbc0
0x01aafba4:  00000000 00000010 00000ba0 00000000
0x01aafbb4:  0071c041 052d0f00 00000ba0 00000000
0x01aafbc4:  01e56810 0000000c 00000000 03028a58
0x01aafbd4:  01e52470 00000000 00718f22 00000000
0x01aafbe4:  01e5f8e0 052fed50 00000001 007131a3
Backtrace:
=>1 0x0071b0bc in euro08 (+0x31b0bc) (0x01e52470)
  2 0x0726f400 (0x0086b940)
  3 0x0071a2e0 in euro08 (+0x31a2e0) (0x0071b060)
  4 0xc0850446 (0x8bf18b56)
0x0071b0bc: call	*0x2c(%ecx)
Modules:
Module	Address			Debug info	Name (104 modules)
PE	  340000-  352000	Deferred        xinput9_1_0
PE	  3a0000-  3cd000	Deferred        xpadlib
PE	  400000- 17a2000	Export          euro08
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c2a7000-7c2bb000	Deferred        lz32<elf>
  \-PE	7c2b0000-7c2bb000	\               lz32
ELF	7c2bb000-7c322000	Deferred        setupapi<elf>
  \-PE	7c2d0000-7c322000	\               setupapi
ELF	7c80e000-7c827000	Deferred        version<elf>
  \-PE	7c810000-7c827000	\               version
ELF	7c88c000-7c8b2000	Deferred        dmusic<elf>
  \-PE	7c890000-7c8b2000	\               dmusic
ELF	7ce5b000-7d970000	Deferred        libglcore.so.1
ELF	7d970000-7da14000	Deferred        libgl.so.1
ELF	7e06e000-7e0a1000	Deferred        uxtheme<elf>
  \-PE	7e070000-7e0a1000	\               uxtheme
ELF	7e0a1000-7e0c7000	Deferred        msacm32<elf>
  \-PE	7e0b0000-7e0c7000	\               msacm32
ELF	7e0c7000-7e0de000	Deferred        msacm32<elf>
  \-PE	7e0d0000-7e0de000	\               msacm32
ELF	7e0de000-7e1a1000	Deferred        libasound.so.2
ELF	7e1a1000-7e1b5000	Deferred        midimap<elf>
  \-PE	7e1b0000-7e1b5000	\               midimap
ELF	7e1b5000-7e1eb000	Deferred        winealsa<elf>
  \-PE	7e1c0000-7e1eb000	\               winealsa
ELF	7e213000-7e21c000	Deferred        libxcursor.so.1
ELF	7e21c000-7e221000	Deferred        libxfixes.so.3
ELF	7e221000-7e224000	Deferred        libxcomposite.so.1
ELF	7e224000-7e22a000	Deferred        libxrandr.so.2
ELF	7e22a000-7e232000	Deferred        libxrender.so.1
ELF	7e232000-7e235000	Deferred        libxinerama.so.1
ELF	7e235000-7e23a000	Deferred        libxdmcp.so.6
ELF	7e23a000-7e252000	Deferred        libxcb.so.1
ELF	7e252000-7e255000	Deferred        libxau.so.6
ELF	7e255000-7e33c000	Deferred        libx11.so.6
ELF	7e33c000-7e34a000	Deferred        libxext.so.6
ELF	7e34a000-7e34f000	Deferred        libxxf86vm.so.1
ELF	7e35f000-7e361000	Deferred        libnvidia-tls.so.1
ELF	7e363000-7e3fa000	Deferred        winex11<elf>
  \-PE	7e370000-7e3fa000	\               winex11
ELF	7e415000-7e436000	Deferred        libexpat.so.1
ELF	7e436000-7e460000	Deferred        libfontconfig.so.1
ELF	7e460000-7e475000	Deferred        libz.so.1
ELF	7e475000-7e4e5000	Deferred        libfreetype.so.6
ELF	7e4e5000-7e4e7000	Deferred        libxcb-xlib.so.0
ELF	7e4f9000-7e516000	Deferred        tapi32<elf>
  \-PE	7e500000-7e516000	\               tapi32
ELF	7e516000-7e5d5000	Deferred        comctl32<elf>
  \-PE	7e520000-7e5d5000	\               comctl32
ELF	7e5d5000-7e62e000	Deferred        shlwapi<elf>
  \-PE	7e5e0000-7e62e000	\               shlwapi
ELF	7e62e000-7e73e000	Deferred        shell32<elf>
  \-PE	7e640000-7e73e000	\               shell32
ELF	7e73e000-7e7e0000	Deferred        oleaut32<elf>
  \-PE	7e750000-7e7e0000	\               oleaut32
ELF	7e7e0000-7e80c000	Deferred        ws2_32<elf>
  \-PE	7e7f0000-7e80c000	\               ws2_32
ELF	7e80c000-7e832000	Deferred        netapi32<elf>
  \-PE	7e810000-7e832000	\               netapi32
ELF	7e832000-7e852000	Deferred        imm32<elf>
  \-PE	7e840000-7e852000	\               imm32
ELF	7e852000-7e8e4000	Deferred        winmm<elf>
  \-PE	7e860000-7e8e4000	\               winmm
ELF	7e8e4000-7e92e000	Deferred        dsound<elf>
  \-PE	7e8f0000-7e92e000	\               dsound
ELF	7e92e000-7e965000	Deferred        dinput<elf>
  \-PE	7e940000-7e965000	\               dinput
ELF	7e965000-7e97d000	Deferred        dinput8<elf>
  \-PE	7e970000-7e97d000	\               dinput8
ELF	7e97d000-7e990000	Deferred        libresolv.so.2
ELF	7e991000-7e9a4000	Deferred        sensapi<elf>
  \-PE	7e9a0000-7e9a4000	\               sensapi
ELF	7e9a4000-7e9c2000	Deferred        iphlpapi<elf>
  \-PE	7e9b0000-7e9c2000	\               iphlpapi
ELF	7e9c2000-7ea23000	Deferred        rpcrt4<elf>
  \-PE	7e9d0000-7ea23000	\               rpcrt4
ELF	7ea23000-7eac7000	Deferred        ole32<elf>
  \-PE	7ea30000-7eac7000	\               ole32
ELF	7eac7000-7eb1e000	Deferred        ddraw<elf>
  \-PE	7ead0000-7eb1e000	\               ddraw
ELF	7eb1e000-7ebb9000	Deferred        gdi32<elf>
  \-PE	7eb30000-7ebb9000	\               gdi32
ELF	7ebb9000-7ed00000	Deferred        user32<elf>
  \-PE	7ebd0000-7ed00000	\               user32
ELF	7ed00000-7ee02000	Deferred        wined3d<elf>
  \-PE	7ed10000-7ee02000	\               wined3d
ELF	7ee02000-7ee32000	Deferred        d3d9<elf>
  \-PE	7ee10000-7ee32000	\               d3d9
ELF	7ee32000-7ee84000	Deferred        advapi32<elf>
  \-PE	7ee40000-7ee84000	\               advapi32
ELF	7efa4000-7efaf000	Deferred        libnss_files.so.2
ELF	7efaf000-7efc7000	Deferred        libnsl.so.1
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	7efed000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	f7cb6000-f7cba000	Deferred        libdl.so.2
ELF	f7cba000-f7e09000	Deferred        libc.so.6
ELF	f7e0a000-f7e22000	Deferred        libpthread.so.0
ELF	f7e36000-f7f6c000	Deferred        libwine.so.1
ELF	f7f6e000-f7f8d000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000019 (D) C:\Program Files\EA Sports\UEFA EURO 2008\EURO08.exe
	00000025   15
	00000024    1
	00000023    0
	00000022    2
	00000021    2
	00000020    1
	0000001f    1
	0000001e   15
	0000001d    2
	0000001a    0 <==
0000001b 
	0000001c    0
Backtrace:
=>1 0x0071b0bc in euro08 (+0x31b0bc) (0x01e52470)
  2 0x0726f400 (0x0086b940)
  3 0x0071a2e0 in euro08 (+0x31a2e0) (0x0071b060)
  4 0xc0850446 (0x8bf18b56)


---

