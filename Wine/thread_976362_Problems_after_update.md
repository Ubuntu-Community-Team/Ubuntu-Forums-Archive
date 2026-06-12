---
title: "Problems after update"
date: 2008-11-09
forum: Wine
---

### Post by qbox on 2008-11-09
I played counter Strike for a long time with wine
Yesterday I make an update so I cant play any more
This is the console output

```
qbox@qbox:~$ wine .wine/drive_c/xtcs\ counter-strike\ 1.6\ final\ release/cstrike.exe 
fixme:ntoskrnl:KeInitializeTimerEx 0x114120 0
wine: Unhandled page fault on read access to 0x00000000 at address 0x14014f9 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x014014f9).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:014014f9 ESP:0032fa94 EBP:0032fbac EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:00000005
 ESI:014113a0 EDI:00000104
Stack dump:
0x0032fa94:  014113a0 0000005c 10015298 014114a8
0x0032faa4:  00000000 2e5c3a48 656e6977 6972645c
0x0032fab4:  635f6576 6374785c 6f632073 65746e75
0x0032fac4:  74732d72 656b6972 362e3120 6e696620
0x0032fad4:  72206c61 61656c65 635c6573 69727473
0x0032fae4:  652e656b 00006578 7bc4a264 10016967
Backtrace:
=>1 0x014014f9 in cstrike (+0x14f9) (0x0032fbac)
  2 0x01401aa3 in cstrike (+0x1aa3) (0x0032fe7c)
  3 0x014038f1 in cstrike (+0x38f1) (0x0032ff08)
  4 0x7b878387 in kernel32 (+0x58387) (0x0032ffe8)
0x014014f9: cmpb	%bl,0x0(%eax)
Modules:
Module	Address			Debug info	Name (51 modules)
PE	 1400000- 351f000	Export          cstrike
PE	10000000-1001f000	Deferred        filesystem_stdio
ELF	7b800000-7b93b000	Export          kernel32<elf>
  \-PE	7b820000-7b93b000	\               kernel32
ELF	7bc00000-7bca9000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca9000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e8a2000-7e8ab000	Deferred        libxcursor.so.1
ELF	7e8ab000-7e8b0000	Deferred        libxfixes.so.3
ELF	7e8b0000-7e8b3000	Deferred        libxcomposite.so.1
ELF	7e8b3000-7e8b9000	Deferred        libxrandr.so.2
ELF	7e8b9000-7e8c1000	Deferred        libxrender.so.1
ELF	7e8c1000-7e8c6000	Deferred        libxxf86vm.so.1
ELF	7e8c6000-7e8c9000	Deferred        libxinerama.so.1
ELF	7e8c9000-7e8e9000	Deferred        imm32<elf>
  \-PE	7e8d0000-7e8e9000	\               imm32
ELF	7e8e9000-7e8ee000	Deferred        libxdmcp.so.6
ELF	7e8ee000-7e906000	Deferred        libxcb.so.1
ELF	7e906000-7e908000	Deferred        libxcb-xlib.so.0
ELF	7e908000-7e90b000	Deferred        libxau.so.6
ELF	7e90b000-7e9f2000	Deferred        libx11.so.6
ELF	7e9f2000-7ea00000	Deferred        libxext.so.6
ELF	7ea1c000-7eab5000	Deferred        winex11<elf>
  \-PE	7ea30000-7eab5000	\               winex11
ELF	7eaef000-7eb10000	Deferred        libexpat.so.1
ELF	7eb10000-7eb3a000	Deferred        libfontconfig.so.1
ELF	7eb3a000-7eb4f000	Deferred        libz.so.1
ELF	7eb4f000-7ebbf000	Deferred        libfreetype.so.6
ELF	7ebbf000-7ec5d000	Deferred        gdi32<elf>
  \-PE	7ebd0000-7ec5d000	\               gdi32
ELF	7ec5d000-7eda6000	Deferred        user32<elf>
  \-PE	7ec80000-7eda6000	\               user32
ELF	7eda6000-7edfa000	Deferred        advapi32<elf>
  \-PE	7edb0000-7edfa000	\               advapi32
ELF	7edfa000-7ee0d000	Deferred        libresolv.so.2
ELF	7ee0d000-7ee2c000	Deferred        iphlpapi<elf>
  \-PE	7ee10000-7ee2c000	\               iphlpapi
ELF	7ee2c000-7ee58000	Deferred        ws2_32<elf>
  \-PE	7ee30000-7ee58000	\               ws2_32
ELF	7ee58000-7ee72000	Deferred        wsock32<elf>
  \-PE	7ee60000-7ee72000	\               wsock32
ELF	7ef92000-7ef9d000	Deferred        libnss_files.so.2
ELF	7ef9d000-7efa7000	Deferred        libnss_nis.so.2
ELF	7efa7000-7efbf000	Deferred        libnsl.so.1
ELF	7efbf000-7efe4000	Deferred        libm.so.6
ELF	f7c45000-f7c4e000	Deferred        libnss_compat.so.2
ELF	f7c4f000-f7c53000	Deferred        libdl.so.2
ELF	f7c53000-f7da2000	Deferred        libc.so.6
ELF	f7da2000-f7dba000	Deferred        libpthread.so.0
ELF	f7dd7000-f7f0d000	Deferred        libwine.so.1
ELF	f7f0f000-f7f2e000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) H:\.wine\drive_c\xtcs counter-strike 1.6 final release\cstrike.exe
	00000009    0 <==
0000000c 
	0000001e    0
	00000019    0
	00000018    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000014    0
	00000011    0
	00000010    0
00000015 
	0000001a    0
	00000017    0
	00000016    0
0000001b 
	00000020    0
	0000001f    0
	0000001d    0
	0000001c    0
Backtrace:
=>1 0x014014f9 in cstrike (+0x14f9) (0x0032fbac)
  2 0x01401aa3 in cstrike (+0x1aa3) (0x0032fe7c)
  3 0x014038f1 in cstrike (+0x38f1) (0x0032ff08)
  4 0x7b878387 in kernel32 (+0x58387) (0x0032ffe8)
qbox@qbox:~$ 

```

---

### Post by bapoumba on 2008-11-09
Moved to Wine.

---

### Post by cogadh on 2008-11-09
What did you update (Wine, the game, Ubuntu)?

---

### Post by qbox on 2008-11-10
I make update on Wine. Automatic update.
I use ubuntu 8.04
The game worked before on older versions...

---

### Post by cogadh on 2008-11-10
Roll back to the previous version of Wine, the most current version (1.1.8) is an unstable build and is likely prone to bugs that a previous working version may not have had.

---

### Post by qbox on 2008-11-12
:S hmm. How to do that? My computer upgrade to 1.1.9 .... how to make him to upgrade to stable version and not to newest unstable version.

---

### Post by cogadh on 2008-11-12
The stable version is the one that it is already available in the Ubuntu repositories. Just uninstall Wine (that won't uninstall your applications), remove the WineHQ repository from your software sources, then re-install Wine from the regular Ubuntu repository. You can do all that through Synaptic Package Manager.

---

### Post by qbox on 2008-11-18
In Synaptic Package Manager I only have 1.1.8 version. That is unstable version. I cant get back to 1.0.1 version from repositories.....

---

### Post by jaysoun on 2008-11-18
i have a prob too 
wen i update all my application ............
how to wirte all my application on a cd or a usb 
to use it on other pc??:(:(:(:(:(:(

---

