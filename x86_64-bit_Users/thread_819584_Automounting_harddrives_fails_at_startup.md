---
title: "Automounting harddrives fails at startup"
date: 2008-06-05
forum: x86 64-bit Users
---

### Post by heinzbitte on 2008-06-05
I used to use 7.10 and my two ntfs partitions (one with windows and one storage) would always automount.  

I updated to 8.04 and now during startup it says something like "Auto Mount disks(maybe filesytems or something, I forget) FAILED" 

If I go to places and click on the drives it will mount them, but it doesn't automount. 

It seems to be the same thing as this thread
[http://ubuntuforums.org/showthread.php?t=818488&highlight=mount+filesystems&page=3](http://ubuntuforums.org/showthread.php?t=818488&highlight=mount+filesystems&page=3)
but I didn't want to butt in there if it wasn't .

---

### Post by Jouke74 on 2008-06-05
In Gutsy I noticed that my drives don't want to automount if there is something wrong with the NTFS file system. What I did in this case is to let chkdsk under windows run a scan on the ntfs disks and correct the errors. Afterwards, it automounted again. 

Haven't had that problem in Hardy yet though.

---

### Post by Kilz on 2008-06-06
> **heinzbitte said:**
> I used to use 7.10 and my two ntfs partitions (one with windows and one storage) would always automount.  

I updated to 8.04 and now during startup it says something like "Auto Mount disks(maybe filesytems or something, I forget) FAILED" 

If I go to places and click on the drives it will mount them, but it doesn't automount. 

It seems to be the same thing as this thread
[http://ubuntuforums.org/showthread.php?t=818488&highlight=mount+filesystems&page=3](http://ubuntuforums.org/showthread.php?t=818488&highlight=mount+filesystems&page=3)
but I didn't want to butt in there if it wasn't .

Did you edit your fstab file to have them mount? If so please post it here, maybe we can see the problem.

---

### Post by fedora on 2008-06-08
try to install package pysdm in synaptic then open system  administration and manage all your drives
thank you

---

