---
title: "Helix, HX Edit, and WINE issues in Kubuntu"
date: 2019-01-13
forum: Wine
---

### Post by meshica7 on 2019-01-13
I must preface this post by stating that I am a newbie to Wine/PlayonLinux.

 I recently installed PlayonLinux in hopes of running a piece of audio software that is not available on the Linux platform. The software is **HX Edit** and **Line 6 Updater** (they're bundled together). This is software made by Line 6 to interface, edit, and perform firmware updates to their Helix Rack, Helix, Floor, and Helix LT effects processors.

 I installed HX Edit using PlayonLinux. The process was easy and straight forward. A desktop shortcut was created for both HX Edit and for Line 6 Updater (The updater performs the firmware updates and is part of the HX Edit instal package). Line 6 Updater launches right way without a hitch. When I attempt to launch HX Edit, however, I get an error stating the following:

"The program HX Edit.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience. Thsi can be caused by a problem in the program or a deficiency in Wine."

The following output was also provided:

```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00649dd0).
Register dump:
CS:0023 SS:002b DS:002b ES:002b FS:006b GS:0063
EIP:00649dd0 ESP:0033f994 EBP:0033f9a8 EFLAGS:00010202( R- -- I - - - )
EAX:00000000 EBX:00000000 ECX:01901cb0 EDX:00000001
ESI:00000000 EDI:0190ef20
Stack dump:
0x0033f994: 0000000e 0190ef20 00000000 00000001
0x0033f9a4: 00000001 0033f9c4 007a1d77 80000001
0x0033f9b4: 00000000 018ed180 00000000 00000000
0x0033f9c4: 0033f9e0 007a1d9f 80000001 00000000
0x0033f9d4: 00000000 018ed180 00000000 0033fa08
0x0033f9e4: 007bb3d0 80000001 00000000 01908ef0
Backtrace:
=>0 0x00649dd0 in hx edit (+0x249dd0) (0x0033f9a8)
1 0x007a1d77 in hx edit (+0x3a1d76) (0x0033f9c4)
2 0x007a1d9f in hx edit (+0x3a1d9e) (0x0033f9e0)
3 0x007bb3d0 in hx edit (+0x3bb3cf) (0x0033fa08)
4 0x006479f3 in hx edit (+0x2479f2) (0x0033fa48)
5 0x0062a5c8 in hx edit (+0x22a5c7) (0x0033fae0)
6 0x00543c47 in hx edit (+0x143c46) (0x0033fb4c)
7 0x005433a7 in hx edit (+0x1433a6) (0x0033fb9c)
8 0x0074e4cd in hx edit (+0x34e4cc) (0x0033fe74)
9 0x007e84ed in hx edit (+0x3e84ec) (0x0033fec0)
10 0x7b4623d2 call_process_entry+0x11() in kernel32 (0x0033fed8)
11 0x7b463d0c in kernel32 (+0x43d0b) (0x0033ffd8)
12 0x7b4623de call_process_entry+0x1d() in kernel32 (0x0033ffec)
0x00649dd0: movl	0x0(%esi),%edx
Modules:
Module	Address	Debug info	Name (117 modules)
PE	400000- c3e000	Export hx edit
PE	10000000-1000c000	Deferred pthreadvc2
ELF	7a800000-7a93e000	Deferred opengl32<elf>
\-PE	7a820000-7a93e000	\ opengl32
ELF	7b400000-7b7ec000	Dwarf kernel32<elf>
\-PE	7b420000-7b7ec000	\ kernel32
ELF	7bc00000-7bcfe000	Deferred ntdll<elf>
\-PE	7bc10000-7bcfe000	\ ntdll
ELF	7c000000-7c005000	Deferred <wine-loader>
ELF	7d80e000-7d958000	Deferred wined3d<elf>
\-PE	7d820000-7d958000	\ wined3d
ELF	7da12000-7da3c000	Deferred dxgi<elf>
\-PE	7da20000-7da3c000	\ dxgi
ELF	7da3c000-7da76000	Deferred wbemprox<elf>
\-PE	7da40000-7da76000	\ wbemprox
ELF	7da98000-7dabb000	Deferred libgpg-error.so.0
ELF	7dabb000-7db9d000	Deferred libgcrypt.so.20
ELF	7db9d000-7dbc5000	Deferred liblz4.so.1
ELF	7dbc5000-7dbf1000	Deferred liblzma.so.5
ELF	7dbf1000-7dc86000	Deferred libsystemd.so.0
ELF	7dc86000-7dc8f000	Deferred libffi.so.6
ELF	7dc8f000-7dca9000	Deferred libresolv.so.2
ELF	7dca9000-7dcae000	Deferred libkeyutils.so.1
ELF	7dcae000-7dd0b000	Deferred libdbus-1.so.3
ELF	7dd0b000-7dd96000	Deferred libgmp.so.10
ELF	7dd96000-7ddcc000	Deferred libhogweed.so.4
ELF	7ddcc000-7de08000	Deferred libnettle.so.6
ELF	7de08000-7de1d000	Deferred libtasn1.so.6
ELF	7de1d000-7df9f000	Deferred libunistring.so.2
ELF	7df9f000-7dfbf000	Deferred libidn2.so.0
ELF	7dfbf000-7e10d000	Deferred libp11-kit.so.0
ELF	7e10d000-7e11b000	Deferred libkrb5support.so.0
ELF	7e11b000-7e120000	Deferred libcom_err.so.2
ELF	7e120000-7e156000	Deferred libk5crypto.so.3
ELF	7e156000-7e234000	Deferred libkrb5.so.3
ELF	7e234000-7e400000	Deferred libgnutls.so.30
ELF	7e400000-7e455000	Deferred libgssapi_krb5.so.2
ELF	7e455000-7e4e8000	Deferred libcups.so.2
ELF	7e513000-7e54d000	Deferred uxtheme<elf>
\-PE	7e520000-7e54d000	\ uxtheme
ELF	7e54d000-7e554000	Deferred libxfixes.so.3
ELF	7e554000-7e560000	Deferred libxcursor.so.1
ELF	7e560000-7e573000	Deferred libxi.so.6
ELF	7e573000-7e577000	Deferred libxcomposite.so.1
ELF	7e577000-7e584000	Deferred libxrandr.so.2
ELF	7e584000-7e590000	Deferred libxrender.so.1
ELF	7e590000-7e597000	Deferred libxxf86vm.so.1
ELF	7e597000-7e59c000	Deferred libxinerama.so.1
ELF	7e59c000-7e5a7000	Deferred librt.so.1
ELF	7e5a7000-7e5c5000	Deferred libbsd.so.0
ELF	7e5c5000-7e5cc000	Deferred libxdmcp.so.6
ELF	7e5cc000-7e5d0000	Deferred libxau.so.6
ELF	7e5d0000-7e5fe000	Deferred libxcb.so.1
ELF	7e5fe000-7e74a000	Deferred libx11.so.6
ELF	7e74a000-7e75f000	Deferred libxext.so.6
ELF	7e763000-7e779000	Deferred libavahi-client.so.3
ELF	7e779000-7e788000	Deferred libavahi-common.so.3
ELF	7e78a000-7e818000	Deferred winex11<elf>
\-PE	7e7a0000-7e818000	\ winex11
ELF	7e818000-7e83d000	Deferred imm32<elf>
\-PE	7e820000-7e83d000	\ imm32
ELF	7e8cb000-7e906000	Deferred libexpat.so.1
ELF	7e906000-7e951000	Deferred libfontconfig.so.1
ELF	7e951000-7e98b000	Deferred libpng16.so.16
ELF	7e98b000-7ea48000	Deferred libfreetype.so.6
ELF	7ea48000-7eb25000	Deferred msvcr100<elf>
\-PE	7ea60000-7eb25000	\ msvcr100
ELF	7eb25000-7ebbd000	Deferred gdiplus<elf>
\-PE	7eb30000-7ebbd000	\ gdiplus
ELF	7ebbd000-7ecef000	Deferred oleaut32<elf>
\-PE	7ebd0000-7ecef000	\ oleaut32
ELF	7ecef000-7ed30000	Deferred winspool<elf>
\-PE	7ed00000-7ed30000	\ winspool
ELF	7ed30000-7ee4f000	Deferred comctl32<elf>
\-PE	7ed40000-7ee4f000	\ comctl32
ELF	7ee4f000-7ef3c000	Deferred comdlg32<elf>
\-PE	7ee60000-7ef3c000	\ comdlg32
ELF	7ef3c000-7ef78000	Deferred ws2_32<elf>
\-PE	7ef40000-7ef78000	\ ws2_32
ELF	7ef78000-7f1ce000	Deferred shell32<elf>
\-PE	7ef90000-7f1ce000	\ shell32
ELF	7f1ce000-7f1f7000	Deferred mpr<elf>
\-PE	7f1e0000-7f1f7000	\ mpr
ELF	7f1f7000-7f216000	Deferred libz.so.1
ELF	7f241000-7f2bc000	Deferred wininet<elf>
\-PE	7f250000-7f2bc000	\ wininet
ELF	7f2bc000-7f2e7000	Deferred iphlpapi<elf>
\-PE	7f2c0000-7f2e7000	\ iphlpapi
ELF	7f2e7000-7f356000	Deferred setupapi<elf>
\-PE	7f2f0000-7f356000	\ setupapi
ELF	7f356000-7f3cf000	Deferred shlwapi<elf>
\-PE	7f360000-7f3cf000	\ shlwapi
ELF	7f3cf000-7f3fa000	Deferred msacm32<elf>
\-PE	7f3e0000-7f3fa000	\ msacm32
ELF	7f3fa000-7f47e000	Deferred rpcrt4<elf>
\-PE	7f410000-7f47e000	\ rpcrt4
ELF	7f47e000-7f5db000	Deferred ole32<elf>
\-PE	7f4a0000-7f5db000	\ ole32
ELF	7f5db000-7f655000	Deferred advapi32<elf>
\-PE	7f5f0000-7f655000	\ advapi32
ELF	7f655000-7f784000	Deferred gdi32<elf>
\-PE	7f660000-7f784000	\ gdi32
ELF	7f784000-7f967000	Deferred user32<elf>
\-PE	7f7a0000-7f967000	\ user32
ELF	7f967000-7fa21000	Deferred winmm<elf>
\-PE	7f970000-7fa21000	\ winmm
ELF	7fa21000-7fa36000	Deferred libnss_files.so.2
ELF	7feaf000-7ffb5000	Deferred libm.so.6
ELF	7ffbb000-7ffc5000	Deferred libuuid.so.1
ELF	7ffc5000-7ffe0000	Deferred version<elf>
\-PE	7ffd0000-7ffe0000	\ version
ELF	f7af3000-f7af9000	Deferred libdl.so.2
ELF	f7af9000-f7cda000	Deferred libc.so.6
ELF	f7cda000-f7cfc000	Deferred libpthread.so.0
ELF	f7d27000-f7edd000	Dwarf libwine.so.1
ELF	f7ee2000-f7ee4000	Deferred [vdso].so
ELF	f7ee4000-f7f0e000	Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
00000008 start.exe
00000009 0
0000000e services.exe
00000023 0
0000001e 0
00000018 0
00000013 0
00000010 0
0000000f 0
00000011 winedevice.exe
0000001b 0
00000017 0
00000016 0
00000012 0
0000001c plugplay.exe
00000020 0
0000001f 0
0000001d 0
00000021 winedevice.exe
00000028 0
00000025 0
00000024 0
00000022 0
00000029 explorer.exe
00000030 0
0000002a 0
0000002b explorer.exe
0000002f 0
0000002e 0
0000002d 0
0000002c 0
00000031 (D) C:\Program Files (x86)\Line6\HX Edit\HX Edit.exe
00000033 0
00000032 0 <==
System information:
Wine build: wine-3.0.3 (Ubuntu 3.0.3-2)
Platform: i386 (WOW64)
Version: Windows 7
Host system: Linux
Host version: 4.18.0-13-generic
```

 I must note that I have yet to test my Helix Rack with the Line 6 Updater..I'm just glad the software launches..I'll figure out USB drivers later if it's a problem. Would love to get the HX Edit software going as it allows editing of the Helix Rack's programs and the like via an icredibly easy GUI.
 Any ideas?

---

### Post by wildmanne39 on 2019-01-13
*Thread moved to **Wine for a more appropriate fit**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

