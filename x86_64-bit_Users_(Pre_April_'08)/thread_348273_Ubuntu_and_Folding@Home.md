---
title: "Ubuntu and Folding@Home"
date: 2007-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hoogie on 2007-01-28
Does  Edgy with kernel 2.6.17-10 generic, installed on an AMD 64 box make it a 64 bit OS? I'm trying to run Folding@Home using the SMP client. The loader says I have an i686 OS, and refuses to install the client. They only allow 64 bit OS's with 2 or more CPU's to run this client.

---

### Post by incubus on 2007-01-28
You actually need to install a 64bit image to your computer to take advantage of its capabilities, Hoogie.  Did you use the AMD64 installation disc?

Anyway, you can check it through:
```

$ uname -a

```

My output says "x86_64", that's one way of finding it out.

incubus

---

### Post by Hoogie on 2007-01-28
```
carl@ELMER-LINUX:~$ uname -a
Linux ELMER-LINUX 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
carl@ELMER-LINUX:~$ 
```
I guess that tells it all. 
Thanks much

---

### Post by incubus on 2007-01-28
Yes, you're running the 32bit version.  The best way of remedying that is to do a fresh install, unfortunately.

What is this Folding@Home and does it really require 64bit?

incubus

---

### Post by Hoogie on 2007-01-28
Folding@Home is a distributed computing project that studies how proteins are formed. They recently added SMP to their Linux client, but are restricting it to 64-bit platforms even though the client is 32-bit.

Hoogie

---

### Post by incubus on 2007-01-28
I see.  That's pretty cool, by the way.

If you don't want to lose the current installation, one thing you could do is create another partition and install Ubuntu 64bit there.  There are Live distros out there that specialize in partitioning discs.  There's Gparted and Insert (which is the one I usually use).

But a fresh install is usually not bad, if you have installed Ubuntu before.  I can usually get everything working from scratch in just a couple of hours (I back up my important config files).

I hope you can get it working somehow.

incubus

---

