---
title: "install os9 after i install ubuntu"
date: 2005-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by erez1012 on 2005-11-24
hii i install ubuntu and i craete 3 partitions
1 swep 
2apple partition map
3 apple free extra

the 3 partition catch the all hdd (30 gb)

now i want to install os9, when i install the os is not let me to select apartition to install the os!!!
what can i do??
thanks

---

### Post by ssam on 2005-11-24
you may need to use apples partitioner to make the hfs+ partition.

you will probably find that when you install mac os it may mess up your yaboot, ie it will boot straight to mac os with out giving you a choice. you may need to learn some open firmware commands to get it to boot linux again, and then use the yaboot conguration tools to set up yaboot again.

the easiest thing to do may be to back everything up, and install everything again, mac os first.

---

### Post by erez1012 on 2005-11-24
i dont install os9 because  i cant choose apartition
if i boot without cd i get to ubuntu
what can i do?

---

### Post by ssam on 2005-11-24
can you post the output of the command
```
sudo fdisk -l /dev/hda
```
(you will need to put in your password) so we can see what partitions you have.

---

### Post by erez1012 on 2005-11-24
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           57482422 @ 2018     ( 27.4G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                1120680 @ 57484440 (547.2M)  Linux swap

Block size=512, Number of Blocks=58605120
DeviceType=0x0, DeviceId=0x0

---

### Post by erez1012 on 2005-11-24
when i install ubuntu i format the all hard disk, and install ubuntu.
now i want to add os9 to my i book g3

---

### Post by peanut butter on 2005-11-24
i dont have a mac so bare with me.
have you tried to boot from the install cd for os9.
you might have to reinstall linux since apple dident make its os for dualbooting.

---

### Post by erez1012 on 2005-11-24
i try to unstall os9 and  at the beginning it work until the partition part
, maybe i need to get afree partition for os?

---

### Post by ssam on 2005-11-24
you will need to repartition your disk, to make a mac (hfs+) partition.

it is just about possible to do this by resizing you existing partion to make new space. but this would be complex.

if you can make a back up of your data on the linux partition, then the easiest method is to wipe the whole disk, repartion it, install mac os, then install ubuntu.

---

### Post by erez1012 on 2005-11-25
soo i must format the hdd and install os and after that ubuntu???

---

### Post by Entity on 2005-11-25
[QUOTE=erez1012]soo i must format the hdd and install os and after that ubuntu???[/QUOTE]

Yes it's the best thing to do in your situation since you don't have the needed free space to install mac os on your hard drive (hda) :

/dev/hda1 Apple_partition_map Apple 63 @ 1 ( 31.5k) Partition map
/dev/hda2 Apple_Bootstrap untitled 1954 @ 64 (977.0k) NewWorld bootblock
/dev/hda3 Apple_UNIX_SVR2 untitled 57482422 @ 2018 ( 27.4G) Linux native
/dev/hda4 Apple_UNIX_SVR2 swap 1120680 @ 57484440 (547.2M) Linux swap

But if you had the necessary space you could of simply installed mac os on a newly created HFS+ volume without deleting your Ubuntu installation.

Then, you would of used a live CD to restore yaboot and apply the needed modifications to dual boot mac os and ubuntu by chrooting your current ubuntu installation.

---

### Post by Entity on 2005-11-27
[QUOTE=Entity]Yes it's the best thing to do in your situation since you don't have the needed free space to install mac os on your hard drive (hda) :

/dev/hda1 Apple_partition_map Apple 63 @ 1 ( 31.5k) Partition map
/dev/hda2 Apple_Bootstrap untitled 1954 @ 64 (977.0k) NewWorld bootblock
/dev/hda3 Apple_UNIX_SVR2 untitled 57482422 @ 2018 ( 27.4G) Linux native
/dev/hda4 Apple_UNIX_SVR2 swap 1120680 @ 57484440 (547.2M) Linux swap

But if you had the necessary space you could of simply installed mac os on a newly created HFS+ volume without deleting your Ubuntu installation.

Then, you would of used a live CD to restore yaboot and apply the needed modifications to dual boot mac os and ubuntu by chrooting your current ubuntu installation.[/QUOTE] Please note that the possibility to resize your partition exists. Since you need to resize your / partition, you can simply boot using you Ubuntu live CD and use gparted to resize your /dev/hda3 partition (it needs to be unmounted during the operation). I did this using a Dapper Live CD earlier today.

But then you would need to create a new HFS+ partition with the free space somehow. gparted doesn't let you do this as hfsplus doesn't create HFS+ partition and hfsutils only creates HFS volumes (2GB max?).

Using the Apple disk utility is not a good idea since it will partition your entire drive and you will loose your data on this drive anyway (and your ubuntu installation that goes with it).

In my case I simply created an unformatted partition with the free space using gparted and restored a Mac OS X image I had previously created using dd.

---

### Post by erez1012 on 2005-11-28
thanks
i delete all the hard disk and install os9 and after thet i install ubuntu
and it whes eazy:)

---

### Post by peter_m on 2005-12-04
Hi everyone, I just did a clean install of OS 9.2 and got it running just the way I wanted it and made sure I left an unpartitioned space for Ubuntu. I then started Ubuntu installation and asked Ubuntu to use the largest free space to create it's partitions. Went back in manualy and changed EXT3 to ReserFS and the install continued ok. When the time came to reboot, Yaboot only gave me 2 choice C for CD-ROM and L for Linux. There was not choice for OS9 and when Linux started, I says loading kernel and it freezes right there. I think it's still in yaboot at that point or just past it.

Does Ubuntu have issues with ReiserFS? Can Ubuntu 5.10 dual boot with OS9 and if so, how?

---

### Post by erez1012 on 2005-12-05
try to holding alt key in the start

---

### Post by erez1012 on 2005-12-05
i dont remember how i did this, but i serch in the forum and change the yaboot.conf.
im trying to serch for you now, try to serch to

---

### Post by erez1012 on 2005-12-05
[http://ubuntuforums.org/showthread.php?t=93309&highlight=yaboot.conf](http://ubuntuforums.org/showthread.php?t=93309&highlight=yaboot.conf)

---

### Post by peter_m on 2005-12-05
Thanx for the link,
Ubuntu is running and I set my default OS to MACOS. All is well tonight!

---

