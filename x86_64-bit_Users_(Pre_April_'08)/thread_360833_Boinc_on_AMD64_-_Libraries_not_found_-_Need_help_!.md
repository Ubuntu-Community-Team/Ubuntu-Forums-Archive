---
title: "Boinc on AMD64 - Libraries not found - Need help !"
date: 2007-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by resist- on 2007-02-13
I'm trying to get boinc working here.... 64bits version of boinc in synaptic does not work since my project does not support 64bit...

I resigned to get the 32bits version working, 5.4.11 did not owrk because libexpat.so not found. I found on the net that using 5.8.11 should solve the problem. But now is still can't run the boinc manager....

*./boincmgr: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory*

now locate libgtk-x11-2.0.so gives:

[I]/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.1000.6
[/I]

creating a link in /lib and /lib32 did not work...


now ldd boincmgr:

 [I]linux-gate.so.1 =>  (0xffffe000)
        libgtk-x11-2.0.so.0 => not found
        libgdk-x11-2.0.so.0 => not found
        libatk-1.0.so.0 => not found
        libgdk_pixbuf-2.0.so.0 => not found
        libpango-1.0.so.0 => not found
        libgobject-2.0.so.0 => not found
        libgmodule-2.0.so.0 => not found
        libgthread-2.0.so.0 => not found
        libglib-2.0.so.0 => not found
        libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf7fd0000)
        libXxf86vm.so.1 => not found
        libdl.so.2 => /lib32/tls/libdl.so.2 (0xf7fcc000)
        libm.so.6 => /lib32/tls/libm.so.6 (0xf7faa000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7f9f000)
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0xf7f8e000)
        libc.so.6 => /lib32/tls/libc.so.6 (0xf7e60000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7da0000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7d92000)
        /lib/ld-linux.so.2 (0xf7fe6000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7d8f000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7d8b000)
[/I]

Lot's of missing libs there...  Looks like i'll have to play with ld.so , but i'm kinda goin nowhere...

Any help for this ?    Or any other way to get boinc working on my amd64 ubuntu ?

TIA

---

### Post by resist- on 2007-02-13
Solution found !

Just need to install ia32-libs and all it's dependencies from feisty packages, and i got the ubuntu package of boinc working :)

---

