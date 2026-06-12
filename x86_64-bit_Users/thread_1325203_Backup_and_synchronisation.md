---
title: "Backup and synchronisation"
date: 2009-11-13
forum: x86 64-bit Users
---

### Post by niw_uk1964 on 2009-11-13
I use virtual machines quite a lot and I have several systems that I use them on. Therefore I want to keep them synchronised on all my machines between two locations. To achieve this I was thinking of syncing them via a portable had drive that I could carry between those locations.

How do I best achieve this?

I've looked at a few of the backup apps in the package manager (back in time, grsync) but have yet to find anything that will do this. Any recommendations?

TIA.

---

### Post by viper8 on 2009-11-13
I use a portable harddrive and let rsync to do the work:

```
rsync -av --delete /home/user/virtual_machines /media/drive/storage/ 
```

It works well in that it will only copy files that changed.

Be careful with the --delete as it will delete files in the target that don't exist in the source...so in other words, don't get source/target mixed up.

You might have to install rsync if you don't have it installed already.

HTH

---

### Post by niw_uk1964 on 2009-11-13
Thanks. I'll give it a try as I do have it installed already. If this works then I will be very happy :)

---

