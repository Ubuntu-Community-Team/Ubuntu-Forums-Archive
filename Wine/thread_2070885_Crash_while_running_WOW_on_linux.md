---
title: "Crash while running WOW on linux"
date: 2012-10-14
forum: Wine
---

### Post by mlm5 on 2012-10-14
I have been running World of Warcraft on wine,
but suddenly today I have this crash right after finishing loading the game. This is the error message.

```

Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:0180fcd0 EBP:0180fd30 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:000083f1 EBX:00010000 ECX:00000de1 EDX:1297aec0
 ESI:00000000 EDI:16209d30
Stack dump:
0x0180fcd0:  004fe2d2 00000de1 00000000 000083f1
0x0180fce0:  00000200 00000100 00000000 00010000
0x0180fcf0:  1297aec0 00000100 16209d30 00000200
0x0180fd00:  00000000 00000000 00000100 00000200
0x0180fd10:  0000813d 00000009 00000000 00000400
0x0180fd20:  1298aec0 00010000 1297aec0 000083f1
000c: sel=0067 base=00000000 limit=00000000 16-bit --x
Backtrace:
=>0 0x00000000 (0x0180fd30)
  1 0x004fe4e9 in wow (+0xfe4e8) (0x0180fd84)
  2 0x004fe592 in wow (+0xfe591) (0x0180fd94)
  3 0x004e32da in wow (+0xe32d9) (0x0180fda0)
  4 0x004e0415 in wow (+0xe0414) (0x0180fdc4)
  5 0x00673f6f in wow (+0x273f6e) (0x0180fdec)
  6 0x0067b492 in wow (+0x27b491) (0x0180fe1c)
  7 0x0047182f in wow (+0x7182e) (0x0180fe50)
  8 0x00471e1a in wow (+0x71e19) (0x0180fe6c)
  9 0x0046ec9b in wow (+0x6ec9a) (0x0180fe94)
  10 0x0047038a in wow (+0x70389) (0x0180fee8)
  11 0x004703d1 in wow (+0x703d0) (0x0180ff00)
  12 0x0040f807 in wow (+0xf806) (0x0180ff08)
  13 0x7b83ac33 in kernel32 (+0x2ac32) (0x0180ffe8)
0x00000000: -- no code accessible --
Modules:
Module	Address			Debug info	Name (139 modules)
PE	  400000- 12ed000	Export          wow
PE	3c910000-3cbcc000	Deferred        battle.net
ELF	7b800000-7ba15000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba15000	\               kernel32
ELF	7bc00000-7bcc3000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d938000-7d941000	Deferred        librt.so.1
ELF	7d941000-7d946000	Deferred        libgpg-error.so.0
ELF	7d946000-7d95e000	Deferred        libresolv.so.2
ELF	7d95e000-7d9a7000	Deferred        libdbus-1.so.3
ELF	7d9a7000-7d9b9000	Deferred        libp11-kit.so.0
ELF	7d9b9000-7da4c000	Deferred        winex11<elf>
  \-PE	7d9c0000-7da4c000	\               winex11
ELF	7db5c000-7dbe1000	Deferred        libgcrypt.so.11
ELF	7dbe1000-7dbf3000	Deferred        libtasn1.so.3
ELF	7dbf3000-7dbfc000	Deferred        libkrb5support.so.0
ELF	7dbfc000-7dc01000	Deferred        libcom_err.so.2
ELF	7dc01000-7dc29000	Deferred        libk5crypto.so.3
ELF	7dc29000-7dcf8000	Deferred        libkrb5.so.3
ELF	7dcf8000-7dd0a000	Deferred        libavahi-client.so.3
ELF	7dd0a000-7ddce000	Deferred        libgnutls.so.26
ELF	7ddce000-7de0c000	Deferred        libgssapi_krb5.so.2
ELF	7de0c000-7de5f000	Deferred        libcups.so.2
ELF	7dea2000-7ded6000	Deferred        uxtheme<elf>
  \-PE	7deb0000-7ded6000	\               uxtheme
ELF	7ded6000-7dedc000	Deferred        libxfixes.so.3
ELF	7dedc000-7dee7000	Deferred        libxcursor.so.1
ELF	7dee8000-7deec000	Deferred        libkeyutils.so.1
ELF	7deec000-7defa000	Deferred        libavahi-common.so.3
ELF	7df34000-7df5e000	Deferred        libexpat.so.1
ELF	7df5e000-7df92000	Deferred        libfontconfig.so.1
ELF	7df92000-7dfa2000	Deferred        libxi.so.6
ELF	7dfa2000-7dfab000	Deferred        libxrandr.so.2
ELF	7dfab000-7dfcc000	Deferred        libxcb.so.1
ELF	7dfcc000-7dfe6000	Deferred        libice.so.6
ELF	7dfe6000-7e11a000	Deferred        libx11.so.6
ELF	7e11a000-7e12c000	Deferred        libxext.so.6
ELF	7e12c000-7e1c6000	Deferred        libfreetype.so.6
ELF	7e1ca000-7e1d4000	Deferred        libxrender.so.1
ELF	7e1db000-7e1f0000	Deferred        hid<elf>
  \-PE	7e1e0000-7e1f0000	\               hid
ELF	7e1f0000-7e22a000	Deferred        winspool<elf>
  \-PE	7e200000-7e22a000	\               winspool
ELF	7e24e000-7e252000	Deferred        libxcomposite.so.1
ELF	7e252000-7e258000	Deferred        libxxf86vm.so.1
ELF	7e258000-7e25c000	Deferred        libxinerama.so.1
ELF	7e25c000-7e265000	Deferred        libsm.so.6
ELF	7e265000-7e2cc000	Deferred        setupapi<elf>
  \-PE	7e270000-7e2cc000	\               setupapi
ELF	7e2cc000-7e2e8000	Deferred        dinput8<elf>
  \-PE	7e2d0000-7e2e8000	\               dinput8
ELF	7e2e8000-7e31a000	Deferred        ws2_32<elf>
  \-PE	7e2f0000-7e31a000	\               ws2_32
ELF	7e31a000-7e33c000	Deferred        imm32<elf>
  \-PE	7e320000-7e33c000	\               imm32
ELF	7e33c000-7e470000	Deferred        wined3d<elf>
  \-PE	7e350000-7e470000	\               wined3d
ELF	7e470000-7e4a9000	Deferred        d3d9<elf>
  \-PE	7e480000-7e4a9000	\               d3d9
ELF	7e4a9000-7e4d1000	Deferred        msacm32<elf>
  \-PE	7e4b0000-7e4d1000	\               msacm32
ELF	7e4d1000-7e546000	Deferred        rpcrt4<elf>
  \-PE	7e4e0000-7e546000	\               rpcrt4
ELF	7e546000-7e64e000	Deferred        ole32<elf>
  \-PE	7e560000-7e64e000	\               ole32
ELF	7e64e000-7e6fb000	Deferred        winmm<elf>
  \-PE	7e660000-7e6fb000	\               winmm
ELF	7e6fb000-7e7f3000	Deferred        comctl32<elf>
  \-PE	7e700000-7e7f3000	\               comctl32
ELF	7e7f3000-7ea04000	Deferred        shell32<elf>
  \-PE	7e800000-7ea04000	\               shell32
ELF	7ea04000-7ea6e000	Deferred        shlwapi<elf>
  \-PE	7ea10000-7ea6e000	\               shlwapi
ELF	7ea6e000-7ea94000	Deferred        mpr<elf>
  \-PE	7ea70000-7ea94000	\               mpr
ELF	7ea94000-7eaaa000	Deferred        libz.so.1
ELF	7eaaa000-7eb19000	Deferred        wininet<elf>
  \-PE	7eab0000-7eb19000	\               wininet
ELF	7eb19000-7eb32000	Deferred        version<elf>
  \-PE	7eb20000-7eb32000	\               version
ELF	7eb32000-7eb92000	Deferred        advapi32<elf>
  \-PE	7eb40000-7eb92000	\               advapi32
ELF	7eb92000-7ec4f000	Deferred        gdi32<elf>
  \-PE	7eba0000-7ec4f000	\               gdi32
ELF	7ec4f000-7ed8f000	Deferred        user32<elf>
  \-PE	7ec60000-7ed8f000	\               user32
ELF	7ed8f000-7ed9c000	Deferred        libnss_files.so.2
ELF	7ed9c000-7edb6000	Deferred        libnsl.so.1
ELF	7edb6000-7edbf000	Deferred        libnss_compat.so.2
ELF	7efbf000-7efeb000	Deferred        libm.so.6
ELF	f4a18000-f4ad0000	Deferred        crypt32<elf>
  \-PE	f4a20000-f4ad0000	\               crypt32
ELF	f4e70000-f4efd000	Deferred        msvcrt<elf>
  \-PE	f4e80000-f4efd000	\               msvcrt
ELF	f5dd4000-f5e32000	Deferred        dbghelp<elf>
  \-PE	f5de0000-f5e32000	\               dbghelp
ELF	f6218000-f6250000	Deferred        winhttp<elf>
  \-PE	f6220000-f6250000	\               winhttp
ELF	f627b000-f629d000	Deferred        iphlpapi<elf>
  \-PE	f6280000-f629d000	\               iphlpapi
ELF	f62cc000-f62e0000	Deferred        psapi<elf>
  \-PE	f62d0000-f62e0000	\               psapi
ELF	f6426000-f6455000	Deferred        msvcr90<elf>
  \-PE	f6430000-f6455000	\               msvcr90
ELF	f6455000-f6480000	Deferred        msvcr80<elf>
  \-PE	f6460000-f6480000	\               msvcr80
ELF	f64e0000-f65d2000	Deferred        libasound.so.2
ELF	f65d2000-f65fe000	Deferred        winealsa<elf>
  \-PE	f65e0000-f65fe000	\               winealsa
ELF	f65fe000-f66f0000	Deferred        oleaut32<elf>
  \-PE	f6610000-f66f0000	\               oleaut32
ELF	f66f0000-f6713000	Deferred        mmdevapi<elf>
  \-PE	f6700000-f6713000	\               mmdevapi
ELF	f699a000-f6a54000	Deferred        opengl32<elf>
  \-PE	f69b0000-f6a54000	\               opengl32
ELF	f6a54000-f6a72000	Deferred        libgcc_s.so.1
ELF	f6b57000-f6b76000	Deferred        libdrm_intel.so.1
ELF	f6b8b000-f6ca8000	Deferred        libglsl.so
ELF	f6ca8000-f6f21000	Deferred        libdricore.so
ELF	f6f21000-f7000000	Deferred        i965_dri.so
ELF	f7319000-f7326000	Deferred        libdrm.so.2
ELF	f7326000-f733e000	Deferred        libxcb-glx.so.0
ELF	f733e000-f7341000	Deferred        libx11-xcb.so.1
ELF	f7341000-f7345000	Deferred        libxdamage.so.1
ELF	f7345000-f735b000	Deferred        libglapi.so.0
ELF	f735b000-f73b4000	Deferred        libgl.so.1
ELF	f73b4000-f73bb000	Deferred        libnss_dns.so.2
ELF	f73c5000-f73d0000	Deferred        libpciaccess.so.0
ELF	f73d1000-f73d8000	Deferred        libxdmcp.so.6
ELF	f73d8000-f73dc000	Deferred        libxau.so.6
ELF	f73dd000-f73e2000	Deferred        libdl.so.2
ELF	f73e2000-f758c000	Deferred        libc.so.6
ELF	f758d000-f75a8000	Deferred        libpthread.so.0
ELF	f75aa000-f75b0000	Deferred        libuuid.so.1
ELF	f75b0000-f75bc000	Deferred        libnss_nis.so.2
ELF	f75bd000-f76ff000	Dwarf           libwine.so.1
ELF	f7701000-f7723000	Deferred        ld-linux.so.2
ELF	f7723000-f7724000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001f    0
	0000001e    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001c    0
	00000019    0
	00000014    0
	00000013    0
0000001a plugplay.exe
	00000020    0
	0000001d    0
	0000001b    0
00000021 explorer.exe
	00000022    0
00000023 (D) Z:\media\FreeAgent GoFlex Drive\World of Warcraft\Wow.exe
	00000049    0
	0000000d    0
	00000009    0
	0000000b    0
	00000047    0
	00000046    0
	00000045    0
	00000044    0
	00000043    0
	00000042    0
	00000041    0
	00000040    0
	0000003f    0
	0000003e    0
	0000003d    0
	0000003c    0
	0000003b    0
	00000037    1
	00000036    1
	00000035    0
	00000034    0
	00000033    0
	00000032    2
	00000031   15
	00000030    0
	0000002f    0
	0000002e    0
	0000002d    0
	0000002c    0
	0000002b    0
	0000002a    0
	00000029    0
	00000028    0
	00000027    0
	00000026    0
	00000024    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.4.0


```

---

### Post by martialartist81 on 2012-10-14
I'm no expert... but after a quick read through... are you playing the 64-bit WoW client on a 32-bit version of WINE/Linux?

System information:
    Wine build: wine-1.4
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.4.0

If that's the case... try to fire up the 32-bit client.  If it's not your issue, then this won't be a whole lot of help to you.  Just thought I'd fire out my thought.

Cheers and best of luck.

---

