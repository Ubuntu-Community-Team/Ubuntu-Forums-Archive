---
title: "same /home partition for both 32bit and 64bit?"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by crgutierrez on 2008-11-02
I have used both systems for a long time, with different /home partitions for each one. The only reason for keeping 32 bit is my scanner (Epson perfection V350)...... Ready for a new instalation of 8.10 I want to know if I can have both OS installed, using the same separate /home partition????? How do I proceed for the second OS to be installed, so it recognizes the /home defined for the first one??

Thks in advance:guitar:

---

### Post by cariboo on 2008-11-02
It really shouldn't make any difference as the only thing in your home directory is configuration, personal files, pictures, music and video files. Nothing either 32bit or 64bit specific.

Jim

---

### Post by Yellow Pasque on 2008-11-03
Read this thread for advantages/disadvantages:
[http://ubuntuforums.org/showthread.php?t=896762](http://ubuntuforums.org/showthread.php?t=896762)

---

### Post by roelpeeters on 2008-11-03
During the installation go for manual partitioning. When you see the partition that contains your /home, click 'Edit Partition' and assign it /home but do NOT check the format check box!. Then it will be automatically mounted upon boot.

Roel

---

