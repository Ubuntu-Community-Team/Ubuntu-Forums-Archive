---
title: "1996 Windows Scrabble program won't load in Wine"
date: 2016-08-09
forum: Wine
---

### Post by mr.alan.andrew on 2016-08-09
Here's the Wine output, which notes a "serious error". Could it be that the program is 16-bit?

Unhandled exception: stack overflow in 32-bit code (0x7bc27d03).
Register dump:
 CS:0023 SS:11f7 DS:002b ES:11ff FS:0063 GS:006b
 EIP:7bc27d03 ESP:fffffff2 EBP:0000a4f0 EFLAGS:00010216(  R- --  I   -A-P- )
 EAX:11ffffff EBX:000011f7 ECX:0066e2e4 EDX:00000000
 ESI:00002000 EDI:000004e4
Bad segment (4599)
Stack dump:
Backtrace:
=>0 0x7bc27d03 in ntdll (+0x17d03) (0x00000000)
0x7bc27d03: pushl	0xc0(%ecx)
Modules:
Module	Address			Debug info	Name (76 modules)
ELF	7b800000-7ba54000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba54000	\               kernel32
ELF	7bc00000-7bcda000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcda000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7df47000-7e076000	Deferred        ole32<elf>
  \-PE	7df60000-7e076000	\               ole32
ELF	7e138000-7e14d000	Deferred        sound.drv16.so
PE	7e140000-7e14d000	Deferred        sound.drv16
ELF	7e14d000-7e177000	Deferred        msacm32<elf>
  \-PE	7e150000-7e177000	\               msacm32
ELF	7e177000-7e1f3000	Deferred        rpcrt4<elf>
  \-PE	7e180000-7e1f3000	\               rpcrt4
ELF	7e1f3000-7e2ab000	Deferred        winmm<elf>
  \-PE	7e200000-7e2ab000	\               winmm
ELF	7e2ab000-7e2d6000	Deferred        mmsystem.dll16.so
PE	7e2b0000-7e2d6000	Deferred        mmsystem.dll16
ELF	7e2d6000-7e2ea000	Deferred        mouse.drv16.so
PE	7e2e0000-7e2ea000	Deferred        mouse.drv16
ELF	7e2ea000-7e2ff000	Deferred        keyboard.drv16.so
PE	7e2f0000-7e2ff000	Deferred        keyboard.drv16
ELF	7e2ff000-7e315000	Deferred        display.drv16.so
PE	7e300000-7e315000	Deferred        display.drv16
ELF	7e315000-7e33c000	Deferred        mpr<elf>
  \-PE	7e320000-7e33c000	\               mpr
ELF	7e33c000-7e38b000	Deferred        user.exe16.so
PE	7e350000-7e38b000	Deferred        user.exe16
ELF	7e38b000-7e3bd000	Deferred        gdi.exe16.so
PE	7e390000-7e3bd000	Deferred        gdi.exe16
ELF	7e3bd000-7e3d2000	Deferred        comm.drv16.so
PE	7e3c0000-7e3d2000	Deferred        comm.drv16
ELF	7e3d2000-7e3d9000	Deferred        libxfixes.so.3
ELF	7e3d9000-7e3e4000	Deferred        libxcursor.so.1
ELF	7e3e4000-7e3f7000	Deferred        libxi.so.6
ELF	7e3f7000-7e3fb000	Deferred        libxcomposite.so.1
ELF	7e3fb000-7e408000	Deferred        libxrandr.so.2
ELF	7e408000-7e414000	Deferred        libxrender.so.1
ELF	7e414000-7e41b000	Deferred        libxxf86vm.so.1
ELF	7e41b000-7e41f000	Deferred        libxinerama.so.1
ELF	7e41f000-7e426000	Deferred        libxdmcp.so.6
ELF	7e426000-7e42a000	Deferred        libxau.so.6
ELF	7e42a000-7e450000	Deferred        libxcb.so.1
ELF	7e450000-7e59b000	Deferred        libx11.so.6
ELF	7e59b000-7e5b0000	Deferred        libxext.so.6
ELF	7e5be000-7e5d3000	Deferred        system.drv16.so
PE	7e5c0000-7e5d3000	Deferred        system.drv16
ELF	7e5d5000-7e662000	Deferred        winex11<elf>
  \-PE	7e5e0000-7e662000	\               winex11
ELF	7e6ef000-7e719000	Deferred        libexpat.so.1
ELF	7e719000-7e762000	Deferred        libfontconfig.so.1
ELF	7e762000-7e78d000	Deferred        libpng12.so.0
ELF	7e78d000-7e7a8000	Deferred        libz.so.1
ELF	7e7a8000-7e858000	Deferred        libfreetype.so.6
ELF	7e87d000-7e925000	Deferred        krnl386.exe16.so
PE	7e890000-7e925000	Deferred        krnl386.exe16
ELF	7e925000-7e93e000	Deferred        version<elf>
  \-PE	7e930000-7e93e000	\               version
ELF	7e93e000-7e9aa000	Deferred        advapi32<elf>
  \-PE	7e950000-7e9aa000	\               advapi32
ELF	7e9aa000-7eac1000	Deferred        gdi32<elf>
  \-PE	7e9c0000-7eac1000	\               gdi32
ELF	7eac1000-7ec0f000	Deferred        user32<elf>
  \-PE	7ead0000-7ec0f000	\               user32
ELF	7ec0f000-7ec22000	Deferred        libnss_files.so.2
ELF	7ec22000-7ec2f000	Deferred        libnss_nis.so.2
ELF	7ec2f000-7ec4a000	Deferred        libnsl.so.1
ELF	7ec4a000-7ec54000	Deferred        libnss_compat.so.2
ELF	7ef86000-7efdb000	Deferred        libm.so.6
ELF	7efe9000-7f000000	Deferred        winevdm<elf>
  \-PE	7eff0000-7f000000	\               winevdm
ELF	f7376000-f737b000	Deferred        libdl.so.2
ELF	f737b000-f7531000	Deferred        libc.so.6
ELF	f7532000-f754f000	Deferred        libpthread.so.0
ELF	f7574000-f7729000	Dwarf           libwine.so.1
ELF	f772b000-f7750000	Deferred        ld-linux.so.2
ELF	f7752000-f7753000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001e    0
	0000001d    0
	00000018    0
	00000016    0
	00000014    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001c    0
	00000019    0
	00000017    0
	00000013    0
0000001a plugplay.exe
	00000020    0
	0000001f    0
	0000001b    0
00000021 explorer.exe
	00000023    0
	00000022    0
00000024 (D) C:\windows\system32\winevdm.exe
	00000026    0 <==
	00000025    0
System information:
    Wine build: wine-1.6.2
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 4.4.0-28-generic

---

### Post by PaulW2U on 2016-08-09
> **mr.alan.andrew said:**
> Here's the Wine output, which notes a "serious error". Could it be that the program is 16-bit?
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=3158](https://appdb.winehq.org/objectManager.php?sClass=application&iId=3158) doesn't look too encouraging although the test results are very old now.

---

