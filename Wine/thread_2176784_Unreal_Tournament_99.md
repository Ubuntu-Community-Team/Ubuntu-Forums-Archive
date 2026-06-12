---
title: "Unreal Tournament 99"
date: 2013-09-26
forum: Wine
---

### Post by cheesekiller on 2013-09-26
I have the cd and i have ubuntu 12.04.....   i can't seem to get it to work. i dont understand how to install the linux version and when i try to wine it no matter what wine version i use i get this ....

```
 Unhandled exception: privileged instruction in 32-bit code (0x0040aae4).Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0040aae4 ESP:0033fd00 EBP:0033fde4 EFLAGS:00010292(  R- --  I S -A- - )
 EAX:003300f2 EBX:00000000 ECX:00000067 EDX:00400000
 ESI:7b869c60 EDI:00400000
Stack dump:
0x0033fd00:  00410fed 00000000 00400000 00000067
0x0033fd10:  0041ab90 0012c38f 7b89c5f0 7bc35537
0x0033fd20:  0033fe70 00000800 00000000 00000000
0x0033fd30:  00000000 0033fd54 00000094 00000005
0x0033fd40:  00000001 00000a28 00000002 76726553
0x0033fd50:  20656369 6b636150 00003320 00000000
Backtrace:
=>0 0x0040aae4 in unrealtournament (+0xaae4) (0x0033fde4)
  1 0x0041ace2 in unrealtournament (+0x1ace1) (0x0033fe70)
  2 0x7b85cc0c call_process_entry+0xb() in kernel32 (0x0033fe88)
  3 0x7b8601bb start_process+0x5a(peb=0x7b869c60) [/root/wine-1.5.10/dlls/kernel32/process.c:1083] in kernel32 (0x0033fec8)
  4 0x7bc77130 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  5 0x7bc79cad call_thread_func+0x7c() in ntdll (0x0033ffa8)
  6 0x7bc7710e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  7 0x7bc4c82e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0x0040aae4: outl	%eax,$0x99
Modules:
Module	Address			Debug info	Name (47 modules)
PE	  400000-  44b000	Export          unrealtournament
ELF	7b800000-7b8fd000	Dwarf           kernel32<elf>
  \-PE	7b810000-7b8fd000	\               kernel32
ELF	7bc00000-7bcca000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcca000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e766000-7e789000	Deferred        imm32<elf>
  \-PE	7e770000-7e789000	\               imm32
ELF	7e7a0000-7e7a6000	Deferred        libxfixes.so.3
ELF	7e7a6000-7e7b1000	Deferred        libxcursor.so.1
ELF	7e7b1000-7e7c1000	Deferred        libxi.so.6
ELF	7e7c1000-7e7ca000	Deferred        libxrandr.so.2
ELF	7e7ca000-7e7d4000	Deferred        libxrender.so.1
ELF	7e7d4000-7e7da000	Deferred        libxxf86vm.so.1
ELF	7e7da000-7e7de000	Deferred        libxinerama.so.1
ELF	7e7de000-7e7e5000	Deferred        libxdmcp.so.6
ELF	7e7e5000-7e806000	Deferred        libxcb.so.1
ELF	7e806000-7e80c000	Deferred        libuuid.so.1
ELF	7e80c000-7e826000	Deferred        libice.so.6
ELF	7e826000-7e95a000	Deferred        libx11.so.6
ELF	7e95a000-7e96c000	Deferred        libxext.so.6
ELF	7e96c000-7e975000	Deferred        libsm.so.6
ELF	7e975000-7e9ff000	Deferred        winex11<elf>
  \-PE	7e980000-7e9ff000	\               winex11
ELF	7e9ff000-7ea15000	Deferred        libz.so.1
ELF	7ea15000-7eaaf000	Deferred        libfreetype.so.6
ELF	7eace000-7eb33000	Deferred        advapi32<elf>
  \-PE	7eae0000-7eb33000	\               advapi32
ELF	7eb33000-7ec3e000	Deferred        gdi32<elf>
  \-PE	7eb40000-7ec3e000	\               gdi32
ELF	7ec3e000-7ed85000	Deferred        user32<elf>
  \-PE	7ec50000-7ed85000	\               user32
ELF	7ed85000-7ed92000	Deferred        libnss_files.so.2
ELF	7ed92000-7edac000	Deferred        libnsl.so.1
ELF	7edac000-7edb5000	Deferred        libnss_compat.so.2
ELF	7efb5000-7efe1000	Deferred        libm.so.6
ELF	7efe2000-7efe6000	Deferred        libxcomposite.so.1
ELF	7efe6000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f73d3000-f73df000	Deferred        libnss_nis.so.2
ELF	f73e0000-f73e5000	Deferred        libdl.so.2
ELF	f73e5000-f758e000	Deferred        libc.so.6
ELF	f758f000-f75aa000	Deferred        libpthread.so.0
ELF	f75ac000-f75b0000	Deferred        libxau.so.6
ELF	f75c9000-f770b000	Dwarf           libwine.so.1
ELF	f770d000-f772f000	Deferred        ld-linux.so.2
ELF	f772f000-f7730000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001f    0
	0000001e    0
	00000018    0
	00000017    0
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
00000023 explorer.exe
	00000024    0
00000025 (D) C:\UnrealTournament\System\UnrealTournament.exe
	00000026    0 <==
System information:
    Wine build: wine-1.5.20
    Platform: i386
    Host system: Linux
    Host version: 3.6.9-030609-generic


 
```

I'm at a complete loss.... Any ideas?

---

### Post by albandy on 2013-09-26
You've to download and execute the installer:
[http://www.atomicgamer.com/files/12712/ut-install-436-run](http://www.atomicgamer.com/files/12712/ut-install-436-run)

---

### Post by cheesekiller on 2013-09-26
i've tried that but ubuntu 12.04 apparently has newer libraries that arent compatible or something....

---

### Post by peeteedee on 2013-09-26
Are you using these instructions to install Wine on 12.04? :?:

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

You might have to purge the old Wine install first.  Open File Manager (if on KDE) and type "ALT + ." to show hidden files.  Then delete ./wine directory.  Maybe try "sudo apt-get purge wine" first too.

Then just put Unreal Tournament CD into your disk drive, let File Manager open up the Unreal CD for you, and then RIGHT click on the "setup.exe" file and use the "use wine installer" (I think?) menu choice in the menu that pops up to install Unreal Tournament.

Easy peasy.  At least that's how it worked out for me re-installing UT two days ago after screwing up the system futzing around trying to install newer Nvidia drivers. :mad:

---

### Post by Toz on 2013-09-26
*Moved to the **Wine** subforum.*

---

### Post by cheesekiller on 2013-09-28
actually i am installing it with the correct wine version and everything. i use playonlinux and install it in its own virtual drive. I'd love to get it working natively but i don't think thats really an option so thank you for moving it to the wine subforum.


[http://appdb.winehq.org/objectManager.php?sClass=application&iId=90](http://appdb.winehq.org/objectManager.php?sClass=application&iId=90)   
wine 1.5.22
but it crashes and gives me the error i pasted above.

---

### Post by enterdavertex on 2013-10-04
Actually this version of Unreal Tournament 99,  was available on Linux. You should give it a try someday.

---

