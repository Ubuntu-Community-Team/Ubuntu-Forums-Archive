---
title: "Why does CXOffice work, but no WINE?"
date: 2005-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by killerfish on 2005-09-17
Just curious if anyone knows what 'magic' the fine folks at crossover office have done so that their version of wine works just fine on Ubuntu64, but from everthing I've read.  Getting Wine from winehq.org will never happen due to compilation issues..??

---

### Post by jdong on 2005-09-17
You can't compile WINE in 64-bit mode... That simply doesn't work (Windows is a 32-bit OS)

You need to pass in the '-m32' flag to the compiler to do it. Downloading binaries will work too...

---

### Post by killerfish on 2005-09-17
I figured as much, but were to get binaries?  Do I just dpkg -i --force the .deb file?  Will this wreak havoc on my install?

---

### Post by jdong on 2005-09-17
[QUOTE=killerfish]I figured as much, but were to get binaries?  Do I just dpkg -i --force the .deb file?  Will this wreak havoc on my install?[/QUOTE]
yep. It won't break anything.

---

### Post by Terracotta on 2005-09-17
Where can one find a .deb package from the latest wine? I can't seem to find one :-(.

---

### Post by jdong on 2005-09-17
[http://wine.sourceforge.net/apt/binary/](http://wine.sourceforge.net/apt/binary/)

---

### Post by Terracotta on 2005-09-18
Tx dude, I'm gonna try it as soon as possible  :-P .

Edit:
I do: sudo dpkg -i --force wine_0.0.20050725-winehq-1_i386.deb
But it sais wine_0.0.20050725-winehq-1_i386.deb is an unknown option to force/refuse (it's in dutch here, so no use to post it all :s).
What am I doing wrong? I am working in the directory where the wine_0.0.20050725-winehq-1_i386.deb file is located??

---

