---
title: "need help setting up ubuntu amd64"
date: 2006-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by zomg_linux on 2006-12-13
Ok so I just downloaded Ubuntu 64bit AMD. Iv got 3 hard drives in my computer, Primary HDD (the first one) has windows, second one just has games and other files. I removed them both when I installed ubuntu just so I would make sure I didnt stuff anything of windows while installing ubuntu. 
So its installed on the 3rd HDD, and when I have my windows disk plugged in it can't detect ubuntu is there so it doesnt show me a boot option screen .. I suppose I have to add it to the boot.ini file?? can someone tell me how??

Also, I cant get my internet going. I use a dialup modem, i have set it up in the network thing, put the number and username/password info but I can't figure out how to get it to connect? 

And lastly I downloaded a 64bit nvidia driver for my graphics cards, it was a ".run" file. I downloaded it in windows and burned it to cd, copied it to my ubuntu desktop and tried to open it but it kept coming up with some error about codename or something and it wouldnt open. How do I install the drivers? Did I downloaded the wrong ones or something?

---

### Post by pay on 2006-12-13
Try this. boot the ubuntu liveCd and open up the terminal```
sudo su
swapon /dev/hda2
mkdir /mnt/ubuntu
mount /dev/hda3 /mnt/ubuntu #could be partition 2 if Ubuntu doesn't use a /boot partition as default
mount /dev/hda1 /mnt/gentoo/boot #note that I think that Ubuntu doesn't use a seperate /boot partition
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev 
chroot /mnt/ubuntu /bin/bash
env-update
env-update
export PS1="(chroot) $PS1"
```now you've mounted your discs and you are inside your Ubuntu installation (note change hda to your disc)
Now install grub and configure it```
sudo aptitude install grub
nano -w /boot/grub/grub.conf
```and add this at the end(change the harddrive```
# The next four lines are only if you dualboot with a Windows system.
# In this case, Windows is hosted on /dev/hda6.
title=Windows XP
rootnoverify (hd0,5)
makeactive
chainloader +1
```now install grub to the mbr```
grep -v rootfs /proc/mounts > /etc/mtab
grub-install /dev/hda
```again change hda to the drive ubuntu is installed on. 
look at this guide in regards to installing nvidia drivers [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)
Good luck.

---

### Post by zomg_linux on 2006-12-13
Sorry but im abit of a noob when it comes to this linux stuff.. How do i get into the terminal on the liveCD? and how do I know which "hda" is which ? 

and "now you've mounted your discs and you are inside your Ubuntu installation (note **change hda to your disc**)" which disc? the ubuntu is installed on?

---

### Post by pay on 2006-12-13
To find out what disc Ubuntu is on try ```
sudo fdisk -l | grep ext3
```or```
sudo fdisk -l | grep reiserfs
```(in all likelyhood if you installed ubuntu with the default settings it would be ext3 but if you used a different file system they can be reiserfs, xfs or jfs (to name a few).> **zomg_linux said:**
> and "now you've mounted your discs and you are inside your Ubuntu installation (note **change hda to your disc**)" which disc? the ubuntu is installed on?I meant the disc that ubuntu is on ie (sudo fdisk -l | grep ext3).

---

### Post by zomg_linux on 2006-12-13
Yeah I will try it as soon as I can figure out how to get into terminal of the LiveCD??

---

### Post by rsambuca on 2006-12-13
Should be in:

Applications --> System Tools

if I remember correctly

---

### Post by zomg_linux on 2006-12-13
yeah i know its there, but he said to do it off the LiveCD because i need to have my windows HDD in the computer, but if I have my windows HDD in the computer it just boots straight to windows so i need to do that GRUB stuff.

---

### Post by rsambuca on 2006-12-13
It is in the same place when using the liveCD.

---

### Post by zomg_linux on 2006-12-13
I couldnt find it. the only options were Install textmode, Install OEM mode, Install commandscript (or something), check cd for defects, memtest, boot from first hard drive.

So i just went to install OEM mode again. I went through it and when i got to partitioning, i deleted the 3rd disks partition completely. 
I started it all over, created like this.

Partition #1 : /boot
Partition #2 :swap space
Partition #3 : /

Then installed everything, It then deteced I had windows installed and asked if I would like GRUB installed to the MBR or MFT, forgot that lol, so it installed. rebooted after it was done and now I can select eitehr windows or ubuntu so that works fine now. 


Now my only problem is connecting to the internet. It sees my modem, and when i go to properties I added the user name and password stuff, phone number etc. 
Then i go into firefox and put in a website to see if it will connect but it doesnt do anything. Just comes up with cannot find server because im not connected to the internet.

---

### Post by pay on 2006-12-13
Oh you have the alternate liveCD. To do this you need a LiveCD that runs an actual grub/kde environment. Any distro will do but for convience it is probably better to use the Ubuntu liveCD (not alternate!). But since you reinstalled Ubuntu and thus installed grub you don't need to do all those steps I told you before. Heres a guide for modems [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by rsambuca on 2006-12-13
Sorry, can't help you with the modem stuff.  I have a direct cable modem and it worked without touching anything.

By the way, I have never heard of anyone using the OEM installer before.

---

