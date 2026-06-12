---
title: "Wine 1.5 segfaults on clean installed Precise"
date: 2012-08-01
forum: Wine
---

### Post by thoriumbr on 2012-08-01
Hi all,

I have a wine 1.5 dying as soon as I try to run it. Even winecfg is dying. I cannot even run notepad:

```

user@myhost:~$ notepad
Segmentation fault (core dumped)

```

I asked Google, but could not get any answer. I got some threads on ancient wine versions (0.9 or earlier), but nothing more recent. Some threads suggested removing pulseaudio (not worked), removing ~/.wine (not needed, is a clean install and the dir doesn't exists yet).

I tried wine-1.4 before, got the same results. So I installed the development version, hoping to get better results, but got exactly the same problem: core dump after a ENOMEM.

I changed /usr/bin/winecfg to add a strace before running wine, and got this (trimmed down to the interesting parts):
```

user@myhost:~$ winecfg
execve("/usr/bin/wine", ["/usr/bin/wine", "winecfg.exe"], [/* 40 vars */]) = 0
brk(0)                                  = 0x7de32000
...
readlink("/proc/self/exe", "/usr/bin/wine", 256) = 13
stat64("/usr/bin/wineserver", {st_mode=S_IFREG|0755, st_size=342196, ...}) = 0
execve("/usr/bin/wine-preloader", ["/usr/bin/wine-preloader", "/usr/bin/wine", "winecfg.exe"], [/* 41 vars */]) = 0
set_thread_area({entry_number:-1 -> 6, base_addr:0x7c402080, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
**old_mmap(NULL, 65536, PROT_NONE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS|MAP_NORESERVE, -1, 0) = -1 EPERM (Operation not permitted)**
old_mmap(0x10000, 1048576, PROT_NONE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS|MAP_NORESERVE, -1, 0) = 0x10000
old_mmap(0x110000, 1743716352, PROT_NONE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS|MAP_NORESERVE, -1, 0) = 0x110000
old_mmap(0x7f000000, 50331648, PROT_NONE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS|MAP_NORESERVE, -1, 0) = 0x7f000000
mprotect(0x7ffff000, 4096, PROT_READ|PROT_EXEC) = 0
open("/usr/bin/wine", O_RDONLY)         = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\2\0\3\0\1\0\0\0\200\f\360{4\0\0\0"..., 2048) = 2048
[B]old_mmap(0x7bf00000, 8192, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED, 3, 0) = -1 ENOMEM (Cannot allocate memory)
old_mmap(0x7bf02000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0x1000) = -1 EBADF (Bad file descriptor)[/B]
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
Segmentation fault (core dumped)

```

My installation:
```

user@myhost:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

user@myhost:~$ uname -a
Linux myhost 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686 i686 i386 GNU/Linux
user@myhost:~$ wine --version
wine-1.5.10
user@myhost:~$ ldd /usr/bin/wine
	linux-gate.so.1 =>  (0xb7794000)
	libwine.so.1 => /usr/bin/../lib/i386-linux-gnu/libwine.so.1 (0xb7650000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb7622000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb747c000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb7477000)
	/lib/ld-linux.so.2 (0xb7795000)


```

---

### Post by Toz on 2012-08-08
Moving to the Wine sub-forum for better visibility.

---

### Post by anaglier on 2012-08-22
Hi all,
I do have the same issue running winecfg . Got a segfault on the preloader.
```
anaglier@anaglierW520:~$ winecfg
Segmentation fault (core dumped)
```

```
uname -a
Linux anaglierW520 3.2.0-30-generic-pae #47-Ubuntu SMP Wed Aug 15 18:52:06 UTC 2012 i686 i686 i386 GNU/Linux

anaglier@anaglierW520:~$ wine --version
wine-1.5.11

anaglier@anaglierW520:~$ ldd /usr/bin/wine
	linux-gate.so.1 =>  (0xb7744000)
	libwine.so.1 => /usr/bin/../lib/i386-linux-gnu/libwine.so.1 (0xb7600000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb75cb000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb7425000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb7420000)
	/lib/ld-linux.so.2 (0xb7745000)

```

I did an upgrade from oneiric where last kernel versions gave the same core dump. In order to let wine work I had to boot from an oldest kernel version. Unfortunately I do not remember whch one right now.
Any help would be much appreciated

Tx

---

### Post by justinshafer on 2012-11-21
Strange... I have an HP Touchpad loaded with 12.10 beta..

I did:
sudo apt-get build-dep wine

downloaded 1.5.11
installed it.
It worked.

Then messed with qemu and x86 stuff... 

When I went back to the arm version... It segfaulted.. Manually removed wine out of /usr/local/bin lib share, etc... did make install on the arm version.. still segfaulted. 

The only thing I really did was delete the /usr/src folder to free up some space. And I am running a different kernel then what is in /usr/src.....???? 2.6.35 palm-tenderloin from ubuntu touchpad which is based of the CyanogenMod9 kernel....

I decided to dump ubuntu and reinstall.. That is what I am doing now.

Maybe it had something to do with VM-SPLIT 3G... I had 2G (default CM9 option) when I was messing with X86 and Qemu and Wine... So I compiled in 3G to get the X86 version of wine and qemu to work along with binfmt... I have the option to boot either kernel.. and it was segfaulting on both. ODD.

---

