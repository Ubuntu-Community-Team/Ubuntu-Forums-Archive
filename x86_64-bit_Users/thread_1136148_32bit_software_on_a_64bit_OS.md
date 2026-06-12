---
title: "32bit software on a 64bit OS?"
date: 2009-04-24
forum: x86 64-bit Users
---

### Post by teixidoj on 2009-04-24
Hi,

 How do I install 32bit software on my 64bit OS?

JOhn...

---

### Post by 3Miro on 2009-04-24
What exactly is it? If you have a .deb you have to use
```

dpkg -i --force-architecture something.deb

```

If you have a source file, you will have to compile it (and you should be able to compile it for 64-bit).

If you have a compiled binary, just running it should be fine.

There might be problems, but those are case specific. Someone can help if you give more details.

---

### Post by Sef on 2009-04-25
Read [Cappy's thread]("http://ubuntuforums.org/showthread.php?t=474790").

---

### Post by teixidoj on 2009-04-26
Thank you, it worked great to install adobe 9, but I got the following error when I tried to install real player:

Unpacking realplay (from RealPlayer11GOLD.deb) ...
dpkg: dependency problems prevent configuration of realplay:
 realplay depends on lsb (>= 3.1); however:
  Package lsb is not installed.
dpkg: error processing realplay (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 realplay


John...

---

