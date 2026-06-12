---
title: "Will Ubuntu 32Bit work on AMD64 PC?"
date: 2009-11-03
forum: x86 64-bit Users
---

### Post by bitec on 2009-11-03
Hi
 
Will Ubuntu 8.10 32Bit work on AMD64? I loaded it as a dual boot with Win XP on the AMD64 PC and it screen freezes once the Ubuntu desktop is loaded. Just out of curiosity will Ub 64bit work on 32 bit processor PCs?
 
Thanks in advance...

---

### Post by P.KO on 2009-11-03
Hi,

You can run 32 bit OS on 64 bit. Only the very first Intel Itanium demanded a 64 bit OS.

And no you can't have a 64 Bit OS on a 32 bit processor.

---

### Post by Kevbert on 2009-11-03
32bit will work fine (but not 64 bit OS on a 32bit PC). If you have problems with freezes this could be anything from memory problems (run memtest from the boot menu), display adapter problems (unlikely) or a corrupt file. Try updating all your files by going to Applications-Accessories-Terminal and entering
```
sudo apt-get update
sudo apt-get upgrade
```
Also enter
```
sudo apt-get install -f
```
to find and repair any corrupted files. 
Please post back any error messages.

---

