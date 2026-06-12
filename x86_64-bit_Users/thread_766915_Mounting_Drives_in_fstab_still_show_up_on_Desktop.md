---
title: "Mounting Drives in fstab still show up on Desktop?"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by keeler1 on 2008-04-25
I have two more partitions other than the the root and /home.  One is a fat32 partition that contains all my music and have it mounted with the type as vfat uid=1000 and everything else default.  I have the second partition which is ext3 mounted with defaults.  I added both into my /etc/fstab.  However, when I log in these two drives have icons on the Desktop.  

This behavior is undesirable and I would like to get rid of it if possible.  For external drives that I plug in but are not in my fstab I would want the icons to show up, but not for the ones I have explicitly mounted to specific locations.

Is this possible.  It worked right on 32bit Gutsy, but now works differently with 64bit Hardy.

---

