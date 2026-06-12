---
title: "Unable to empty Trash."
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by EnixFalco on 2008-07-14
Hi, I'm fairly new to the ubuntu scene, and I'm having an issue with my trash.
There's a file that won't delete in there, Keeps giving me this error message.
```
Error removing file: Permission denied
```
Can anyone here help me please?
I'm running Ubuntu 8.04.

---

### Post by grim4593 on 2008-07-14
This thread contains info about that problem:
[http://ubuntuforums.org/showthread.php?t=850710](http://ubuntuforums.org/showthread.php?t=850710)

---

### Post by EnixFalco on 2008-07-14
Thanks for the reply, Luckly the command on the second page from the link you posted,
```
sudo rm -rf /home/yourusername/.local/share/Trash/files/*
```
Removed the items that I couldn't delete from the trash.
Thank you so much.

---

