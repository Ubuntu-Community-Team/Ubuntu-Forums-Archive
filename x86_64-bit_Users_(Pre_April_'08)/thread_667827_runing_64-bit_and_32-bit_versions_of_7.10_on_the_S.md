---
title: "runing 64-bit and 32-bit versions of 7.10 on the SAME machine"
date: 2008-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by crgutierrez on 2008-01-14
I have already read and tried to follow an interesting thread on this issue
[COLOR="Black"][SIZE="3"]"fsck check forced on EVERY reboot..."[/SIZE][/COLOR]
*see*: [http://ubuntuforums.org/showthread.php?t=665567](http://ubuntuforums.org/showthread.php?t=665567)
But the comments are really beyond my capabilities (and I expect Ubuntu to be user friendly).

Feisty runs smoothly on 32bit, as well as on 64bit, BUT don expect GRUB to handle it without trouble. In may case the fsck  stops me every time I want to go into the 64-bit version, and i can only get there trough a reboot command. From my feeling of more than two years of Ubuntu use (and dedication, and love and etc. etc.) and those comments, it seems to me that there should be a particular way in partitioning the disk and making the sequential installations to make this work but didn't found the necessary recommendations on that.

So I'm trying with a few simple questions again
[LIST]
[*]can i run both version in the same machine?
[*]should I install one of the version BEFORE the other one?
[*]can both versions share the same /home directory?
[/LIST]

Muchas gracias well in advance

Please see the solution proposed by Herman in the second page of 
[http://ubuntuforums.org/showthread.php?t=665567](http://ubuntuforums.org/showthread.php?t=665567)

The cross check and editing of UUID numbers in /etc/fstab worked for me

---

### Post by Moop on 2008-01-14
I've run both 32bit and 64bit, dual booting and didn't have any problems with grub. I'm using 64bit now and also have a 32bit installation of Mint on this PC. 

I've never tried using the same home directory and I even make sure to use different user names. I don't know that it makes a difference but it helps keeping things organized.

---

### Post by crgutierrez on 2008-01-15
I did use the same user names. Maybe there is the problem. Thanks

---

