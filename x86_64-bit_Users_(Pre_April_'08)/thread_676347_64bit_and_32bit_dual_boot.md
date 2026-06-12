---
title: "64bit and 32bit dual boot?"
date: 2008-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by rabbit73 on 2008-01-23
Hi all, newly registered but not new to the forums or ubuntu.  I tried searching, but didn't find my exact issue.

Background: I've been running 7.04 32bit since I moved to ubuntu. No issues, runs great, still learning about it but it works and it's stable. Bought a totally new computer, swapped over the hard drive, followed some simple advice in the forums and I'm up and running on the new box. Still totally amazing to me that it worked with just an entry to the fstab and a video reconfig. I read the psychocats guide and successfully created a separate /home partition (which I didn't do during the initial install) as prep for the move to 64bit. 

Now I want to install/upgrade to 7.10 64bit as a dual boot. Tried it on the live CD and it seems great, but I want to keep 7.04 around just like I have it until I'm totally happy everything is working correctly.

My question is can I shrink down the unused space at the end of my new /home partition to create a new place for 7.10? How much space will I need and can that be done as part of the install? Then, assuming all goes well, can I delete the partition at the front of the drive that has 7.04 and backwards expand my /home (toward the front of the drive) to use the space?

---

### Post by Moop on 2008-01-23
Hi, I dual boot 64bit and 32 bit too. You can definitely shrink your /home to make room for a new partition. It will offer you that option during the install process.  A new install is less than 4GB so you probably only need about 6GB.

You could add extra space onto the beginning of your /home but it might cause problems with the uuid and you would need to edit fstab. I'm not to sure. ](*,)

---

### Post by Kilz on 2008-01-23
Ill second that, its a great way to move to 64bit. Just in case some issue pops up you have a working install to fall back to.

---

### Post by rabbit73 on 2008-01-23
Thanks for the replies, glad to hear it will work. I wasn't sure if I could resize the /home in both directions. Time to back up some of the important stuff to DVD and give 'er a go.

---

### Post by tflanders on 2008-01-23
I'm looking to do the same thing. I have already shrank the partitions so I'm all set there. I would  like to install 32bit on the first half of the drive and 64bit on the other. 

No problem there.
My question is when I install the 64bit version do you install grub again?
Or do you _not_ install grub and manully add entries the /boot/grub/menu.lst on the 32bit OS.

I'm just curious how you did it because I often try out other distros and may end up blowing away the 32bit portion and reload another linux OS and have grub find it on installation of the new OS.

To not make it too confusing, I noticed the boot files are named the same for both 32 and 64 bit /boot partitions. Could you paste your working /boot/grub/menu.lst ?

:confused:

---

### Post by rabbit73 on 2008-01-24
Don't know if it helps or not, but here's my menu list:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3f0895cf-a003-42fa-92e7-2a0e27dcde2c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3f0895cf-a003-42fa-92e7-2a0e27dcde2c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cb25bfd2-5640-4c0e-a9cb-6c6f9590cad0 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cb25bfd2-5640-4c0e-a9cb-6c6f9590cad0 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cb25bfd2-5640-4c0e-a9cb-6c6f9590cad0 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cb25bfd2-5640-4c0e-a9cb-6c6f9590cad0 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, memtest86+ (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by macaholic on 2008-01-24
I always have a 32-bit fallback gutsy partition (i run hardy 64 as my main) and I use it whenever 64-bit hardy is giving me issues and i would highly suggest it.

---

