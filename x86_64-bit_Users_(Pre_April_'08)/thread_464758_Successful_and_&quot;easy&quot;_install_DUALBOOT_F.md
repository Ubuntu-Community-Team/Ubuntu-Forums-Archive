---
title: "Successful and &quot;easy&quot; install DUALBOOT FeistyFawn/XP with nvdia raid0 stripeset"
date: 2007-06-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by s1mmel on 2007-06-05
Hi everybody,

as my post is getting more and more hits (not far from 10.000 now 29 October 2007 @ 19:52 pm), I thought it might be a good idea to update this information. I've updated to a new system and moved on to Gutsy Gibbon and it worked as well.
[COLOR="DarkOrange"]
THIS VERSION WORKS FOR  FEISTY AND GUTSY![/COLOR]

In this version I'm trying to be more detailed and easier in my descriptions, I will even add some pictures, so you better understand what to do.


**[COLOR="DarkGreen"]Step 0 - Preparation[/COLOR]**

Before you start, there are a few things to consider and a few things that should be done previously.

First of all, if you already have XP installed, make sure to backup your data. If this is done carelessly you might end up with a broken RAID which can't be fixed. Also you have to make sure that the bootloader for Linux is in the 1024 Cylinder range (just to make sure it works). So if you have a bunch of Partitions, you may want to delete or resize. 

[COLOR="Red"]I'd recommend a /boot partition, it's safer anyway, if you don't do it you'll have to set a boot flag (see the comments from other users in this thread).[/COLOR]

Before you partition your Ubuntu you should take some time to think about the layout. My suggestion would be, create an extended partition, which includes the partitions you need. E.g. I have 2*400 GB Seagates, and did a XP Install with 30 GB on a primary partition, then I did another primary partition for the /boot dir with about 150 MB, after that an extended partition with the size of about 50 GB. In there I placed partitions the so called logical drives for / /root /var /usr /home swap / tmp. That leaves one big partition (there can be 4 on each HDD, the RAID is seen as one big HDD), this one I'll use for my data.

So make sure you know what you're planning to do.

BTW, this "small" post doesn't cover the installation of the raid0 itself and does not cover the installation of the M$ XP onto the raid0 (it's not a M$ board here ^^).

**[COLOR="DarkGreen"]Step 1 - Activate the RAID[/COLOR]**

Start up the Gutsy Gibbon or Feisty Fawn Live CD, open Synaptic and add the universe and multiverse repositories.

Load the packages ```
dmraid
``` and ```
debootstrap
```

Open up a terminal and type in```
 sudo -s 
```then ```
dmraid -ay
``` to activate the RAID0, after that type in ```
dmraid -r
``` and you'll see the active RAID0 


```
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# dmraid -ay
RAID set "jmicron_RAIDsimmelstripe" already active
RAID set "jmicron_RAIDsimmelstripe1" already active
root@ubuntu:~# dmraid -r
/dev/sda: jmicron, "jmicron_RAIDsimmelstripe", stripe, ok, 781385728 sectors, data@ 0
/dev/sdb: jmicron, "jmicron_RAIDsimmelstripe", stripe, ok, 781385728 sectors, data@ 0
```

I had a little problem with my RAID-Controller-BIOS though, it lets me choose a name but filled up the rest with whitespace, so I had something like this &#8222;jmicron_GRAIDO                               &#8220; and I couldn't access it under Ubuntu, but after I rebuild and changed the name to &#8222;jmicron_RAIDsimmelstripe&#8220;, filling up the complete whitespace I was able to access it.


**[COLOR="DarkGreen"]Step 2 - Partitioning your RAID[/COLOR]**

Now Start up gparted with the RAID name behind it, like so


```
root@ubuntu:~# gparted /dev/mapper/jmicron_RAIDsimmelstripe
```

It is important to use no filesystem, just do the partitioning with gparted, anything else won't work. [COLOR="Red"]A lot of people are making their first mistake here. You won't need fdisk or else. Just make sure you dont use e.g. ext2 etc. here. The INSTALLER will do this part for you later on.
[/COLOR]
[http://q3.grasschnixe.de/pix/simmel/ubuntu/partitioning.png](http://q3.grasschnixe.de/pix/simmel/ubuntu/partitioning.png)

Once you are ready doing your partioning it should look something like this.

OOOOOOPs, there is an error here!I deleted the wrong picture here! [COLOR="Red"]Don't use the SWAP FS![/COLOR] Just use not formatted like the other's ones, sorry for the mistake! Maybe someone could take a picture and post it here?

[http://q3.grasschnixe.de/pix/simmel/ubuntu/partitioning1.png](http://q3.grasschnixe.de/pix/simmel/ubuntu/partitioning1.png)

 As you can see, the first partition is my XP (ntfs), then I created another primary partition with a 125 MB partition, which I'll use for /boot and I created an extended one, in this there are several logical drives.

~01 GB will be used as / ~05 GB will be used as /var ~05 GB will be used as /usr ~05 GB will be used as /root ~02 GB will be used as /tmp ~13 GB will be used as /home ~08 GB will be used as swap

The partioning should work without any problems, you can simply recheck, just open the gparted again with your RAID-name attached.

I did, to make sure it still works and well it's looking good

[http://q3.grasschnixe.de/pix/simmel/ubuntu/partitioning2.png](http://q3.grasschnixe.de/pix/simmel/ubuntu/partitioning2.png)

For the last partition I'll choose NTFS, I'll format it later in XP though. BTW the best way to mount it is the package ntfs-3g, make sure to keep it in mind and install it when you first boot up your fresh Gutsy-Installation.

**[COLOR="DarkGreen"]Step 3 - Install the system[/COLOR]**


Now it's time to start up the installer. Just choose your options and make sure you choose manually when it comes to hard drive partioning. 

[http://q3.grasschnixe.de/pix/simmel/ubuntu/installer.png](http://q3.grasschnixe.de/pix/simmel/ubuntu/installer.png)

The partitions show up twice. Make sure to use the &#8222;second set&#8220;, the partitions with the numbers behind them, the &#8222;first set&#8220; without the numbers should be left alone completly. Don't use the partition number 1 in both cases, this is your NTFS partition, simplay don't touch it. Make sure to mark the second set for formatting and make sure that the above ones aren't used at all.

[http://q3.grasschnixe.de/pix/simmel/ubuntu/installer2.png](http://q3.grasschnixe.de/pix/simmel/ubuntu/installer2.png)

Your partions should look something like the picture above.

Fill out the rest of the questions your asked and the Live-CD will start installing your system. After the install, the system will tell you that grub couldn't find the boot partition. That's normal because the dmraid package won't be isntalled with the Live-CD (I hope the ppl. from Ubuntu will fix that soon (and I also hope they find a way to put the rest above from here in the installer one day)).

**[COLOR="DarkGreen"]Step 4 - Fix the missing GRUB[/COLOR]**

Okay, now comes the hard part. We are going to work with the console for a while. Better yet, we work with two consoles. We start off with one, and when it's time we'll start a second one.

Make sure to concentrate and follow the instructions.

First of all kill the acpid. 

```
killall acpid
```

then cat your mtab

```
ubuntu@ubuntu:/target$ cat /etc/mtab
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
/dev/mapper/jmicron_RAIDsimmelstripe5 /target ext3 rw 0 0
/dev/mapper/jmicron_RAIDsimmelstripe2 /target/boot ext3 rw 0 0
/dev/mapper/jmicron_RAIDsimmelstripe10 /target/home ext3 rw 0 0
/dev/mapper/jmicron_RAIDsimmelstripe6 /target/root ext3 rw 0 0
/dev/mapper/jmicron_RAIDsimmelstripe9 /target/tmp ext3 rw 0 0
/dev/mapper/jmicron_RAIDsimmelstripe8 /target/usr ext3 rw 0 0
/dev/mapper/jmicron_RAIDsimmelstripe7 /target/var ext3 rw 0 0
/cdrom /target/media/cdrom0 none rw,bind 0 0
```

As you can see, my partitions are all mounted by the installer into a target directory, if yours aren't, which I doubt, you'll have to do that manually.

Okay additionally we'll have to mount 2 other &#8222;partitions&#8220;. 

```
mount --bind /dev /target/dev
mount -t sysfs sysfs /target/sys
```

Now we chroot into our new system

```
chroot /target
```

and then we will install the dmraid package.

```
aptitude install dmraid
```

Next we need to copy the stages to the grub folder

```
cp /usr/lib/grub/i386-pc/* /boot/grub/
```

Now we enter the grub shell

```
grub
```

and setup the grub boot device (the raid0)

```
device (hd0) /dev/mapper/jmicron_RAIDsimmelstripe
```

This does not refer to the boot or / partition but to the raid itself

after that we tell the system the boot partition

```
root (hd0,1)
```

I created a boot partition and its number was /dev/mapper/jmicron_RAIDsimmelstripe2, but grub begins it's count with 0, so i had to do 2 minus 1 equals 1, therefore (hd0,1) and not (hd0,2)

If you don't have an extra boot partition, you'll have to use the number of your / partition (don't forget minus 1) 

```
setup (hd0)
quit
```

The bootloader grub has now been installed.

now run

```
update-grub
```

if you are asked if the menu.lst file under /boot/grub should be created you say y(es). Now we have to modify it to our needs.

**[COLOR="DarkGreen"]Step 5 - Work on the /boot/grub/menu.lst[/COLOR]**

```
nano /boot/grub/menu.lst
```

As this is also pretty error prone, I'll walk you through it step by step.

This is the number which will be booted by default, the first entry in your list

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0
```

Change the timeout to a higher value, it's more comfortable

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         30

```

comment in hiddenmenu, to see your grub menu

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

uncomment this line to get some pretty colors in your menu

```
# Pretty colours
color cyan/blue white/blue

```

go into your other terminal and run

```
sudo grub-md5-crypt
```

and then copy/paste it like so (Example)

There is no # in front of this line, make sure to comment it out.

This will protect the single user mode with the password of your choice 

```
## password ['--md5'] passwd
password --md5 $1$zlhoC$7XeY.dNAjSVVJzuGL5Dh8.

```

Thsi would be the Gates OS, otherwise know as Windows. If you'd like to start it first, let it stay here. If you don't then copy it to the end of the choices down below in the file.

```
#
# examples
#
title           7 Gates of Jambala
root            (hd0,0)
makeactive
chainloader     +1


```

Should already be here, but make sure to check that this is the partition with your / Filesystem. Don't uncomment the line, it's perfect the way it is.

```
# kopt=root=UUID=xxxxx-xxxx-xxx-xxxx-xxxxxxxx ro
# kopt_2_6=root=/dev/mapper/jmicron_RAIDsimmelstripe5 ro

```


This line needs to be modified in most cases. If you have a boot partition the boot partition needs to put in here, Otherwise it would be the / partition (remember to count minus 1, see above)

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

```

Locks the single user mode

```
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

```

Make sure it's set to false and make sure there isn't any savefault entry in all of the boot choices, or your system won't boot up. This is fairly important for feisty users, in gutsy it's already changed.

```
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

```


Okay, this is also very important. If you use a boot partition make sure to use this example. If you don't take a look at the second one.
Make sure to remove /boot in fromt of the kernel and the initrd


```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/jmicron_RAIDsimmelstripe5 ro quiet splash
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/jmicron_RAIDsimmelstripe5 ro single
initrd          /initrd.img-2.6.22-14-generic

```

This is the way to make your entries if you don't habe another boot partition. See the /boot

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/mapper/jmicron_RAIDsimmelstripe5 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/mapper/jmicron_RAIDsimmelstripe5 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

```

In both cases make sure that (hdX,X) matches your /boot or / partition.


Save and quit nano. A final check of your /etc/fstab couldn't hurt.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/jmicron_RAIDsimmelstripe5
UUID=xxxxx-xxx-xxxx-xxxx-xxxxxxxxxxxxx /               ext3    defaults,errors=remount-ro 0       1
# /dev/mapper/jmicron_RAIDsimmelstripe2
UUID=xxxxx-xxx-xxxx-xxxx-xxxxxxxxxxxxx /boot           ext3    defaults        0       2
# /dev/mapper/jmicron_RAIDsimmelstripe10
UUID=xxxxx-xxx-xxxx-xxxx-xxxxxxxxxxxxx /home           ext3    defaults        0       2
/dev/mapper/jmicron_RAIDsimmelstripe /media/mapper_jmicron_RAIDsimmelstripe ntfs    defaults,umask=007,gid=46 0       1
# /dev/mapper/jmicron_RAIDsimmelstripe6
UUID=xxxxx-xxx-xxxx-xxxx-xxxxxxxxxxxxx /root           ext3    defaults        0       2
# /dev/mapper/jmicron_RAIDsimmelstripe9
UUID=xxxxx-xxx-xxxx-xxxx-xxxxxxxxxxxxx /tmp            ext3    defaults        0       2
# /dev/mapper/jmicron_RAIDsimmelstripe8
UUID=xxxxx-xxx-xxxx-xxxx-xxxxxxxxxxxxx /usr            ext3    defaults        0       2
# /dev/mapper/jmicron_RAIDsimmelstripe7
UUID=xxxxx-xxx-xxxx-xxxx-xxxxxxxxxxxxx /var            ext3    defaults        0       2
# /dev/mapper/jmicron_RAIDsimmelstripe11
UUID=xxxxx-xxx-xxxx-xxxx-xxxxxxxxxxxxx none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

You won't have to change a thing,

If there is a /target in there, make sure to remove it.

As some users here had problems with the boot flags, make sure to check it out


```
cfdisk /dev/mapper/<your fakeraid>
```

If the BOOT Flag is on the Windows Partition, leave it that way. If not, simply go to the partition and press BOOT, then you go to your windows partition and press BOOT again. You should see now that the BOOT flag is set properly to your chosen partition.

Don't forget to save.

Everything okay?

then simply

```
reboot
```

and try it out. :popcorn:

Have fun, Simmel 

I used [this tutorial ]("https://help.ubuntu.com/community/FakeRaidHowto")to do it, there are way more infos in there but also stuff you won't need. Combine them if you don't have a clue what I'm talking about.

---

### Post by igloocentral on 2007-06-05
sounds like my post...
[http://ubuntuforums.org/showpost.php?p=2782560&postcount=6](http://ubuntuforums.org/showpost.php?p=2782560&postcount=6)

---

### Post by s1mmel on 2007-06-06
Whish I had found that one sooner ^^
Well it's almost the same you're right. Looks like you don't have to rewrite yours then. Maybe we should link them up?

:D

---

### Post by Manganic on 2007-07-15
Wow.

Well, I finally got it.  I have a few more kinks to work out, (such as it having what looks like a buffer overrun on my CD-ROM drives and such) but I got it.  Thank you thank you thank you.

This install is on a system with Windows VIsta preinstalled.  I allocated my Ubuntu space, and divided it up into a boot, swap, and root partitions (all primary).  I started by following the FAKERAID:HOWTO page, and got problems almost immediately.

Eventually, I got annoyed and deleted the paritions, which, in the process, messed up the GRUB, so  it gave me a huge fright that Vista had gone kaplooey.  After working through the steps above, I managed to get the GRUB recovered and Vista with it.  

With that said, however, I noticed a few items in the above instructions that confused me a bit:

Here's the part, with my comments:

> Step 5:
> 
> Create a directory like /target and mount your / into it
> 
> sudo mkdir /target  
> sudo mount -t <filesystem ext3, reiserfs, etc.> /dev/mapper/nvidia_<blabla><number of 
> your / partition> /target

/target is already there.  It gets created during the install process.  Additionally, the partitions are already mounted to the appropriate subdirectories within /target.

> Repeat this step with every mount point you have created.
>
> sudo mount -t <filesystem ext3, reiserfs, etc.> /dev/mapper/nvidia_<blabla><number of 
> your part.> /target/<dirname>

Again, this is already done for you.

> Okay additionally we'll have to mount 3 other partitions
>
> mount --bind /dev /target/dev

This is a required step, as the install routine does NOT do it for you.

> mount -t proc proc /target/proc

Oddly enough, this one IS done for you.

> mount -t sysfs sysfs /target/sys

This is a required step.

Also, a minor update to your GRUB configuration section, ALL instances of ROOT (hd0,0) need to be changed to match the n-1, where n is the number of the BOOT partition.  (If it is /dev/mapper/xxx2, then use "hd0,1") 

This, of course, is what happened to me.  Others may experience different things altogether.

---

### Post by McSwordfish on 2007-07-29
Hi there.

I'm bumping this thread as I'm trying to follow through your instructions but the process keeps jamming at a certain point and I can't seem to get past it.

I get as far as starting **Step 2**, using GParted to create my partition table, I set up my disk as I want it: 100ish Gigs for XP (the size I set the NTFS partition when I installed XP), 90ish gigs for my ext3 and 2G for Swap. However, when I hit apply, GParted hits a snag and can't progress. It aborts at the "Create new ext3 file system" bit. It doesn't like the line "**mkfs.ext3 /dev/mapper/nvidia_dcbbhdcj**" because 
> /dev/mapper/nvidia_dcbbhdcj is apparently in use by the system; will not make a filesystem here!

Anyone got any ideas as to what's going on. The only thing I can think that's causing a problem is I somehow managed to create a swap partition on one of the two disks in the array. Could the liveCD be making use of that partition somehow and this is what's causing the trouble? I appear to have removed that partition and I've rebooted the computer a couple of times now.

Thanks in advance.

---

### Post by jlintz on 2007-07-29
> **McSwordfish said:**
> Hi there.

I'm bumping this thread as I'm trying to follow through your instructions but the process keeps jamming at a certain point and I can't seem to get past it.

I get as far as starting **Step 2**, using GParted to create my partition table, I set up my disk as I want it: 100ish Gigs for XP (the size I set the NTFS partition when I installed XP), 90ish gigs for my ext3 and 2G for Swap. However, when I hit apply, GParted hits a snag and can't progress. It aborts at the "Create new ext3 file system" bit. It doesn't like the line "**mkfs.ext3 /dev/mapper/nvidia_dcbbhdcj**" because 



/dev/mapper/nvidia_dcbbhdcj refers to the RAID, you need to specify which partition you want to make the filesystem on.  BTW gparted does cooperate well with fakeraid.  You should be doing something like mkfs.ext3 /dev/mapper/nvidia_dcbbhdcj1 or 2 or 3, etc.

---

### Post by McSwordfish on 2007-07-29
I'm not typing any of these commands in. I just hit "Apply" in GParted and copied the error messages here when it failed. Is there a step I'm missing out in GParted that could be crucial to the operation? 
At present, I'm selecting the unallocated space, hitting "New" and creating first my ext3 and then my swap partitions before hitting "Apply" where GParted displays the above message.

---

### Post by jlintz on 2007-07-31
try using fdisk or parted for the partitioning

---

### Post by McSwordfish on 2007-08-01
I've just tried rebuilding my RAID from scratch - I buggered my windows installation a bit and decided to start everything afresh. I install windows and then run steps one and two as above and I'm still getting the same problems. I've also tried using parted and fdisk, but neither of them seem to work.

Gparted allows me to create an empty extended partition on the empty half of my disk, but it won't let me create and ext3 partition on that same space, either within or without the extended partition there.

Parted did nothing and fdisk aborts claiming "error 22: invalid argument" - which I can't fully understand as I'm going through fdisks guided mode where it asks me what to do every step of the way.

As always, any and all help you can offer would be greatly appreciated.

---

### Post by RamonS2007 on 2007-08-04
I tried to do this on an Asus M2N32-SLI board with the 590 NVidia SATA RAID. I have it set as RAID1. It all works out OK until I get to the point to chroot into the /target system. The shell tells me that it cannot execute /bin/bash.
I went over this now for the fourth time and substituted non-applicable steps with the steps from the Ubuntu India FakeRAID doc. Still, won't work as advertised.

I really am at a loss and wish that there would be any purpose in complaining, but with Ubuntu being all the hype these days it ought to handle hardware easily that not only is out for two years, but also has drivers available (albeit not open source).
I could just install Ubuntu on an IDE drive and not use the SATA RAID, but that means going back to the early 90s when it was advisable to boot Linux from floppy since GRUB will not write correctly to the SATA RAID I want to use for booting (dual-boot with XP).And of course, Asus officially only supports SuSE and RedHat, but no Debian based Linux. And running it as 32bit version in VMWare on Windope isn't really that appealing.
OK, I stop whining and just have to hope that the makers of Ubuntu get their act together and put working FakeRAID support in from the start. Maybe next time.....

Trying Fedora now, which supposedly can handle the FakeRAID. :(:confused::mad:](*,):cry:[-o<:roll:

---

### Post by bsmith1051 on 2007-08-05
why not just use the 'standard' Linux software RAID?  It should work as well as -- if not better than -- the fakeraid.  Here's how I did it,
[http://ubuntuforums.org/showthread.php?p=2899075](http://ubuntuforums.org/showthread.php?p=2899075)

---

### Post by popat007 on 2007-08-18
Thanks s1mmel, i have successfully installed Ubuntu 7.04 64bit on my raid0 volume with Bootit NG as bootmanager  with Windows Xp pro , Media centre , Vista , Ms Dos installed on my ATA intel raid0 on 2x100 HDD Serial ATA_FUJITSU 82801GHM (ICH7-M DH) Serial ATA Storage Controller RAID :guitar:

My Config.

Sony VGN-AR 290G Laptop
CPU       : Intel(R) Core(TM)2 CPU T7200  @ 2.00GHz
Display : 17" Display - Nvidia 7800 GT -- (gave me perfect 1900x1200 resolution @ 60Hz)
Ram      : 2 GB Ram
Sound   : Sigmatel High Definition Audio
Net        : PRO/100 VE Network Connection/PRO/Wireless 3945ABG Network Connection
Optical  : DVD/CD/BlueRay-model_BD_MLT_UJ_210S -- (BlueRay not tested yet.)
Sticks    : 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) -- (does not show in file     
                  browser, needs config)

All seems working , but if some issues will post it

Thanks Again :lolflag:

---

### Post by username132 on 2007-08-19
When will it be able to just install from the DVD? I use SUSE and it recognised my fakeRAID and installed without any trouble - can't canonical copy? (Contrary to my sig., my computer doesn't have Kubuntu installed).

---

### Post by eigenaar on 2007-08-20
Thanks s1mel for your guide!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! :guitar:

I'm running Vista AND Ubuntu FF now in RAID0! It was a bit of a hassle though. First time linux started complaining about 'apt-get' not being installed and ended up in the terminal without booting completely. I read about typing "fsck" BUT THIS SCREWED GRUB!!! so dont do this command (with raid).

Then i tried second time the same guide and now it went perfectly!

I have only on question remaining:
my windows vista partition doesnt show up on the ubuntu dekstop so i dont have acces to those files... how can i make the default vista partition appear on my desktop so i can acces (and modify) the files?

---

### Post by pjman on 2007-08-20
Thanks for this guide, it looks promising.

I'm having trouble configuring grub...

Here are commands and outputs after chrooting to /target:


Ubuntu is installed on "nvidia_aieebdef3"
```
root@ubuntu:/# dmraid -ay
RAID set "nvidia_aieebdef" already active
RAID set "nvidia_aieebdef1" already active
RAID set "nvidia_aieebdef2" already active
RAID set "nvidia_aieebdef3" already active
RAID set "nvidia_aieebdef4" already active
```


```
grub> device (hd0) /dev/mapper/nvidia_aieebdef  

grub> root (hd0,2)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub>
```

Any idea what I should try next? Is there any other info I could post that might help?

Thanks!

---

### Post by pjman on 2007-08-27
I figured it out :popcorn:

The partition you are trying to modify with grub needs to have the boot flag set either using fdisk or gparted :oops:

---

### Post by eigenaar on 2007-08-28
I would strongly advise using FDisk (or an other partitioning program) to partition and add filesystems to the RAID disk. I couldn't get the partitioning right with GParted (the default installation used).
With FDisk no problems at all. It immediatly recognized all my raid partitions.

---

### Post by highlanderc on 2007-09-09
Thank you for this post... I wish i would have bumped on it WAY SOONER. Because of raid (fake or not) i have never been able to install linux... I like raid.. its a huge boost in performance.

---

### Post by rwillia2001 on 2007-09-25
Hi,

I have had success installing 32bit  raid1 on my fake raid system (ASUS P5B-E, intel E6600, ICHR8). Thanks for the post.  However, when I try and and install the 64 bit system starting from a LIVE CD I do:

sudo debootstrap  --arch amd64 feisty /target

then it errors after the download, validation and extraction with

W: Failure trying to run: chroot /target mount -t proc proc /proc

and if I try

sudo chroot /target 

chroot cannot run command /bin/bash: Exec format error

I think this is something to do with building a cross-platform  system, starting the install  from a i386 LIVE CD and then trying to chroot into the amd64 bit feisty system. However, it looks like you have solved this problem. I would be very grateful if you could give a short explanation as to how you managed to start in 32 bit and end in 64 bit.

Many thanks

RMW

---

### Post by RamonS2007 on 2007-10-06
> **bsmith1051 said:**
> why not just use the 'standard' Linux software RAID?  It should work as well as -- if not better than -- the fakeraid.  Here's how I did it,
[http://ubuntuforums.org/showthread.php?p=2899075](http://ubuntuforums.org/showthread.php?p=2899075)

Because I want a dual boot with XP and my experiences with Windows using a fake RAID and Linux using a software raid were quite horrible on my old PATA based fake raid system (some Abit board with a HighPoint fake raid on board).
I really do not get the why there such a bad vibe against the fake RAID. After all, it isn't any different in performance than a software raid (assuming on the code used, which may or may not be better in Linux). The CPU still has to do the raid tasks either way. Besides that, mobos with fake raids are around for at least four years if not longer, so expecting to have that type of hardware supported isn't really asking that much. In fact, Fedora and SuSE **do** support fake raid out of the box, so having Ubuntu fail miserably in this aspect isn't really anything that can be spun into something positive.

This is the stuff that makes people diss Linux in general. Oh, and that there are no drivers for my new TV card, but I blame Hauppauge for that.

---

### Post by McSwordfish on 2007-10-21
> **s1mmel said:**
> 
**Step 3:**

After you've finished your partition setup start up the  live installer. When you are asked to setup your harddrives choose manual. You'll see your partitions now, but twice. The first set is without any numbers attached to them. Choose edit partition and tell the system [COLOR="Red"]DON'T USE[/COLOR], repeat that with every partition. MAke sure those are not marked to be formatted.

Then you'll change to the second set, here you can see your partitions attached with numbers 1-X. Set your mount points and tell the installer which filesystem should be used, make sure to mark them for formatting.

If you've done everything right the installer will format and then start to install the system.



Having solved my partitioning woes (using a windows based partitioner that can creat ext3 and swap partitions), I now hit a snag at this stage. Here's a screenshot of what I get presented with when I select manual disk configuration:
[img]http://homepages.tesco.net/swordfish/pix/Screenshot.png[/img]

I assume that to edit the partition, I need to select "New partition table", but what about this whole numbering thing? Both appear to have identical numbers. Have I done something wrong elsewhere or will the distinction in numbering come when I come to edit the partitions?

Cheers,
Swordfish

---

### Post by ZsZso on 2007-10-22
Hi guys!

First of all, I'd like say a big thanx for this guide.

There were some problems I crashed in while I was installing my dual boot system on my RAID 1

1. **There was no partition files in the directory /dev/mapper/** , there was only one (RAID set - besides the control).
_Solution_: My RAID SET's name has a space in it. It was a big problem, after renaming it from "Normal raid" to "Raid", everything was OK.

2. **Vista can't boot (NTLDR is missing)**
I couldn't use the GRUB boot manager, because my first partition was the ext3 (/) partition, and the second was the Vista. It's not a big problem, but I need to make my linux partition active (bootable) to be able to boot from GRUB. But if it is active Vista can't boot!
_Solution_: I removed the active flag from the linux partition, and thereby vista was able to repair my system. I created a menu with EasyBCD, it was a piece of cake.

3.** I can't activate my raid set, if there's a linux swap partition on it.**
It's really odd ... I'll explain my problem:
[INDENT]3.1 there's only the NTFS partition.
3.2 creating every partition that it needs ... ext3, swap, and another NTFS (for programs). Everything is OK.
3.3 installing ubuntu
3.4 restarting
3.5 trying to mount the raid partition again (on the live cd, 'cause there's no usable grub installed on the computer). dmraid installed fine, but the 

*dmraid -ay* command DOES NOTHING!
tryed *dmraid -tay* (it shows, that everyting is ok with my raid set, but it don't activate it)
ok ... *dmaid -an*
my raid set is shown here as inactive

So everything is fine except I can't make my raid set active (so there's no file in the /dev/mapper directory (except control)). After deleting the swap partition on from a live windows cd I can activate my raid set again (this way, I don't have a swap partition ... sadly).[/INDENT]

**Pls help me with the problem 3.!** I'd really appreciate any help, or idea!

 I hope I could help you with my other 2 problems (+ solutions) :).

**UDPATE**: If I change the partition's system ID from 82 (swap) to 83 (ext3) raid can be activated too ... but the partition can't be used as a swap :(
**UDPATE 2**: Another problem:
My Raid set has 2 NTFS partition. All of them appears twice (ex. WindowsVista and WindowsVista (2)) when I click on Places > Computer (I can't mount them fortunately). There's no corresponding line in fstab. Any idea, how to get rid of the useless icons?

Thx in advance!

---

### Post by ZsZso on 2007-10-22
McSwordfish, you need to partition your raid set BEFORE you run the installer. (I would say, you have to FORMAT them too). Use fdisk /dev/mapper/XXX (<= Raid set's name, there's no numbers in it), it's easy to use.

---

### Post by McSwordfish on 2007-10-23
I have no /dev/mapper/nvidia_stuff.

Here's a screenshot of stuff:
[img]http://homepages.tesco.net/swordfish/pix/terminal.png[/img]

I'm guessing I've done something really wrong, but I have no idea what. It's only appearing as /dev/sda and /dev/sdb. 

Am I missing something screamingly obvious?

As far as I am aware, the partitions I created (as shown in the above) should be formatted. I hit the "format" on both the ext3 swap partitions and it appeared to do something. Whether it's done it well is another story entirely, but I'm an eternal optimist.

---

### Post by GnarusLeo on 2007-10-24
I have exacly the same problem as mcswordfish. Same error on Gparted, though everything looks ok. I have the /dev/mapper/nvidia thingy, and it is recognized by gparted .... but ut says that it is in use when I try to format them. 

This happens on both the gparted thing, and the kubuntu installer ... same error.

Any help will be very appriciated!

Eirik

---

### Post by ZsZso on 2007-10-25
Same happened to me, after I had created a LINUX SWAP (Id 82) partition on the raid. Don't you have any?

As I see, McSwordfish has one. I had written down already, but maybe that should be the problem for you too. So ... change your SWAP partition to LINUX (83 to 82), and use that partition as swap. Yeah ... it's not a good solution, but this way, you'll have a swap partition.

(You have to remove the swap partition from windows, or any other live os, that can identify the raid)

One more thing ... I'm kind of newbie to linux, but I've spent my whole life near computers. (and about a week near this RAID configuration ... :D)


OK, another info ...
I've installed Ubuntu to a ICH8R/ICH9R raid controller (GA-P35-DS4). There were no problem renaming the raid set (It had space in it) - I've used windows tool for it. I'm trying to install Ubuntu on a new configuration (GA-P35-DS3) with a JMicron Raid controller. THERE'S NO WAY TO RENAME IT! :( I don't have any space in it's name, but it works like it has 11 in it ("GRAID           "). So the solution ... you have to give it a nice long (exactly 16 chars long) name ... like GRAIDGRAIDGRAIDG. It works like a charm :). (the bad part is, you have to delete all the data on your raid devices)

---

### Post by s1mmel on 2007-10-27
> **GnarusLeo said:**
> I have exacly the same problem as mcswordfish. Same error on Gparted, though everything looks ok. I have the /dev/mapper/nvidia thingy, and it is recognized by gparted .... but ut says that it is in use when I try to format them. 

This happens on both the gparted thing, and the kubuntu installer ... same error.

Any help will be very appriciated!

Eirik


As I stated in my post, DON'T EVER FORMAT THE DRIVES WITH THE GPARTED *SCREAM*

Dudes, the installer will give it a FileSystem later, just make your partitioning with it, leave the FS to "not formatted" (don't chosse something else!).

That's the mistake a lot of ppl. are making. Sorry but, just read more careful

):P

---

### Post by er999 on 2007-10-29
Hi !

I've tried to install on a nForce 680i fake raid, here is the config  :
(The hidden boot partition is to be able to install windows on C:\ 
and to be able to have a grub boot partition under 1024 cylinders)

```

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_ccfiaefb1   *           1          32      257008+  1b  Hidden W95 FAT32
/dev/mapper/nvidia_ccfiaefb2              33        8001    64010992+   7  HPFS/NTFS
/dev/mapper/nvidia_ccfiaefb3            8002       24711   134223075    7  HPFS/NTFS
/dev/mapper/nvidia_ccfiaefb4           24712       97282   582926557+   f  W95 Ext'd (LBA)
/dev/mapper/nvidia_ccfiaefb5           24712       25233     4192933+  83  Linux

```

and then with "grub" :

```

device (hd0) /dev/mapper/nvidia_ccfiaefb
root (hd0,0)
setup (hd0)

Grub Error 17: Cannot mount selected partition 

```
I have figured out finally, for all who have similar problems :

[COLOR="Red"][B]1) Change the Id of your boot partition to 83 (linux) 
2) and always set bootable flag (only) on the boot partition[/B][/COLOR]

To do it, simply use "cfdisk", instead of "fdisk" that crashes sometimes with dmraid.
Don't forget "sudo" if you aren't in the chroot.

```
cfdisk /dev/mapper/<your fakeraid>
```

Hope this helps... :)

---

### Post by Wilco on 2007-10-29
> **s1mmel said:**
> As I stated in my post, DON'T EVER FORMAT THE DRIVES WITH THE GPARTED *SCREAM*

Dudes, the installer will give it a FileSystem later, just make your partitioning with it, leave the FS to "not formatted" (don't chosse something else!).

That's the mistake a lot of ppl. are making. Sorry but, just read more careful

):P

When I allow the installer to format the paritions, it still fails when it attempts to format my main partition. Here's a breakdown:

/dev/sda1      -> 20 GB (unformatted, plan to put XP here later)
/dev/sda2      -> 20GB (unformatted) - fails to format to ext3
/dev/sda3      -> 2GB - successfully formatted as linux swap

Where can I look to see why the format failed. I want to assume it's the same reason GParted couldn't do it, but I know better than that. Is there an installer log somewhere?

---

### Post by s1mmel on 2007-10-29
> **Wilco said:**
> When I allow the installer to format the paritions, it still fails when it attempts to format my main partition. Here's a breakdown:

/dev/sda1      -> 20 GB (unformatted, plan to put XP here later)
/dev/sda2      -> 20GB (unformatted) - fails to format to ext3
/dev/sda3      -> 2GB - successfully formatted as linux swap

Where can I look to see why the format failed. I want to assume it's the same reason GParted couldn't do it, but I know better than that. Is there an installer log somewhere?

First of all, it's better if you install Windows first, because if you do that afterwards, GRUB will be overwritten. It looks that you dont have a /boot Partition. Could be that the installer doesn't give it a boot flag.

Do you see the two sets of your partitions? Did you use the second, as described in the pictures? Maybe you need to load ```
cfdisk <yourraidnamehere>

``` and give your / partition the boot flag. Just look at the advice 2 or 3 posts above.

I'm sorry, I can't be of much help with that scenario.

Try to install XP first (don't do updates, just the plain isntall), then kick in the Gutsy disc and use a /boot partition a / partition and a swap.

See how that works out for you... I had no problems in 2 installs with 2 different systems and 2 different chipsets (nvidia and intel).

If you have an Intel Chipset, you might have the same problem I had. If you can name your RAID make sure to use the full lentgh of the name field.

---

### Post by Wilco on 2007-10-29
Good call on installing XP first. I actually had Vista on there originally, and ran into this same problem. I do see both sets of partitions and am using the second set. I will go ahead and get XP up and running and then switch back to this, though I am anticipating the same problem surfacing again. If anyone can offer some tips let me know.

As a side note, one thing I did try earlier when I still had Vista installed on that first partition was to use Acronis Disk Director to create/format the partitions there. However after I did this I could no longer use dmraid to find my RAID partitions. I could go this route if it turns out this problem could be a simple fix.

EDIT: In case it helps, the RAID chipset is of the NVIDIA n-Force variety (can't remember which version, it's an AW m9700 notebook).

---

### Post by s1mmel on 2007-10-31
> **Wilco said:**
> Good call on installing XP first. I actually had Vista on there originally, and ran into this same problem. I do see both sets of partitions and am using the second set. I will go ahead and get XP up and running and then switch back to this, though I am anticipating the same problem surfacing again. If anyone can offer some tips let me know.

As a side note, one thing I did try earlier when I still had Vista installed on that first partition was to use Acronis Disk Director to create/format the partitions there. However after I did this I could no longer use dmraid to find my RAID partitions. I could go this route if it turns out this problem could be a simple fix.

EDIT: In case it helps, the RAID chipset is of the NVIDIA n-Force variety (can't remember which version, it's an AW m9700 notebook).


I've seen that you made a mistake!

Don't partition the drive with /dev/sda and /dev/sdb... remove the partitions. You need to build up the partitions with the /dev/mapper/<yourraidnamegoeshere> added

---

### Post by pjman on 2007-11-05
Two months ago I installed Feisty on a RAID 1 array using this guide. I've since upgraded to Gutsy using the update manager. 

I've now decided I want to do a fresh install of Gutsy with the x86-64 version. I thought this would be simple enough since all the partitions are already made but it's not working out so well. I boot up to the Gutsy x86-64 LiveCD and install dmraid. After running "dmraid -ay" and "dmraid -r", my partitions are not listed under /dev/mapper. The only thing in /dev/mapper is 'control'. 

[LIST]
[*]I have 4 partitions in the mirror: First two for Windows, third for Ubuntu and the fourth is swap. Are my current partitions messing up dmraid?
[*]Is there a bug in dmraid that is in the gutsy repositories?
[*]Could the 64bit version have a bug?
[/LIST]

Thank you!

**Edit**
Deleting my swap partition allowed everything to show up under /dev/mapper. Can someone explain why swap has to be deleted in order for this to work? Just curious.

Thanks

---

### Post by pjman on 2007-11-08
This isn't working out to well. I'm kinda wishing I would have just left well enough alone and stayed with the 32 bit version...

Ubiquity is giving me a lot of problems. The size of the partitions don't make sense.

The basics - dmraid and fdisk info:


```
ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: nvidia, "nvidia_aeedigej", mirror, ok, 976773166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_aeedigej", mirror, ok, 976773166 sectors, data@ 0
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "nvidia_aeedigej" already active
RAID set "nvidia_aeedigej1" already active
RAID set "nvidia_aeedigej2" already active
RAID set "nvidia_aeedigej3" already active
RAID set "nvidia_aeedigej4" already active
ubuntu@ubuntu:~$ 
```


```

ubuntu@ubuntu:~$ sudo fdisk /dev/mapper/nvidia_aeedigej

Command (m for help): p

Disk /dev/mapper/nvidia_aeedigej: 500.1 GB, 500107860992 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bccd9

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_aeedigej1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/mapper/nvidia_aeedigej2            3265       50358   378282555    7  HPFS/NTFS
/dev/mapper/nvidia_aeedigej3           50359       50421      506047+  83  Linux
/dev/mapper/nvidia_aeedigej4   *       50422       60801    83377350   83  Linux
```

Now see the attached picture. This is what comes up when I choose to manually configure the partitions. _Disregard the "type" & "mount point" for all devices._ This would be cleaned up if I went further before taking the screenshot.

The portion circled in [COLOR="Red"]red[/COLOR] is what's confusing me. I don't have a nvidia_aeedigej5 or nvidia_aeedigej6. Even the partition sizes are wrong (also circled in [COLOR="Red"]red[/COLOR]). 

The top portion that is circled in [COLOR="Blue"]blue[/COLOR] has the correct sizes and numbers of partitions (4) but I can't choose these to install since they have the same name.

If I just choose nvidia_aeedigej3 (for swap) and nvidia_aeedigej4 (for /) I get an error when the installer tries to mount swap. After searching the error I found this person getting the same thing: [http://ubuntuforums.org/showthread.php?t=320588](http://ubuntuforums.org/showthread.php?t=320588)

Any ideas?

---

### Post by s1mmel on 2007-11-13
Hi,

I've seen the picture and there are some things taht are disturbing me. 

As you can see, the /dev/hda and /dev/hdb, also show partitions. But that shouldn't be the case.

This is very strange, normally those 2 entries should only show up but have NO partitions at all.

I guess that is the problem you are encountering. I don't know how to fix this to be honest, as I only started this guide with a fresh install.

:-/

---

### Post by pjman on 2007-11-13
Thanks for taking a look at it. I've decided to install the OS on my 40GB IDE drive and mount a slice of my NVidia dmraid array for data. 

Hopefully someday soon installing the OS with dmraid will be built in and wont be a hassle at all :-)

---

### Post by hannestum on 2007-12-13
I have Windows Vista running and also want to install 7.10 on my existing RAID 0 (using Intel Matrix Storage Contoller).

I also used Acronis Disk Director for creating a root and swap partition.

When i start GParted after installing dmraid it shows the existing disks but
also writes the following errors to the command line:
```

Can't have overlapping partitions.
Can't have a partition outside the disk!
Can't have a partition outside the disk!
Can't have a partition outside the disk!
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.
Can't have a partition outside the disk!
Unable to open /dev/sdb - unrecognised disk label.

```

When Trying to install the Partition Dialog also doesn't give the mentioned "two sections".
Every Partition is listed only once. When I try to install grub it also gives me some errors..

So, I think it must be that I'm too stupid to get my PC partitioned in the right way.

dmraid -ay says:
```

RAID set "isw_ecfgdiahib_Volume0" already active
RAID set "isw_ecfgdiahib_Volume01" already active
RAID set "isw_ecfgdiahib_Volume02" already active
RAID set "isw_ecfgdiahib_Volume04" already active
RAID set "isw_ecfgdiahib_Volume05" already active
RAID set "isw_ecfgdiahib_Volume06" already active

```

and fdisk says:
```

/dev/mapper/isw_ecfgdiahib_Volume0p1   *           1       13015   104542956    7  HPFS/NTFS
/dev/mapper/isw_ecfgdiahib_Volume0p2           13016       13979     7743330   12  Compaq diagnostics
/dev/mapper/isw_ecfgdiahib_Volume0p3           13980       38914   200290387+   5  Extended
/dev/mapper/isw_ecfgdiahib_Volume0p4           37478       38783    10490443+  83  Linux
/dev/mapper/isw_ecfgdiahib_Volume0p5           13980       37477   188747650+   7  HPFS/NTFS
/dev/mapper/isw_ecfgdiahib_Volume0p6           38784       38914     1052226   82  Linux swap / Solaris

```

The first NTFS Partition should be root of Windows Vista
The Compaq Diagnostics is a Drive Image
The second NTFS should be Data Partition
Volume0p4 should be Linux Native and Volume0p6 Linux Swap

Can Anyone tell me what's wrong with theese partitions?????
I'm shure there must be a mistake....

---

### Post by s1mmel on 2007-12-13
> **hannestum said:**
> 

Can Anyone tell me what's wrong with theese partitions?????
I'm shure there must be a mistake....

The partitions itself are looking good mate, what does dmraid -r tell you, are there both HDDs mentioned?

Funny, the gparted gives back that the partitions are outside of the disk, as if the disk(s) are too small to maintain them.

If gparted wont work for you, you can also try cfdisk.

```

cfdisk your/raidname/goes/here

```

One more thing before you do so, what exactly did you do, did you just create the partitions or did you also try to install a Filesystem on them (like ext2 or similar). Trying to create a Filesystem will crash the gparted and won't work, as mentioned in my Guide, the installer will take care of that.

Well hope you can get it running.

---

### Post by s1mmel on 2007-12-13
> **hannestum said:**
> I have Windows Vista running and also want to install 7.10 on my existing RAID 0 (using Intel Matrix Storage Contoller).

I also used Acronis Disk Director for creating a root and swap partition.


and fdisk says:
```

/dev/mapper/isw_ecfgdiahib_Volume0p1   *           1       13015   104542956    7  HPFS/NTFS
/dev/mapper/isw_ecfgdiahib_Volume0p2           13016       13979     7743330   12  Compaq diagnostics
/dev/mapper/isw_ecfgdiahib_Volume0p3           13980       38914   200290387+   5  Extended
/dev/mapper/isw_ecfgdiahib_Volume0p4           37478       38783    10490443+  83  Linux
/dev/mapper/isw_ecfgdiahib_Volume0p5           13980       37477   188747650+   7  HPFS/NTFS
/dev/mapper/isw_ecfgdiahib_Volume0p6           38784       38914     1052226   82  Linux swap / Solaris

```



Two additional questions!

First of all, how did you install Vista and the Compaq partition, did you install them as a RAID0 or 1 too? This guide is RAIDonly so to say and doesn't work like mdadm!!!

So before you installed Vista did you put your Disks 2gether as a RAID0/1?

If you didn't that might be the error, this would also explain the GRUB errors.


Second, while using Acronis, was the RAID already activated? Or did you create the partitions without RAID0/1 setup?

Again, this tutorial only works if you use both operating systems on the RAID0/1. I know that it's possible to work different with mdadm, but in this case the controller is in charge and not the software.

HTH,
Simmel

---

### Post by hannestum on 2007-12-13
> The partitions itself are looking good mate, what does dmraid -r tell you, are there both HDDs mentioned?

Yes, both HDDs are mentioned:
```
 
sudo dmraid -r
/dev/sda: isw, "isw_ecfgdiahib", GROUP, ok, 312581806 sectors, data@ 0
/dev/sdb: isw, "isw_ecfgdiahib", GROUP, ok, 312581806 sectors, data@ 0

```


But I'm wondering because when I type:
```

sudo gparted /dev/mapper/isw_ecfgdiahib

```
Gparted opens and tells me that there are no drives selected.

When I type: 
```

sudo gparted /dev/mapper/isw_ecfgdiahib_Volume0

```
Gparted shows 298GB of unallocated Space (althogh I have 2 x 160 GB)

But when I type: sudo fdisk /dev/mapper/isw_ecfgdiahib_Volume0 it says:
```

Disk /dev/mapper/isw_ecfgdiahib_Volume0: 320.0 GB, 320079134720 bytes
......
/dev/mapper/isw_ecfgdiahib_Volume0p1   *           1       13015   104542956    7  HPFS/NTFS
/dev/mapper/isw_ecfgdiahib_Volume0p2           13016       13979     7743330   12  Compaq diagnostics
/dev/mapper/isw_ecfgdiahib_Volume0p3           13980       38914   200290387+   5  Extended
/dev/mapper/isw_ecfgdiahib_Volume0p4           37478       38783    10490443+  83  Linux
/dev/mapper/isw_ecfgdiahib_Volume0p5           13980       37477   188747650+   7  HPFS/NTFS
/dev/mapper/isw_ecfgdiahib_Volume0p6           38784       38914     1052226   82  Linux swap / Solaris

```

So fdisk does it's Job right and gparted isn't...

I'm also wondering because fdisk for example prints the name 
"isw_ecfgdiahib_Volume0p4" and dmraid -ay prints
"isw_ecfgdiahib_Volume04"


To your other Questions:
I got the Notebook with vista already installed. Also the Recover Partition mentioned as Compaq was already there. But i think they installed everything with RAID 0 enabled because when you want to change the RAID level via the Intel Matrix Storage BIOS everything would be deleted...

I'm really helpless in the moment.....

---

### Post by s1mmel on 2007-12-15
> **hannestum said:**
> Yes, both HDDs are mentioned:
```
 
sudo dmraid -r
/dev/sda: isw, "isw_ecfgdiahib", GROUP, ok, 312581806 sectors, data@ 0
/dev/sdb: isw, "isw_ecfgdiahib", GROUP, ok, 312581806 sectors, data@ 0

```


But I'm wondering because when I type:
```

sudo gparted /dev/mapper/isw_ecfgdiahib

```
Gparted opens and tells me that there are no drives selected.

When I type: 
```

sudo gparted /dev/mapper/isw_ecfgdiahib_Volume0

```
Gparted shows 298GB of unallocated Space (althogh I have 2 x 160 GB)

But when I type: sudo fdisk /dev/mapper/isw_ecfgdiahib_Volume0 it says:
```

Disk /dev/mapper/isw_ecfgdiahib_Volume0: 320.0 GB, 320079134720 bytes
......
/dev/mapper/isw_ecfgdiahib_Volume0p1   *           1       13015   104542956    7  HPFS/NTFS
/dev/mapper/isw_ecfgdiahib_Volume0p2           13016       13979     7743330   12  Compaq diagnostics
/dev/mapper/isw_ecfgdiahib_Volume0p3           13980       38914   200290387+   5  Extended
/dev/mapper/isw_ecfgdiahib_Volume0p4           37478       38783    10490443+  83  Linux
/dev/mapper/isw_ecfgdiahib_Volume0p5           13980       37477   188747650+   7  HPFS/NTFS
/dev/mapper/isw_ecfgdiahib_Volume0p6           38784       38914     1052226   82  Linux swap / Solaris

```

So fdisk does it's Job right and gparted isn't...

I'm also wondering because fdisk for example prints the name 
"isw_ecfgdiahib_Volume0p4" and dmraid -ay prints
"isw_ecfgdiahib_Volume04"


To your other Questions:
I got the Notebook with vista already installed. Also the Recover Partition mentioned as Compaq was already there. But i think they installed everything with RAID 0 enabled because when you want to change the RAID level via the Intel Matrix Storage BIOS everything would be deleted...

I'm really helpless in the moment.....

Hmh,

sure you haven't installed a RAID10? I tried to accomplish this with a friend, but dmraid is not able to work in that mode with Intel-Controllers.

It's very strange indeed, hmh, cld. be that this is a RAID10-Setup, not sure. Well you gotta get gparted running because this is what the installer is using. Otherwise you'll have to try without the installer und use the link privided at the end of my post.

So sorry

:confused:

---

### Post by hannestum on 2007-12-15
Thanks for your Help. Im sure it is a RAID 0 (Striping)...

strange thing...:confused::confused::confused:

---

### Post by hannestum on 2007-12-15
Mhm, just installed dmraid rc14.

Now, nothing happens when I type dmraid -ay.......

:-k

---

### Post by s1mmel on 2007-12-16
> **hannestum said:**
> Mhm, just installed dmraid rc14.

Now, nothing happens when I type dmraid -ay.......

:-k

Well seems like the dmraid is having problems with your fakeraid controller :-&

```

root@monolith:~# dmraid -l
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs

```

This is the list that's supported, Is you controller mentioned there (besides the word intel ^^)???

---

### Post by hannestum on 2007-12-16
Mhm, already read the list. I think it must be an Intel Software Raid.
When I boot the System there comes something like a RAID Bios called
"Intel Matrix Storage Manager (ICH7MR)"

I also instelled the Intel Matrix Storage Console using Windows.
There the Hardware is known as Intel 82801 GHM SATA RAID Controller.

But I don't know if this is meant by "Intel Software RAID".

---

### Post by hannestum on 2007-12-17
Ok, tried to install Gutsy via debootstrap, and it worked :guitar:

thanks for your help s1mmel :KS

---

### Post by psusi on 2007-12-20
The last time I tried this, the installer got very confused by dmraid and thought it was lvm, so I had to install via debootstrap.  Your instructions seem to say to use debootstrap and then the normal installer, which makese no sense.  After you debootstrap the system, you have performed a minimal install.  Then you just chroot in and install ubuntu-desktop to get everything else.

---

### Post by s1mmel on 2007-12-21
> **psusi said:**
> The last time I tried this, the installer got very confused by dmraid and thought it was lvm, so I had to install via debootstrap.  Your instructions seem to say to use debootstrap and then the normal installer, which makese no sense.  After you debootstrap the system, you have performed a minimal install.  Then you just chroot in and install ubuntu-desktop to get everything else.

Never said you had to debootstrap into the system. But you need some stuff from the debootstrap package, to correct the grub error.

Please read first and then comment properly, appreciate it.

:lolflag:

---

### Post by jrsutton on 2007-12-30
First I want to say thank you for writing up this guide. It has been extremely helpful. I have ran into a snag though. I followed the guide up to the installation process where it preps the partitions and here is what I see:

Do the two NTFS partitions have the same map point because of the Vista Bootloader? When I cancel the install and boot w/o the LiveDVD I can boot into either OS from the Vista Bootloader. Anyone ever seen this, or know how I would go about getting this to work with Ubuntu?

---

### Post by psusi on 2007-12-30
I finally got around to trying this again, and it went surprisingly smoothly, but found two corrections to your instructions:

1)  debootstrap package is not needed
2)  you have to edit fstab because UUIDs on dmraid partitions do NOT work.  The system doesn't try to find UUIDs for the /dev/mapper devices, but it may incorrectly find IDs on the underlying physical disks, which you do NOT want to access.

---

### Post by bernardfrancois on 2007-12-31
I'm considering using this method to install ubuntu on a new computer (because windows already uses raid).

Aren't there any problems when there are upgrades for the kernel or grub?

Another option would be to switch to a different distribution. The installers of gentoo, suse and fedora seem to support fakeraid... Maybe it's safer when it's officially supported (so updates won't break anything).

---

### Post by s1mmel on 2008-01-02
> **jrsutton said:**
> First I want to say thank you for writing up this guide. It has been extremely helpful. I have ran into a snag though. I followed the guide up to the installation process where it preps the partitions and here is what I see:

Do the two NTFS partitions have the same map point because of the Vista Bootloader? When I cancel the install and boot w/o the LiveDVD I can boot into either OS from the Vista Bootloader. Anyone ever seen this, or know how I would go about getting this to work with Ubuntu?


Sorry mate,

as I don't use Vista I can't answer your question, with XP I didn't experience this kind of problem.

Cheerio,
S1mmel

---

### Post by s1mmel on 2008-01-02
> **bernardfrancois said:**
> I'm considering using this method to install ubuntu on a new computer (because windows already uses raid).

Aren't there any problems when there are upgrades for the kernel or grub?

Another option would be to switch to a different distribution. The installers of gentoo, suse and fedora seem to support fakeraid... Maybe it's safer when it's officially supported (so updates won't break anything).


Kernelupdates aren't a problem, as the installer always uses the old config file. All the options are in there, so this isn't an issue at all.

Please do yourself a favour, this is of course a guide and as you can see some ppl. have problems with chipsets and the according controllers. So if you decide to go along, consider to backup your data first and play it save.

S1mmel

---

### Post by s1mmel on 2008-01-02
> **psusi said:**
> I finally got around to trying this again, and it went surprisingly smoothly, but found two corrections to your instructions:

1)  debootstrap package is not needed
2)  you have to edit fstab because UUIDs on dmraid partitions do NOT work.  The system doesn't try to find UUIDs for the /dev/mapper devices, but it may incorrectly find IDs on the underlying physical disks, which you do NOT want to access.

Well

debootstrap is needed with Feisty, I know that 4 sure... coz I started the guide with Feisty.

About the uuids, I'm not sure about that, cld. be different from system to system, but it's allright that you mention it here, as it cld. help other users who may encounter the same problems.

I can only speak for myself, the uuids work fine with my setup.

Cheers,
S1mmel

---

### Post by bernardfrancois on 2008-01-10
After backing up my data, I wanted to move the ntfs partition to the beginning of the disk. Gparted couldn't do that. I attached a screenshot of the error I got.

Perhaps I will try to do the partitioning manually (with the command line tools).

[edit]
[INDENT]I tried to move the partition with Acronis Disk Director Suite (in windows vista).
It only moved the partition on the first disk, but because I'm using RAID1 (mirroring), the data from the first disk got automatically copied to the second disk.

I suppose that could also have worked with gparted; just doing the partitioning for one disk and then rebooting to windows, where the software raid controller fixes the inconsistency.
Note that this only works for RAID1 and that you need to partition the right disk of the two.[/INDENT]
[/edit]

[edit2]
[INDENT]A suggestion for the tutorial: The raid name displayed with **dmraid -ay** and **dmraid -r** isn't always the same. The first name worked in my case. To find the right name, you can execute **ls /dev/mapper**.

```

ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# dmraid -ay
RAID set "isw_biigdfjeeh_ARRAY" already active
RAID set "isw_biigdfjeeh_ARRAY1" already active
root@ubuntu:~# dmraid -r
/dev/sda: isw, "isw_biigdfjeeh", GROUP, ok, 625142446 sectors, data@ 0
/dev/sdb: isw, "isw_biigdfjeeh", GROUP, ok, 625142446 sectors, data@ 0
root@ubuntu:~# ls /dev/mapper
control  isw_biigdfjeeh_ARRAY  isw_biigdfjeeh_ARRAY1

```[/INDENT]
[/edit2]

[edit3]
[INDENT]The installer's partitioner failed to create the partitions. This is the message I got:
> 
The attempt to mount a file system with type swap in LVM VG isw_biigdfjeeh_ARRAY, LV isw_biigdfjeeh_ARRAY at none failed.

You may resume partitioning from the partitioning menu.
[ Go Back ]  [ Continue ]


I gave up on using the installer and succeeded installing ubuntu using the following howto:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Note that I used a /boot partition of 50mb and a swap partition of 512mb, which works fine.[/INDENT]
[/edit3]

---

