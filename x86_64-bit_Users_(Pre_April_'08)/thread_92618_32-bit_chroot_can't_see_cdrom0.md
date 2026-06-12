---
title: "32-bit chroot can't see cdrom0"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by nalmeth on 2005-11-20
Following a very helpful howto on creating a 32-bit chroot environment on my 64-bit ubuntu environment, and succesfully achieving it, I thought I would finally be able to play starcraft through wine, but as my thread post says, my chroot evironment can't read the cdrom. It acknowledges its existence, but cannot locate any files inside.
So I then created a symlink for wine to */usr/local/bin/do_dchroot* and tried to operate from 64-bit environment 
and heres what happens:

[B]nalmeth@ubuntu:~$ wine /media/cdrom0/setup.exe
(breezy) wine /media/cdrom0/setup.exe
wine: cannot find '/media/cdrom0/setup.exe'
dchroot: Child exited non-zero.
dchroot: Operation failed.[/B]

heres my fstab:
[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/home /chroot/home none bind 0 0
/tmp /chroot/tmp none bind 0 0
/dev /chroot/dev none bind 0 0
/proc /chroot/proc proc defaults 0 0
/media/cdrom0 /chroot/media/cdrom0 none bind 0 0
/usr/share/fonts /chroot/usr/share/fonts none bind 0 0[/B]

I tried adding this line to no avail:
**/media/cdrom /chroot/media/cdrom none bind 0 0**

So to summarize, from 64-bit environment I can see the Starcraft CD in /media/cdrom0, but when calling upon it through my 32-bit chroot, it does not appear/operate.

Any suggestions? Any at all? Even the most far-fetched idea will be appreciated and attempted.

Thanks guys and gals
nalmeth

---

### Post by casper_2095 on 2005-11-20
copy the cdrom as a dd image onto your HDD and mount it?

---

### Post by UrbanFallout on 2005-11-24
Hi I've had a similar problem before.

I think its because the chroot environment doesn't automatically mount a new cdrom when you insert it into the drive.

Try jusr manually mounting it (This worked fine for me - but it is a pain):
sudo mount /dev/cdrom /media/cdrom0

If you're still having troubles, try changing "bind" to "rbind" for the /chroot/dev entry in your fstab.

Hope this helps
Nick

---

### Post by nalmeth on 2005-11-27
thanks for replying guys..
I had sort of just given up on this, but both are good ideas.
The second I feel I should of thought of, the first I certainly wouldn't have.
I will try both.
Thank you for ideas

---

