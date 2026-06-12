---
title: "Post-Linux Mac OS X Install?"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by yhahn on 2005-11-18
Hi there. Just wondering if it's possible to install OS X 10.4 on an HFS partition after having installed Ubuntu. I've got my partitions all set up and Ubuntu is running just fine. Anything I need to look out for if I try to install OS X on my other partition now?

Thanks in advance!

---

### Post by kingler on 2005-11-18
[QUOTE=yhahn]Hi there. Just wondering if it's possible to install OS X 10.4 on an HFS partition after having installed Ubuntu. I've got my partitions all set up and Ubuntu is running just fine. Anything I need to look out for if I try to install OS X on my other partition now?
Thanks in advance![/QUOTE]

Ubuntu uses ext3 partition format, not Apple HFS.
So, you'll have to make sure you didn't use up all the disk space for Ubuntu. 

If you are using 100% of the disk, use partition tools (parted?) to resize the ext3 partition for Ubuntu. And then your OS X Tiger should install just fine.

---

### Post by Joe_lurker on 2005-11-18
I believe that installing OSX will overwrite the boot loader although I am not 100% sure.  If it does you will have to uses your Ubuntu install disk to boot into Ubuntu and run ybin.  You might want to make sure your /etc/yaboot.conf is set to find the OSX partition.

-Joe

---

### Post by felix_stegerman on 2005-11-18
[QUOTE=Joe_lurker]I believe that installing OSX will overwrite the boot loader although I am not 100% sure.[/QUOTE]

It will ! (I just installed OSX after Ubuntu on my iBook).

I rebooted from a Ubuntu PPC Live CD, mounted my partitions in /mnt like this:
# mount /dev/<your_root_device_here> /mnt
# mount -t proc none /mnt/proc
(If /usr, /var and/or /tmp are on separate partitions, mount those too)
and chrooted to /mnt:
# chroot /mnt
and then I just ran
# ybin -v
to restore yaboot.

Then I "exit"ed the chroot, unmounted the partitions I mounted and rebooted.


Felix

---

### Post by yhahn on 2005-11-18
Hmm, will heed when I install OS X.

Many thanks!

---

### Post by autocrosser on 2005-11-19
The other thing you can do after install is: boot into open-firmware--Option key during boot & select your Linux partition--this will re-set you path to Ubuntu--I Apple>Option>P>R (hold all four keys down at the same time) a couple of times during boot to reset the PRAM--OSX sets a "new" path during install in the PRAM that you need to clear.

---

