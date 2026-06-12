---
title: "no scsi devs on breezy old world mac"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by tonyB on 2005-12-12
I've been trying to get Breezy installed on an old world mac.  Initially I had problems with scsi naming during install, but that seems to have gone away with the latest install cd.  I have Hoary on one external scsi drive, and I installed Breezy on another external scsi drive (used to hold Warty) last night.  Everything seemed to go as expected, but when I tried to boot into Breezy via Xboot I got the infamous busybox after a message saying it could not find /dev/sdc8, the partition holding Breezy.  There are indeed *no* scsi devices in /dev, neither sda nor sdb.  I looked through the forums but did not find anything that helped.  Any suggestions on what I might try?

My system:

Mac 7300 w/ G3 upgrade (appears to be a 7500)
350Meg RAM
internal 2GB has Mac OS
external 4GB has a Mac partition and initial Breezy install
external 9GB has Hoary

Also has USB: mouse, DVD, backup disk

Thanks for your help.

tonyB

---

### Post by stuporglue on 2005-12-12
This tutorial isn't very polished, but might be helpful. 

[http://stuporglue.org/oldworld.php](http://stuporglue.org/oldworld.php)
edit: The new url is [http://stuporglue.org/initrd.php](http://stuporglue.org/initrd.php)

I wrote it about a month ago, and will polish it up some when I get to the next OldWorld Mac in my closet. :-) 

Basicly, you have to modprobe the right drivers, then chroot to the root disk (which will show up after modprobing the drivers), rebuild the initrd, copy it over to the HFS partition, and reboot. Easy, right? :-D

---

### Post by tonyB on 2005-12-12
[QUOTE=stuporglue]This tutorial isn't very polished, but might be helpful. 

[http://stuporglue.org/oldworld.php](http://stuporglue.org/oldworld.php)

I wrote it about a month ago, and will polish it up some when I get to the next OldWorld Mac in my closet. :-) 

Basicly, you have to modprobe the right drivers, then chroot to the root disk (which will show up after modprobing the drivers), rebuild the initrd, copy it over to the HFS partition, and reboot. Easy, right? :-D[/QUOTE]


Polished or not, it shines like a beacon in the dark for me. :)

It's almost there but not quite.  A couple of things different for me.

1. In addition to the modules you listed I also had to modprobe mac53c94.  mesh only found the internal hd and the cdrom; mac53c94 picked up the external drives.  I stumbled across that when installing breezy.

2. Everything else went as you describe until I tried to update the modules file.  I don't have an /etc/mkinitrd dir, but there is a modules file in /etc, and it listed all the modules (plus a couple) except for sd_mod.  I included a line for it.

dpkg-reconfigure failed, however, with a rather lengthy message.  The gist of it was: depmod failed with a sig 127 and dumped.  Something was misconfigured.  It did not delete the file
/lib/modules/2.6.12-9-powerpc/modules.dep, and recommended aborting at that point.  I aborted.  I also tried running it without the sd_mod lin in /etc/modules, and it failed the same way, so I think there must be something else awry.

I grep'd that file for the modules I used to get the disks found, and they all were in there.  I floundered around a bit trying to find something else to do but no joy.  The only thing I can think to do at this point is to save a copy of the modules.dep file and let the dpkg-reconfigure continue.  I'm not too hopeful about that, however, so if you have any more suggestions I'm ready to try them out first.

And finally, THANKS!  Your site has been a big help.

Regards,
tonyB

---

### Post by tonyB on 2005-12-13
Well, I'm happier than a pig in a pile of poop.  After hunting around to see what the problem was with dpkg-reconfigure I gave up and let it run to completion.  Copied the new initrd file to the mac, and it came up just fine.  An hour or two later the install completed :), and I'm posting this from inside Breezy.

Many thanks Stuporglue.  There is no way I would have ever gotten this done without your help.

Regards,
tonyB

---

### Post by stuporglue on 2005-12-14
I finished up the tutorial on creating a new initrd.img for Ubuntu a bit more and made it a little less Mac specific. I'm posting the link here in case anyone comes along later and needs help. 

[http://stuporglue.org/initrd.php]("http://stuporglue.org/initrd.php")

---

### Post by tonyB on 2005-12-22
Not to embarrass myself, but even though I got Breezy installed thanks to stuporglue's site, I really got the wrong idea about what needed to be done.  I *thought* I had to change /etc/modules, but when I had to re-install Breezy last weekend, that didn't work.  The changes are to the file /etc/mkinitramfs/modules.  stuporglue's site says it's in -- I think it was -- /etc/mkinitrd/ but I don't have that dir.  Whatever dir you have like one of those should work.

tonyB

---

