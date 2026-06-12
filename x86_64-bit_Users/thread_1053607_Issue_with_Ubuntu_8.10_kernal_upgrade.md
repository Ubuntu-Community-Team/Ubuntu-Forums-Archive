---
title: "Issue with Ubuntu 8.10 kernal upgrade"
date: 2009-01-28
forum: x86 64-bit Users
---

### Post by -RYknow on 2009-01-28
This is the output of sudo apt-get upgrade...

> ryknow@ryknow-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.27-11-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/23.1MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 148179 files and directories currently installed.)
Preparing to replace linux-image-2.6.27-11-generic 2.6.27-11.25 (using .../linux-image-2.6.27-11-generic_2.6.27-11.26_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.27-11-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.26_amd64.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/System.map-2.6.27-11-generic': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.27-11-generic
Found kernel: /vmlinuz-2.6.27-9-generic
Found kernel: /vmlinuz-2.6.27-7-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.26_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be great! 
Thanks, 
-RYknow

---

### Post by Yellow Pasque on 2009-01-29
> No space left on device
Do you have a seperate /boot partition?

---

### Post by -RYknow on 2009-01-29
The drive is a 320gb drive in my laptop. I have it dual booted. When I set it up, I used a guide and these are the partitions I made. 

512mb for swap
50mb for /boot
and the rest is just ext3.

I'm assuming that either the swap of the /boot is too small, if not both. Is there a way (with gparted maybe?) to enlarge the partitions? I'd hate to start the machine from scratch. It's been running flawless from the start. 

-RYknow.

**Edit**: Looking at Gparted, would appear that the /boot partition has 3.24mb left. I assume that is where my issue lies?

---

### Post by rileinc on 2009-01-29
50MB for /boot is rather small. Installation guides I've seen all have at least 100MB for /boot. I set mine to 150MB just in case. 
Increase /boot size should solve the problem.

---

### Post by -RYknow on 2009-01-29
How would I go about changing the size? Can I do that with Gparted? I'd like to do it undestructively if at all possible...

-RYknow

---

### Post by Yellow Pasque on 2009-01-30
You shouldn't need to resize partitions if you remove at least one old kernel. In your case, I would recommend removing the 2.6.27-7 kernel. You could probably also remove the 2.6.27-9 kernel, but I recommend keeping one old kernel in case something goes wrong with your current one.

For future reference, if you do need to resize partitions, the best way is with a LiveCD that has gparted on it (Ubuntu LiveCd will work). Just make sure your hard disk's partitions aren't mounted before running gparted. Also, beware that moving/resizing partitions will change the UUID and you may need to edit /etc/fstab and/or /boot/grub/menu.lst and paste in the new UUID's that the blkid command gives.

---

### Post by GordonPMartin on 2009-01-31
How does one manage the kernels (deletions).  Is there a good guide on this?

Also, is there a guide about how I might go about multi-booting Linux with a new distro? 

I'm getting tired of all the software that doesn't quite work right in 64-bit - I think it's time to move to 32-bit, but I'd like to have both for comparison purposes...


Thanks,

Gordon

---

### Post by -RYknow on 2009-01-31
Gparted worked like a charm. Thanks guys!

-RYknow

---

