---
title: "gothic 2 problems in wine"
date: 2008-07-29
forum: Wine
---

### Post by aestrivex on 2008-07-29
have been trying for the last few days to get gothic II working in wine.

gothic 2 would not allow me to install it because it would not allow the CDs to be removed and reinserted.  i circumvented this problem by copying the data from CDs 2 and 3 to the wine C drive and inputting the directories manually when the auto-installer program asked me for the next CD.  as far as i can tell, this worked perfectly, and the game has been successfully installed.


this is the terminal output:

```
aestrivex@ometob:~/.wine/drive_c/Program Files/Atari/JoWooD/Gothic2/System$ wine gothic2.exe
wine: Unhandled page fault on execute access to 0x0162fd78 at address 0x162fd78 (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x0162fd78 in 32-bit code (0x0162fd78).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0162fd78 ESP:0162fd78 EBP:00e1530e EFLAGS:00010a03(   - 00      -ROI1C)
 EAX:0000001d EBX:00e15000 ECX:00e190e1 EDX:001100bc
 ESI:00e1a4b2 EDI:00e1a4b2
Stack dump:
0x0162fd78:  0003e860 ebd20000 01eb580a 01eb4048
0x0162fd88:  61e0ff35 346677bb 0001e812 e8e80000
0x0162fd98:  00000002 048320cd 44830b24 c3130424
0x0162fda8:  c703ebe9 1c336984 c703eb24 fb81e884
0x0162fdb8:  2a60200f 84c703eb eb2674e9 9a84c703
0x0162fdc8:  eb04c483 8d84c703 346677bb c703eb12
Backtrace:
=>1 0x0162fd78 (0x00e1530e)
0x0162fd78: pushal	
Modules:
Module	Address			Debug info	Name (58 modules)
PE	  400000-  e25000	Deferred        gothic2
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e577000-7e58a000	Deferred        libresolv.so.2
ELF	7e59e000-7e5bc000	Deferred        iphlpapi<elf>
  \-PE	7e5a0000-7e5bc000	\               iphlpapi
ELF	7e5bc000-7e61d000	Deferred        rpcrt4<elf>
  \-PE	7e5d0000-7e61d000	\               rpcrt4
ELF	7e61d000-7e6c1000	Deferred        ole32<elf>
  \-PE	7e630000-7e6c1000	\               ole32
ELF	7e6e9000-7e71c000	Deferred        uxtheme<elf>
  \-PE	7e6f0000-7e71c000	\               uxtheme
ELF	7e71c000-7e725000	Deferred        libxcursor.so.1
ELF	7e725000-7e72a000	Deferred        libxfixes.so.3
ELF	7e72a000-7e72d000	Deferred        libxcomposite.so.1
ELF	7e72d000-7e733000	Deferred        libxrandr.so.2
ELF	7e733000-7e73b000	Deferred        libxrender.so.1
ELF	7e73b000-7e73e000	Deferred        libxinerama.so.1
ELF	7e73e000-7e75e000	Deferred        imm32<elf>
  \-PE	7e740000-7e75e000	\               imm32
ELF	7e75e000-7e763000	Deferred        libxdmcp.so.6
ELF	7e763000-7e77b000	Deferred        libxcb.so.1
ELF	7e77b000-7e77e000	Deferred        libxau.so.6
ELF	7e77e000-7e865000	Deferred        libx11.so.6
ELF	7e865000-7e873000	Deferred        libxext.so.6
ELF	7e873000-7e878000	Deferred        libxxf86vm.so.1
ELF	7e88c000-7e923000	Deferred        winex11<elf>
  \-PE	7e8a0000-7e923000	\               winex11
ELF	7e941000-7e962000	Deferred        libexpat.so.1
ELF	7e962000-7e98c000	Deferred        libfontconfig.so.1
ELF	7e98c000-7e9a1000	Deferred        libz.so.1
ELF	7e9a1000-7ea11000	Deferred        libfreetype.so.6
ELF	7ea25000-7eae4000	Deferred        comctl32<elf>
  \-PE	7ea30000-7eae4000	\               comctl32
ELF	7eae4000-7eb3d000	Deferred        shlwapi<elf>
  \-PE	7eaf0000-7eb3d000	\               shlwapi
ELF	7eb3d000-7ec50000	Deferred        shell32<elf>
  \-PE	7eb50000-7ec50000	\               shell32
ELF	7ec50000-7eca2000	Deferred        advapi32<elf>
  \-PE	7ec60000-7eca2000	\               advapi32
ELF	7eca2000-7ed3d000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed3d000	\               gdi32
ELF	7ed3d000-7ee84000	Deferred        user32<elf>
  \-PE	7ed60000-7ee84000	\               user32
ELF	7efa4000-7efaf000	Deferred        libnss_files.so.2
ELF	7efaf000-7efc7000	Deferred        libnsl.so.1
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	7efec000-7efee000	Deferred        libxcb-xlib.so.0
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	f7c81000-f7c8a000	Deferred        libnss_compat.so.2
ELF	f7c8b000-f7c8f000	Deferred        libdl.so.2
ELF	f7c8f000-f7dde000	Deferred        libc.so.6
ELF	f7ddf000-f7df7000	Deferred        libpthread.so.0
ELF	f7e0b000-f7f41000	Deferred        libwine.so.1
ELF	f7f43000-f7f62000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Atari\JoWooD\Gothic2\System\gothic2.exe
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
Backtrace:
=>1 0x0162fd78 (0x00e1530e)

```

i have an nVidia 8800, 4 GB ram, AMD phenom.  running 64-bit hardy with wine 1.1.0 (haven't updated to 1.1.1 because of a bug which prevents me from running oblivion).

this is gothic 2 vanilla, without the night of the raven expansion.

at the moment the only other software i have running on wine is oblivion.

i also have tried this both with the native music DLLs described at the appDB page [here](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5023) and without -- although i'm not sure i'm using them right, but i did set them to native in winecfg and made sure the program had access to these DLLs in the Gothic2/System/ folder.

---

### Post by aestrivex on 2008-07-31
bump

---

