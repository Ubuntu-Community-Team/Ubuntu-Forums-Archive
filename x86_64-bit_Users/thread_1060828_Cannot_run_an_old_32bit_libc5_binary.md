---
title: "Cannot run an old 32bit libc5 binary"
date: 2009-02-05
forum: x86 64-bit Users
---

### Post by hgerstung on 2009-02-05
I just had to reinstall my machine after a hd crash :-/ and chose the 64bit version of 8.10 on this occasion.

In our company we have a pretty old revision control system (MKS Source Integrity) which basically does what we want and since we have years of development in MKSSI archives, we are reluctant to switch to another software. 

Now, the Linux version of this thing is even older than the windows version and requires libc5 ... I managed to add old libraries from a debian packet to a dedicated lib path and added that one to ld.so.conf.d .. That is how I managed to get it running on my previous 32bit Ubuntu 8.10 system.

On the new system I do not even have a chance to find out if I have all libraries in place, because despite installing ia32-libs I get an error "no such file or directory" whenever I try to run the binary:
```

root@pc:/usr/local/mkssi/lnx# ls -l mkssi 
-rwxr-xr-x 1 root root 1889328 2009-01-26 15:51 mkssi
root@pc:/usr/local/mkssi/lnx# file ./mkssi
./mkssi: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped
root@pc:/usr/local/mkssi/lnx# ./mkssi 
bash: ./mkssi: No such file or directory

```

The same happens with ldd:

```

root@pc:/usr/local/mkssi/lnx# ldd mkssi 
/usr/bin/ldd: line 117: ./mkssi: No such file or directory

```

It looks a little bit like the kernel is not supporting this binary format although it can run other 32bit programs that I throw at it. 

A colleague using a recently installed OpenSuSE 11.2 system (64bit) does not have this problem, which would require me to switch to OpenSuSE in order to get myself up and running again ... but I would like to avoid that for various reasons ;-)

Thanks in advance for hints, wild guesses and other ways of showing support B-)

Regards,
  Heiko

---

### Post by MetalFanLiam on 2009-02-05
Have you tried getlibs? Serch ubuntuforums for it, install it and rune "getlibs <libhere>" and it should automatically install it for you. It helps in running 32bit libraries on a 64bit machine.

---

### Post by hgerstung on 2009-02-05
> **MetalFanLiam said:**
> Have you tried getlibs? Serch ubuntuforums for it, install it and rune "getlibs <libhere>" and it should automatically install it for you. It helps in running 32bit libraries on a 64bit machine.

Just tried it, thank you for the hint. Unfortunately it uses ldd which fails on the binaries of MKSSI. If ldd would work, I could probably find the missing libs on one of the PCs of my colleagues and copy them into a lib path on my machine. 

This must be a fundamental problem with the binary file format and does not seem to be related to missing libraries (at this stage).

Regards.
  Heiko

---

### Post by Cappy on 2009-02-05
Have you tried installing the same libraries from the 32-bit system but replacing the directory path of /usr/lib32 and /lib32 to /usr/lib or /lib?

> getlibs -w old-releases.ubuntu.com/ubuntu/pool/universe/libc/libc/libc5_5.4.46-15_i386.deb

may also do it.

You're missing some libraries which are causing you not to be able to run the program (it may only be libc5).

```
sudo apt-get install binutils
```
and try
```
strings ./mkssi | grep so
```
(or ldd if it starts working) if you have any more problems.

---

### Post by hgerstung on 2009-02-10
Wow! The "strings" hint solved it for me. 

```

# strings ./mkssi | grep "\.so"
/lib/ld-linux.so.1
libX11.so.6
libm.so.5
libc.so.5

```

revealed that it looks for /lib/ld-linux.so.1 which did not exist on my machine. I created a link which pointed to the right file (which I put in a /usr/local/libc5/lib32 directory). 

I already added this directory to ld.so.conf but the output of the strings command shows that the binary has a hardcoded reference to the older loader (?) which pointed to /lib ...

Fantastic! Thanks a lot to everybody who helped! 

It plays now! :guitar:

Regards,
  Heiko

---

### Post by IQRules on 2009-02-10
Interesting. Should we deserve a FAQ or how to "install 32-bit old glib or missing libs for 8.10 64-bit system"?

---

