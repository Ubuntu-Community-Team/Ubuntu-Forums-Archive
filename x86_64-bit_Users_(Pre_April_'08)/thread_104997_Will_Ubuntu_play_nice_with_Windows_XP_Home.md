---
title: "Will Ubuntu play nice with Windows XP Home?"
date: 2005-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mercurybird on 2005-12-17
I have an extra PC to install Ubuntu on once the CDs get here. But what about installing it on my 64-Bit AMD Windows XP Home machine? Will it install along side Windows and give me a choice upon each boot to Linux, or no to Linux? I don't want to crap out my Windows system. But if its made to do that then I'm game for it. \\:D/

---

### Post by Ted D. on 2005-12-17
Works fine on my Intel machine. However, I have Ubuntu on a a slave drive that was been reformatted before installing Ubuntu.

---

### Post by dcast on 2005-12-17
It will do all that right away after the install without doing anything or at least it should

---

### Post by Suger on 2005-12-17
Yes, you just need a free partition and it works like a charm. Only drawback : after 3 weeks, I was so satisfied with Ubuntu I completely removed Windows ;)

---

### Post by openmind on 2005-12-17
[quote=Suger]Yes, you just need a free partition and it works like a charm. Only drawback : after 3 weeks, I was so satisfied with Ubuntu I completely removed Windows ;)[/quote]


LOL! Yeah, same here.:D

---

### Post by grsing on 2005-12-18
As long as you get the partitions right (I'm guessing the Windows box is probably all one partition now, and you'll have to make one for Ubuntu, or just install another HD, which is the better but more expensive option), it should work fine; I recently installed Ubuntu on the same HD as a Windows installation that's been there for about 6 months, went quite smoothly.  Just be very careful in setting up the partitions not to reformat your Windows.

---

### Post by Mercurybird on 2005-12-18
[QUOTE=grsing]As long as you get the partitions right (I'm guessing the Windows box is probably all one partition now, and you'll have to make one for Ubuntu, or just install another HD, which is the better but more expensive option), it should work fine; I recently installed Ubuntu on the same HD as a Windows installation that's been there for about 6 months, went quite smoothly.  Just be very careful in setting up the partitions not to reformat your Windows.[/QUOTE]
Okay will do. Yeah the XP box is all one partition. I'm going to do a backup before I launch it all. My understanding is that Ubuntu comes with a disk partitioner. It's reported to work very well. Looking forward to it.

---

### Post by sabredog on 2005-12-18
I am in the same boat and am ready to install Ubuntu on a recently acquired 20GB HDD that will be installed into my spare Duron running WinXP SP2.

Is it best to re-partition using Fdisk? Say two 10gb partitions on the new 20GB? That would be 1 partition for installed Ubuntu and another for a shared data disk.

Would I need to format both partitions to Fat32 as well, prior to installing Breezy or will the install format the partitions for me?

I assume that the install will recognise and set up XP as a boot option.

---

### Post by Suger on 2005-12-21
Use Fat32 for the shared partition (or install an ext2 for Windows utility...), leave the Ubuntu partition alone, the installer will put it in ext3 all by itself.

---

