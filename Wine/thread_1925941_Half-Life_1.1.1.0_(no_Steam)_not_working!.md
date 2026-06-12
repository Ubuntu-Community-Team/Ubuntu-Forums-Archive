---
title: "Half-Life 1.1.1.0 (no Steam) not working!"
date: 2012-02-15
forum: Wine
---

### Post by ?#Yhf%*&amp; on 2012-02-15
I have installed the WINE meta package from the Ubuntu Software Center, set everything up, and installed Half-Life from the CD. The installation went fine and no alerts showed up, so I'm not sure why it won't work. I have WINE on a Mac OS X system and it works fine on there, so I'm not quite sure why.

I'm running Ubuntu 11.10 on an HP Compaq tower (old)
I have WINE 1.3.28 installed

This is what I get when I run hl.exe:
```
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 001f), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0032d4a0 EBP:7d336a44 EFLAGS:00010216(  R- --  I   -A-P- )
 EAX:00000003 EBX:280a8ff4 ECX:7d01b888 EDX:7d336ce8
 ESI:7d01b888 EDI:7d337060
Stack dump:
0x0032d4a0:  2808efcc 7d01b888 00000003 00000012
0x0032d4b0:  4fb74354 682d6ff4 280a8ff4 7d3369d8
0x0032d4c0:  2808f12e 7d01b888 00008058 7d3370d4
0x0032d4d0:  4fb52fd4 7d337060 00000000 682d8400
0x0032d4e0:  280a8ff4 7d337060 7d336f00 7d3369d8
0x0032d4f0:  2808fcff 7d336a44 ffffffff 7d336780
Backtrace:
=>0 0x00000000 (0x7d336a44)
  1 0x00000000 (0x7d336a58)
0x00000000: -- no code accessible --
Modules:
Module	Address			Debug info	Name (116 modules)
PE	  330000-  3d1000	Deferred        woncrypt
PE	  400000-  519000	Deferred        hl
PE	  520000-  578000	Deferred        vgui
PE	10000000-100a1000	Deferred        wonauth
PE	17000000-1700c000	Deferred        hl_res
ELF	20000000-20004000	Deferred        libxdamage.so.1
ELF	20004000-2004f000	Deferred        dsound<elf>
  \-PE	20010000-2004f000	\               dsound
ELF	2004f000-20163000	Deferred        libglsl.so
ELF	28034000-280ab000	Deferred        i915_dri.so
ELF	28121000-28175000	Deferred        libgl.so.1
ELF	28560000-2856a000	Deferred        libpciaccess.so.0
ELF	3ef62000-3ef6e000	Deferred        libdrm.so.2
ELF	4faad000-4fcf4000	Deferred        libdricore.so
ELF	5cce6000-5ccf3000	Deferred        libdrm_intel.so.1
ELF	68000000-68144000	Dwarf           libwine.so.1
ELF	68144000-6815f000	Deferred        libpthread.so.0
ELF	6815f000-682db000	Deferred        libc.so.6
ELF	682db000-683ad000	Deferred        ntdll<elf>
  \-PE	682f0000-683ad000	\               ntdll
ELF	683ad000-683d7000	Deferred        libm.so.6
ELF	683d7000-683e1000	Deferred        libnss_compat.so.2
ELF	683e1000-683fa000	Deferred        libnsl.so.1
ELF	683fa000-68406000	Deferred        libnss_nis.so.2
ELF	68406000-68413000	Deferred        libnss_files.so.2
ELF	68413000-6847c000	Deferred        advapi32<elf>
  \-PE	68420000-6847c000	\               advapi32
ELF	6847c000-68496000	Deferred        version<elf>
  \-PE	68480000-68496000	\               version
ELF	68496000-6853c000	Deferred        winmm<elf>
  \-PE	684a0000-6853c000	\               winmm
ELF	6853c000-6866b000	Deferred        ole32<elf>
  \-PE	68550000-6866b000	\               ole32
ELF	6866b000-686e9000	Deferred        rpcrt4<elf>
  \-PE	68680000-686e9000	\               rpcrt4
ELF	686e9000-68714000	Deferred        msacm32<elf>
  \-PE	686f0000-68714000	\               msacm32
ELF	68714000-6880d000	Deferred        comdlg32<elf>
  \-PE	68720000-6880d000	\               comdlg32
ELF	6880d000-68a32000	Deferred        shell32<elf>
  \-PE	68820000-68a32000	\               shell32
ELF	68a32000-68aa5000	Deferred        shlwapi<elf>
  \-PE	68a40000-68aa5000	\               shlwapi
ELF	68aa5000-68ae1000	Deferred        winspool<elf>
  \-PE	68ab0000-68ae1000	\               winspool
ELF	68ae1000-68b15000	Deferred        ws2_32<elf>
  \-PE	68af0000-68b15000	\               ws2_32
ELF	68b15000-68b86000	Deferred        wininet<elf>
  \-PE	68b20000-68b86000	\               wininet
ELF	68b86000-68b9b000	Deferred        libz.so.1
ELF	68b9b000-68bc1000	Deferred        mpr<elf>
  \-PE	68ba0000-68bc1000	\               mpr
ELF	68bc1000-68be3000	Deferred        libncurses.so.5
ELF	68be3000-68c02000	Deferred        libtinfo.so.5
ELF	68c02000-68c99000	Deferred        libfreetype.so.6
ELF	68c99000-68cce000	Deferred        libfontconfig.so.1
ELF	68cce000-68cf8000	Deferred        libexpat.so.1
ELF	68cf8000-68da8000	Deferred        winex11<elf>
  \-PE	68d00000-68da8000	\               winex11
ELF	68da8000-68db1000	Deferred        libsm.so.6
ELF	68db1000-68dc4000	Deferred        libxext.so.6
ELF	68dc4000-68efa000	Deferred        libx11.so.6
ELF	68efa000-68f00000	Deferred        libuuid.so.1
ELF	68f00000-68f1f000	Deferred        libxcb.so.1
ELF	68f1f000-68f23000	Deferred        libxau.so.6
ELF	68f23000-68f27000	Deferred        libxinerama.so.1
ELF	68f27000-68f2d000	Deferred        libxxf86vm.so.1
ELF	68f2d000-68f38000	Deferred        libxrender.so.1
ELF	68f38000-68f3c000	Deferred        libxcomposite.so.1
ELF	68f3c000-68f4c000	Deferred        libxi.so.6
ELF	68f4c000-68f57000	Deferred        libxcursor.so.1
ELF	68f57000-68f5d000	Deferred        libxfixes.so.3
ELF	68f5d000-68f94000	Deferred        uxtheme<elf>
  \-PE	68f60000-68f94000	\               uxtheme
ELF	68f94000-68fd2000	Deferred        libgssapi_krb5.so.2
ELF	68fd2000-69082000	Deferred        libgnutls.so.26
ELF	69082000-69090000	Deferred        libavahi-common.so.3
ELF	69090000-690a3000	Deferred        libavahi-client.so.3
ELF	690a3000-6916c000	Deferred        libkrb5.so.3
ELF	6916c000-69170000	Deferred        libcom_err.so.2
ELF	69170000-69182000	Deferred        libtasn1.so.3
ELF	69182000-69207000	Deferred        libgcrypt.so.11
ELF	69207000-69250000	Deferred        libdbus-1.so.3
ELF	69250000-69254000	Deferred        libkeyutils.so.1
ELF	69254000-6926b000	Deferred        libresolv.so.2
ELF	6926b000-69274000	Deferred        librt.so.1
ELF	6c694000-6c84d000	Deferred        kernel32<elf>
  \-PE	6c6b0000-6c84d000	\               kernel32
ELF	6e42b000-6e441000	Deferred        libglapi.so.0
ELF	6e5ad000-6e5b6000	Deferred        libxrandr.so.2
ELF	6e947000-6e96b000	Deferred        imm32<elf>
  \-PE	6e950000-6e96b000	\               imm32
ELF	6e9a9000-6e9c3000	Deferred        libice.so.6
ELF	6f288000-6f2a3000	Deferred        wsock32<elf>
  \-PE	6f290000-6f2a3000	\               wsock32
ELF	6f983000-6fa38000	Deferred        gdi32<elf>
  \-PE	6f990000-6fa38000	\               gdi32
ELF	6fab4000-6fabd000	Deferred        libkrb5support.so.0
ELF	6fb0d000-6fc0e000	Deferred        comctl32<elf>
  \-PE	6fb10000-6fc0e000	\               comctl32
ELF	6fcd7000-6fcdc000	Deferred        libdl.so.2
ELF	70fa5000-70fc5000	Deferred        ld-linux.so.2
ELF	71304000-71327000	Deferred        iphlpapi<elf>
  \-PE	71310000-71327000	\               iphlpapi
ELF	71c16000-71c1d000	Deferred        libxdmcp.so.6
ELF	722ca000-7233b000	Deferred        ddraw<elf>
  \-PE	722d0000-7233b000	\               ddraw
ELF	73fa0000-740f0000	Deferred        user32<elf>
  \-PE	73fb0000-740f0000	\               user32
ELF	7589c000-758ee000	Deferred        libcups.so.2
ELF	77cb6000-77cbb000	Deferred        libgpg-error.so.0
ELF	79807000-7994a000	Deferred        wined3d<elf>
  \-PE	79810000-7994a000	\               wined3d
ELF	7be80000-7bea9000	Deferred        libk5crypto.so.3
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c018000-7c036000	Deferred        libgcc_s.so.1
Threads:
process  tid      prio (all id:s are in hex)
00000008 winecfg.exe
	00000009    0
0000000e services.exe
	0000001a    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000016    0
	00000013    0
	00000012    0
00000017 plugplay.exe
	0000001b    0
	00000019    0
	00000018    0
0000001c explorer.exe
	0000001d    0
0000001e (D) C:\Sierra\Half-Life\hl.exe
	00000020    0
	0000001f    0 <==
Backtrace:
=>0 0x00000000 (0x7d336a44)
  1 0x00000000 (0x7d336a58)

```

Can anyone identify the problem? I would love to play this game :)

---

### Post by ?#Yhf%*&amp; on 2012-02-15
bump

---

### Post by ?#Yhf%*&amp; on 2012-02-16
Can anyone help? :(

---

