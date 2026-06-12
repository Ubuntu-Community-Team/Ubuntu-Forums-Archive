---
title: "Lost GRUB"
date: 2005-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by sexesande on 2005-09-20
Hi,

I lost grub when I re-installed Windows XP.

Is there a way to install grub without re-installing the OS.

Sande.

---

### Post by DancingSun on 2005-09-20
You might want to try posting this at the "Installation help" forum.

---

### Post by mlomker on 2005-09-20
Sure, but you'll have to boot up to a liveCD--Ubuntu, Knoppix, etc.

[Look at this post.](http://www.ubuntuforums.org/showpost.php?p=332903&postcount=4) 

You'll need to change the command to match the drive/partition number that your Ubuntu is on.  If it is the first hard disk and the first partition then the command would be **root (hd0,0)**.

---

### Post by sande on 2005-09-21
[QUOTE=mlomker]Sure, but you'll have to boot up to a liveCD--Ubuntu, Knoppix, etc.

[Look at this post.](http://www.ubuntuforums.org/showpost.php?p=332903&postcount=4) 

You'll need to change the command to match the drive/partition number that your Ubuntu is on.  If it is the first hard disk and the first partition then the command would be **root (hd0,0)**.[/QUOTE]
 Thanks for the post **mlomker**

Found the following in the forum

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Sande.

---

### Post by sande on 2005-09-21
Thanks for the post **mlomker**

Found the following in the forum

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Sande.

---

### Post by Xiata on 2005-09-21
[QUOTE=mlomker]Sure, but you'll have to boot up to a liveCD--Ubuntu, Knoppix, etc.

[Look at this post.](http://www.ubuntuforums.org/showpost.php?p=332903&postcount=4) 

You'll need to change the command to match the drive/partition number that your Ubuntu is on.  If it is the first hard disk and the first partition then the command would be **root (hd0,0)**.[/QUOTE]

If I remember correctly, the Ubuntu install cd has the grub installer in the rescue portion of the disk. I can't verify this right now, but later today I will look into this.

---

