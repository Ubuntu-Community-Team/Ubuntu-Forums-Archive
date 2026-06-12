---
title: "Does firewire work in 5.10?"
date: 2005-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by danderso on 2005-11-04
I just installed 5.10 on a blue and white g3 powermac, and I cannot seem to recognize my Lacie firewire drive.  Any ideas?

---

### Post by autocrosser on 2005-11-04
Firewire works just fine in breezy--I have a cd burner & two external drives setup this way--look thru your / directory for /media---could be listed as ieee1394disk or sda1--I have a mounter in one of my panels--right click on a panel>add to panel>System & Hardware>Disk Mounter---Also look at /etc/mtab to see if it was found during boot.

---

### Post by danderso on 2005-11-04
Hmm, nothing seems to have shown up in /media except for cdrom.  What should I be looking for in /etc/mtab?  I see an /dev/sda3, but that is my internal harddrive.

---

### Post by craks on 2005-11-04
[QUOTE=danderso]Hmm, nothing seems to have shown up in /media except for cdrom.  What should I be looking for in /etc/mtab?  I see an /dev/sda3, but that is my internal harddrive.[/QUOTE]
you may try lsmod to see if ieee1394 and ehci1394 is in the list. if not, you should modprobe it manually, and see dmesg, if any error occurs, that will help you to find the problem, and you can paste it here

---

### Post by Jason-X on 2005-11-04
I have a Lacie external firewire drive and it works just fine in 5.10. Here's the line from my **/etc/fstab** file relating to the Lacie drive:

> /dev/sda3              /media/lacie    ext2 noauto,user,rw     0       0

I created a directory in my media directory to mount the drive:

> sudo mkdir /media/lacie

Hope this helps:smile:

---

