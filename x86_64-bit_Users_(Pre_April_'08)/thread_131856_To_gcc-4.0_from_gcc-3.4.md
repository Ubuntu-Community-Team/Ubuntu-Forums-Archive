---
title: "To gcc-4.0 from gcc-3.4"
date: 2006-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by alesdoc on 2006-02-17
Hi everybody, how are you,

I'd like to compile qemu on my Laptop (Turion 64bit).

How can i set the compiler? I want to compile it with gcc-3.4.

Thanks

Alessandro

---

### Post by jon_gunnar on 2006-02-17
[QUOTE=alesdoc]Hi everybody, how are you,

I'd like to compile qemu on my Laptop (Turion 64bit).

How can i set the compiler? I want to compile it with gcc-3.4.

Thanks

Alessandro[/QUOTE]

Something like this maybe.
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC

---

### Post by alesdoc on 2006-02-17
Thanks a lot,

i solved my problem editing the cofigure file, but i can not compile it.

I receive back an error during the compilation...:( 

Bye

---

### Post by queenorych on 2006-02-17
the error may be helpful.  The qemu website/forum/lists may be more helpul in compiling qemu.

---

### Post by gabi_2 on 2006-02-17
Hi I got also same pc and problem I try to compile 3.4.5 version and I got error from /libstdc++-v3/testsuite/testsuite_hooks.cc lin 293

---

