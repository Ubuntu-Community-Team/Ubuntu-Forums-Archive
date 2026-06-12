---
title: "compile gcc 32 bit on 64-bit processor"
date: 2006-09-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by biberli on 2006-09-26
Hi there,
I'm trying to compile my C++ application with gcc on an amd64 in 32 bits, but I have some troubles at the link stage: 

/usr/bin/ld: warning: i386 architecture of input file `XXX.os' is incompatible with i386:x86-64 output
,,,,

I am working on Dapper, already tried to install the packages libc6-dev-i386 and lib32bz2-dev instead of ia32-libs-dev

I have also put the -m32 option for gcc.

Does anyone have an idea? Thanks!

---

### Post by patrickfromspain on 2006-09-26
I think you must create a chroot environment..

---

### Post by RAOF on 2006-09-26
You might want to try passing -m32 to your link stage, as well.

---

### Post by biberli on 2006-09-26
Hey thanks, you were right! 
By adding the flag -m32 to the link options it works! Well... It worked a little more, until I tried to link with opengl... I have my nvidia drivers for the amd64 and the linking goes wrong. 

/usr/bin/ld: skipping incompatible
/usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libGL.so when searching for -lGL
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libGL.so when searching for -lGL
/usr/bin/ld: skipping incompatible /usr/lib/libGL.so when searching for -lGL

I have tried to install the drivers ia32, but ubuntu refuses since it recognizes my machine as an amd64... Maybe you also know how to solve this problem? It should be possible to use a 32 bit version of libGL, right?

For now, it seems that it tries to link with the libs in /usr/lib, but I have noticed that there is also a lib32/ directory containing their 32 bit version. However I don't know how to switch to this directory.

---

### Post by RAOF on 2006-09-26
You might want to try adding -L/usr/lib32 to the linker flags.  That's how you specify the directories to search.

---

### Post by biberli on 2006-09-27
Hi!
Of course you're right! However, I've just bumped into the next trouble: now it is glew (library for loading opengl extensions) that gives me some trouble: it can't link with libXmu because I don't have it in 32 bit version. I've looked everywhere on the internet for the correct package, checked synaptic, but I can't find it... Thanks for your help, it is most welcome!

---

### Post by RAOF on 2006-09-27
You may actually find it easier to create a 32bit chroot in this case.  It will be **possible** to find 32 bit binaries for all the libraries you use, but it'll rapidly get much easier and simpler to just install a 32bit system inside your 64bit one and let apt to the looking for you.

Why do you want to build a 32bit binary anyway?

---

### Post by biberli on 2006-09-28
The problem is I need to access a database containing serialized binary 32bit data. I am going to try chroot. Thanks for your help!

---

### Post by RAOF on 2006-09-28
> **biberli said:**
> The problem is I need to access a database containing serialized binary 32bit data. I am going to try chroot. Thanks for your help!

Can't you just write a converter?  Read the bytestream in raw, and extract the 32bit blocks from that?  Bitmask using & and then bitshift?

This is why just writing in-memory structures raw to files is a Bad Idea(tm) :).  It makes your code non-portable.  What happens on a system with different endian-ness?

---

