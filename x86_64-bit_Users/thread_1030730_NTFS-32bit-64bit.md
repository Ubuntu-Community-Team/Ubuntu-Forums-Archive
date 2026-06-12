---
title: "NTFS-32bit-64bit"
date: 2009-01-04
forum: x86 64-bit Users
---

### Post by jimmy2975 on 2009-01-04
Hi,

I run 8.04 64bit in dual boot with 32bit XP. I am planning to mount the NTFS XP partitions for read/write in the 64bit ubuntu. I am worried about the 32/64 bit. Is there a problem in opening and editing a file between 32 and 64bit systems? I cant affordfor the files to get corrupted. Is am planing to use ntfs-3g and ntfs-config for this.is this right?

Any suggestions is appreciated.
Thanks
Jimmy

---

### Post by 2hot6ft2 on 2009-01-04
Shouldn't be a problem as I have the same setup and haven't had any issues.

---

### Post by crazyness003 on 2009-01-04
i second what [2hot6ft2]("http://ubuntuforums.org/member.php?u=568708") said. Your 32bit install has nothign to do with the file system. since you havent booted into it, it doenst even exist (to your 64bit install).
You will need ntfs-3g to do this.
As for mounting or automounting, i believe there are a bunch of apps in the repos to help you out. ntfs-config is good tool to use for automounting ntfs partitions.

None of these should corrupt your ntfs data, but if somethign like that happens, you have a bunch of gnu/linux-native apps to help you. Dont sweat it.

---

### Post by jimmy2975 on 2009-01-04
Thanks to both of you for clarifying this !
Jimmy

---

### Post by crazyness003 on 2009-01-04
I forgot to add one app: Disk-Manager its sweet for managing all your disks/partitions

---

