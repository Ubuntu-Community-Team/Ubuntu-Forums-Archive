---
title: "Wine crashes"
date: 2008-02-16
forum: Wine
---

### Post by lennyn on 2008-02-16
Hi
Wine or winecfg crashes each time I try to run it on my 64-bit Ubuntu 7.10.

I tried wine versions 0.9.54 (from winehq.org repo) and the one from Ubuntu repository (0.9.46).

I also tried replacing nvidia driver (in xorg.conf) with nv. My kernel version is 2.6.22-14-generic and nvidia proprietary drivers are installed from Ubuntu repository. I've got GeForce 7300GT.

Anyone had the same problem and can help me?

Here is output:

```
lennyn@ubuntu:~$ winecfg
wine: creating configuration directory '/home/lennyn/.wine'...
wine: Unhandled page fault on write access to 0x7e8f74a0 at address 0x7de0c45a (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x7e8f74a0 in 32-bit code (0x7de0c45a).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7de0c45a ESP:0033e97c EBP:0033e9d8 EFLAGS:00010202(   - 00      - -RI1)
 EAX:7e8f74a0 EBX:f7f8dff4 ECX:ffffffb4 EDX:00000006
 ESI:7c05b3b8 EDI:0000000b
Stack dump:
0x0033e97c:  7e90cc7b f7e27000 03c46a09 f7f8dff4
0x0033e98c:  f7e28e88 f7f70d20 0033e9d0 f7f7faf3
0x0033e99c:  f7f70ed8 f7f8dff4 7c05b3b8 0000000b
0x0033e9ac:  f7f80050 00000006 ffa879b8 ffa879d4
0x0033e9bc:  00015048 ffa879b8 00000006 00000020
0x0033e9cc:  f7f8dff4 fffffffc 0000000b 0033ea18
Backtrace:
=>1 0x7de0c45a _nv000000gl+0xa() in libnvidia-tls.so.1 (0x0033e9d8)
  2 0xf7f80183 in ld-linux.so.2 (+0xf183) (0x0033ea18)
  3 0xf7f8409c in ld-linux.so.2 (+0x1309c) (0x0033ea88)
  4 0xf7f7fc96 in ld-linux.so.2 (+0xec96) (0x0033eb68)
  5 0xf7f836ee in ld-linux.so.2 (+0x126ee) (0x0033ebc8)
  6 0xf7cd9c19 GLIBC_2+0xc19() in libdl.so.2 (0x0033ec08)
  7 0xf7f7fc96 in ld-linux.so.2 (+0xec96) (0x0033ece8)
  8 0xf7cda2bc in libdl.so.2 (+0x12bc) (0x0033ed08)
  9 0xf7cd9b51 GLIBC_2+0xb51() in libdl.so.2 (0x0033ed38)
  10 0xf7e61016 wine_dlopen+0x36() in libwine.so.1 (0x0033ed68)
  11 0x7ead54a0 in winex11 (+0x454a0) (0x0033edf8)
  12 0x7ead8cbc X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0033eef8)
  13 0x7eaec033 in winex11 (+0x5c033) (0x0033f108)
  14 0x7eafc608 in winex11 (+0x6c608) (0x0033f128)
  15 0x7bc43115 call_dll_entry_point+0x15() in ntdll (0x0033f148)
  16 0x7bc456a1 in ntdll (+0x356a1) (0x0033f1d8)
  17 0x7bc45943 in ntdll (+0x35943) (0x0033f218)
  18 0x7bc48086 LdrLoadDll+0x66() in ntdll (0x0033f238)
  19 0x7b863bb7 in kernel32 (+0x43bb7) (0x0033f4a8)
  20 0x7b863e93 LoadLibraryExW+0x43() in kernel32 (0x0033f4c8)
  21 0x7b863f83 LoadLibraryExA+0x43() in kernel32 (0x0033f4e8)
  22 0x7b863fbd LoadLibraryA+0x2d() in kernel32 (0x0033f508)
  23 0x7ecc2691 in gdi32 (+0x22691) (0x0033f698)
  24 0x7ecbc060 CreateDCW+0x60() in gdi32 (0x0033f948)
  25 0x7ed6af66 CreateIconFromResourceEx+0x756() in user32 (0x0033fa18)
  26 0x7ed6b535 in user32 (+0x2b535) (0x0033fa88)
  27 0x7ed6dfc9 LoadImageW+0x479() in user32 (0x0033fb38)
  28 0x7ed6e7df LoadImageA+0x1bf() in user32 (0x0033fc38)
  29 0x7ed6e995 LoadCursorA+0x55() in user32 (0x0033fc68)
  30 0x7ed62411 in user32 (+0x22411) (0x0033fc98)
  31 0x7ed6246d in user32 (+0x2246d) (0x0033fcb8)
  32 0x7eddc2c0 in user32 (+0x9c2c0) (0x0033fd68)
  33 0x7edf21e8 in user32 (+0xb21e8) (0x0033fd88)
  34 0x7bc43115 call_dll_entry_point+0x15() in ntdll (0x0033fda8)
  35 0x7bc456a1 in ntdll (+0x356a1) (0x0033fe38)
  36 0x7bc45943 in ntdll (+0x35943) (0x0033fe78)
  37 0x7bc459c8 in ntdll (+0x359c8) (0x0033feb8)
  38 0x7bc48397 LdrInitializeThunk+0x287() in ntdll (0x0033ff08)
  39 0x7b8707ae in kernel32 (+0x507ae) (0x0033ffe8)
  40 0xf7e623d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7de0c45a _nv000000gl+0xa in libnvidia-tls.so.1: movl  %ecx,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (36 modules)
ELF     7b800000-7b928000       Export          kernel32<elf>
  \-PE  7b820000-7b928000       \               kernel32
ELF     7bc00000-7bca3000       Export          ntdll<elf>
  \-PE  7bc10000-7bca3000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7de0c000-7de0e000       Export          libnvidia-tls.so.1
ELF     7de0e000-7e8c1000       Deferred        libglcore.so.1
ELF     7e8c1000-7e965000       Deferred        libgl.so.1
ELF     7e965000-7e96a000       Deferred        libxdmcp.so.6
ELF     7e96a000-7e96d000       Deferred        libxau.so.6
ELF     7e96d000-7ea5e000       Deferred        libx11.so.6
ELF     7ea5e000-7ea6c000       Deferred        libxext.so.6
ELF     7ea87000-7eb17000       Export          winex11<elf>
  \-PE  7ea90000-7eb17000       \               winex11
ELF     7eb72000-7eb92000       Deferred        libexpat.so.1
ELF     7eb92000-7ebbd000       Deferred        libfontconfig.so.1
ELF     7ebbd000-7ebd2000       Deferred        libz.so.1
ELF     7ebd2000-7ec42000       Deferred        libfreetype.so.6
ELF     7ec42000-7ec8d000       Deferred        advapi32<elf>
  \-PE  7ec50000-7ec8d000       \               advapi32
ELF     7ec8d000-7ed25000       Export          gdi32<elf>
  \-PE  7eca0000-7ed25000       \               gdi32
ELF     7ed25000-7ee60000       Export          user32<elf>
  \-PE  7ed40000-7ee60000       \               user32
ELF     7ee60000-7ee74000       Deferred        rundll32<elf>
  \-PE  7ee70000-7ee74000       \               rundll32
ELF     7ef93000-7ef9e000       Deferred        libnss_files.so.2
ELF     7ef9e000-7efa8000       Deferred        libnss_nis.so.2
ELF     7efa8000-7efc0000       Deferred        libnsl.so.1
ELF     7efc0000-7efe5000       Deferred        libm.so.6
ELF     f7cd9000-f7cdd000       Export          libdl.so.2
ELF     f7cdd000-f7e27000       Deferred        libc.so.6
ELF     f7e28000-f7e40000       Deferred        libpthread.so.0
ELF     f7e52000-f7e5b000       Deferred        libnss_compat.so.2
ELF     f7e5b000-f7f6f000       Export          libwine.so.1
ELF     f7f71000-f7f8f000       Export          ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\rundll32.exe
        00000009    0 <==
0000000a 
        0000000b    0
Backtrace:
=>1 0x7de0c45a _nv000000gl+0xa() in libnvidia-tls.so.1 (0x0033e9d8)
  2 0xf7f80183 in ld-linux.so.2 (+0xf183) (0x0033ea18)
  3 0xf7f8409c in ld-linux.so.2 (+0x1309c) (0x0033ea88)
  4 0xf7f7fc96 in ld-linux.so.2 (+0xec96) (0x0033eb68)
  5 0xf7f836ee in ld-linux.so.2 (+0x126ee) (0x0033ebc8)
  6 0xf7cd9c19 GLIBC_2+0xc19() in libdl.so.2 (0x0033ec08)
  7 0xf7f7fc96 in ld-linux.so.2 (+0xec96) (0x0033ece8)
  8 0xf7cda2bc in libdl.so.2 (+0x12bc) (0x0033ed08)
  9 0xf7cd9b51 GLIBC_2+0xb51() in libdl.so.2 (0x0033ed38)
  10 0xf7e61016 wine_dlopen+0x36() in libwine.so.1 (0x0033ed68)
  11 0x7ead54a0 in winex11 (+0x454a0) (0x0033edf8)
  12 0x7ead8cbc X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0033eef8)
  13 0x7eaec033 in winex11 (+0x5c033) (0x0033f108)
  14 0x7eafc608 in winex11 (+0x6c608) (0x0033f128)
  15 0x7bc43115 call_dll_entry_point+0x15() in ntdll (0x0033f148)
  16 0x7bc456a1 in ntdll (+0x356a1) (0x0033f1d8)
  17 0x7bc45943 in ntdll (+0x35943) (0x0033f218)
  18 0x7bc48086 LdrLoadDll+0x66() in ntdll (0x0033f238)
  19 0x7b863bb7 in kernel32 (+0x43bb7) (0x0033f4a8)
  20 0x7b863e93 LoadLibraryExW+0x43() in kernel32 (0x0033f4c8)
  21 0x7b863f83 LoadLibraryExA+0x43() in kernel32 (0x0033f4e8)
  22 0x7b863fbd LoadLibraryA+0x2d() in kernel32 (0x0033f508)
  23 0x7ecc2691 in gdi32 (+0x22691) (0x0033f698)
  24 0x7ecbc060 CreateDCW+0x60() in gdi32 (0x0033f948)
  25 0x7ed6af66 CreateIconFromResourceEx+0x756() in user32 (0x0033fa18)
  26 0x7ed6b535 in user32 (+0x2b535) (0x0033fa88)
  27 0x7ed6dfc9 LoadImageW+0x479() in user32 (0x0033fb38)
  28 0x7ed6e7df LoadImageA+0x1bf() in user32 (0x0033fc38)
  29 0x7ed6e995 LoadCursorA+0x55() in user32 (0x0033fc68)
  30 0x7ed62411 in user32 (+0x22411) (0x0033fc98)
  31 0x7ed6246d in user32 (+0x2246d) (0x0033fcb8)
  32 0x7eddc2c0 in user32 (+0x9c2c0) (0x0033fd68)
  33 0x7edf21e8 in user32 (+0xb21e8) (0x0033fd88)
  34 0x7bc43115 call_dll_entry_point+0x15() in ntdll (0x0033fda8)
  35 0x7bc456a1 in ntdll (+0x356a1) (0x0033fe38)
  36 0x7bc45943 in ntdll (+0x35943) (0x0033fe78)
  37 0x7bc459c8 in ntdll (+0x359c8) (0x0033feb8)
  38 0x7bc48397 LdrInitializeThunk+0x287() in ntdll (0x0033ff08)
  39 0x7b8707ae in kernel32 (+0x507ae) (0x0033ffe8)
  40 0xf7e623d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)
wine: wineprefixcreate failed while creating '/home/lennyn/.wine'.
lennyn@ubuntu:~$ wineserver: could not save registry branch to /home/lennyn/.wine-kPTNll/system.reg : No such file or directory
wineserver: could not save registry branch to /home/lennyn/.wine-kPTNll/user.reg : No such file or directory
```

Thanks in advance.

---

### Post by gsmanners on 2008-02-16
Do you have the dependencies? That is: binfmt-support, ia32-libs, lib32asound2, libc6-i386

---

### Post by lennyn on 2008-02-16
> **gsmanners said:**
> Do you have the dependencies? That is: binfmt-support, ia32-libs, lib32asound2, libc6-i386

Yes, I have. I installed wine with apt.

---

### Post by dankegel on 2008-02-19
> **lennyn said:**
> 
```

Backtrace:
=>1 0x7de0c45a _nv000000gl+0xa() in libnvidia-tls.so.1 (0x0033e9d8)

```


Sure looks like you're still using the proprietary nvidia
driver.  Your attempt to switch to nv didn't work.

Time to reinstall the nvidia driver, I think.

---

### Post by lennyn on 2008-02-19
I installed latest Nvidia drivers from nvidia.com and now it works.
I wonder what was wrong with that drivers from repository...

---

### Post by gsmanners on 2008-02-20
Were you using nvidia-glx or nvidia-glx-new? The new driver is a bit more stable in my experience (with my 7600 GT).

---

### Post by lennyn on 2008-02-20
It was nvidia-glx-new. With nvidia-glx it didn't work well..

---

