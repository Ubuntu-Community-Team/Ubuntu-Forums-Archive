---
title: "Help me, play game with wine"
date: 2008-07-12
forum: Wine
---

### Post by sothacom on 2008-07-12
I have a game online, but when i run it with wine it report

```

 wine '/home/sotacom/.wine/drive_c/Program Files/VTCGame/Audition/Patcher.exe' 
fixme:wininet:InternetAttemptConnect Stub
wine: Unhandled page fault on read access to 0x76726573 at address 0x7e79dcb9 (thread 001d), starting debugger...
Unhandled exception: page fault on read access to 0x76726573 in 32-bit code (0x7e79dcb9).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e79dcb9 ESP:0032a020 EBP:0032a088 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00007672 EBX:7e7bb890 ECX:00000004 EDX:76726573
 ESI:0032a0c0 EDI:00000001
Stack dump:
0x0032a020:  00000000 00000000 004409d6 00000001
0x0032a030:  001345c0 00000001 0041725f 004568d8
0x0032a040:  0032a07c 00416df3 0000000d 00416de8
0x0032a050:  00440cd8 00000000 00000000 7e7b5d8a
0x0032a060:  00133cd0 00133d90 001345a0 001345c0
0x0032a070:  00000000 0032c0f8 7e79d9bb 00000000
Backtrace:
=>1 0x7e79dcb9 HttpOpenRequestA+0x309() in wininet (0x0032a088)
  2 0x00403907 in patcher (+0x3907) (0x0032b0c8)
  3 0x004041b0 in patcher (+0x41b0) (0x0032e104)
  4 0x0040503c in patcher (+0x503c) (0x00454708)
  5 0x00000001 (0x00440c00)
  6 0x00404a90 in patcher (+0x4a90) (0x0043afa5)
  7 0x8b56c300 (0x442d78b8)
0x7e79dcb9 HttpOpenRequestA+0x309 in wininet: cmpb	$0x0,0x0(%edx)
Modules:
Module	Address			Debug info	Name (87 modules)
PE	  400000-  479000	Export          patcher
PE	65340000-653d2000	Deferred        oleaut32
ELF	7b800000-7b930000	Deferred        kernel32<elf>
  \-PE	7b820000-7b930000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e0b1000-7e0c8000	Deferred        spoolss<elf>
  \-PE	7e0c0000-7e0c8000	\               spoolss
ELF	7e0c8000-7e0e1000	Deferred        localspl<elf>
  \-PE	7e0d0000-7e0e1000	\               localspl
ELF	7e0e1000-7e0e5000	Deferred        libgpg-error.so.0
ELF	7e0e5000-7e132000	Deferred        libgcrypt.so.11
ELF	7e132000-7e142000	Deferred        libtasn1.so.3
ELF	7e142000-7e14a000	Deferred        libkrb5support.so.0
ELF	7e14a000-7e17c000	Deferred        libcrypt.so.1
ELF	7e17c000-7e1f2000	Deferred        libgnutls.so.13
ELF	7e1f2000-7e215000	Deferred        libk5crypto.so.3
ELF	7e215000-7e2a2000	Deferred        libkrb5.so.3
ELF	7e2a2000-7e2cb000	Deferred        libgssapi_krb5.so.2
ELF	7e2cb000-7e2fe000	Deferred        libcups.so.2
ELF	7e3eb000-7e41e000	Deferred        uxtheme<elf>
  \-PE	7e3f0000-7e41e000	\               uxtheme
ELF	7e41e000-7e427000	Deferred        libxcursor.so.1
ELF	7e427000-7e42c000	Deferred        libxfixes.so.3
ELF	7e42c000-7e42f000	Deferred        libxcomposite.so.1
ELF	7e42f000-7e435000	Deferred        libxrandr.so.2
ELF	7e435000-7e43d000	Deferred        libxrender.so.1
ELF	7e43d000-7e440000	Deferred        libxinerama.so.1
ELF	7e440000-7e460000	Deferred        imm32<elf>
  \-PE	7e450000-7e460000	\               imm32
ELF	7e460000-7e465000	Deferred        libxdmcp.so.6
ELF	7e465000-7e47d000	Deferred        libxcb.so.1
ELF	7e47d000-7e47f000	Deferred        libxcb-xlib.so.0
ELF	7e47f000-7e482000	Deferred        libxau.so.6
ELF	7e482000-7e569000	Deferred        libx11.so.6
ELF	7e569000-7e577000	Deferred        libxext.so.6
ELF	7e577000-7e58f000	Deferred        libice.so.6
ELF	7e58f000-7e597000	Deferred        libsm.so.6
ELF	7e599000-7e59c000	Deferred        libkeyutils.so.1
ELF	7e5a6000-7e5a9000	Deferred        libcom_err.so.2
ELF	7e5ab000-7e642000	Deferred        winex11<elf>
  \-PE	7e5c0000-7e642000	\               winex11
ELF	7e684000-7e6a5000	Deferred        libexpat.so.1
ELF	7e6a5000-7e6cf000	Deferred        libfontconfig.so.1
ELF	7e6cf000-7e6e4000	Deferred        libz.so.1
ELF	7e6e4000-7e754000	Deferred        libfreetype.so.6
ELF	7e754000-7e775000	Deferred        mpr<elf>
  \-PE	7e760000-7e775000	\               mpr
ELF	7e775000-7e7c3000	Export          wininet<elf>
  \-PE	7e780000-7e7c3000	\               wininet
ELF	7e7c3000-7e7d6000	Deferred        libresolv.so.2
ELF	7e7d6000-7e7db000	Deferred        libxxf86vm.so.1
ELF	7e7ea000-7e808000	Deferred        iphlpapi<elf>
  \-PE	7e7f0000-7e808000	\               iphlpapi
ELF	7e808000-7e86a000	Deferred        rpcrt4<elf>
  \-PE	7e810000-7e86a000	\               rpcrt4
ELF	7e86a000-7e90e000	Deferred        ole32<elf>
  \-PE	7e880000-7e90e000	\               ole32
ELF	7e90e000-7e935000	Deferred        oledlg<elf>
  \-PE	7e910000-7e935000	\               oledlg
ELF	7e935000-7e96b000	Deferred        winspool<elf>
  \-PE	7e940000-7e96b000	\               winspool
ELF	7e96b000-7ea2a000	Deferred        comctl32<elf>
  \-PE	7e970000-7ea2a000	\               comctl32
ELF	7ea2a000-7ea83000	Deferred        shlwapi<elf>
  \-PE	7ea40000-7ea83000	\               shlwapi
ELF	7ea83000-7eb98000	Deferred        shell32<elf>
  \-PE	7ea90000-7eb98000	\               shell32
ELF	7eb98000-7ec43000	Deferred        comdlg32<elf>
  \-PE	7eba0000-7ec43000	\               comdlg32
ELF	7ec43000-7ec95000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec95000	\               advapi32
ELF	7ec95000-7ed33000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed33000	\               gdi32
ELF	7ed33000-7ee7a000	Deferred        user32<elf>
  \-PE	7ed50000-7ee7a000	\               user32
ELF	7ef9a000-7efa5000	Deferred        libnss_files.so.2
ELF	7efa5000-7efaf000	Deferred        libnss_nis.so.2
ELF	7efaf000-7efc7000	Deferred        libnsl.so.1
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	b7c26000-b7c2f000	Deferred        libnss_compat.so.2
ELF	b7c30000-b7c34000	Deferred        libdl.so.2
ELF	b7c34000-b7d83000	Deferred        libc.so.6
ELF	b7d84000-b7d9c000	Deferred        libpthread.so.0
ELF	b7db0000-b7ee6000	Deferred        libwine.so.1
ELF	b7ee8000-b7f04000	Deferred        ld-linux.so.2
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
0000001c (D) C:\Program Files\VTCGame\Audition\Patcher.exe
	0000001d    0 <==
0000001e 
	0000001f    0
Backtrace:
=>1 0x7e79dcb9 HttpOpenRequestA+0x309() in wininet (0x0032a088)
  2 0x00403907 in patcher (+0x3907) (0x0032b0c8)
  3 0x004041b0 in patcher (+0x41b0) (0x0032e104)
  4 0x0040503c in patcher (+0x503c) (0x00454708)
  5 0x00000001 (0x00440c00)
  6 0x00404a90 in patcher (+0x4a90) (0x0043afa5)
  7 0x8b56c300 (0x442d78b8)


```

Somebody help me!!!! :confused::confused:

---

### Post by sothacom on 2008-07-12
Please help me

---

### Post by happyhamster on 2008-07-12
- Do you get the same result when running 

wine Patcher.exe

- from within the /home/sotacom/.wine/drive_c/Program Files/VTCGame/Audition/ folder? (first navigate to the correct folder, then run wine Patcher.exe).

- Which ubuntu and wine version are you using? The latest wine (wine 1.1.1) got a few fixes for wininet.dll again.

- It's a long shot, but take a look at:
[http://wiki.winehq.org/FAQ#head-0344b4325219c69636aeffeaa3596d6855283afd](http://wiki.winehq.org/FAQ#head-0344b4325219c69636aeffeaa3596d6855283afd)

Good luck.

---

### Post by sothacom on 2008-07-12
I use Ubuntu 8.04 and wine 1.1.0, i tried wine Patcher.exe but didn't run.

---

