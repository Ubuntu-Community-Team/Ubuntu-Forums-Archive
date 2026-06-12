---
title: "removing studio"
date: 2008-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by bigtom2 on 2008-03-07
I have 32bit studio and 64bit ubuntu install on a 320 gig sata drive.
how do i remove the 32bit studio without messing up my 64bit install
an reclaming the hd . studio is the first on boot loader.

---

### Post by wolfen69 on 2008-03-07
download and boot into partedmagic cd. [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)
then you can delete the 32bit partition you want and resize the 64bit.

---

### Post by bigtom2 on 2008-03-07
> **wolfen69 said:**
> download and boot into partedmagic cd. [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)
then you can delete the 32bit partition you want and resize the 64bit.

thank you   bigtom2

---

### Post by cjm5229 on 2008-03-07
You can do that with gparted in a Ubuntu live CD, but it will also mess up your grub loader, you can install grub from the live CD, There are several "How to's" on the subject in the forums. Partition Magic will also take out your grub.

---

