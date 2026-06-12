---
title: "Determining Bit Depth of Programs ..."
date: 2008-07-21
forum: x86 64-bit Users
---

### Post by xen-uno on 2008-07-21
When running Task Manager in XP x64 and viewing processes, a 32 bit program will have a *32 next to it. Is there something similar in Ubuntu? Curious as I don't know for sure whether FireFox 3 as included in 8.04 x64 (and FF2 in 7.10 x64) is 32 bit or 64 bit. Need for ndiswrapper seems to say that FF is 64, but it could also be needed for emulation of Windows code.

---

### Post by jpkotta on 2008-07-22
You can do it with ldd.  E.g.:

```
[jpkotta@gauss][/usr/lib/opera/9.27-20080331.1][0]
$ ldd opera 
	linux-gate.so.1 =>  (0xffffe000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7e81000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7e73000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7e6a000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7e52000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7e3a000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7e36000)
	libm.so.6 => /lib32/libm.so.6 (0xf7e11000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7dfc000)
	libc.so.6 => /lib32/libc.so.6 (0xf7cac000)
	libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf7caa000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf7c92000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7c8f000)
	/lib/ld-linux.so.2 (0xf7f82000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7c8a000)
```

My Opera is 32-bit, and you can see it uses the ia32-libs.

---

### Post by xen-uno on 2008-07-22
I get...

root@ubuntu:/usr/lib/firefox-3.0# ldd firefox
	linux-vdso.so.1 =>  (0x00007fff0e9fe000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f4606505000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f4606301000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f4605ff6000)
	libm.so.6 => /lib/libm.so.6 (0x00007f4605d75000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f4605b67000)
	libc.so.6 => /lib/libc.so.6 (0x00007f4605805000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f4606721000)

... so it appears FF is 64 bit though it's not nearly as cut & dried as Opera. There is 3 lib dirs; lib, lib32, & lib64. Last 2 are self evident as far as depth, but what about lib?

Thanks ...

---

### Post by jpkotta on 2008-07-22
It's 64-bit.  On a 64-bit system, /lib is where 64-bit libraries live.  Also, look at the last line, I'd say that's pretty cut and dried.  AFAIK, a given binary will be either 64-bit or 32-bit, not both.

---

### Post by xen-uno on 2008-07-22
I suppose it is given that lib is x64, and lib64 must be there for legacy purposes. Still, ldd lists dependencies, and some of those could be 32 bit if accessed through a wrapper or thunker ... I think.

---

### Post by Cappy on 2008-07-23
Use
```
file /path/to/binary/or/library
```
and it will say ELF 32-bit or ELF 64-bit

---

### Post by xen-uno on 2008-07-23
Indeed (both FF & Tbird bins are 64 bit) ... gracias amigo

---

### Post by Ptero-4 on 2008-07-23
Actually. lib is a symlink to lib64, lib32 is there for 32-bit stuff.

---

### Post by jpkotta on 2008-07-23
> **Ptero-4 said:**
> Actually. lib is a symlink to lib64, lib32 is there for 32-bit stuff.

No, /lib64 is a symlink to /lib.  /lib is for the native binaries, which are 64-bit on a 64-bit system.

```
[jpkotta@gauss][~][0]
$ ls  -ld /lib*
drwxr-xr-x 15 root root 12288 2008-07-17 02:09 /lib/
drwxr-xr-x  4 root root  4096 2008-06-11 21:29 /lib32/
lrwxrwxrwx  1 root root     4 2007-10-21 01:40 /lib64 -> /lib/

```

---

### Post by Ptero-4 on 2008-07-23
Oops got the distros mixed up. In a gentoo distro I tested a while ago it was the other way around. /lib was the symlink. It was like that for some apps that expect to see the /lib directory.

---

