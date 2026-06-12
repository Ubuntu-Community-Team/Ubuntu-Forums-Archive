---
title: "Java utilizing 200 MB+ memory!"
date: 2007-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by d00by on 2007-11-16
Is this normal?

My system comes to a crawl when I run Azureus 3 and firefox simultaneously.

I need to shutdown Zaureus to remove the java memory usage.

```
java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)


```

```
user@hogwarts:~$ ls /usr/lib/jvm 
java-1.5.0-gcj-4.2-1.5.0.0  java-gcj

```

---

### Post by jamesford on 2007-11-16
if i were u id get deluge and use that instead of azureus. has pretty much all the same features but doesent use java [http://deluge-torrent.org/News:Portal](http://deluge-torrent.org/News:Portal)

---

### Post by d00by on 2007-11-16
deluge su@ks! :(

I had a very hard time using safepeer plugin on it. I am not dowloading stuff without anti-p2p protection.

---

### Post by jpkotta on 2007-11-16
Java uses a lot of memory.  IIRC, there is an option you can give to Azureus (and Java apps in general) that limits the amount of memory they can allocate.  I saw it somewhere in the Azureus wiki.

> Q: How many Java programmers does it take to screw in a light bulb?
A: Just one, but he needs to install a LightBulb virtual machine, and it takes up the whole basement.

---

