---
title: "64-bit Install Woes..."
date: 2008-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Siyfion on 2008-02-01
I currently have an Adaptec 1430SA SATA II RAID controller card, with 4 disks paired off into 2 separate RAID 0 arrays. I have installed Vista on, lets call it the "master" RAID 0 disk, and purposely left some room to install Ubuntu on there as well.

When I start the LiveCD it sees the drives as 4 separate drives, although this is NOT a "fakeRaid". I am a little bit stumped now as to how to actually install Ubuntu onto the disk, even more so, without destorying my Windows install/partition.

After doing some digging, on here: [http://www.adaptec.com/en-US/product...ry/AAR-1430SA/](http://www.adaptec.com/en-US/product...ry/AAR-1430SA/)

It looks at though my adaptec card utilizes HostRAID technology.. Isn't that supported by dmraid? 

My problem is that after doing the "sudo dmraid -r" I get this:

```
ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: ddf1, ".ddf1_disks", GROUP, ok, 624737856 sectors, data@ 0
/dev/sdb: ddf1, ".ddf1_disks", GROUP, ok, 624737856 sectors, data@ 0
/dev/sdc: ddf1, ".ddf1_disks", GROUP, ok, 489972231 sectors, data@ 0
/dev/sdd: ddf1, ".ddf1_disks", GROUP, ok, 489972231 sectors, data@ 0
```

Now thats all well and good, but it doesn't seem to have realized which drives are in which array. Although I know that the top two are in a Raid 0 and the bottom two are in another Raid 0, it doesnt. Which means I can't do the "fakeRaid" How-To steps.. :(

(Also just to note I did ask this in the installation forum, but nobody seemed to have a clue so I thought i'd come ask you lovely people. :confused:

---

### Post by Black Magix on 2008-02-01
I'm having the same problem with my RAID Array. No one has answered me either.

---

### Post by Siyfion on 2008-02-02
> **Black Magix said:**
> I'm having the same problem with my RAID Array. No one has answered me either.

Well I guess we can both wait for someone who "knows" together then. :)

---

### Post by Siyfion on 2008-02-02
Anyone have any idea at least why dmraid dectects it incorrectly?

---

### Post by Siyfion on 2008-02-03
Ok, after doing it a different way... Dmraid, then Admin->Partition Setup (or similar) it shows me each drive individiually, but ALSO shows me the two raid 0 drives. I tried to create an ext3 and a swap partition though and it failed and then crashed. :S Idea's?

---

### Post by Siyfion on 2008-02-03
The plot thickens, after trying to fdisk the drives they wouldn't work. Turns out that I think the problem was because the drive labels had a " " character in them, so I re-made the RAID 0 drives, installed dmraid, and now even the installer's manual partition shows the drives, allows me to set the partitions up, but now fails on the screen attached.

The original drive names were "Master Drive" and "Slave Drive", now they are labeled "Master" and "Slave" it at least detects them.

EDIT: Attached screenshot of how the drives were partitioned in the installer.

---

### Post by gruss on 2008-02-03
I do not have any experiance setting up raid array's in ubuntu so I may be way off, but I had a server once that the only way to activate the hardware raid was to literally disable it, load the os on disk 0 and a simple volume, install the necessary drivers then re enable the raid array and force a rebuild.  This was in w2k3 but thought it might help

---

### Post by Siyfion on 2008-02-03
Thanks, but if I disable the RAID I can't install onto it. And as creating/destroying RAID array's lose all data, I can't do that. :(

---

