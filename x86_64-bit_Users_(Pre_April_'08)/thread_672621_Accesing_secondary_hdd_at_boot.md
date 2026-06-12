---
title: "Accesing secondary hdd at boot"
date: 2008-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by dayanandasaraswati on 2008-01-19
Hi,
    I have two hdd. In the slave drive i've installed ubuntu 7.10 and in the master drive windows resides. Whenever i boot up ubuntu, i am just able to see the partitions in the master drive and am unable to use it...If i double click on the icons of the partitions, it asks me for root password and after giving that ubuntu 7.10 automatically mounts that partition. 
My question is, this kind of manual mount everytime is really tedious. I have four partitions in the master hdd and mounting each of them after reboot is irritating. I want to know if i can run some scripts at startup which would automatically mount my master hdd all at once

---

### Post by logos34 on 2008-01-20
[install ntfs-config]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971"), and run it to configure windows partitions to automount at boot in read+write mode using the pre-installed ntfs-3g driver.  It will edit fstab for you.  

hopefully that will solve the problem

---

