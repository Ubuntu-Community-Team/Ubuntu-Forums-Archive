---
title: "Ragnarok problems"
date: 2008-08-07
forum: Wine
---

### Post by Uzelth on 2008-08-07
Heya,

I've recently installed Wine (XP emulation) and Ragnarok Online (Legend RO)... Though the patcher won't run *at all*.

I've installed the two missing DLLs needed... The game/client runs just fine, but the patcher doesn't.  The output of running it is as follows:

**wine llragnarok.exe**
```
wine: Unhandled page fault on execute access to 0x0040160f at address 0x40160f (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x0040160f in 32-bit code (0x0040160f).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0040160f ESP:0032fe74 EBP:0032ff08 EFLAGS:00010206(   - 00      - RIP1)
 EAX:0040160f EBX:7b8b3884 ECX:7b8b3884 EDX:004168c2
 ESI:0041d004 EDI:0041157e
Stack dump:
0x0032fe74:  00411ebe 00000000 00411dec 0041d000
0x0032fe84:  0041d058 0041d05c 0041d070 00411616
0x0032fe94:  0041157e 7ffdf000 7b8b3884 c0000005
0x0032fea4:  000c000b 00180016 7ffd8c00 7ffdf000
0x0032feb4:  0041157e 0032fed8 7b868111 7ffd8c00
0x0032fec4:  00000000 00000000 00000000 7b8680d9
Backtrace:
=>1 0x0040160f in llragnarok (+0x160f) (0x0032ff08)
  2 0x7b877b27 in kernel32 (+0x57b27) (0x0032ffe8)
0x0040160f: testb	$0x1,0x00422cd8
Modules:
Module	Address			Debug info	Name (84 modules)
PE	  330000-  34a000	Deferred        pclient
PE	  400000-  429000	Export          llragnarok
PE	21100000-2115d000	Deferred        mss32
PE	22600000-22616000	Deferred        mssfast.m3d
PE	26f00000-26f2a000	Deferred        mp3dec.asi
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7df18000-7df62000	Deferred        dsound<elf>
  \-PE	7df20000-7df62000	\               dsound
ELF	7df62000-7df76000	Deferred        midimap<elf>
  \-PE	7df70000-7df76000	\               midimap
ELF	7df76000-7df9c000	Deferred        msacm32<elf>
  \-PE	7df80000-7df9c000	\               msacm32
ELF	7df9c000-7dfb3000	Deferred        msacm32<elf>
  \-PE	7dfa0000-7dfb3000	\               msacm32
ELF	7dfb3000-7e076000	Deferred        libasound.so.2
ELF	7e076000-7e0ac000	Deferred        winealsa<elf>
  \-PE	7e080000-7e0ac000	\               winealsa
ELF	7e0ac000-7e13e000	Deferred        winmm<elf>
  \-PE	7e0c0000-7e13e000	\               winmm
ELF	7e411000-7e4b3000	Deferred        oleaut32<elf>
  \-PE	7e420000-7e4b3000	\               oleaut32
ELF	7e4b3000-7e4c6000	Deferred        olepro32<elf>
  \-PE	7e4c0000-7e4c6000	\               olepro32
ELF	7e4ea000-7e4fd000	Deferred        libresolv.so.2
ELF	7e503000-7e50e000	Deferred        libgcc_s.so.1
ELF	7e50e000-7e52c000	Deferred        iphlpapi<elf>
  \-PE	7e510000-7e52c000	\               iphlpapi
ELF	7e52c000-7e58d000	Deferred        rpcrt4<elf>
  \-PE	7e540000-7e58d000	\               rpcrt4
ELF	7e58d000-7e631000	Deferred        ole32<elf>
  \-PE	7e5a0000-7e631000	\               ole32
ELF	7e659000-7e68c000	Deferred        uxtheme<elf>
  \-PE	7e660000-7e68c000	\               uxtheme
ELF	7e68c000-7e695000	Deferred        libxcursor.so.1
ELF	7e695000-7e69a000	Deferred        libxfixes.so.3
ELF	7e69a000-7e69d000	Deferred        libxcomposite.so.1
ELF	7e69d000-7e6a3000	Deferred        libxrandr.so.2
ELF	7e6a3000-7e6ab000	Deferred        libxrender.so.1
ELF	7e6ab000-7e6ae000	Deferred        libxinerama.so.1
ELF	7e6ae000-7e6ce000	Deferred        imm32<elf>
  \-PE	7e6b0000-7e6ce000	\               imm32
ELF	7e6ce000-7e6d3000	Deferred        libxdmcp.so.6
ELF	7e6d3000-7e6eb000	Deferred        libxcb.so.1
ELF	7e6eb000-7e6ed000	Deferred        libxcb-xlib.so.0
ELF	7e6ed000-7e6f0000	Deferred        libxau.so.6
ELF	7e6f0000-7e7d7000	Deferred        libx11.so.6
ELF	7e7d7000-7e7e5000	Deferred        libxext.so.6
ELF	7e7e5000-7e7ea000	Deferred        libxxf86vm.so.1
ELF	7e7fb000-7e892000	Deferred        winex11<elf>
  \-PE	7e810000-7e892000	\               winex11
ELF	7e8bd000-7e8de000	Deferred        libexpat.so.1
ELF	7e8de000-7e908000	Deferred        libfontconfig.so.1
ELF	7e919000-7e92e000	Deferred        libz.so.1
ELF	7e92e000-7e99e000	Deferred        libfreetype.so.6
ELF	7e9af000-7ea6e000	Deferred        comctl32<elf>
  \-PE	7e9c0000-7ea6e000	\               comctl32
ELF	7ea6e000-7eb81000	Deferred        shell32<elf>
  \-PE	7ea80000-7eb81000	\               shell32
ELF	7eb81000-7ebda000	Deferred        shlwapi<elf>
  \-PE	7eb90000-7ebda000	\               shlwapi
ELF	7ebda000-7ec2c000	Deferred        advapi32<elf>
  \-PE	7ebf0000-7ec2c000	\               advapi32
ELF	7ec2c000-7ecc7000	Deferred        gdi32<elf>
  \-PE	7ec40000-7ecc7000	\               gdi32
ELF	7ecc7000-7ee0e000	Deferred        user32<elf>
  \-PE	7ece0000-7ee0e000	\               user32
ELF	7ee0e000-7ee2f000	Deferred        mpr<elf>
  \-PE	7ee10000-7ee2f000	\               mpr
ELF	7ee2f000-7ee7d000	Deferred        wininet<elf>
  \-PE	7ee40000-7ee7d000	\               wininet
ELF	7ef9d000-7efa8000	Deferred        libnss_files.so.2
ELF	7efa8000-7efb2000	Deferred        libnss_nis.so.2
ELF	7efb2000-7efca000	Deferred        libnsl.so.1
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	f7c91000-f7c95000	Deferred        libdl.so.2
ELF	f7c95000-f7de4000	Deferred        libc.so.6
ELF	f7de5000-f7dfd000	Deferred        libpthread.so.0
ELF	f7e0e000-f7f44000	Deferred        libwine.so.1
ELF	f7f46000-f7f65000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Games\Lightside - Legend Ragnarok\llragnarok.exe
	00000016    0
	00000009    0 <==
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>1 0x0040160f in llragnarok (+0x160f) (0x0032ff08)
  2 0x7b877b27 in kernel32 (+0x57b27) (0x0032ffe8)
```

I'm running Ubuntu amd64 incidentally.

Any help would be much appreciated.

---

### Post by wingnux on 2008-08-07
Can you read??

[http://ubuntuforums.org/showthread.php?t=624170](http://ubuntuforums.org/showthread.php?t=624170)

---

### Post by Rocket2DMn on 2008-08-07
Moved to the Wine forum area.

---

