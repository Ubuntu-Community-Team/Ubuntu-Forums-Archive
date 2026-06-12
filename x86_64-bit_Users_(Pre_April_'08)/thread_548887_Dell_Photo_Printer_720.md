---
title: "Dell Photo Printer 720"
date: 2007-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by trim17 on 2007-09-11
I have a free Dell Photo Printer 720. I've read just about every guide on how to get the driver to work, but they all are for the i386 architecture. Is there any way to use alien to build a .deb for amd64 arch?

The guide is mean is [http://ubuntuforums.org/showthread.php?t=56631&highlight=dell+720]("http://ubuntuforums.org/showthread.php?t=56631&highlight=dell+720")

---

### Post by bford16 on 2007-09-13
> **trim17 said:**
> I have a free Dell Photo Printer 720. I've read just about every guide on how to get the driver to work, but they all are for the i386 architecture. Is there any way to use alien to build a .deb for amd64 arch?

The guide is mean is [http://ubuntuforums.org/showthread.php?t=56631&highlight=dell+720]("http://ubuntuforums.org/showthread.php?t=56631&highlight=dell+720")

Have you tried installing the computer via the CUPS Web page interface ([http://localhost:631/)?](http://localhost:631/)?)  I was having trouble installing my Epson CX3810 on KDE (it was easy on Gnome), and I stumbled across the Web interface there.  The drivers that appeared invisible to the KDE printer installer were plainly available on the Web interface.

---

### Post by hazysonic on 2008-07-09
Finally got it to work for me. I'm using 64bit, and for me the issue was installing libsdc++5 in the package manager. Now it works great!

---

