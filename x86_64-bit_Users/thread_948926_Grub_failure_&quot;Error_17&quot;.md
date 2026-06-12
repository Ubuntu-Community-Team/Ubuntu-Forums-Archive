---
title: "Grub failure &quot;Error 17&quot;"
date: 2008-10-15
forum: x86 64-bit Users
---

### Post by BarnabasDK on 2008-10-15
Hi all,

I own a HP 8510w Laptop, that I have used with success with Ubuntu 8.04 for a while.

Today there was a bunch of updates in the queue, among here a new kernel version 2.6.24-21-generic.

After installing this and rebooting as the system told me Grub will no longer start the new linux image or the old one. I have a windows partion on my lappie that works fine.

The actual error is:

**Error 17 - Cannot mount selected partition.**

So the boot sector is there, and Grub loads but now cannot find the partition? I can mount the partition manually when booting of the cd. Its still there.

I have absolutely no idea what went wrong other than some magic in the update process made a mess of the boot setup.:confused:

I think this is the first kernel update I have done on this lappie since there is only two available. The curious thing is that the old one can't boot either. Its seems to me that the file system cannot be mounted by grub all of a sudden.

Here is more info on layout:

**Doing mount:**

ubuntu@ubuntu:~$ ls /dev/s
scd0        sda2        sequencer2  shm/        sndstat     stdin
sda         sda3        sg0         snapshot    sr0         stdout
sda1        sequencer   sg1         snd/        stderr      
ubuntu@ubuntu:~$ cd /media
ubuntu@ubuntu:/media$ ls
ubuntu@ubuntu:/media$ sudo mkdir disk
ubuntu@ubuntu:/media$ mount /dev/sda1 /media/disk/
mount: only root can do that
ubuntu@ubuntu:/media$ sudo mount /dev/sda1 /media/disk/
/dev/sda1 looks like swapspace - not mounted
mount: you must specify the filesystem type
ubuntu@ubuntu:/media$ sudo mount /dev/sda2 /media/disk/
ubuntu@ubuntu:/media$ cat /media/disk/boot/grub/
default            installed-version  menu.lst.bak       stage1
device.map         jfs_stage1_5       menu.lst.bak~      stage2
e2fs_stage1_5      menu.lst           minix_stage1_5     xfs_stage1_5
fat_stage1_5       menu.lst~          reiserfs_stage1_5  

**In fstab:**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=e7d7b510-5dd2-4e64-8d3a-2edf5f8a5f86 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

**Disk layout**

ubuntu@ubuntu:/media$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc51bc51b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1992    16000708+  82  Linux swap / Solaris
/dev/sda2            1993       14150    97659135   83  Linux
/dev/sda3   *       14151       24320    81690525    7  HPFS/NTFS
ubuntu@ubuntu:/media$

**menu.lst**

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows 95/98/NT/2000
root (hd0,2)
makeactive
chainloader +1

---

### Post by briandu on 2008-10-15
it looks like you partition mappings are corrupted.

Boot from lice CD and open terminqal

then:

sudo update-grub /dev/sda3

followed by pwd

and bingo! should be OK again.

That's what I would do.

Cheers.

---

### Post by caljohnsmith on 2008-10-15
It looks like it is just a simple problem with your menu.lst. Your Linux partition is on sda2, which is (hd0,1) in Grub's World, not (hd0,2). So all you should need to do is change all your Ubuntu entries similar to:
```
title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root [COLOR="Red"](hd0,1)[/COLOR]
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5 ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet
```
Probably what happened is your "#groot=(hdX,Y)" line is incorrectly using (hd0,2), which is how the Ubuntu entries in your menu.lst were incorrectly changed when the menu.lst was updated; therefore make sure it is:
```
#groot=(hd0,1)
```
And I think you should be all set. Let me know how it goes. :)

---

### Post by BarnabasDK on 2008-10-15
Is this sort of what you are thinking of doing? SDA2 is the linux part.

ubuntu@ubuntu:/media/disk/boot/grub$ cd
ubuntu@ubuntu:~$ umount /media/disk/
umount: /media/disk is not in the fstab (and you are not root)
ubuntu@ubuntu:~$ sudo umount /media/disk/
ubuntu@ubuntu:~$ sudo update-grub /dev/sda
sda   sda1  sda2  sda3  
ubuntu@ubuntu:~$ sudo update-grub /dev/sda3
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

ubuntu@ubuntu:~$ pwd
/home/ubuntu
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/disk/
ubuntu@ubuntu:~$ sudo update-grub /dev/sda2
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

ubuntu@ubuntu:~$ sudo update-grub /dev/sda2 /media/disk/boot/grub/
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

ubuntu@ubuntu:~$ chroot /media/disk/
chroot: cannot change root directory to /media/disk/: Operation not permitted
ubuntu@ubuntu:~$ sudo chroot /media/disk/
root@ubuntu:/# update-grub /dev/sda3
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "da_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "da_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "da_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# update-grub /dev/sda2
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "da_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "da_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "da_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Updating /boot/grub/menu.lst ... done

root@ubuntu:/#

---

### Post by BarnabasDK on 2008-10-15
Solved:

I do not know why exactly the system update process decided to increment the hd params in menu.lst disregarding the swap partition placed first on the disk. But this is the working boot.lst

Anyway the update process should be smart enough to not set the main linux boot device to point at a filesystem with type NTFS since finding a linuxkernel on it is unlikely in any event :-)

But I am up and running again. :guitar:

Thanks.

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2355cf7f-d8fa-4a33-b041-9e87683a0ee5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows 95/98/NT/2000
root (hd0,2)
makeactive
chainloader +1

---

### Post by briandu on 2008-10-15
you are on the right track


the linux is on /dev/sda2            1993       14150    97659135   83  Linux


this is where your bot is as well
on Live CD open term and state upgrade-grub /dev/sda2 and should be OK as it will rewrite the menu.lst file for you

(I made typo on /dev/sda3)

if upgrade-grub fails then type in apt-get install grub -although it should be there by default.

---

### Post by BarnabasDK on 2008-10-15
> Probably what happened is your "#groot=(hdX,Y)" line is incorrectly using (hd0,2), which is how the Ubuntu entries in your menu.lst were incorrectly changed when the menu.lst was updated; therefore make sure it is:
```
#groot=(hd0,1)
```



You are absolutely right, and since this is the first kernel update on this thing it is also the first failure of the update of the list.

Thanks!

On the other hand - all that console work just made me realize that the screen on this lappe already has a dead pixel - grrr....

Hope HP has a sensible policy about such things.

---

### Post by Staggered Eclipse on 2008-10-15
Hi,

I'm having a similar problem to Barnabas. I downloaded the kernel update this morning, but after I restarted I got the same Grub Error 17 message. I've tried most of the suggestions on this thread but none help. There are a couple odd things happening that lead me to believe that there may actually be a problem on the hard drive that is causing this error.

**Disk Layout:**

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 137.4 GB, 137438953472 bytes
255 heads, 63 sectors/track, 16709 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00056a27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12819   102968586    7  HPFS/NTFS
/dev/sda2           12820       16261    27647865   83  Linux
/dev/sda3           16262       16709     3598560    5  Extended
/dev/sda5           16262       16709     3598528+  82  Linux swap / Solaris

The problem is /dev/sda is a 250G hard drive and my linux partition, /dev/sda4 is missing. I can open linux using my live cd and access all the other partitions on this drive but not my main linux partition. This 100G partition has vanished.

I tried opening /boot/grub/menu.lst but it is on the missing partition. Opening the command ubuntu@ubuntu:~$ sudo gedit /boot/grub/menu.lst
simply opens a blank page.

Further, when Grub loads on startup it tells me to select an operating system. Normally I can choose between Ubuntu and Windows XP, but now there are four copies of linux there and none work. Grub displays Ubuntu Kernel 2.6.24-21 as well as 2.6.24-19, 2.6.24-18, 2.6.24-16.

I can't find anything regarding the missing partition. Even Gparted shows the hard drive as 137G instead of 250, and the partition does not show up. All attempts to access it through the terminal are unable to find it. Any advice?

---

### Post by caljohnsmith on 2008-10-15
Staggered Eclipse, it sounds like you may have your HDD incorrectly set up in BIOS. I don't know what BIOS settings your have related to your HDD, but I would try changing them one at a time and seeing if you can get your HDD recognized as 250 GB again. Some of the settings you may find in BIOS for your HDD are LBA, CHS, AHCI vs. IDE, etc. Let me know how it goes.

---

### Post by Staggered Eclipse on 2008-10-15
Hmm, I looked in to this earlier. Unfortunately my BIOS does not allow me to change my settings for HDD. I assume it detects automatically.

---

### Post by CrystalMoth on 2008-10-20
I hava a siilar problem. My desktop when turned on gets to grub stage 1.5 and then displays a message: "Error 22". I've been able to boot with a live disk but can't boot into my installed ubuntu or windows. I am a total Newb! please help.

---

### Post by caljohnsmith on 2008-10-20
So just to clarify, you get the Grub error 22 before seeing the Grub menu on start up? 

If that is true, go ahead and boot your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Post the output of the above commands, and also post:
```
sudo fdisk -lu
```
Reboot, and let me know what happens on start up. :)

---

