---
title: "External hard drive mount"
date: 2007-02-04
forum: openSUSE and SUSE Linux Enterprise
---

### Post by ubunick on 2007-02-04
I know this is the ubuntu forums but the command for mounting a hard drive should be the same, right? Well, opensuse 10.2 isn't showing my seagate 80gb external drive and I'm not sure if I'm suppose to mount it or something.. your thoughts?

Thaaaanks.

---

### Post by taurus on 2007-02-04
You have to log in as root and then do

```
mkdir /mnt/harddrive
mount -t vfat /dev/sda1 /mnt/harddrive
```

p.s.  And move over to the suse area.

---

### Post by chronusdark on 2007-02-04
what filesystem is your external drive

i have a Western digital 500 GB My Book Essential and it loads automatically with all linux's i have tried

assuming your drive is ext3

sudo mkdir /media/External
sudo mount -t <filesystem> /dev/<insert device name here (ie. sdb1) /media/External

when you plug in your drive it should show the device name in your dmesg
if its a USB drive its probably vfat filesystem

---

### Post by ubunick on 2007-02-04
The device is called "ST380011A 8.01" in my boot options but.. I get this error when I put that in the terminal:

```

sudo mount -t vfat /dev/ST380011A 8.01/media/External
mount: mount point 8.01/media/External does not exist

```

---

### Post by taurus on 2007-02-04
What's the output of this command from a terminal (as root)?

```
fdisk -l
```

---

### Post by ubunick on 2007-02-04
I fixed it.  Thanks anyways.

---

### Post by ub-noob on 2007-06-17
> **ubunick said:**
> I fixed it.  Thanks anyways.

Can you tell us how you fixed it?  I am unable to mount my external HDD too.

Thanks.

---

### Post by onux16 on 2007-09-16
ubunick said he typed:
*sudo mount -t vfat /dev/ST380011A 8.01/media/External*

I'm just beginning to play with the linux terminal, so I'm not well versed, but I do believe he should have a \ before any spaces in a name. In addition, he never placed a space after 8.01, making it a part if the next command.

Shouldn't it look more like this?
*sudo mount -t vfat /dev/ST380011A\ 8.01 /media/External*

---

### Post by kraymore on 2007-12-09
i have a external hard drive formatted as ext3 through gparted.  gparted in ubuntu sees it as /dev/sdb1 however the following does not work for me:

avis@desktop:~$ sudo mount -t ext3 /dev/sdb1 /media/disk
[sudo] password for avis:
mount: special device /dev/sdb1 does not exist

it is also not listed under 'df' however gparted see's it fine.  

not sure what to do to get it recognized.

---

### Post by hetLemming on 2007-12-31
> **taurus said:**
> You have to log in as root and then do

```
mkdir /mnt/harddrive
mount -t vfat /dev/sda1 /mnt/harddrive
```



I did this, but now my mount point is only writable by root.  How can I make it so regular users can write to this mount point?

"sudo chmod a+w /mnt/harddrive" doesn't work.

Any help would be greatly appreciated.

---

### Post by lespaul_rentals on 2008-01-09
> **hetLemming said:**
> I did this, but now my mount point is only writable by root.  How can I make it so regular users can write to this mount point?

"sudo chmod a+w /mnt/harddrive" doesn't work.

Any help would be greatly appreciated.

```
sudo chmod 777 /mnt/<mountpoint>
```

---

### Post by Deathmoon on 2008-11-01
you will want to do

```
sudo chmod -R 777 /media/external
```

The -R parameter gives full permissions to all files/folders within the drive.

---

