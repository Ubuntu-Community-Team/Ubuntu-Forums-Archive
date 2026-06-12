---
title: "Problem with wine and Sony Ericsson Theme Creator"
date: 2008-03-11
forum: Wine
---

### Post by Grone1985 on 2008-03-11
So I installed Sony Ericsson Themes Creator with wine and it worked fine, but when I tried to run the program this came up:

```
maitreyi@maitreyi-laptop:~/.wine/drive_c/Program Files/Sony Ericsson/Themes Creator$ wine ThemesCreator.exe
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x4162b5 (thread 000f), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x004162b5).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:004162b5 ESP:7e6599c0 EBP:7e659a08 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7ee0d64c ECX:00000000 EDX:7ffd0000
 ESI:001238e0 EDI:00000000
Stack dump:
0x7e6599c0:  00000000 00000000 001238e0 7edfefdf
0x7e6599d0:  00000000 00000000 f7dca1a0 7bc330f7
0x7e6599e0:  00000000 f7df6ca3 7bc4580d 7bc8743c
0x7e6599f0:  7bc331b9 00000000 00123948 7bc8743c
0x7e659a00:  001238e0 7edfee90 7e659a18 7bc69cbe
0x7e659a10:  001238e0 7edfee90 7e659ab8 7bc6aaa2
Backtrace:
=>1 0x004162b5 in mdnsresponder (+0x162b5) (0x7e659a08)
  2 0x7bc69cbe call_thread_entry_point+0xe() in ntdll (0x7e659a18)
  3 0x7bc6aaa2 in ntdll (+0x5aaa2) (0x7e659ab8)
  4 0x7bc6b639 in ntdll (+0x5b639) (0x7e65a3d8)
  5 0xf7dee46b start_thread+0xcb() in libpthread.so.0 (0x7e65a4c8)
  6 0xf7d738ce __clone+0x5e() in libc.so.6 (0x00000000)
0x004162b5: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (48 modules)
PE        400000-  457000       Export          mdnsresponder
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca3000       Export          ntdll<elf>
  \-PE  7bc10000-7bca3000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e76c000-7e771000       Deferred        libxfixes.so.3
ELF     7e771000-7e77a000       Deferred        libxcursor.so.1
ELF     7e77a000-7e780000       Deferred        libxrandr.so.2
ELF     7e780000-7e788000       Deferred        libxrender.so.1
ELF     7e788000-7e78b000       Deferred        libxinerama.so.1
ELF     7e78b000-7e790000       Deferred        libxdmcp.so.6
ELF     7e790000-7e793000       Deferred        libxau.so.6
ELF     7e793000-7e884000       Deferred        libx11.so.6
ELF     7e884000-7e892000       Deferred        libxext.so.6
ELF     7e8a3000-7e932000       Deferred        winex11<elf>
  \-PE  7e8b0000-7e932000       \               winex11
ELF     7e96b000-7e98b000       Deferred        libexpat.so.1
ELF     7e98b000-7e9b6000       Deferred        libfontconfig.so.1
ELF     7e9c7000-7e9dc000       Deferred        libz.so.1
ELF     7e9dc000-7ea4c000       Deferred        libfreetype.so.6
ELF     7ea4c000-7eaef000       Deferred        oleaut32<elf>
  \-PE  7ea60000-7eaef000       \               oleaut32
ELF     7eaef000-7eb4e000       Deferred        rpcrt4<elf>
  \-PE  7eb00000-7eb4e000       \               rpcrt4
ELF     7eb4e000-7ebf1000       Deferred        ole32<elf>
  \-PE  7eb60000-7ebf1000       \               ole32
ELF     7ebf1000-7ec89000       Deferred        gdi32<elf>
  \-PE  7ec00000-7ec89000       \               gdi32
ELF     7ec89000-7edc7000       Deferred        user32<elf>
  \-PE  7eca0000-7edc7000       \               user32
ELF     7edc7000-7ee12000       Deferred        advapi32<elf>
  \-PE  7edd0000-7ee12000       \               advapi32
ELF     7ee12000-7ee25000       Deferred        libresolv.so.2
ELF     7ee25000-7ee43000       Deferred        iphlpapi<elf>
  \-PE  7ee30000-7ee43000       \               iphlpapi
ELF     7ee43000-7ee6e000       Deferred        ws2_32<elf>
  \-PE  7ee50000-7ee6e000       \               ws2_32
ELF     7ee6e000-7ee79000       Deferred        libnss_files.so.2
ELF     7ee79000-7ee91000       Deferred        libnsl.so.1
ELF     7ee91000-7ee9a000       Deferred        libnss_compat.so.2
ELF     7efca000-7efef000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     f7c9a000-f7c9e000       Deferred        libdl.so.2
ELF     f7c9e000-f7de8000       Export          libc.so.6
ELF     f7de9000-f7e01000       Export          libpthread.so.0
ELF     f7e12000-f7f26000       Deferred        libwine.so.1
ELF     f7f28000-f7f46000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
        00000009    0
0000000a 
        0000000b    0
0000000c (D) C:\Program Files\Bonjour\mDNSResponder.exe
        0000000f    0 <==
        0000000e    0
        0000000d    0
Backtrace:
=>1 0x004162b5 in mdnsresponder (+0x162b5) (0x7e659a08)
  2 0x7bc69cbe call_thread_entry_point+0xe() in ntdll (0x7e659a18)
  3 0x7bc6aaa2 in ntdll (+0x5aaa2) (0x7e659ab8)
  4 0x7bc6b639 in ntdll (+0x5b639) (0x7e65a3d8)
  5 0xf7dee46b start_thread+0xcb() in libpthread.so.0 (0x7e65a4c8)
  6 0xf7d738ce __clone+0x5e() in libc.so.6 (0x00000000)
err:advapi:service_control_dispatcher pipe connect failed
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Sony Ericsson\\Themes Creator\\SEMC_FilterImagesDLL.dll") not found
err:module:import_dll Library SEMC_FilterImagesDLL.dll (which is needed by L"C:\\Program Files\\Sony Ericsson\\Themes Creator\\ThemesCreator.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Sony Ericsson\\Themes Creator\\ThemesCreator.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Sony Ericsson\\Themes Creator\\ThemesCreator.exe" failed, status c0000135
```

I'm thinking that this huge backtrace is two problems together that are not related because the first part of it (that involves Bonjour Service and related) come up even when I try to open winecfg (even though winecfg works). I'm running on wine 0.9.57 and Ubuntu Gutsy 64x.

Any one can help?
Thanks in advance!

Jorge

---

### Post by depeha on 2008-03-11
[http://developer.sonyericsson.com/site/global/docstools/multimedia/p_multimedia.jsp](http://developer.sonyericsson.com/site/global/docstools/multimedia/p_multimedia.jsp)

;)

---

### Post by Grone1985 on 2008-03-11
I know there is a native linux version but it won't work because is missing "Gstreamer 0.8" libraries which I don't know how to get on Gutsy cause they are not on the repos.

So I don't know how to fix the problem... Any thoughts??

---

### Post by khalidaziz on 2008-05-05
*bump

same problem.

How to install Gstreamer 0.8 on Gutsy?

---

### Post by ace214 on 2008-05-10
Try reading the output...

It says it needs two DLL files. MSVCP60.dll and SEMC_FilterImagesDLL.dll.

The latter is in the installed directory so you're find there. Google the first and you can download it. Unzip and put the dll file in you ~/.wine/Windows/system32 directory and you should be good to go.

---

### Post by corden on 2008-09-26
Solution:
1. Add this - deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe - to System -> Administration -> Software Sources -> Third-Party Software

2. Open - System -> Administration -> Synaptic Package Manager and search the following: libgstreamer0.8-0 and libgstreamer-plugins0.8-0

Feel free to contact me about this matter.

---

### Post by Vlammetje on 2008-10-05
Hi,

I have followed almost every instruction I could find on the matter, including the above, however theme creator (3.29) will not install. It has previously worked on ubuntu, however, currently on Kubuntu 8.04 I seem to hit a wall somewhere. What else might fix this?

---

### Post by Mangust22 on 2008-10-07
> **khalidaziz said:**
> *bump

same problem.

How to install Gstreamer 0.8 on Gutsy?

You have to download DEB (hardy heron or earlier) from package.ubuntu and install it. That's all.

---

