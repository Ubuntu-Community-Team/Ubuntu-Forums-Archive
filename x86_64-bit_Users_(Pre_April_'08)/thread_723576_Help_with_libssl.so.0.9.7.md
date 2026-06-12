---
title: "Help with libssl.so.0.9.7"
date: 2008-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by the_nite_owl on 2008-03-13
Hi All
I am running 7.04 bit and am trying to install Aventail Connect.
During install I get the message:
Aborting install, AvConnect has unresolved dependencies
        linux-gate.so.1 =>  (0xffffe000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ee0000)
        libssl.so.0.9.7 => not found
        libcrypto.so.0.9.7 => not found
        libm.so.6 => /lib32/libm.so.6 (0xf7eb8000)
        libc.so.6 => /lib32/libc.so.6 (0xf7d77000)
        /lib/ld-linux.so.2 (0xf7f0b000)

I have libssl0.9.8.  Have tried loading the older version without success.
Is this a 32bit vs 64bit issue?
Any suggestion on how to get around it?
I would love to be able to use Aventail directly in Linux instead of having to load a virtual Win XP instance.

---

### Post by Kilz on 2008-03-13
> **the_nite_owl said:**
> Hi All
I am running 7.04 bit and am trying to install Aventail Connect.
During install I get the message:
Aborting install, AvConnect has unresolved dependencies
        linux-gate.so.1 =>  (0xffffe000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ee0000)
        libssl.so.0.9.7 => not found
        libcrypto.so.0.9.7 => not found
        libm.so.6 => /lib32/libm.so.6 (0xf7eb8000)
        libc.so.6 => /lib32/libc.so.6 (0xf7d77000)
        /lib/ld-linux.so.2 (0xf7f0b000)

I have libssl0.9.8.  Have tried loading the older version without success.
Is this a 32bit vs 64bit issue?
Any suggestion on how to get around it?
I would love to be able to use Aventail directly in Linux instead of having to load a virtual Win XP instance.

Since it is listing the location of the libs it has found as /usr/lib32, yes it looks to be a 32bit application on 64bit problem. [Try getlibs.]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")

---

### Post by the_nite_owl on 2008-03-13
Excellent, that did it.
I now have to figure out how to setup Aventail but at least it has been installed.

Thanks.

---

