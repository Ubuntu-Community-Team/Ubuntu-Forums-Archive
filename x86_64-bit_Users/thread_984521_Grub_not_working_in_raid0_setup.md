---
title: "Grub not working in raid0 setup"
date: 2008-11-16
forum: x86 64-bit Users
---

### Post by stimulus2da on 2008-11-16
Hello, I'm fairly new to Ubuntu and I am having trouble with trying to get a dual boot of ubuntu and vista64 working.  I first tried using the Alternate CD and everything seemed to install fine until I rebooted, and then it went straight into vista.  After that, I have been following this tutorial:

[https://help.ubuntu.com/community/FakeRaidHowto#In%20Long%20without%20detail%20as%20above%20(2008-10-26%20update](https://help.ubuntu.com/community/FakeRaidHowto#In%20Long%20without%20detail%20as%20above%20(2008-10-26%20update))

Everything seems okay until I get to step 27 where I get "Error 15: File not found."  I've tried many things and am at a loss.  If anyone has any suggestions, they would be greatly appreciated.

---

### Post by caljohnsmith on 2008-11-16
I see at least one typo in that tutorial you are following:
> 16. sudo mount --bin /dev /target/dev 
That should be:
```
sudo mount [COLOR="Red"]--bind[/COLOR] /dev /target/dev
```
That typo could be responsible for your Grub error 15, because if /dev is not mounted on the target directory that you chroot into, then Grub can't see the drives as it should. Did you all ready notice that was a typo and correct it? If not, try that and let me know how it goes. :)

P.S. I just now edited the Wiki to correct that typo, so at least that part of the tutorial should be OK now.

---

### Post by stimulus2da on 2008-11-16
> **caljohnsmith said:**
> I see at least one typo in that tutorial you are following:

That should be:
```
sudo mount [COLOR="Red"]--bind[/COLOR] /dev /target/dev
```
That typo could be responsible for you Grub error 15, because if /dev is not mounted on the target directory that you chroot into, then Grub can't see the drives as it should. Did you all ready notice that was a typo and correct it? If not, try that and let me know how it goes. :)

P.S. I just now edited the Wiki to correct that typo, so at least that part of the tutorial should be OK now.

I tried it with the modification to "bind" and it does the same thing.  I don't know if it matters but when I type ```
grub --no-curses
``` I get ```
Probing devices to guess BIOS drives.  This may take a long time.
Unknown partition table signature

         [ Minimal BASH-like line editing is supported.....
```
Any other thoughts?

---

### Post by caljohnsmith on 2008-11-16
That error might actually be OK since you are trying to set up RAID, the important thing is the command that you do after going into the Grub shell:
```
grub> device (hd0) /dev/mapper/nvidia_cjbgcjgd
```
If your RAID is set up correctly, that should work so that when you do the "find" command, it will find the partition with Grub's stage1 file. One other thing--do you have a /boot partition? If you do, you should instead use:
```
grub> find /grub/stage1

```
If you still have trouble, how about posting your entire terminal session from when you start that tutorial so I can maybe get a better idea of where something went wrong.

---

### Post by stimulus2da on 2008-11-16
I do not have a /boot partition.
Here is my terminal session:
```

ubuntu@ubuntu:~$ sudo apt-get install dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdmraid1.0.0.rc14
The following NEW packages will be installed:
  dmraid libdmraid1.0.0.rc14
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 109kB of archives.
After this operation, 393kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com intrepid/main libdmraid1.0.0.rc14 1.0.0.rc14-2ubuntu12 [80.8kB]
Get:2 http://archive.ubuntu.com intrepid/main dmraid 1.0.0.rc14-2ubuntu12 [28.6kB]
Fetched 109kB in 1s (89.1kB/s)
Selecting previously deselected package libdmraid1.0.0.rc14.
(Reading database ... 100452 files and directories currently installed.)
Unpacking libdmraid1.0.0.rc14 (from .../libdmraid1.0.0.rc14_1.0.0.rc14-2ubuntu12_amd64.deb) ...
Selecting previously deselected package dmraid.
Unpacking dmraid (from .../dmraid_1.0.0.rc14-2ubuntu12_amd64.deb) ...
Processing triggers for man-db ...
Setting up libdmraid1.0.0.rc14 (1.0.0.rc14-2ubuntu12) ...

Setting up dmraid (1.0.0.rc14-2ubuntu12) ...
update-initramfs is disabled since running on a live CD

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ubuntu@ubuntu:~$ sudo modprobe dm-raid4-5
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_bjgiiaibhe_Volume0" already active
RAID set "isw_bjgiiaibhe_Volume01" already active
RAID set "isw_bjgiiaibhe_Volume05" already active
RAID set "isw_bjgiiaibhe_Volume06" already active
RAID set "isw_bjgiiaibhe_Volume07" already active
ubuntu@ubuntu:~$ cd /dev/mapper
ubuntu@ubuntu:/dev/mapper$ ls
control  isw_bjgiiaibhe_Volume0  isw_bjgiiaibhe_Volume01  isw_bjgiiaibhe_Volume05  isw_bjgiiaibhe_Volume06  isw_bjgiiaibhe_Volume07
ubuntu@ubuntu:/dev/mapper$ sudo fdisk isw_bjgiiaibhe_Volume0 -l

Disk isw_bjgiiaibhe_Volume0: 1280.2 GB, 1280265420800 bytes
255 heads, 63 sectors/track, 155650 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c286c28

                  Device Boot      Start         End      Blocks   Id  System
isw_bjgiiaibhe_Volume0p1   *           1       21672   174078976    7  HPFS/NTFS
isw_bjgiiaibhe_Volume0p2           21673      155650  1076178285    f  W95 Ext'd (LBA)
isw_bjgiiaibhe_Volume0p5           21673      149154  1023999133+   7  HPFS/NTFS
isw_bjgiiaibhe_Volume0p6          149155      155379    50002281   83  Linux
isw_bjgiiaibhe_Volume0p7          155380      155650     2176776   82  Linux swap / Solaris
ubuntu@ubuntu:/dev/mapper$ sudo mkdir /target
ubuntu@ubuntu:/dev/mapper$ sudo mount isw_bjgiiaibhe_Volume06 /target
ubuntu@ubuntu:/dev/mapper$ sudo mount --bind /dev /target/dev
ubuntu@ubuntu:/dev/mapper$ sudo mount -t proc proc /target/proc
ubuntu@ubuntu:/dev/mapper$ sudo mount -t sysfs sys /target/sys
ubuntu@ubuntu:/dev/mapper$ sudo chroot /target
root@ubuntu:/# apt-get update
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release
Hit http://us.archive.ubuntu.com intrepid-updates Release           
Hit http://security.ubuntu.com intrepid-security/main Packages
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Reading package lists... Done
root@ubuntu:/# apt-get install dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdmraid1.0.0.rc14
The following NEW packages will be installed:
  dmraid libdmraid1.0.0.rc14
0 upgraded, 2 newly installed, 0 to remove and 75 not upgraded.
Need to get 109kB of archives.
After this operation, 393kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid/main libdmraid1.0.0.rc14 1.0.0.rc14-2ubuntu12 [80.8kB]
Get:2 http://us.archive.ubuntu.com intrepid/main dmraid 1.0.0.rc14-2ubuntu12 [28.6kB]
Fetched 109kB in 1s (80.7kB/s)              
Selecting previously deselected package libdmraid1.0.0.rc14.
(Reading database ... 99122 files and directories currently installed.)
Unpacking libdmraid1.0.0.rc14 (from .../libdmraid1.0.0.rc14_1.0.0.rc14-2ubuntu12_amd64.deb) ...
Selecting previously deselected package dmraid.
Unpacking dmraid (from .../dmraid_1.0.0.rc14-2ubuntu12_amd64.deb) ...
Processing triggers for man-db ...
Setting up libdmraid1.0.0.rc14 (1.0.0.rc14-2ubuntu12) ...

Setting up dmraid (1.0.0.rc14-2ubuntu12) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 75 not upgraded.
Need to get 907kB of archives.
After this operation, 2011kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com intrepid/main grub 0.97-29ubuntu45 [907kB]
Fetched 907kB in 3s (295kB/s)
Preconfiguring packages ...
Selecting previously deselected package grub.
(Reading database ... 99141 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu45_amd64.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu45) ...

root@ubuntu:/# mkdir /boot/grub
root@ubuntu:/# cp /usr/lib/grub/x86_64-pc/* /boot/grub
root@ubuntu:/# grub --no-curses
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/isw_bjgiiaibhe_Volume0
device (hd0) /dev/mapper/isw_bjgiiaibhe_Volume0
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found

```

---

### Post by caljohnsmith on 2008-11-16
OK, while you are in the Grub shell, and after you've done the "device" command, try:
```
grub> geometry (hd0)
```
If that shows your five partitions, then type:
```
grub> null (hd0,5)/boot/grub/
```
And hit TAB for tab-completion; that should show your Grub files. If not, you should check if the /boot/grub directory in the isw_bjgiiaibhe_Volume0p6 partition has the Grub boot files.

---

### Post by John Jason Jordan on 2008-11-16
> **caljohnsmith said:**
> 
```
grub> null (hd0,5)/boot/grub/
```

First, what does that command do?

Second, I have a problem with a broken Grub after upgrading Hardy to Intrepid (x86_64). At the moment it won't boot (Error 15). At first it would boot, but it booted to the old Hardy kernel (2.6.24-19), even though the correct Intrepid kernel (2.6.27-7) was listed in /boot/grub/menu.lst and the vmlinuz file was also for 2.6.27-7. I used:

grub-install --root-directory=/ /dev/sda

To get it to show the 2.6.27-7 kernel in the boot menu. But now I get Error 15. 

I'm trying to figure out how to tell it where the boot files are, but the problem is that I use software RAID (created with mdadm) and I can't get the syntax right.

People tell me to use a live CD or rescue CD, then mount the filesystem, then run grub-install and stuff. Well, that's dandy, but none of the Intrepid live CDs can even see the RAID devices. I do have a GRML rescue CD that will mount MD1 (the device where Intrepid is installed), but when I tried "null" from the grub shell it said there was no such command. Evidently the Grub on the GRML rescue CD is too old or something.

Also, currently the boot parameters are:

root   (hd0,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/md1 ro quiet splash
initrd /boot/initrd.img-2.26.27-7-generic
quiet

All the files are properly located in the /boot and /boot/grub folders. I just can't figure out how to tell the MBR where to look for them.

Another issue to consider is that MD1 does not exist until early in the boot process when the software RAID is set up. The devices themselves (in this case sda1 and sdb1) do exist, but nothing can read the filesystem  because they are part of a RAID array.

Any advice gratefully accepted. Even if it doesn't work, it might trigger some additional thoughts that would lead to a solution.

---

### Post by John Jason Jordan on 2008-11-17
I finally succeeded in fixing my broken Grub after the upgrade from Hardy to Intrepid x86_64 on a computer with RAID1 setup.

I struggled with a lot of things and read countless pages on the Ubuntu forums and elsewhere trying to figure it out. Eventually I discovered the problem. It seems that the upgrade had upgraded Grub, but only on one of the partitions that was in the array.

The computer has two identical SATA-2 hard disks. Each has a 50 GB partition (sda1 and sdb1) on which Ubuntu is installed. The two partitions are assembled with mdadm into a RAID1 device (md1). The Intrepid update ignored md1 and just installed the new Grub files on sdb1. After I discovered this I used a rescue CD to mount both partitions individually, delete all the files in /boot on sda1 and then copy the files in /boot from sdb1 to sda1. Once I did that the Error 15 messages disappeared and Intrepid booted normally.

For rescue CDs I started with Intrepid, but I was not able to figure out how to mount the individual partitions with it. Then I tried Knoppix, which always automatically mounts all your partitions, but as read-only. (I later discovered that you can mount them read-write, but at the time I didn't know the secret.) Eventually I used the Emergency and Cool Linux CD (Gentoo based). 

I just want to post back here for the benefit of others who have trouble with Grub not finding the files in a RAID.

Edit November 30, 2008: Update Manager said there were new things so I applied the updates, one of which was upgrading the kernel from 2.6.27-7 to 2.6.27-9. Guess what happened on rebooting? Yup. Error 15 again. Am I going to have to go through this every time there is a small kernel upgrade? This computer started with Gutsy and Grub was always correctly updated until I upgraded from Hardy to Intrepid.

---

### Post by stimulus2da on 2008-11-17
> **caljohnsmith said:**
> OK, while you are in the Grub shell, and after you've done the "device" command, try:
```
grub> geometry (hd0)
```
If that shows your five partitions, then type:
```
grub> null (hd0,5)/boot/grub/
```
And hit TAB for tab-completion; that should show your Grub files. If not, you should check if the /boot/grub directory in the isw_bjgiiaibhe_Volume0p6 partition has the Grub boot files.

when I try the device and geometry part this is what I get:

```
grub> device (hd0) /dev/mapper/isw_bjgiiaibhe_Volume0                                                             
device (hd0) /dev/mapper/isw_bjgiiaibhe_Volume0
grub> geometry (hd0)
geometry (hd0)
drive 0x80: C/H/S = 155650/255/63, The number of sectors = -1794448896, /dev/mapper/isw_bjgiiaibhe_Volume0
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7
```

btw, thanks for you help so far.  I really appreciate it.

This lists only 2 of my 4 partitions or I guess it's five?  I only made 4 but the partitioning made a bigger one encompassing a few or something?  I don't know exactly how that works.

---

### Post by caljohnsmith on 2008-11-17
I think I might see at least part of your problem:

[QUOTE=stimulus2da]```
ubuntu@ubuntu:/dev/mapper$ ls
control  isw_bjgiiaibhe_Volume0  isw_bjgiiaibhe_Volume01  isw_bjgiiaibhe_Volume05  isw_bjgiiaibhe_Volume06  isw_bjgiiaibhe_Volume07
ubuntu@ubuntu:/dev/mapper$ sudo fdisk isw_bjgiiaibhe_Volume0 -l

Disk isw_bjgiiaibhe_Volume0: 1280.2 GB, 1280265420800 bytes
255 heads, 63 sectors/track, 155650 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c286c28

                  Device Boot      Start         End      Blocks   Id  System
isw_bjgiiaibhe_Volume0p1   *           1       21672   174078976    7  HPFS/NTFS
isw_bjgiiaibhe_Volume0p2           21673      155650  1076178285    f  W95 Ext'd (LBA)
isw_bjgiiaibhe_Volume0p5           21673      149154  1023999133+   7  HPFS/NTFS
isw_bjgiiaibhe_Volume0p6          149155      155379    50002281   83  Linux
isw_bjgiiaibhe_Volume0p7          155380      155650     2176776   82  Linux swap / Solaris
ubuntu@ubuntu:/dev/mapper$ sudo mkdir /target
ubuntu@ubuntu:/dev/mapper$ sudo mount [COLOR="Red"]isw_bjgiiaibhe_Volume06 [/COLOR]/target
```[/QUOTE]
Above, you mounted the disk volume; shouldn't that be instead the linux partition "isw_bjgiiaibhe_Volume0p6"? Or did I miss something? Also, when you invoke grub, how about just doing "grub" instead of "grub --no-curses". Let me know how it goes.

---

### Post by stimulus2da on 2008-11-17
I tried that, but it wouldn't let me mount the p6 partition.  Says it doesn't exist.
Also, using just grub gives the same problem.

As a point of clarification to make sure I'm doing it right, how do you enable community content?  Also, when installing, I'm using "manual" for the partition setup and using number 6 as ext3 journaling file system and formatting it.  I make it's mount point "/"  and make the number 7 partition swap.

I assume just letting the installer install grub to the Volume0 slot will not work either?

---

### Post by caljohnsmith on 2008-11-17
> **stimulus2da said:**
> I tried that, but it wouldn't let me mount the p6 partition.  Says it doesn't exist.
Also, using just grub gives the same problem.

As a point of clarification to make sure I'm doing it right, how do you enable community content? 
I'm sorry, I don't know what you mean by enable "community content." Can you explain further? 
> **stimulus2da said:**
> 
 Also, when installing, I'm using "manual" for the partition setup and using number 6 as ext3 journaling file system and formatting it.  I make it's mount point "/"  and make the number 7 partition swap.

I assume just letting the installer install grub to the Volume0 slot will not work either?
Using the "manual" option sounds good, but just letting Grub install to Volume0 I'm almost certain won't work, because that's why they have to jump through so many hoops to install Grub in that RAID tutorial. And by the way, have you by chance seen this RAID tutorial:

[http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/](http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/)

And this post is also relevant I think:

[http://ubuntuforums.org/showthread.php?t=972068](http://ubuntuforums.org/showthread.php?t=972068)

In both those tutorials they don't do the "sudo modprobe dm-raid4-5" step that the Ubuntu Wiki tutorial shows. How about skipping that step and go to the partitioning stage right after you do the "sudo apt-get install dmraid" step. It seems like the crux of your problem right now is the partitions are not being set up correctly; you weren't able to mount the linux partition, and also Grub didn't see your partitions correctly either. So after omitting that "sudo modprobe dm-raid4-5" step, I would open up Ubuntu's partition editor:
```
gksudo gparted
```
And use that to delete your existing Ubuntu partitions, and then create them fresh again. Let me know how it goes. :)

---

### Post by stimulus2da on 2008-11-17
By enable community content, I mean step #2 in the fakeraid howto.  Though I doubt that's really the problem.

I'm rather confused as to why when I go into the grub prompt and do the find /boot/grub/stage1 command that it can't find it, but when I exit the grub prompt and list the contents of /boot/grub/, everything is there.

I did try to delete the partitions and remake them from scratch and it didn't change anything. I assume that the isw_bjgiiaibhe_Volume0**6** is the right one (as opposed to the p6 suffix) since that is what is listed when I list what's in /dev/mapper/. 
 
I am rather stumped right now.  I did try some things off those websites you posted as well, and nothing changed.
I'm very thankful though that the worst that's happened so far is that my computer boots straight into Vista.  No change is better than change for the worse eh?

---

