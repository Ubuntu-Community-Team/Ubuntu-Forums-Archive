---
title: "Trouble installing 9.04 and booting it from 500gb usb external hd"
date: 2009-05-14
forum: x86 64-bit Users
---

### Post by j0hnnya on 2009-05-14
Not sure if I should be posting here or in the installation area, but I'm using 9.04 64bit, so let me know if this ain't right.

OBJECTIVE #1:  To boot Ubuntu 9.04(64) from my 500GB external USB hard drive (WD Passport Essential) on any computer (whose BIOS allows it).  In short, I want to use my external HD like a mobile computer, using everyone else's hardware :)

NOTE:  I've removed ALL other HD's from my computer before doing this so it will only boot to the CD or this external HD.  I didn't feel like messing up my boot loaders :)

I have been able to do this intermittently.  I set up three partitions:  1) Primary using the "/" directory using about 10GB - 2) 2GB Swap - 3) 400GB+ as "/home" (which is where I think I'm messing up, but we'll get to that in a min.)

It boots, then it doesn't, sends me to unfamiliar menu's (somewhat of a n00b to Linux, but learning...), then it boots, then it just turns to crap.  So I reinstall, this time won't boot to shell.  Repartition, nothing.  Wipe the whole GD thing out, repartition using the install disc, it works, but only for couple of times.

My big concern here - is it possible that using an external HD to boot is a bad idea?  If it's bumped during any point it'd prob have a high likelyhood of f-ing up, right?  I mean a spinning disc on my lap, chair, etc may not be such a hot idea.  (You can tell me that it's for storage only and I'm an idiot for trying).

I guess even after familiarising myself with the directory structure of Ubuntu I still just don't get it.

This is what I *imagine* I want on the HD:
1st Partition - /boot
2nd Partition - swap
3rd Partition - /home

BUT, do I (and could I) have the 1st and 3rd BOTH be primary partitions?  I would also like to plug this HD in (to let's say my Ubuntu desktop computer) and use it simply as storage, or be able to transfer things onto it from the desktop, just like a regular external HD (this is where I had problems accessing it because of permissions, and don't get me started on the GD f-ing "lost+found" file!  Makes my OCD flair up!)

OBJECTIVE #2:  Can I do all of this using simple, but good encryption?

I would love to go up to any computer, plug in and boot off of this HD into Ubuntu or booted to a password prompt due to the encryption.  Once through to the Ubuntu I would like to have the 400+ partition also be hidden (not sure what this entails).

If someone steals or tries anything fully with my HD, I want them at best to only tell that I have the boot, swap, and whatever partitions, but not the 400GB.

I know this is a long post, when I get better I'm sure I'll be able to truncate a lot of this stuff.

All of your help is extremely appreciated!

j0hnnya****

---

