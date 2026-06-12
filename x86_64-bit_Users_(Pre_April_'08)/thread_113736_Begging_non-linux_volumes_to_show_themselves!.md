---
title: "Begging non-linux volumes to show themselves!"
date: 2006-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by rubeole on 2006-01-07
I'm on a G4 MDD FW800, running Mac OS 10.3.9 and (just started) Ubuntu 5.10.

I have two drives:
Drive 1: All data-type files in three partitions - no bootable OS. Formatted HFS.
Drive 2: The Mac OS on one partition, Ubuntu in the other.

I have looked all over, but I can not find the command or means of using the appropriate utility to allow me to mount my data drive ("drive 1") on my nice, brown Ubuntu desktop. 

I am sure this is the most remedial question, so I hope the answer is simple as well. I apologize for it!

Thank you,

James.

---

### Post by dombleu on 2006-01-07
My installation of breezy ( upgraded now to dapper drake ) did not show my HFS+ partition. I got to add by myself a line in /etc/fstab about that partition. Mine looks like this:

/dev/hda5       /media/osx       hfsplus       defaults,umask=0000       0       0

Maybe you can get it mounted through the disks manager located in System/Administration but I had no lock with it. But at least i got my partition numbers showing in it.

so edit /etc/fstab and do a

sudo mount -a

and you should be done

man mount and man fstab had been really useful to me understanding what is happening with that fstab file.

---

### Post by rubeole on 2006-01-07
Yeah - I could see the HFS+ disk & partitions in disks manager, but could find no way to move things around using that utility.

I'll try out your suggestions as soon as I can (and I thank you for them!) but as soon as I finished that first post, I found some serious directory corruptions on my Mac OS partition - so I've got to deal with that business first. I am hoping this is unrelated to the Ubuntu install...

Again, thanks.

---

### Post by jleedev on 2006-01-07
It's also important to know that a drive will only show up on the desktop if its mount point begins with "/media".

---

