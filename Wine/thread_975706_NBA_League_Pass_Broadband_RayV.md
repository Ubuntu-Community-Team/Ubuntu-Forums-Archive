---
title: "NBA League Pass Broadband RayV"
date: 2008-11-08
forum: Wine
---

### Post by pt123 on 2008-11-08
I am trying to install NBA League Pass International. But it requires the installation of a software called RayV
[http://rayv.tv/](http://rayv.tv/)

which only has client versions for Windows and Mac.

So I tried to install it through Wine,  version wine-1.1.8 on Hardy
(note I installed Windows Media Player 9 using winetricks),

I am stuck at the installation screen of RayV as it thinks I have "worse" than Windows XP SP2 (attached is a screen shot). I have tried changing the setting to Vista through winecfg but no luck. 
Does anyone know what it might be looking for to determine if I have SP2. 

Below is the output of the terminal when it seems to be checking for SP2
```

fixme:win:EnumDisplayDevicesW ((null),0,0x33ea28,0x00000000), stub!

```


Below is the full output
```

wine: Call from 0x7b844e10 to unimplemented function ntoskrnl.exe.KeInitializeQueue, aborting
wine: Call from 0x7b844e10 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Unimplemented function ntoskrnl.exe.ExInitializeResourceLite called at address 0x7b844e10 (thread 001c), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.ExInitializeResourceLite called in 32-bit code (0x7b844e86).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b844e86 ESP:7ec29658 EBP:7ec296bc EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82ec55 EBX:7b8b3824 ECX:00000000 EDX:00114918
 ESI:00114918 EDI:001149d2
Stack dump:
0x7ec29658:  7ec296e4 00000008 7ec29668 0000004c
0x7ec29668:  80000100 00000001 00000000 7b844e10
0x7ec29678:  00000002 7edf37e0 7edf42c8 00000000
0x7ec29688:  00000000 00000000 00000000 00000000
0x7ec29698:  00000000 00000000 00000000 00000000
0x7ec296a8:  00000001 7bc41d95 004502c0 00000020
Backtrace:
=>1 0x7b844e86 in kernel32 (+0x24e86) (0x7ec296bc)
  2 0x7edf3775 in ntoskrnl (+0x13775) (0x7ec296ec)
  3 0x7ede9248 in ntoskrnl (+0x9248) (0x7ec29728)
  4 0x7ee71fe8 in winedevice (+0x1fe8) (0x7ec299e8)
  5 0x7ee47937 in advapi32 (+0x27937) (0x7ec29a38)
  6 0x7bc6d9ce call_thread_entry_point+0xe() in ntdll (0x7ec29a48)
  7 0x7bc6e0a2 in ntdll (+0x5e0a2) (0x7ec29ae8)
  8 0x7bc6e2d2 in ntdll (+0x5e2d2) (0x7ec2a3d8)
  9 0xb7e254fb start_thread+0xcb() in libpthread.so.0 (0x7ec2a4c8)
0x7b844e86: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (31 modules)
PE	  450000-  455560	Deferred        cdralw2k.sys
ELF	7b800000-7b93b000	Export          kernel32<elf>
  \-PE	7b820000-7b93b000	\               kernel32
ELF	7bc00000-7bca9000	Export          ntdll<elf>
  \-PE	7bc10000-7bca9000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7ea9b000-7eab0000	Deferred        hal<elf>
  \-PE	7eaa0000-7eab0000	\               hal
ELF	7eab0000-7eb1a000	Deferred        msvcrt<elf>
  \-PE	7eac0000-7eb1a000	\               msvcrt
ELF	7ec2b000-7ec3e000	Deferred        libresolv.so.2
ELF	7ec3e000-7ec5d000	Deferred        iphlpapi<elf>
  \-PE	7ec40000-7ec5d000	\               iphlpapi
ELF	7ec5d000-7ecc2000	Deferred        rpcrt4<elf>
  \-PE	7ec70000-7ecc2000	\               rpcrt4
ELF	7edd3000-7ee0c000	Export          ntoskrnl<elf>
  \-PE	7ede0000-7ee0c000	\               ntoskrnl
ELF	7ee0c000-7ee60000	Export          advapi32<elf>
  \-PE	7ee20000-7ee60000	\               advapi32
ELF	7ee60000-7ee74000	Export          winedevice<elf>
  \-PE	7ee70000-7ee74000	\               winedevice
ELF	7ee74000-7ee8c000	Deferred        libnsl.so.1
ELF	7ee8c000-7ee95000	Deferred        libnss_compat.so.2
ELF	7efc8000-7efed000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_files.so.2
ELF	b7cc1000-b7ccb000	Deferred        libnss_nis.so.2
ELF	b7ccc000-b7cd0000	Deferred        libdl.so.2
ELF	b7cd0000-b7e1f000	Deferred        libc.so.6
ELF	b7e20000-b7e38000	Export          libpthread.so.0
ELF	b7e4b000-b7f81000	Deferred        libwine.so.1
ELF	b7f83000-b7f9f000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	0000001b    0
	0000001a    0
	00000013    0
	0000000e    0
	0000000d    0
00000017 (D) c:\windows\system32\winedevice.exe
	0000001c    0 <==
	00000019    0
	00000018    0
Backtrace:
=>1 0x7b844e86 in kernel32 (+0x24e86) (0x7ec296bc)
  2 0x7edf3775 in ntoskrnl (+0x13775) (0x7ec296ec)
  3 0x7ede9248 in ntoskrnl (+0x9248) (0x7ec29728)
  4 0x7ee71fe8 in winedevice (+0x1fe8) (0x7ec299e8)
  5 0x7ee47937 in advapi32 (+0x27937) (0x7ec29a38)
  6 0x7bc6d9ce call_thread_entry_point+0xe() in ntdll (0x7ec29a48)
  7 0x7bc6e0a2 in ntdll (+0x5e0a2) (0x7ec29ae8)
  8 0x7bc6e2d2 in ntdll (+0x5e2d2) (0x7ec2a3d8)
  9 0xb7e254fb start_thread+0xcb() in libpthread.so.0 (0x7ec2a4c8)
wine: Call from 0x7b844e10 to unimplemented function ntoskrnl.exe.ExInitializeZone, aborting
wine: Call from 0x7b844e10 to unimplemented function ntoskrnl.exe.ExInterlockedAddLargeInteger, aborting
fixme:win:EnumDisplayDevicesW ((null),0,0x33ea28,0x00000000), stub!


```

Thanks

---

### Post by jeffsjazz on 2008-11-24
I have this same problem,have you been able to correct it?
Thanks, Dr. Jeff

---

### Post by pt123 on 2008-11-25
No I tried even copying the WIndows installation files into wine and running it from there. But it was saying Adobe Flash ActiveX was not installed. No sure if it is even possible to install than on Wine.

---

### Post by stayfly on 2009-04-25
any progress with this?

---

### Post by neaorin on 2010-04-24
(deleted)

---

