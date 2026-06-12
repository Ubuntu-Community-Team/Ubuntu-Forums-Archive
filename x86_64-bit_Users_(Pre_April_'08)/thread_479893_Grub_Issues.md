---
title: "Grub Issues"
date: 2007-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by civic_si on 2007-06-20
This computer used to dual boot between windows and Ubuntu 6.10. Since I have taken the windows hard drive out and have just the Edgy drive installed as a master now. Unfortunately grub was installed on the xp disk and now the system will not boot. what is the easiest way to get Grub installed on the boot sector of the drive. I need to keep everything that is installed on the machine it is a VMware server that I setup for school use. I have also added a second 160gb drive to hold the images. Any help is appreciated i need to get the machine back up very quickly. I do not have a floppy drive installed in this computer but it will boot from usb drive if needed.

---

### Post by logos34 on 2007-06-20
Boot up the ubuntu live cd, load the desktop, open a terminal and type:

[B]sudo grub
find /boot/grub/stage1[/B]
(enter the output '(hdx,y)' in the next comannd)
[B]root (hdx,y)
setup (hdx)
quit[/B]

---

### Post by phidia on 2007-06-20
Hopefully you have the install cd you can boot from that open a terminal window and type > sudo grub-install hda That should install grub to the MBR but since your drive geometry has changed you probably have to edit your fstab and go into the grub commandline and set up grub.
From the live cd mount your install partition and then chroot into it. Type "grub" at the grub prompt type "find /boot/grub/stage1" that should output something like (hd0,0) Maybe. Normally at this point you type "root" grub then tells you the filesystem if it recognizes one and you can use the drive/partition output to do "setup hdX,X,"
Hope that helps.

---

### Post by logos34 on 2007-06-20
If ubuntu drive was previously slave and you switched it to master then you'll need to edit /boot/grub/menu.lst

And I would put grub on the mbr (hd0) rather than the root partition (hd0,x)

---

### Post by civic_si on 2007-06-20
I have done what both of you have suggested and now it boots to grub. :D But I need to edit something else within grub it is giving me an error code of Error 21: The selected disk does not exist. so then i go back to the grub screen and I hit e to edit the commands and it shows 

(root 2,0)
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/hdd1 10 quiet splash


when I do an fdisk -l that is not the drive I need to boot from.

I will post the fdisk -l screen in a minute i am waiting for the computer to boot to the cdrom again.

---

### Post by civic_si on 2007-06-20
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9726     1486012+   5  Extended
/dev/sda5            9542        9726     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       20673   156287848+   7  HPFS/NTFS

---

### Post by logos34 on 2007-06-20
'e' to edit:

change thus:
[B]
(root [COLOR="Red"]0[/COLOR],0)
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/[COLOR="Red"]sda1[/COLOR] 10 quiet splash[/B]

---

### Post by civic_si on 2007-06-20
thats what i thought ill try that.

---

### Post by civic_si on 2007-06-20
that fixed it. :D thanks I had to edit the menu.lst file using the live cd it would not save the changes if i used e. but thanks alot I have never had this problem before but I wil remember this.

---

### Post by civic_si on 2007-06-20
Just incase somebody else needs to use this I had to change a few things

(root 0,0)
kernel /boot/vmlinuz-2.6.17-10-server root=/dev/sda1 10 quiet splash

I had to change the sda1 to hda1 and everything worked fine. I guess since the hard drive is IDE.

---

### Post by logos34 on 2007-06-20
> I had to change the sda1 to hda1 and everything worked fine. I guess since the hard drive is IDE.

forgot you were using 6.10 edgy...In 7.04 Feisty everything ide is 'sdx'and 'scd'...the devs changed to using the scsi libata driver subsystem for storage devices.  (although I did a test install not to long ago of feisty and my ide drives were still seen as 'hdx'.  maybe that was just the 2.5.20-15 kernel though)

---

