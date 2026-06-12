---
title: "Ubuntu not booting..."
date: 2008-10-07
forum: x86 64-bit Users
---

### Post by oaktree on 2008-10-07
Hello All,

I am completely new to the Ubuntu bandwagon. So my questions may not be very clear but any help here I would really appreciate.

I installed Ubuntu 64 bit latest edition(8.04) on my Q9450 CPU, PC. It already had Win XP installed. I had some unused partition on the same drive XP was installed. I installed Ubuntu on that unused space. Everything went fine. I could dual boot. I then tried playing with the desktop display settings and chose some options to enable more skins..Idont beleive exactly. Ubuntu prompted me to install some drivers automatically and I restarted after the installation. Since then I am unable to boot into Ubuntu..It only says "Kernel is alive" and on the next line says:
"Kernel direct mapping tables upto 1400000000 ..."

I tried recovery mode it always stops at some line and doesn't do anything. I tried the live CD but again I get just the command prompt no display. 

If i delete the partition and start all over again..will I disturb the XP booting...

Please suggest what could be wrong...

CPU: Q9450
Video Card: XFX GeForce 8600GT 512MB 128-bit DDR2 540MHz PCI-E Dual DVI/TV-Out SLI Ready Video Card


Thanks in advance...!

---

### Post by Kevbert on 2008-10-07
If you just re-install over the top of the faulty Ubuntu install it will set up the grub boot menu again and you'll be able to dual boot. The windows partition will be untouched.  I normally just delete the old partition, create a new partition in the same space and go from there. Do this via manual partitioning remove the old Ubuntu one and then create a new one making sure the format box is ticked. Mount point is / partitioning should be ext3.  Your swap partition should be ideally twice the amount of ram in the PC.

---

### Post by oaktree on 2008-10-07
Or can I delete the partition in Windows, I have partition magic windows version. So i thought it would be easier to do it in Windows.

But Iam wondering the root cause of this problem, could it be that the video card does not have good 64 bit support...?

---

### Post by Kevbert on 2008-10-08
You could, but it's probably better to do it as part of the CD install process. Your nvidia card is supported, but there have been loads of changes recently with nvidia drivers. Have a look at this [COLOR="Red"][post]("http://ubuntuforums.org/showthread.php?t=57368")[/COLOR].

---

### Post by wfp on 2008-10-08
Correct me if i am wrong but if he removes the partition in windows and grub is installed, will he not have problems booting into windows again because of his windows mbr. I think it would be safer just to use the live cd and delete the partition, reformat that partition then install ubuntu on the new clean partition.

---

### Post by Kevbert on 2008-10-08
The windows mbr has been overwitten by grub, so it's safer to delete partition and re-install via the CD.  The install of a new Ubuntu will write a new grub/boot sector and will see Windows XP and add it to the mew grub menu.  In the case of Vista things would be different.

---

### Post by oaktree on 2008-10-08
Thank you everybody for your valuable suggestions..I will try and keep you posted on what happens..

Thanks!

---

### Post by oaktree on 2008-10-23
Hello Guys,

I tried reinstalling ubuntu, I deleted the old partitions manually, created new ones:

Here's what I created 

Created a ext3 180GB for /
Created a swap 3GB (I have 4 GB RAM)

Everything installed properly, but when I boot, I only get a intramfs prompt and no graphics console. 
I tried recovery mode, it stops at random places and after a long gap gives me the message below:

*************************************************************************************************
check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules/ ls /dev

ALERT! /dev/disk/by-uuid/1b2e7503-830e-4371-816a-8a4409b32aae1 does not exist, dropping to Shell!
*************************************************************************************************

It then gives me a propmpt but no graphics login screen.

At the time of installation I had my MagicJack USB phone plugged in, may be this has anything to do with it...
I am just guessing...any thoughts..pls help...!!..:(

---

### Post by oaktree on 2008-10-24
bump!!!

---

### Post by phlembob on 2008-10-24
If I understand correctly, your Windows still works and it wasn't touched.  Ubuntu 8.04 Live CD always will put a kernel on the HDD which will say live kernel with RAM address.  Without removing anything, reboot from the Live CD.  Install Ubuntu is what you select.  You now have format options, do not touch the Windows section because it is working.  Select the remaining Ubuntu area and let it install from its default.  This will eliminate any human error in the format.  You will see grub afterwards with Ubuntu first choice.  You can select it or let it default within 10 sec.  You will read live kernel with memory location.  It may take up to 1 minute to get the sign in page.  If after a certain time frame it doesn't go to login for ubuntu, check your windows to make sure it is working and get back to us.
:guitar:

---

### Post by oaktree on 2008-10-25
Thanks phlembob, for your answer!...yes my Windows boots up fine..I tried what you suggested but there are still problems..When I tried to reinstall using the live CD, in the partition menu, I cannot see any partitions at all. It is all empty and I am unable to move ahead with the installation...Could it be a HDD problem..I am really stuck..Any thoughts?

---

### Post by oaktree on 2008-10-25
Can i delete the ubuntu partitions from my Windows..I am just worried that may not boot Windows..Is there a safe way to fix the MBR and then remove everything related to ubuntu..and start over.

---

