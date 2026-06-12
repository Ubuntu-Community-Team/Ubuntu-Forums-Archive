---
title: "[SOLVED] Mounting FAT32 Partitions at boot"
date: 2008-11-23
forum: x86 64-bit Users
---

### Post by BigJohnA on 2008-11-23
I am a new Ubuntu user converted from Windows XP.

I have been trying to get two windows fat32 volumes to mount at boot without success.  

I have edited /etc/fstab with the following entries:
```

/dev/sda1   /media/68.2G  vfat  isocharset=utf8,umask=000   0       0
/dev/sdb    /media/13G  vfat  isocharset=utf8,umask=000   0       0

```

Obviously, the /media/ paths point to existing locations.

I have tried various iterations of these entries, using UUID, labels, you name it. I have also tried pointing the mount points to locations in the /mnt/ directory. None of my attempts have resulted in either partitions/drives being mounted at boot. In fact, they usually will become completely invisible until I delete the lines from fstab. I am not sure what I am doing wrong, it appears this is the appropriate way to proceed.

Sorry if this is a dumb newbie question.

---

### Post by Bucky Ball on 2008-11-23
You are best using the UUID number. This is my vfat entry in fstab:

```
# /dev/**sda8**
**UUID=4893-E3A6 **                           /media/**fatso**    vfat    defaults,umask=0002,gid=46 0 0
```This should be entered as is here, on two lines. You need to change the parts I have in bold to the details of your partition. To obtain the UUID, enter in a terminal:

**sudo blkid**

You will also need to create an appropriate mount point:

[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

Good luck.

---

### Post by BigJohnA on 2008-11-24
It worked like a charm, thanks for the help. :)

---

### Post by Bucky Ball on 2008-11-24
Good news and you're welcome. Could you mark this thread as 'solved' from Thread Tools, upper right, so others might get a fix here. :)

---

