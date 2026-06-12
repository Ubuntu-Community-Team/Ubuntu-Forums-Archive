---
title: "Age of Mythology install problem"
date: 2008-06-08
forum: Wine
---

### Post by Trebawa on 2008-06-08
I am trying to install Age of Mythology Gold using WINE 0.9.59 on 8.04 Hardy.  When I try to open the AOMSetup.exe on the first of the two CDs, nothing happens.  When I try to do it from the terminal:
```
myname@myname-laptop:/media/cdrom$ wine AOMSetup.exe
myname@myname-laptop:/media/cdrom$ wine: Unhandled page fault on write access to 0x7bc337cf at address 0x7eac22a1 (thread 001d), starting debugger...
Unhandled exception: page fault on write access to 0x7bc337cf in 32-bit code (0x7eac22a1).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7eac22a1 ESP:0033f164 EBP:0033f18c EFLAGS:00010202(   - 00      - -RI1)
 EAX:7bc3377f EBX:7eac6ec8 ECX:0033f198 EDX:00000000
 ESI:00130958 EDI:00010026
Stack dump:
0x0033f164:  00000100 00010026 00010026 0033f238
0x0033f174:  004251d6 00010026 00000000 7eac227a
0x0033f184:  7ed8d70c 00000000 0033f238 0042531f
0x0033f194:  00130958 00130958 0044e608 00010026
0x0033f1a4:  00000100 00010026 00000000 0033f238
0x0033f1b4:  7ed8d70c 0033f1f8 7b88e4e6 7edad520
Backtrace:
=>1 0x7eac22a1 ImmDestroyContext+0x31() in imm32 (0x0033f18c)
  2 0x0042531f in mgs36f (+0x2531f) (0x0033f238)
  3 0x7ed6a4d8 in user32 (+0xaa4d8) (0x0033f278)
  4 0x7ed6d615 in user32 (+0xad615) (0x0033f748)
  5 0x7ed6df40 in user32 (+0xadf40) (0x0033f788)
  6 0x7ecf7b87 DefDlgProcW+0x87() in user32 (0x0033f7b8)
  7 0x7ed6869a WINPROC_wrapper+0x1a() in user32 (0x0033f7e8)
  8 0x7ed68d7e WINPROC_wrapper+0x6fe() in user32 (0x0033f828)
  9 0x7ed6e151 in user32 (+0xae151) (0x0033f868)
  10 0x7ed3187a in user32 (+0x7187a) (0x0033f8d8)
  11 0x7ed34afd in user32 (+0x74afd) (0x0033f938)
  12 0x7ed34f6a SendMessageW+0x4a() in user32 (0x0033f978)
  13 0x7ecfd43c in user32 (+0x3d43c) (0x0033fb48)
  14 0x7ecfe666 CreateDialogIndirectParamAorW+0x36() in user32 (0x0033fb68)
  15 0x7ecfe791 CreateDialogIndirectParamA+0x41() in user32 (0x0033fb98)
  16 0x0044e80a in mgs36f (+0x4e80a) (0x00000001)
  17 0x00000000 (0x00000000)
0x7eac22a1 ImmDestroyContext+0x31 in imm32: subl	$1,0x50(%eax)
Modules:
Module	Address			Debug info	Name (78 modules)
PE	  400000-  566000	Export          mgs36f
PE	10000000-10cfe000	Deferred        mgs5e7
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e2fe000-7e330000	Deferred        uxtheme<elf>
  \-PE	7e300000-7e330000	\               uxtheme
ELF	7e330000-7e344000	Deferred        midimap<elf>
  \-PE	7e340000-7e344000	\               midimap
ELF	7e344000-7e36a000	Deferred        msacm32<elf>
  \-PE	7e350000-7e36a000	\               msacm32
ELF	7e36a000-7e381000	Deferred        msacm32<elf>
  \-PE	7e370000-7e381000	\               msacm32
ELF	7e381000-7e444000	Deferred        libasound.so.2
ELF	7e444000-7e47a000	Deferred        winealsa<elf>
  \-PE	7e450000-7e47a000	\               winealsa
ELF	7e47a000-7e483000	Deferred        libxcursor.so.1
ELF	7e483000-7e488000	Deferred        libxfixes.so.3
ELF	7e488000-7e48b000	Deferred        libxcomposite.so.1
ELF	7e48b000-7e491000	Deferred        libxrandr.so.2
ELF	7e491000-7e499000	Deferred        libxrender.so.1
ELF	7e499000-7e49c000	Deferred        libxinerama.so.1
ELF	7e49c000-7e4a1000	Deferred        libxdmcp.so.6
ELF	7e4a1000-7e4b9000	Deferred        libxcb.so.1
ELF	7e4b9000-7e4bc000	Deferred        libxau.so.6
ELF	7e4bc000-7e5a3000	Deferred        libx11.so.6
ELF	7e5a3000-7e5b1000	Deferred        libxext.so.6
ELF	7e5b1000-7e5c9000	Deferred        libice.so.6
ELF	7e5c9000-7e5d1000	Deferred        libsm.so.6
ELF	7e5de000-7e66f000	Deferred        winex11<elf>
  \-PE	7e5f0000-7e66f000	\               winex11
ELF	7e693000-7e6b4000	Deferred        libexpat.so.1
ELF	7e6b4000-7e6de000	Deferred        libfontconfig.so.1
ELF	7e6de000-7e6e3000	Deferred        libxxf86vm.so.1
ELF	7e6eb000-7e700000	Deferred        libz.so.1
ELF	7e700000-7e770000	Deferred        libfreetype.so.6
ELF	7e770000-7e812000	Deferred        oleaut32<elf>
  \-PE	7e780000-7e812000	\               oleaut32
ELF	7e812000-7e825000	Deferred        libresolv.so.2
ELF	7e825000-7e843000	Deferred        iphlpapi<elf>
  \-PE	7e830000-7e843000	\               iphlpapi
ELF	7e843000-7e8a3000	Deferred        rpcrt4<elf>
  \-PE	7e850000-7e8a3000	\               rpcrt4
ELF	7e8a3000-7e947000	Deferred        ole32<elf>
  \-PE	7e8b0000-7e947000	\               ole32
ELF	7e947000-7e9a0000	Deferred        shlwapi<elf>
  \-PE	7e950000-7e9a0000	\               shlwapi
ELF	7e9a0000-7eaaa000	Deferred        shell32<elf>
  \-PE	7e9b0000-7eaaa000	\               shell32
ELF	7eaaa000-7eac9000	Export          imm32<elf>
  \-PE	7eab0000-7eac9000	\               imm32
ELF	7eac9000-7eadd000	Deferred        lz32<elf>
  \-PE	7ead0000-7eadd000	\               lz32
ELF	7eadd000-7eaf6000	Deferred        version<elf>
  \-PE	7eae0000-7eaf6000	\               version
ELF	7eaf6000-7ebb5000	Deferred        comctl32<elf>
  \-PE	7eb00000-7ebb5000	\               comctl32
ELF	7ebb5000-7ec06000	Deferred        advapi32<elf>
  \-PE	7ebc0000-7ec06000	\               advapi32
ELF	7ec06000-7eca1000	Deferred        gdi32<elf>
  \-PE	7ec20000-7eca1000	\               gdi32
ELF	7eca1000-7ede7000	Export          user32<elf>
  \-PE	7ecc0000-7ede7000	\               user32
ELF	7ede7000-7ee75000	Deferred        winmm<elf>
  \-PE	7edf0000-7ee75000	\               winmm
ELF	7ee75000-7ee80000	Deferred        libnss_files.so.2
ELF	7ee80000-7ee98000	Deferred        libnsl.so.1
ELF	7ee98000-7eea1000	Deferred        libnss_compat.so.2
ELF	7efce000-7eff3000	Deferred        libm.so.6
ELF	7eff3000-7eff5000	Deferred        libxcb-xlib.so.0
ELF	7eff5000-7efff000	Deferred        libnss_nis.so.2
ELF	b7d24000-b7d28000	Deferred        libdl.so.2
ELF	b7d28000-b7e77000	Deferred        libc.so.6
ELF	b7e78000-b7e90000	Deferred        libpthread.so.0
ELF	b7e9d000-b7fb2000	Deferred        libwine.so.1
ELF	b7fb4000-b7fd0000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	0000001b    0
	00000016    0
	00000014    0
	00000010    0
	0000000e    0
	0000000d    0
00000011 
	00000015    0
	00000013    0
	00000012    0
00000017 
	0000001a    0
	00000019    0
	00000018    0
0000001c (D) C:\windows\temp\MGS36f.exe
	0000001d    0 <==
0000001e 
	00000020    0
	0000001f    0
Backtrace:
=>1 0x7eac22a1 ImmDestroyContext+0x31() in imm32 (0x0033f18c)
  2 0x0042531f in mgs36f (+0x2531f) (0x0033f238)
  3 0x7ed6a4d8 in user32 (+0xaa4d8) (0x0033f278)
  4 0x7ed6d615 in user32 (+0xad615) (0x0033f748)
  5 0x7ed6df40 in user32 (+0xadf40) (0x0033f788)
  6 0x7ecf7b87 DefDlgProcW+0x87() in user32 (0x0033f7b8)
  7 0x7ed6869a WINPROC_wrapper+0x1a() in user32 (0x0033f7e8)
  8 0x7ed68d7e WINPROC_wrapper+0x6fe() in user32 (0x0033f828)
  9 0x7ed6e151 in user32 (+0xae151) (0x0033f868)
  10 0x7ed3187a in user32 (+0x7187a) (0x0033f8d8)
  11 0x7ed34afd in user32 (+0x74afd) (0x0033f938)
  12 0x7ed34f6a SendMessageW+0x4a() in user32 (0x0033f978)
  13 0x7ecfd43c in user32 (+0x3d43c) (0x0033fb48)
  14 0x7ecfe666 CreateDialogIndirectParamAorW+0x36() in user32 (0x0033fb68)
  15 0x7ecfe791 CreateDialogIndirectParamA+0x41() in user32 (0x0033fb98)
  16 0x0044e80a in mgs36f (+0x4e80a) (0x00000001)
  17 0x00000000 (0x00000000)
```

Does anyone know what is causing this and how I can fix it?

I previously had the preloader problem described [here]("http://wiki.winehq.org/PreloaderPageZeroProblem"), but the workaround fixed that.

---

### Post by aneeshm on 2008-07-04
I've got exactly the same problem. I JFGd it, but couldn't find anything. Any ideas?

---

### Post by mickey46834 on 2008-10-06
First update your wine to at least version 1.0. Use Synaptic Software manager to do this, it's easier. 

1.) Copy mfc42.dll and pidgen.dll to .wine/C/windows/system32 folder then 2.) Install AOM

During setup before switching to disk 2 click file browser and then file, then click unmount before removing the cd. Then put in cd 2 and it will resume, you must unmount the first cd or it will not locate cd 2.

3.) Then install msxmlenu.msi (it's in cd 2) right click and then 'run as' then choose wine.

4.) Then find a no cd patch copy to the directory to overwrite the original AOM.exe and there ya go it should work just fine. Thats what I did and been playin it for a few days no problems. 

5.) ENJOY

Age of Mythology may be designed for Windows but plays better in Linux

---

