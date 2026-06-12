---
title: "file shares not persistent"
date: 2009-09-12
forum: x86 64-bit Users
---

### Post by bosbeemer on 2009-09-12
I installed Ubuntu 9.04 which automatically mounted Windows 7 NTFS partitions. 

When I share folders in those mounted disks, it works fine. I am able to access those folders from windows xp. The problem is that the share goes away every time I reboot.

Does anyone know if that is by design or if I'm doing something wrong.

So I tried to edit smb.conf to keep the shares persistent.
I modified smb.conf to create a new share, however the 'read only = no' doesn't work in that case. I can't change folders when sharing through smb.conf.

Anyone came across this issue please let me know.

Thanks

---

### Post by michael37 on 2009-09-13
> **bosbeemer said:**
> I installed Ubuntu 9.04 which automatically mounted Windows 7 NTFS partitions. 

When I share folders in those mounted disks, it works fine. I am able to access those folders from windows xp. The problem is that the share goes away every time I reboot.

Does anyone know if that is by design or if I'm doing something wrong.

So I tried to edit smb.conf to keep the shares persistent.
I modified smb.conf to create a new share, however the 'read only = no' doesn't work in that case. I can't change folders when sharing through smb.conf.

Anyone came across this issue please let me know.

Thanks

My educated guess: check the bootup sequence (/etc/rc5.d; dmesg).  Perhaps your samba starts before the ntfs-3g mounts the drives which would explain why it can't export them.

---

### Post by bosbeemer on 2009-09-16
Thanks Michael. While the order in the boot script was correct, the problem was that ntfs drives weren't mounted until I accessed them from Nautilus. Hence when Samba came up, it would not see them.

I manually added lines to /etc/fstab file to mount the drives on startup and that fixed the problem. I'm not sure if that was the best solution but it worked.

Thanks again.

---

### Post by michael37 on 2009-09-16
Interesting.  I guess this problem would be a relatively rare since most users export ext3, ext4 and fat32 partitions (I do the latter on external USB HDs) using kernel file system drivers.

---

