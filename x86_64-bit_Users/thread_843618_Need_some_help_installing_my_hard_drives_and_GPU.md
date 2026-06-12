---
title: "Need some help installing my hard drives and GPU"
date: 2008-06-28
forum: x86 64-bit Users
---

### Post by marduk418 on 2008-06-28
Hey guys, I installed the Ubuntu 8.04 a few days ago and I'm having some problems with my Drivers and my old Windows Hard Drives.

This is the information about my computer

Intel Core 2 Duo E4500 Processor
Motherboard ASUS P5B
XFX Nvidia GeForce 9600GT 512Mb GDDR3
2x Kingston 1GB DDR2 RAM
Maxtor 160Gb SATA2 (partitioned)
Seagate 250Gb SATA2

After I installed the Ubuntu and all the updates, i noticed that i couldn't access my Hard Drives, it tells me that the drive could not be mounted. I'm pretty lost here.

I also need some help with my nvidia drivers. I'm getting the right resolution for my screen, but i can't use anything with 3D also if i watch movies in fullscreen I seem to get some sort of "lag" while i watch them. I read other threads about the same GPU but none of them work for me. I downloaded the newest drivers from nvidia and did the "sh NVIDIA-Linux-x86_64-173.14.09-pkg2.run" line but it tells me that there is no such file or directory, even though I am on the right directory.

I also tried the System > Administration > Hardware Drivers  but there is nothing in there.

I would like to configure the drivers, so that i can use Compiz fusion on my Comp.

I appreciate your help in advance.

---

### Post by rzrgenesys187 on 2008-06-28
For the hard drives run
```
sudo fdisk -l
```
 and post it here

---

### Post by marduk418 on 2008-06-28
Thanks for your fast reply :)
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fe30fe3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10160    81610168+   7  HPFS/NTFS
/dev/sda2           10161       19457    74678152+   5  Extended
/dev/sda5           10161       19073    71593641   83  Linux
/dev/sda6           19074       19457     3084448+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2556c43c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

```

---

### Post by rzrgenesys187 on 2008-06-28
How are you trying to mount the partitions? Also if you could post the contents of the file /etc/fstab that would be helpful.

---

### Post by marduk418 on 2008-06-28
First I just tried to open the drives, as I did a long time ago with Feisty Fawn, back then i had no problems at all.

Then i just tried to right click and mount it, but nothing happened. I'm pretty new to Ubuntu, although I used it more than once. *sigh*

here is my fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=cea6368e-f8fa-48a3-97af-b2e1f5b930fe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=07507a7b-5680-46e4-98a8-50e8f6e81e55 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by bijeeshvs on 2008-06-28
was your's a clean install or an upgrade????///
a clean install is a good point to start with................
for your graphics problem install "envy"
go to "system>administration>synaptic package manager" search for envyng-gtk
and install
run envy from "applications> system tools>envyng" 
and select automatic install
hope this could help as u have made multiple unsuccessful installs!!!!!!!!!!!!!

---

### Post by marduk418 on 2008-06-28
I had a Windows OS installed on my hard drive. For some reason on my Windows I always got the blue screen of death, so I partitioned my disk and installed Ubuntu. so it's a fresh install i guess..

I'm trying the envy thing now, i selected automatic install, but it didn't recognize my card, so i did the manual install.. i think now it's working, (still needs some tweaking, but the drivers are on) Thank you so much, if anyone has some more suggestions i would love to read them.

thanks for your help

---

### Post by rzrgenesys187 on 2008-06-29
Alright for the mounting I believe that your windows partition is what you are trying to mount and that it is on the first partition (sda1).  So here's my idea first create a folder in media
```
sudo mkdir /media/sda1
```
then try to mount the windows partition with
```
sudo mount /dev/sda1 /media/sda1
```
Let me know what happens

EDIT:  Also would you like the partition to automount whenever you log in or are you fine with just running the code when you want access to the partition?

---

### Post by marduk418 on 2008-06-29
I'm getting the same error message like when I mount my drive by rightclicking it.

Here is the message that i get.

```
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g force 0 0

```

Note the part which says "$LogFile indicates unclean shutdown (0, 1)" I decided to install Ubuntu, because i couldn't get into my Windows OS

---

### Post by rzrgenesys187 on 2008-06-29
It's a pain that just because windows can't shut down right you can't access your data.  My suggestion would be to boot up your windows install disk and see if you can get it to fix the problem (its worked for me before).  If that doesn't work I'm out of ideas sadly :(

---

### Post by marduk418 on 2008-06-29
yeah.. tell me about the pain.. it really sucks..

I did a fresh windows install now, trying to get some data back. Is there a way to get into my ubuntu partition again without reinstalling ubuntu? Or would it be better if i reinstall it? (i really don't want to, but if there's no other way, i guess i have no choice)

---

### Post by bijeeshvs on 2008-06-30
dont worry about it what is happened is windows had messed ur master boot record ( assuming grub is ur boot loader ) the following thread will help you to fix it good luck

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

