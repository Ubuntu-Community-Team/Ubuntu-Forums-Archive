---
title: "Segmentation faults with most windows progs"
date: 2008-11-22
forum: Wine
---

### Post by themusicalduck on 2008-11-22
Hey, I have a strange problem and can't seem to find anything which might help to fix it.. When I try to run about half of the programs installed in wine, I get a segmentation fault.

So far, I can't run Wow, Enemy Territory, Max/Msp 5 or Steam.. Each program gives a segmentation fault at some stage.

Wow I can get as far as the launcher, but if I try to run the Wow.exe it comes up with segmentation. ET gets as far as the console, then segmentation. On steam it happens if I try to install a game. On Max/Msp, the one time I tried to run it it came up with this in the console -

```
wine: Call from 0x7b845810 to unimplemented function ntoskrnl.exe.KeInitializeMutex, aborting
wine: Unimplemented function ntoskrnl.exe.KeInitializeMutex called at address 0x7b845810 (thread 0015), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.KeInitializeMutex called in 32-bit code (0x7b845883).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b845883 ESP:7ec0c618 EBP:7ec0c67c EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82f005 EBX:7b8b7ff4 ECX:00000000 EDX:7ec0c6a4
 ESI:7ec0c6a4 EDI:00467004
Stack dump:
0x7ec0c618:  7ec0c6a4 00000008 0000003c 80000100
0x7ec0c628:  00000001 00000000 7b845810 00000002
0x7ec0c638:  7edf5a20 7edf8826 7bc8fff4 f7ed3ff4
0x7ec0c648:  7ee0e000 7ec0c67c f7db6212 7ee0e000
0x7ec0c658:  00110000 00000002 00110000 00000000
0x7ec0c668:  00113ff8 00110014 7b84581a 7ee9dff4
Backtrace:
=>1 0x7b845883 in kernel32 (+0x25883) (0x7ec0c67c)
  2 0x7edf59b5 in ntoskrnl (+0x159b5) (0x7ec0c6ac)
  3 0x7edee990 in ntoskrnl (+0xe990) (0x7ec0c6dc)
  4 0x00469337 in tpkd.sys (+0x19337) (0x7ec0c988)
  5 0x7ee9c336 in winedevice (+0xc336) (0x7ec0c9d8)
  6 0x7ee4b2dc in advapi32 (+0x2b2dc) (0x7ec0ca28)
  7 0x7bc701de call_thread_entry_point+0xe() in ntdll (0x7ec0ca38)
  8 0x7bc71842 in ntdll (+0x61842) (0x7ec0cad8)
  9 0x7bc71a3d in ntdll (+0x61a3d) (0x7ec0d3c8)
  10 0xf7d8350f start_thread+0xbf() in libpthread.so.0 (0x7ec0d4c8)
  11 0xf7d01ece __clone+0x5e() in libc.so.6 (0x00000000)
0x7b845883: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (31 modules)
PE	  450000-  46e000	Export          tpkd.sys
ELF	7b800000-7b940000	Export          kernel32<elf>
  \-PE	7b820000-7b940000	\               kernel32
ELF	7bc00000-7bcac000	Export          ntdll<elf>
  \-PE	7bc10000-7bcac000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ea91000-7eafd000	Deferred        msvcrt<elf>
  \-PE	7eaa0000-7eafd000	\               msvcrt
ELF	7ec0e000-7ec22000	Deferred        libresolv.so.2
ELF	7ec27000-7ec3d000	Deferred        hal<elf>
  \-PE	7ec30000-7ec3d000	\               hal
ELF	7ec3d000-7ec5d000	Deferred        iphlpapi<elf>
  \-PE	7ec40000-7ec5d000	\               iphlpapi
ELF	7ec5d000-7ecc4000	Deferred        rpcrt4<elf>
  \-PE	7ec70000-7ecc4000	\               rpcrt4
ELF	7edd5000-7ee0f000	Export          ntoskrnl<elf>
  \-PE	7ede0000-7ee0f000	\               ntoskrnl
ELF	7ee0f000-7ee64000	Export          advapi32<elf>
  \-PE	7ee20000-7ee64000	\               advapi32
ELF	7ee64000-7ee70000	Deferred        libnss_files.so.2
ELF	7ee70000-7ee7b000	Deferred        libnss_nis.so.2
ELF	7ee7b000-7ee84000	Deferred        libnss_compat.so.2
ELF	7ee8a000-7ee9f000	Export          winedevice<elf>
  \-PE	7ee90000-7ee9f000	\               winedevice
ELF	7efbf000-7efe5000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        libnsl.so.1
ELF	f7c1a000-f7c1e000	Deferred        libdl.so.2
ELF	f7c1e000-f7d7c000	Export          libc.so.6
ELF	f7d7d000-f7d96000	Export          libpthread.so.0
ELF	f7db1000-f7ee8000	Deferred        libwine.so.1
ELF	f7eea000-f7f0a000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f (D) C:\windows\system32\winedevice.exe
	00000015    0 <==
	00000011    0
	00000010    0
Backtrace:
=>1 0x7b845883 in kernel32 (+0x25883) (0x7ec0c67c)
  2 0x7edf59b5 in ntoskrnl (+0x159b5) (0x7ec0c6ac)
  3 0x7edee990 in ntoskrnl (+0xe990) (0x7ec0c6dc)
  4 0x00469337 in tpkd.sys (+0x19337) (0x7ec0c988)
  5 0x7ee9c336 in winedevice (+0xc336) (0x7ec0c9d8)
  6 0x7ee4b2dc in advapi32 (+0x2b2dc) (0x7ec0ca28)
  7 0x7bc701de call_thread_entry_point+0xe() in ntdll (0x7ec0ca38)
  8 0x7bc71842 in ntdll (+0x61842) (0x7ec0cad8)
  9 0x7bc71a3d in ntdll (+0x61a3d) (0x7ec0d3c8)
  10 0xf7d8350f start_thread+0xbf() in libpthread.so.0 (0x7ec0d4c8)
  11 0xf7d01ece __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b845810 to unimplemented function ntoskrnl.exe.KeInitializeQueue, aborting
wine: Call from 0x7b845810 to unimplemented function ntoskrnl.exe.KeInitializeSemaphore, aborting
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d23c9f8, overlapped 0x7d23c9dc): stub
fixme:shell:DllCanUnloadNow stub
err:rpc:I_RpcReceive we got fault packet with status 0x3e6
err:seh:setup_exception_record stack overflow 436 bytes in thread 000b eip 7bc69cc7 esp 0024117c stack 0x240000-0x241000-0x340000
Segmentation fault

```

Second time I tried, it went straight to segmentation fault.

The only programs which do work are photoshop 7, IE6, winecfg, regedit and notepad. :(

---

### Post by themusicalduck on 2008-11-22
bump

---

### Post by ciscosurfer on 2008-11-22
I've had very good luck with Crossover in the past.  If you're interested, you should look into [http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by themusicalduck on 2008-11-23
Isn't crossover based on wine? I'll give it a go, but I did try it before and didn't like it all that much compared to just having wine.

I have just tried doing a fresh install of intrepid, and am STILL getting segmentation faults.. :|

I thought reinstall would be the last resort, definite fix but something really seems to be wrong here.. :(

---

