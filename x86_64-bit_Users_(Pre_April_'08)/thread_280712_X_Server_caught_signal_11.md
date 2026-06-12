---
title: "X Server caught signal 11"
date: 2006-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by StandardBlueCaboose on 2006-10-19
My X server caught signal 11 as I was playing with it. I was attempting to upgrade from compiz to beryl, I bought a new monitor, and I upgraded and edgy and downgraded back to dapper.

From what I understand signal "11" means that a program tried to access memory that it doesn't have access to. 

Anybody know what I should do? If it helps, the details of what I did are in this thread.

[url="http://ubuntuforums.org/showthread.php?t=277009"]

---

### Post by John.Michael.Kane on 2006-10-20
Have you tried ```
sudo dpkg-reconfigure xserver-xorg
```


And from reading the thread you linked to. I'm incline to tell you to reinstall,and take notes of everything you do.

---

