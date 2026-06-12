---
title: "!!!HELP!!!  booting win and ubuntu"
date: 2006-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Uhospaghetto on 2006-06-04
nOOb here... 

i backed up everything on my computer and decided that i wanted a dedicated 25gig for ubuntu and the rest 55gig for my windows... my kid had messed up win anyway so i wanted a clean install for diffrent reasons... so i installed windows on the entire drive, then i used the 64bit ubuntu install dvd that i had downloaded... installed... rebooted then.... kazammm no boot system found... so... bummer... wtf... went to reinstall windows and i went to delete the partitions that were on there, 3 i think... one for win and two for ubuntu - went to remount and it couldnt... im frustrated... please help me... i want to install win and ubuntu, i need some kind of linux for school and im lost... again, im a noob at linux so any help is in great need....

Spagg

---

### Post by PhoenixP3K on 2006-06-04
If I understand correctly. You have a 80GB hard drive. You want to dedicate 25GB to Ubuntu and 55GB to Windows. You need to make a clean install of Windows, it will use the hole hard drive. Then what I usualy do is use a Windows Partitionner to modify the Windows partition from 80GB to 55GB. The rest of the space I usualy format it as FAT32. After the resize and reboot I should boot into windows and see my C: now at 55GB and a new letter drive appear at 25GB. 

Next up is using "Linstall" CD and tell Ubuntu to use the hole 25GB you dedicated to Ubuntu. Since it's the same hard drive / a virtual partition you shouldn't have any booting problem, GRUB installer will detect your Windows installation and automaticaly add it to the GRUB booting screen. All you'll have to do is change the default later on.

---

### Post by Uhospaghetto on 2006-06-04
ok that makes sense... now how the heck am i supposed to make windows mount again... im getting all kinds of stuff from blue screen of death to it just saying that the drive is not connected... any suggestions...
thanks
spagg

---

### Post by Uhospaghetto on 2006-06-04
ok nevermind that last post, i went into winboot and did repair and did fixmbr, that solved the problem... now just getting ubuntu to boot and be an option... that didnt happen last time...

---

### Post by jrobbio on 2006-06-04
With the grub boot system there is a list file in /boot/grub called menu.lst that you can edit within Ubuntu (but not Windows).  I changed the order of mine so the Windows boot was the first option followed by Ubuntu so that the others using the machine don't get confused with my sandbox system.

JR

---

