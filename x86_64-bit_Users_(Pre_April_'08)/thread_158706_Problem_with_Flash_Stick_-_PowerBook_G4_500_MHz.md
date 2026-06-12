---
title: "Problem with Flash Stick - PowerBook G4 500 MHz"
date: 2006-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by daWabbit on 2006-04-11
Ubuntu Breezy runs fine on my G5 desktop and my x86 and AMD 64 boxes. But on the PowerBook, I've lost the ability to mount any flash memory devices, even as root. There is no error message except one saying "Mount /dev/sda failed". Also, no desktop icon appears when the drive is present, as happens on all the other machines. 

I expect it's something I've done, but I can't imagine what it is. I don't want to reinstall because I'm on dialup and getting all the software installed on the machine was a very, very long job. 

Any help would be greatly appreciated.

Jack

---

### Post by erniewinner on 2006-04-11
:-k well i'm 99% sure "sda" refers to your flash drive, and that accounts to it not being mounted. just out of curiosity how many drives have you tried? what os have you used to format them? and when was the last time you formatted them? usb devices should be plug and play if the driver is there for them which in ubuntu's case is true for my 3, which windows isn't one of my reasons for liking the os i haven't got some 98 drivers for them. do you know the make or chip of the drive? i'm no expert but these are the questions i would ask myself.

---

### Post by daWabbit on 2006-04-11
Most of the flash devices are San Disk Cruzer Minis of 512 MB. We also have some off brand ones that give the same results and some Verbatim ones that simply won't work with Linux anywhere. 

I have formatted them FAT32 on my desktop Mac G5 and some other machines. No luck, even if I format them on the PowerBook. Formatting them in ext2 doesn't help, either. I've tried it with several. As I usually use them for transferring software from my laptop to customer's Windows boxes, it's not practical for me to format them in ext2, but I did give it a try. 

So far, nothing has helped though everything worked fine for 4 weeks after the original installation. 

Jack

---

### Post by erniewinner on 2006-04-12
:confused: sounds like something under the bonnet of your os is misconfigured somewhere then... nice to know they did work. fat32 is well supported under linux you could stick with that. so it's down to the obvious. 1. a reinstall. 2. someone who is able and willing to probe further with this issue... unfortunately i'm not that able. but i wish you good luck.

---

### Post by daWabbit on 2006-04-12
Thanks.

Because FAT32 and hotplug via USB is so well supported by Ubuntu (and most other distros now) I've got to figure it's something I did, though I have so many more applications and utilities than most install on the machine it's either to do with all those installations (not too likely) or something I unintentionally did (VERY LIKELY). I just can't figure it any other way.

If I don't find more help with this post,I will take this laptop to my next LUG meeting and if there's no help there, I'll bite the bullet and reinstall. Seems a shame to do that, but the default config after install worked just fine for a good while and is still working on 5 other computers here, including another Mac. 

Jack

---

### Post by Scunizi on 2006-04-14
Edit/Note: I'm still curious why I had to do the following to fix what the hotplug system should have taken care of.  But since it works I have more pressing things to figure out.

I have FINALLY found the solution to this problem. It was really quite easy after I learned a little about how the file system work and how the system mounts things. You have to remember, the system needs a place holder/directory for each device that is mounted. That is accomplished in the media directory. Also everything you type below is case/CASE sensitive. I have 2 internal SATA drives and 1 IDE internal. I also wanted to be able to plug in my 3 USB devices at the same time and have them recognized with icons displayed on the Desktop. The 3 devices are... 1gig usb stick, 256m Cruzer Mini usb stick, 1 256m mp3 player (creative rhomba). I had to do a little editing of the fstab and media directory in order to get everything working correctly. In my case I already had sda1, sdb1,2,3,5, and hda1.

1> Go to the consol and type sudo gedit /etc/fstab (enter) - This will open up your editor. It will ask for your password. Enter it.

2> In fstab I added these three lines
/dev/sdc1 /media/usb1 vfat rw,user,fmask=0111,dmask=0000 0 0
/dev/sdd1 /media/usb2 vfat rw,user,fmask=0111,dmask=0000 0 0
/dev/sde1 /media/usb3 vfat rw,user,fmask=0111,dmask=0000 0 0

Now click save at the top of the screen.

The vfat referance above is for Fat32 formatted devices. Anything other than that and you'll have to change the formatting designator and possibly the fmask. dmask=0000 simply means that any user of the system can read and write to the device. If I remember correctly, if you substitute 0000 with 1000 only the logged user who created all this will be able to use the device. Someone may correct me here if I'm wrong. 

You'll notice all my usb referances are sdc sdd sde because I already have 2 SATA drives in the machine that are labeled sda & sdb respectively (the numbers represent the different partitions on the harddrives) I you don't have any SATA drives then you should designate sda, sdb, sdc respectively. I made three seperate entries in case I plug in all three devices at the same time otherwise it won't make any differance.


3> Go back to your consol and click "File" "Open Tab". You'll now see two tabs at the top of the consol. Click the second one and you should have an active prompt like "mgarrow@ubuntu:/$". Type cd /media (enter). This will take you to the media folder/directory.
4> Now type
sudo mkdir usb1 (enter) (maybe enter password)
sudo mkdir usb2 (enter) (maybe enter password)
sudo mkdir usb3 (enter) (maybe enter password)
These lines give a place for the drives/devices to attach to. You can use other names if you want. I just did it this way for simpicity.

Now you're done! Restart your machine then plug in one of your usb devices. I may take a moment but the system should recoginze it, mount it and place an icon for it on the Desktop...

I'm about fairly new into learning this system from a cold start and really learning to love it between my bouts of frustration with my ignorance. Happy Ubuntu-ing!!!

---

