---
title: "partimage not working with amd64"
date: 2006-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by denni on 2006-06-12
so it is not possible to clone the hard drive.  In my understanding.  Any suggestiong?

---

### Post by an.echte.trilingue on 2006-06-12
Just to check, you are not trying to clone a mounted hard drive, right?  You need to boot from another source (like a liveCD) to make a mirror.

Honestly, you don't need partimage to make a clone, it is just a nice walk-through.  You can just as easily use tar.

---

### Post by Hendrik van den Boogaard on 2006-06-12
I have had the same experience in Ubuntu 64 bit, as described in: [http://www.ubuntuforums.org/showthread.php?t=191205](http://www.ubuntuforums.org/showthread.php?t=191205)

The problem seems that partimage compiled for 64 bit actually compare if the size of a dword is 4 bytes long (4x8=32bit), which under Dapper 64 it is 8 bytes long (8x8=64bit).

Edit: Ah, actually I found solution, presented in the thread above. You just replace the binary with the statically built version from the PartiImage website.

---

### Post by denni on 2006-07-25
Thanks, it did work!!

---

