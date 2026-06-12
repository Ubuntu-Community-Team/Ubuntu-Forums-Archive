---
title: "numerous problems DOH!"
date: 2008-06-17
forum: x86 64-bit Users
---

### Post by MrBucket101 on 2008-06-17
okay, so i've recently installed ubuntu, i like it but i dont think im going to give up on windows

anyways, sometimes when i restart the machine or turn it on, grub will hang.

The screen will pop up saying that grub is loading please wait... and then there is like an underscore underneath it

at this point, nothing works, not even ctrl+alt+del. The only way i can escape this issue is by holding down the power button on my laptop for 5 secs IE a hard shutdown. At next reboot it just magically starts working again...its odd but very annoying


i have startup manager installed, and the only tweaks i have made are, changing the res on to 1024x768, adding some color, and setting windows as my default boot
-------------------------------------------------------------------
I'm also having trouble with my external NTFS hard drive, i've read somewhere that if it wont mount that i need to force it but last time i tried that it only mounted one partition, 

i have ntfs-3g config installed as well as kdiskfree, i cant seem to browse my files...

they appear to be mounted now... meaning i can browse them, but i was looking for a fix so if windows accidentally forgets to clean up or safely remove
------------------------------------------------------------------------

I appreciate any help i may get. Thanks guys


PS: i saw a lot of users requesting the output of sudo fdisk -l so here is mine ahead of time...not sure if it helps

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       12161    15759765    5  Extended
/dev/sda5           10200       10264      522081   82  Linux swap / Solaris
/dev/sda6           10265       10872     4883728+  83  Linux
/dev/sda7           10873       12161    10353861   83  Linux

---

### Post by MrBucket101 on 2008-06-25
I erased my linux partitions, did a fixmbr then resized my HD again and reinstalled linux and i am having the same problems...something is not right here

can anyone please help

---

### Post by pixel :-) on 2008-06-26
This part of the forum is for 64 specific stuff,you would have better luck in [http://ubuntuforums.org/forumdisplay.php?f=332]("http://ubuntuforums.org/forumdisplay.php?f=332")

grub will hang.
the default settings are they working corectly?

Post as an attachment of /boot/grub/menu.lst
It may be useful

Is it a sata,it appears that they are problems booting with satas.

-------------------------------------------------------------------
external NTFS

Reformat,is it a option?As Fat?Is't big?It's for backup?
Fat is less efficient,in various aspects.For ext3 you need to install a driver for windows, and in general other PCs will not be able to acces it.

 they appear to be mounted now... meaning i can browse them, but i was looking for a fix
how did you mounted them,with force?You can make a little script that automates the prosses and add it on the menu/Desktop.

---

