---
title: "reinstalling feisty 32bit from 64bit"
date: 2007-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by misterf1 on 2007-09-18
Hello all.  Quick question and probably a silly one.  I've installed fiesty 64bit (as described in my signature) and it has gone into a loop that I can't get out of.  I would imagine it has something to do with Compiz.  So, to make a long story short, I was wanting to put 32bit fiesty on my system in order to have all the eye-candy and useability back in place.  I loved the idea of 64bit and where it is/will be going.  But I was hoping to find a Catia/Pro-Engineer/Solidworks/Matlab sort of solution available for Linux and I haven't been *that* impressed.  So, I've got the swap partition, the home partition and the OS partition on a dual boot XP using Grub.  Anything I should know before I pull the plug?  Thanks all, I'm loving Linux and can't wait to be windows free.

---

### Post by dabl on 2007-09-18
Assuming Windows is the only other OS on that system, it should be no major problem to just install the new OS in the same partition where you have the 64-bit OS installed now.  It will put Grub in the same place that it is now, and write a new boot menu that has Ubuntu first and Windows "below the line", same as it is now.  During installation, mount the swap and /home partitions same as they are now, and make sure you set the /home partition NOT to reformat.

A minor issue is that the settings that are in your /home partition will probably leave you with some non-functional stuff (from the prior configuration), but you can just send them to trash.  :)

---

### Post by Kilz on 2007-09-18
> **misterf1 said:**
> Hello all.  Quick question and probably a silly one.  I've installed fiesty 64bit (as described in my signature) and it has gone into a loop that I can't get out of.  I would imagine it has something to do with Compiz.  So, to make a long story short, I was wanting to put 32bit fiesty on my system in order to have all the eye-candy and useability back in place.  I loved the idea of 64bit and where it is/will be going.  But I was hoping to find a Catia/Pro-Engineer/Solidworks/Matlab sort of solution available for Linux and I haven't been *that* impressed.  So, I've got the swap partition, the home partition and the OS partition on a dual boot XP using Grub.  Anything I should know before I pull the plug?  Thanks all, I'm loving Linux and can't wait to be windows free.

You do understand that the 32bit version is not perfect. That you may have the exact same problems you have now and no benefit from all the work. 3d desktop problems are common in 32bit as well. That you will have to wipe out the 64bit install and reinstall the 32bit version.

---

### Post by saru411 on 2007-09-18
COMPIZ IS ALPHA SOFTWARE! it will break your machine. it will possibly break when installing other software! IT WILL DO THIS EVEN ON 32BIT!!! changing the o/s will not fix your problem. you are new and have screwed something up. dont blame it on the o/s ask for help it the correct forum(the one about desktop effect) and someone will help you fix your mess.

---

