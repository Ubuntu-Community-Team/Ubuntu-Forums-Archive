---
title: "upgrade to 64 bit"
date: 2006-08-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrw on 2006-08-27
I've installed Ubuntu 386 - is it possible to upgrade (replace) it to the 64 bit version without doing a clean install?

---

### Post by hopstah on 2006-08-27
short answer - no

---

### Post by mrw on 2006-08-27
Thanks, I thought so.

---

### Post by mrw on 2006-08-27
As a follow up: what's the best approach on a dual windows/Ubuntu installation. Should I just install the 64 bit erasing the previoius partition or will that cause me some Grub problems?

---

### Post by Kilz on 2006-08-27
> **mrw said:**
> As a follow up: what's the best approach on a dual windows/Ubuntu installation. Should I just install the 64 bit erasing the previoius partition or will that cause me some Grub problems?

You could do a tripple boot install and leave the 32bit partition alone while you setup and test the 64bit one. If you have the hard drive room.

---

### Post by mrw on 2006-08-27
I think that's what I'll do, I assume I will be able to access the 32 bit partition from Ubunut 64. If thinks work out there will just be question of how to delete and cleanup the old version.

---

### Post by Kilz on 2006-08-27
> **mrw said:**
> I think that's what I'll do, I assume I will be able to access the 32 bit partition from Ubunut 64. If thinks work out there will just be question of how to delete and cleanup the old version.

All you would have to do is delete the partition to remove the install. The 32bit partition should mount, if not its easy to do, that way you can copy over files. 
Also if the 64bit install doesnt work, you could remove it and still have the working 32bit setup. You might have to fix grub if you install it to the 64bit partition. But thats easy to do with an install disk and the rescue install option.

---

### Post by mrw on 2006-08-27
> **Kilz said:**
> All you would have to do is delete the partition to remove the install. The 32bit partition should mount, if not its easy to do, that way you can copy over files. 
Also if the 64bit install doesnt work, you could remove it and still have the working 32bit setup. You might have to fix grub if you install it to the 64bit partition. But thats easy to do with an install disk and the rescue install option.
Tell me more about the "rescue install" option.

---

### Post by Kilz on 2006-08-27
> **mrw said:**
> Tell me more about the "rescue install" option.

If you install the 64bit partition, Ubuntu will set up grub in that partition. It will give entries for the existing installs like winedows, and the 32bit Ubuntu. It will setup grub in the master boot record to point to those files in the 64bit install. 
If you descide that you dont want 64bit, you would delete the partition. The files that grub in the master boot record is pointing to will no longet be there.
But the files from the grub in the 32bit install can be used. By poping in the i386 install disk and booting it you will see an option "rescue install" select that and it will automaticly repair grub to point to the files in the 32bit install.

---

