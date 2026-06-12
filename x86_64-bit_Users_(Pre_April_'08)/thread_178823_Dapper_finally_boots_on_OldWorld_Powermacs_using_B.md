---
title: "Dapper finally boots on OldWorld Powermacs using BootX."
date: 2006-05-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by nkbj on 2006-05-18
The latest update of the Dapper kernel (2.6.15-23-powerpc) contains a patch which makes it possible to boot the kernel on OldWorld Powermacs using BootX. Time to test Dapper on our good old beige boxes. :) 

Regards,
Niels Kristian

---

### Post by jeglin on 2006-06-03
Actually, I'm not finding this to be the case. On a box that 5.10 installs on just fine (PowerTowerPro with PL G4/800 upgrade card), the 6.06 install, dated 30-May, definitely gets futher than the earlier dapper betas, but still hangs, at 'starting system log daemons: syslogd, klogd...'

Any recommendations for this?


Stefan Jeglinski

---

### Post by iamdigitalman on 2006-06-04
I just wressled it on my wallstreet, which has a dead CD-ROM module (makes a loud grinding noise). I put the hard drive in my B&W, and ran the setup. one word of note is to make sure you have a small partition with bootx (I managed to squeeze 9.2.2 down to 64mb with bootx), and then partition the extra space. note there are now a total of 12 partitions on this 4.9gb hard drive. the first 9 are for 9.2.2, with the firs 8 being less than 1mb each. then the 9th is hfs+ and has OS 9, then #10 is a less than 1mb unknown format partition, 11 is ubuntu ext3, and the last #12 is 256mb of swap space.

not bad for a machine with only 160mb of ram. 

one note, in my case, I had to run dpkg-reconfigure xserver-xorg to get it to run gnome, otherwise it would drop to a shell.

oh, does anyone know how to get the ubuntu graphic back? I saw alot of people who want to get rid of it, and go back to the flying text.

[/topic hijack]

-digital ;)

---

### Post by RoadTripDK on 2006-06-18
Is there somewhere that this patch is documented? I would like to get Xubuntu up and running on my Wally, but I am unsure if I need to reformat my hfs+ partition to hfs to get the patch to work, not to mention that I know nothing about the procedure involved for BootX

---

### Post by iamdigitalman on 2006-06-18
[QUOTE=RoadTripDK]Is there somewhere that this patch is documented? I would like to get Xubuntu up and running on my Wally, but I am unsure if I need to reformat my hfs+ partition to hfs to get the patch to work, not to mention that I know nothing about the procedure involved for BootX[/QUOTE]

relax. just follow the steps [here](http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/) and you should be fine. note that when it comes time to format the hard drive, dont delete any of the small partitions. personally, I got away with a 64mb partition for OS 9.2.2, and the rest of the drive is for Ubuntu. also note that in my case, I ended up with 12 partitions. the first 10 were for Mac OS 9, with #9 being the one with the actuall OS, and #11 is the main Ubuntu partition. 12 is swap space. thus, in the exta kernel arguments line, I have root= /dev/hda11.

oh, and to switch which one is the default OS, hit the tab key. that way it will boot into linux when the timer in the corner hits 0. or you could click either button.

hope this helps.

-digital ;)

---

