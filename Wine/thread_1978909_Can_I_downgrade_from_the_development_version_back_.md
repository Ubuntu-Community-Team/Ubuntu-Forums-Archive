---
title: "Can I downgrade from the development version back to the stable version ?"
date: 2012-05-12
forum: Wine
---

### Post by Docmero on 2012-05-12
[CENTER]Hi , I'm a new ubuntu 11.10 user . 
I installed wine 1.4 , used it to install few apps 
and it's working well except for few bugs .
I want to install 1.55 which is the developmental version to fix these bugs , 
but I'm afraid off missing up my wine apps , 
Can I downgrade from the development version back to the stable version 
just in case any problem happened ?
If yes , How to do it ?
Thanks
[/CENTER]

---

### Post by sudodus on 2012-05-12
I think it is a good idea to have one 'production platform' and one 'experimental platform'. For example, you can shrink your current Ubuntu partition and make a small partition, maybe 10 GB, where you can test different and new things including new OS versions and special software.

Use dual booting, and select at the grub menu which system to boot. This way you will have peace of mind when experimenting.

But rememeber to ***backup*** at least your personal data, at best your whole system before editing the partitions!

---

### Post by Docmero on 2012-05-12
I already have dual booting but win7 and ubuntu 11.10 . I had the idea to install another ubuntu 11.10 in a virtual box inside ubuntu 11.10 , but I didn't do it because it may affect the host performance which I'm trying to avoid . I have core i5 750 and 4GB ram by the way 
.........................................
How to make a backup of the whole system in ubuntu ?
Is there an option like system restore point to backup just the system settings as in windows ?
thanks

---

### Post by sudodus on 2012-05-12
> **Docmero said:**
> I already have dual booting but win7 and ubuntu 11.10 . I had the idea to install another ubuntu 11.10 in a virtual box inside ubuntu 11.10 , but I didn't do it because it may affect the host performance which I'm trying to avoid . I have core i5 750 and 4GB ram by the way

The virtual machine won't interfere at all, when shut off. It is like any application program, only occupies disk space until it is started. And your system has horsepower enough ...
> 
.........................................
How to make a backup of the whole system in ubuntu ?
Is there an option like system restore point to backup just the system settings as in windows ?
thanks
If you want a complete backup, I suggest a boot CD or USB drive with ***Clonezilla***. It can make a clone (identical copy to another HDD), but normally you would make an image. It is easy to restore the system from the image to the old or a new HDD when necessary.

It is also possible to use ***rsync***, or some GUI application, that is probably using rsync under the hood, to make incremental backup, which in some way corresponds to the restore points in Windows.

---

