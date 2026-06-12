---
title: "Recovery partition and re-installing windows and ubuntu"
date: 2008-06-17
forum: x86 64-bit Users
---

### Post by drjonze on 2008-06-17
Hi everyone, 

When I installed Ubuntu (5 days ago, I'm the definition of a newbie) I saw that there was a small partition on my c drive. I was afraid to touch it until I later learned it was to re-install windows. I wanted to have 3 partitions for ubuntu, I wanted my /home directory to be its own partition. Because you can only have 4 on the hard drive and I'm dual booting, I could not do this. 

I would like to get rid of that partition, re-size the partition that windows is on and re-install Ubuntu as I wanted to do it.  How can I do this and still be able to re-install windows? Also, I've heard that I should install Windows first, but will it reformat the hard drive first and erase my partions before it re-installs?

Thanks!!

---

### Post by Rocket2DMn on 2008-06-18
You CAN have more than 4 partitions by using a logical partition rather than a physical one.  If you try to add more partitions, this is usually done for you automatically.
You can use the GParted LiveCD to resize your partitions: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
Your normal LiveCD would work, too, just make sure swap doesn't get mounted.  You can acceess GParted on the Ubuntu LiveCD from System->Administration->Partition Editor.

If you reinstall windows, just make sure you install it to the correct partition on the drive.  Since this will overwrite the MBR, you will have to put GRUB back in it.  See [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) or the Super Grub Disk - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

For more info about adding a /home partition, see [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Ultimately you will have to configure /etc/fstab to know about /home.

---

### Post by philinux on 2008-06-18
Info on removing the recovery partition.
[http://www.computing.net/answers/windows-xp/removing-hp-recovery-partition/164757.html](http://www.computing.net/answers/windows-xp/removing-hp-recovery-partition/164757.html)

You'll have to check your recovery disks work and work the same way.

When you reinstall ubuntu just add /home as a partition at the partition stage, ubuntu will sort everything out.

---

