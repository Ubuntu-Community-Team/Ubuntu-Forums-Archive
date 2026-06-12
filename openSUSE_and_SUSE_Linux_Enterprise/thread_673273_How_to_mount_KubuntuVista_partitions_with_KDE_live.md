---
title: "How to mount Kubuntu/Vista partitions with KDE live cd?"
date: 2008-01-20
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 67GTA on 2008-01-20
I was trying to pull a modem rpm I stored on Kubuntu and Vista over to the live cd. When Suse boots up it doesn't add my existing hard drive partitions to fstab. How can I mount them while running the live cd? I can slap the driver on a usb drive, but it is just annoying that they are not mounted automatically by the live cd. With other live cd's, you can see other partitions in Konqeuror under "Media". Why doesn't Suse do this?

---

### Post by RebounD11 on 2008-01-20
for each partition do sth like this in the terminal/konsole:

```

su
<enter_root_password>
mkdir /media/Mount_point_4_partition1
mount /dev/sdXX /media/Mount_point_4_partition1

```

where XX stand for the letter for the physical hard disk and the number of the partition, for example if you have 2 hard drives with 3 partitions each they would be named sth like this:

First drive: sda1, sda2 and sda3 
2nd drive: sdb1, sdb2 and sdb3

To find out what those partitions are you can use Gparted although I don't know if it's on the OpenSuSE LiveCD or the command line tools fdisk to list your partition table for each drive:

Sth like this:
```

su
<enter_root_password>
fdisk -l /dev/sda

```

for me it lists sth like this:
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00044a88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5602    44998033+  83  Linux
/dev/sda2            5603        6100     4000185   82  Linux swap / Solaris
/dev/sda3            6101       30401   195197782+   5  Extended
/dev/sda5            6101       13570    60002743+  83  Linux
/dev/sda6           13571       30401   135194976   83  Linux

```

You are interested to mount the partitions marked Linux and NTFS, not the Extended ones or the Swap.

Hope this helps...

PS: I wouldn't edit fstab in the LiveCD because it's not a persisent change and it will be lost on the next boot, and it requires a restart to take effect as far as I can remember.

---

### Post by 67GTA on 2008-01-21
Thanks. That worked perfectly. Am I just spoiled by Ubuntu/Mint live cd's, or should distros in 2007 do this by default?

---

### Post by RebounD11 on 2008-01-21
They should do this by default imo, SuSE liveCDs were never sth to be proud of... the fully installed system however is great.

I like Ubuntu LiveCDs too, I hate the installer though, it's to vague... like Windows, you never know exactly what it's doing behind your back :D

---

### Post by 67GTA on 2008-01-21
I've always said that if someone could make a distro with Suse's installer, Ubuntu's creature comforts, and Mandriva's control center it would be awesome. I always liked Yast, but could never stick with opensuse because of the package manager. Everything else was always pretty slick.

---

### Post by RebounD11 on 2008-01-21
I would like a distro that would use Yast as a control center (so far I think it's the most complete one), SuSE's installer and hardware support, Fedora's speed (for me Fedora booted the fastest and was by far the most responsive) and Mandriva's user-friendliness and Ubuntu's Synaptic and community.

So far Mandriva is a distro that came close to being perfect (it's missing a little in every section :D) and SuSE if Yast wouldn't be so freakin slow as a package management and the somewhat difficult way to install and configure some apps (like CompizFusion or Synaptic - of course they have the 1-click install which is great but could use improving).

---

### Post by 67GTA on 2008-01-22
I forgot about the hardware support. Opensuse is the only distro to ever identify my LCD monitor. It even had the model #. Most distros just show it as generic. Maybe they will catch up on some of this stuff for opensuse 11.

---

