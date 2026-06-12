---
title: "Need libcpc++-libc6.1-2.so.3 for x64 Gutsy"
date: 2008-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by scamper_22 on 2008-01-10
Hi,

I need to install libcpc++-libc6.1-2.so.3 on my x64 gutsy install.
Anyone know where i can find it.  I've found it on various places, but it just refuses to link.
Can anyone help with step by step instruction on how to get this linked properly?

Background:
I'm trying to get a ssh extender to work on my x64 gutsy install.  
I can't seem to get this one library to work.

~/system$ sudo ldd /usr/bin/snx
        linux-gate.so.1 =>  (0xffffe000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7e72000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7e5a000)
        libresolv.so.2 => /lib32/libresolv.so.2 (0xf7e46000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7e42000)
        libpam.so.0 => /lib32/libpam.so.0 (0xf7e38000)
        libnsl.so.1 => /lib32/libnsl.so.1 (0xf7e20000)
        libcpc++-libc6.1-2.so.3 => not found
        libc.so.6 => /lib32/libc.so.6 (0xf7cd6000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7cd2000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7ccd000)
        /lib/ld-linux.so.2 (0xf7f7b000)
Thanks,

Y

---

### Post by scamper_22 on 2008-01-10
Never mind, i found it...well kindof

I found this old rpm: [ftp://ftp.uni-duesseldorf.de/pub/unix/linux/distributions/suse/suse91/suse/i586/compat-2004.4.2-3.i586.rpm](ftp://ftp.uni-duesseldorf.de/pub/unix/linux/distributions/suse/suse91/suse/i586/compat-2004.4.2-3.i586.rpm)

opened it in archive manager.
There is a file called:libstdc++-libc6.2-2.so.3

I copied this /usr/lib32 and /usr/lib32/libcpc++-libc6.1-2.so.3 (wasteful, but safer)

works fine now...looks like I have connectivity :)  vpn looks like it works.

---

