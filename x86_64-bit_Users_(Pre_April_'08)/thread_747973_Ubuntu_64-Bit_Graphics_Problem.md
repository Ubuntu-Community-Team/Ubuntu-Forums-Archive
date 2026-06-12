---
title: "Ubuntu 64-Bit Graphics Problem"
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by madvic on 2008-04-07
Hi, I have Asus F3SA, I've installed Ubuntu 64-bit, but i configured my graphics wrong and now my screen looks strange, i can't see anything, and i am new at linux, how can i fix this problem? I've tried to re-install ubuntu but i wasn't able to install it =( i don't want my recovery partition and the partition that has vista installed to be deleted =( how can i fix ubuntu or uninstall without deleting my other partitions? I've attached pictures to the post

---

### Post by ajmorris on 2008-04-07
hi there,
We should be able to do this, without re-installing ubuntu, however, if worst comes to worst, you can re-install it without losing all of your other partitions. Can you see the grub menu (the boot loader when you turn on your computer where you can choose to boot the various ubuntu kernels, or windows, if you have windows installed), if so, choose the recovery option from the menu. If you cannot see the grub menu, boot into the ubuntu live cd, and mount your ubuntu partition. the command '```
sudo fdisk -l
```' can tell you your device block number, so you can do the following:

```
1) sudo su  (puts you as root so you no longer have to use sudo
2) fdisk -l
3) mkdir /media/ubuntu
4) mount /dev/<device for your ubuntu partition (step 2 will tell you what it is, if you cant figure out which one to use, just ask)> /media/ubuntu
5)chroot /media/ubuntu
6)export PS1="(chroot) $PS1"  (this command add (chroot) out the front of your user@hostmask in case you open more than one terminal, you can tell which one is your chrooted environment.)
7) (make sure this is from your chroot terminal) dpkg-reconfigure -phigh xserver-xorg (you can remove the -phigh if you would like to be asked more questions)
8) after number 7 has been completed, do exit
9) exit again if you have to, i.e. if the first one did not exit from the chroot environment
10) reboot, and see how your screen looks now. 
```

---

### Post by felker2 on 2008-04-07
Two possibilities:

If your Ubuntu is still there and you can boot it, and your screen is garbage, reboot Ubuntu and select the second boot option: Safe Graphics. Then select something like "repair X server".

If your Ubuntu cannot boot anymore, put in the live/install CD and boot it. After booting it, start the Install Procedure, and in the 3th/4th screen saying "Partition" or something like that, select the Manual option: select the partition to which you want to install Ubuntu.

HTH

---

### Post by prshah on 2008-04-07
> **madvic said:**
> Hi, I have Asus F3SA, I've installed Ubuntu 64-bit, but i configured my graphics wrong and now my screen looks strange, i can't see anything, and i am new at linux, how 

looks like a refresh rate issue... try ctrl+alt+numpad+ and/or ctrl+alt+numpad- to see if it gives you back a recognizable (albeit resized) screen...

---

### Post by bford16 on 2008-04-07
If you can reboot the machine, you can reconfigure the X server.  When you see the message, "hit ESC for menu," hit the <ESC> key, then choose to boot in recovery mode.  You won't have to log in; recovery mode loads the root account, so you can make changes easily.  Once you get the "root@computer" prompt, type, "dpkg-reconfigure -phigh xserver-xorg" and hit <enter>.  Follow the prompts.  When you are finished configuring the X server, type "exit" to log in normally.  If you still have problems, try again without the "-phigh" option.

---

