---
title: "Gparted"
date: 2006-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bhawns on 2006-12-03
I have Ubuntu 64bit installed and want to create a data patition, how do I do that and what software do I use?

Thanks

---

### Post by ReaderRat on 2006-12-03
> **Bhawns said:**
> I have Ubuntu 64bit installed and want to create a data patition, how do I do that and what software do I use?

Thanks
gparted is fine for it. It is on your LiveCD. You cannot run gparted from the installed version, because you cannot partition a drive that is mounted.

---

### Post by Biker on 2006-12-04
> **ReaderRat said:**
> gparted is fine for it. It is on your LiveCD. You cannot run gparted from the installed version, because you cannot partition a drive that is mounted.

Sure, you can run GParted from the installed version on the harddisk so long as it's not the *partition* from ubuntu.

I have three partitions for Ubuntu /dev/sda1 (root) and /dev/sda2 (home) and /dev/sda5 (swap). I can manipulate all the other *unmounted* partitions on my 320GB harddisk.

Install Gparted with 'sudo apt-get install gparted'

---

### Post by Bhawns on 2006-12-04
I opened synaptic marked gparted for install, applied, it downloaded the package of four and gparted appeared in the system tools list. I clicked gparted it opened and looked fine to me. Saw all the partitions on the Ubuntu hard disk. hda1, hda2 and hda5. 
You mean I can`t use gparted like partition magic and just create a data partition on the Ubuntu drive? If that is the case the program is a waste.

---

### Post by Biker on 2006-12-04
Sure you can do it but you can't manipulate the 'in use' partitions like hda1, hda2 and hda5.

You can create and format new partitions on the free space. You can delete, unmounted, existing partitions but again you cannot, for example, resize the Ubuntu partitions hda1, hda2 and hda5 like Partition Magic. If you want that, boot the live CD with the include GParted program. Your Ubuntu partitions are not in use when you boot with the live CD.

---

### Post by Bhawns on 2006-12-07
Then I can create a DATA partition on the Ubuntu partition? Correct. Biker This would be great.

---

