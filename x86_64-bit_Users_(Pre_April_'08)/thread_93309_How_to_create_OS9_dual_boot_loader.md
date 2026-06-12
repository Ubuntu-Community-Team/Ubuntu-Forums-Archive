---
title: "How to create OS9 dual boot loader"
date: 2005-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by djshep on 2005-11-21
Hi,

I am very new to Ubuntu (or any Linux for that matter), and I have very recently installed Breezy Badger on my hobby Mac (G3 iBook) which normally runs OS9.

I made a fresh OS9 install, creating a spare partition for Linux, and then installed Ubuntu. Everything appeared to go fine, until rebooting the machine. The only options I get upon starting boot-up are for GNU/Linux or CD-ROM. I cannot find the yaboot.conf file to edit and am very unsure how to go about making the changes I need.

Any help anyone can give me would be most appreciated!

Darren

---

### Post by teripittman on 2005-11-21
If it's an old world mac (and many of the G3s are), you can't use yaboot. You need bootx instead. It puts a control panel and pref file into system and will give you the choice of which os to use when you boot up. If yaboot isn't working for you, you might try bootx. It works for me on my Beige G3.

---

### Post by djshep on 2005-11-22
Thanks for your suggestion, really appreciate it.

I think my iBook is New World, as it came out after the iMac. I also remember making a New World boot partition when installing Ubuntu..

I will look into bootx all the same though.

Thanks again!

---

### Post by Ptero-4 on 2005-11-22
iBooks are new world Macs, BootX doesn't work on them. Fortunatelly adding OS 9 to yaboot is easy. run sudo fdisk -l /dev/hda (to see the partition number of your OS 9 partition), then run sudo pico /etc/yaboot.conf (edits yaboot config file) and add macos=/dev/hdaX where the X is the partition number for your OS 9 partition, save the file and finally run sudo ybin -v to apply the changes.

---

### Post by deteringb on 2006-01-29
That was entirely too simple to install a dual boot using this thread...I just did as instructed with the trusty OS9 boot disk (talk about a fast OS, so much faster than Ubuntu or X), installed 9 first, then Ubuntu, ran Ptero's sudos and Voila!!  Could not be much simpler.. Only wish that I had read this forum !before! I installed Ubuntu the first time.. So much faster than YDL (at least on my Pismo)

---

### Post by 3rdalbum on 2006-01-30
Heh, I just set the Startup Disk control panel to boot Mac OS 9 by default. When I want Linux, I go into Open Firmware and type "boot hd:6,yaboot".

---

