---
title: "problem reading ntfs partiton"
date: 2007-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by tikal26 on 2007-05-15
Hello, 

before I upgraded I was able to read and write to ntfs partition, but since I upgraded I can't. I checked that ntfs-3g was installed and manually checked and everything seems fine.

---

### Post by Ken_Lewis81 on 2007-05-17
Does your filesystems table at '/etc/fstab' list the NTFS partitions as mounted read-write ('rw') or read-only ('ro')?

Take care.
Ken.

---

### Post by mlind on 2007-05-17
Here's a line from my /etc/fstab for ntfs partition using ntfs-3g driver
```

UUID=B05401AE540177FC   /media/D        ntfs-3g locale=fi_FI.utf8,umask=0007,gid=46     0       1

```

You probably want to use different locale. gid=46 means that members of **plugdev** group have read/write/execute permissions to ntfs-3g mounted drives. If you want to use UUID for your drive, then use vol_id to find it out.

---

### Post by tikal26 on 2007-05-21
It was weird, I had to restart into windows and properly  shut it down and the problem was fixed.

---

### Post by diddler on 2007-05-21
Didn't understand ANY of that.  God, I hate learning new languages.

---

### Post by shad0w_walker on 2007-05-22
I have found this problem before, its basically because the NTFS partition didnt cleanly unmount and the driver refuses to allow write access (Help prevent damage to files) until a check is run. 

I think there is a linux tool to check and repair any damage to the file system but i cannot remember its name right now.

---

