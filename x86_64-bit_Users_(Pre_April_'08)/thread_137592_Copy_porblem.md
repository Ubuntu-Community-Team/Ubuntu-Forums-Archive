---
title: "Copy porblem"
date: 2006-02-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by eheron on 2006-02-28
I have just installed Unbuntu 64 bit on my computer, but i still need some files from my windows partition.  I mounted the ntfs drive ok and I have access to but when I try to copy anything out of it nothing happens.  Does  anyone know how to fix this problem?

---

### Post by brk3 on 2006-02-28
what method are you using to copy the files? drag and drop?

---

### Post by amd-64 on 2006-03-03
Make sure you are copying and not trying to move the files, you should have only read permissions on the NTFS partition. 

You can drag and drop between two file manager windows (Nautilus, konqueror or krusader) or copy from the command line using 

cp  <files> <path to distination>

You must have write access to the destination, for example your home folder or su access if you wish to place the files elsewhere.

---

