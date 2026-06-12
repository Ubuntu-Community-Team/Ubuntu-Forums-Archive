---
title: "unmount probleme"
date: 2008-10-26
forum: x86 64-bit Users
---

### Post by yamoodii on 2008-10-26
[SIZE="3"]I was trying # NTFS Configuration Tool #

and after that I found this problem

# You are not privileged to unmount the volume 'HYDRA'

only root can unmount /dev/sdb5 from /media/ARIS #


I used   # sudo umount /media/HYDRA # 
 
I get    # /media/HYDRA: not found #    !!!!??

but when I write  # sudo umount /media/ARIS #  HYDRA unmounted 

How can I fix that [/SIZE]

---

### Post by robobot on 2008-10-26
You're trying to unmount a folder, not the actual device/partition. Try this:
```
sudo umount /dev/sdb5
```

---

