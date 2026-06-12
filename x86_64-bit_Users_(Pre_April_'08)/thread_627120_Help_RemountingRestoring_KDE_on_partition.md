---
title: "Help Remounting/Restoring KDE on partition"
date: 2007-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by wcarloss on 2007-11-29
I installed Kubuntu 7.10 x86_54 a couple of weeks ago and everything was going great, until I decided to start installing packages using Adept to try to get the toolbar icons to load in Firefox 3.0b1.  I didn't preview the changes before I applied them, and basically all of KDE was uninstalled (650MB worth).  When Ireboot, I receive a message from kinit saying that no previous sessions were found so it will perform a normal boot.  Unfortunately nothing seems to happen.

In order to get around this, I reinstalled Kubuntu 7.10 x86_64 on another partition using the live CD.  This partition loads properly.  I tried to go to the media directory in Dolphin and look at the contents of the old partition, but I received an error saying that it couldn't mount hal id 1000.  I checked fstab and it had no information on the old partition.  I found out the correct uuid for the partition and added it to fstab with the same options as the working partition.  Now, when I try to access the partition, it says "Permission denied".  Below is the contents of fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dd2c5665-edb0-4664-92eb-6ee50e8db179 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=fee9e34e-3b7f-4d35-99d9-c095811ec790 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=2c3f3218-8f37-46c7-a831-b982d3f60745 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Can someone help me get permission to the old partition, and possibly restore the old partition to booting order?

Thanks!

---

### Post by Radon on 2007-11-29
What must have happened is that you accidentally uninstalled (k)ubuntu-desktop.  I have uninstalled a few programs before that had ubuntu-desktop as a dependancy, so after deleting the software I just reinstalled the desktop package.  This is still nothing compared to the dependency hell that I used to have in OpenSuSE 10.2 :)

The next time it happens to you just log into failsafe mode to get a command line and enter: 'sudo apt-get install kubuntu-desktop' or whatever DE you need.

As for the "Permission denied" error, you can still access it while being root.

I always keep the /home directory on a seperate partition to the OS, which, while reducing risk of losing data due to hosed OS, also allows me to share the same desktop and user programs (eg. firefox) from Ubuntu 7.10 and OpenSuSE 10.3.

---

### Post by wcarloss on 2007-11-29
Thanks for the suggestion, but when I try to apt-get install kubuntu-desktop I get a bunch of unmet dependencies because it can't resolve the ubuntu server address.  It seems like my network connection won't work, and that's what's preventing me from installing kubuntu-desktop.

Also, after rebooting I can no longer see the old partition in Dolphin, so I can't get to the partition, even as root.

---

### Post by Radon on 2007-11-30
If the partition is on a different drive, you might want to check the cable connections just in case :) The partition should always be visible in /dev.  From the terminal try:  ```
cd /dev
``` ```
ls
``` There should be a long list of files on your screen by now.  If your HDD is ATA it should show up as hda or hdb otherwise if it's SATA it should start as 'sda' up to 'sd*z*'.  Please post your list of hd*x* or sd*x* drives here so I can help you mount them.

You mentioned that there are unmet dependencies for kubuntu-desktop, Do you have a Ubuntu or Xubuntu disk somewhere, or maybe your friends might have it? It can be 7.04 or 6.06.  If you have >1GB free space on your HDD you might as well install Gnome temporarily so that it's easier to fix your KDE problem from a GUI.

---

### Post by wcarloss on 2007-12-02
Alf, sorry for the delay.  I have no IDE drives, everything is SATA including my DVD burner.

sda
sda1
sda2
sda3
sda3
sda5
sda6


I only have one hard drive with 2 partitions.  I'm currently working from the second partition with Kubuntu 7.10 x64 installed.  Do I install need to install Ubuntu, or can I remount the drives from Kubuntu?

Thanks for your help

---

### Post by Radon on 2007-12-03
> **wcarloss said:**
> Alf, sorry for the delay. 
Lol, I'm not Alf.  I just came across him on the net and it brought back good memories :)
> Thanks for your help
No problems, glad to be of some help to a fellow geek, but the problem isn't solved yet.

Can you vaguelly remember which HDD from that list you installed the OS?  If you haven't set up /home on a different partition then reinstalling Ubuntu will mean a loss of everything. 

What you can do now to access your data is mount the partitions individually.  Make a temporary partition in e.g. /media
```
sudo mkdir /media/DATA
```

Now to mount:
```
sudo mount /dev/sda1 /media/DATA
```
Access this folder to see if your data is there.  If it isn't, unmount it and mount the next partition:
```
sudo umount /dev/sda1
sudo mount /dev/sda2 /media/DATA
```

Hope this helps :)

---

### Post by wcarloss on 2007-12-03
Lucky for me it was on sda1, Radon :)  

It mounted correctly and I copied my Firefox profile and other files.

---

### Post by Radon on 2007-12-04
Good to hear \\:D/

---

