---
title: "Graphics drivers for ATi"
date: 2006-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bishop Hill on 2006-03-07
Sorry for the name of the thread, but I'm dead tired when I'm writing this (I'm also sorry for my spelling and grammar):

I have a HP ZV6000 with an 128 MB ATi Radeon express 200M graphics card which Ubuntu does not support. I get no graphics whatsoever (Ubuntu says something about that it cant load xserver (my graphical hud, gui or whatever it is called) or something).

I DLd the correct drivers from ATi's homepage, and I put them on my 250 gb external FAT 32-formated USB 2.0 drive (I have a dualboot with win XP home,  NTFS formatted, but Windows does not detect the partition). Since I only have the Win DOS-style of Ubuntu thanks to no graphics, it's pretty hard for a guy who fails at Linux to navigate and such (I sure hope I'll leard someday).

The point of the above is that Ubuntu does not find my HD, which contains the driver.

So I called a friend, a 1337 Linux-user who can help me, and he tries a few commands, and after about 5 minuits he understands that Ubuntu does not find the drive (he promised to help me tomorrow afternoon, but I though I'd try here in case he would also fail). 

I Google up something very good about that, but of course I forget what I first typed. The stuff that was good was not only that a guy had found that it is hard to mount an external HD in Ubuntu, but also that it works with a USB-memory. 
So I empty my iPod shuffle 512 mb, I save the driver I need on it and starts Ubuntu. 

So here's my question (all the crap above is mainly info for faster problemsolving):

Can someone help me load the driver of either the HD or the iPod, whichever is easier? I would owe you my.... Something. And I would love you for eternity.

Thanks for this forum /Daniel aka Bishop Hill

---

### Post by jpkotta on 2006-03-07
Is the external HD USB?  If so, do ```
tail -f /var/log/messages
```
Now plug the HD in.  A bunch of stuff should appear in the terminal, including something about a SCSI device sd?, where the ? may be a,b,...  This is the device name of your drive.  Press Ctrl-C to stop tail.  Now mount the drive with ```
mount /dev/sda /mnt
``` assuming you saw sda before.  You should be able to access your HD in /mnt now.  If it doesn't work, post any errors you get.

---

