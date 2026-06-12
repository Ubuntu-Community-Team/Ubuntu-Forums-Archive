---
title: "How do I check exactly what version am I running?"
date: 2007-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by briandu on 2007-10-18
I use **uname -aso**i


and get

**2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux**

however this does not tell if I am using AMD64 bit versionor AMD32 bit version - I know it is SMP but........

I ask because I have downloaded an Ubuntu version of application and a Debian version of .deb files and dpkg -i xxx.deb results in error message re the architecture. the app version is for AMD64

Can someone help on this?

---

### Post by Dr. Nick on 2007-10-18
I think they abandoned the x86, x64 etc in the kernel names and just use generic now.

I use uname -r and it doesnt tell me my architecture either.

Perhaps the program is built for a different kernel version?

---

### Post by steveneddy on 2007-10-18
The i686 says that it is 32 bit.

Here's what it looks like with 64 bit:

```

2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux


```

64 bit will have x86_64 in uname -a

:popcorn:

---

### Post by steveneddy on 2007-10-18
Or you could use this command

```

sudo lshw -C cpu

```

:popcorn:

---

### Post by ericartman on 2007-10-21
So uname -a doesn't show the 32 bit note and it does show the 64? This is what I got from it

2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

so I assume I am running 32 bit, dang. everything is working so nice. well off to dload the 64 bit.

sudo lshw -C cpu

shows the processor being used, got it. thanks


Cart

---

