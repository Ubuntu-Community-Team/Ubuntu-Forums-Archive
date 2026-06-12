---
title: "Uninstal question"
date: 2006-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Disabled20240622 on 2006-05-30
OK...

I have a Laptop running Ubuntu 5.10 and Windows XP Pro with the Grub boot loader.


I'm selling the laptop so I need to remove Ubuntu and the boot loader and leave XP. I'll then use the built in recovery system to restore it to factory settings.




My question is how do I get XP to boot automatically after I've removed the boot loader?

---

### Post by jbrader on 2006-05-30
It seems to me that using the recovery disk should do all that for you.

---

### Post by Kilz on 2006-05-30
[QUOTE=BigglesPiP]OK...

I have a Laptop running Ubuntu 5.10 and Windows XP Pro with the Grub boot loader.


I'm selling the laptop so I need to remove Ubuntu and the boot loader and leave XP. I'll then use the built in recovery system to restore it to factory settings.




My question is how do I get XP to boot automatically after I've removed the boot loader?[/QUOTE]

If for some reason the recovery disk doesnt, you could go here [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm) download the win98 boot disk maker while in the windows XP, make the disk, put it in the drive , reboot, type in fdisk /mbr at the a: prompt and hit enter.

---

### Post by Disabled20240622 on 2006-05-31
Eventually I did this:


Slap XP disk in and boot from it.

Press any key to boot from CD.

Press R to enter the recovery console.

Log on to the main XP installation.

enter the command: fixmbr

Reastart and boot from the Ubuntu Live disk.

Delete the Partitions Ubuntu used (To unmount the swap file you need "sudo swapoff /dev/hd[hard drive letter][partition number]").

Do what you want with the new hard drive space.

Restart and XP will load streight up.

---

