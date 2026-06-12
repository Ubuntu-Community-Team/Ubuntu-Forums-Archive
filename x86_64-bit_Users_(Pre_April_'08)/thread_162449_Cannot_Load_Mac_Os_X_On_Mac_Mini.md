---
title: "Cannot Load Mac Os X On Mac Mini"
date: 2006-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by SACHIN_VIJAN on 2006-04-19
I have installed ubuntu 5.10 on my mac mini. During installation it asked me where to install ubuntu & i selected the maximum continous free space option. Everything went smoothly but now when i boot my machine it does not give me a option as to which os I want to boot & it automatically boots ubuntu. Can anyone help me as to how to select mac os x to boot while startup.

---

### Post by AlphaMack on 2006-04-19
[QUOTE=SACHIN_VIJAN]Can anyone help me as to how to select mac os x to boot while startup.[/QUOTE]

Press X when you see the menu to boot into OS X.  Then go into the System Prefs and choose Startup Disk as usual.  Note that you will LOSE the yaboot menu by doing this.  To get it back, hold down option on startup until you see a GUI of your disk partitions.  Select Ubuntu (represented by Tux the penguin) and you'll be booting into Linux.  Once logged in, type this in a terminal window:

*sudo ybin*

HTH

---

### Post by SACHIN_VIJAN on 2006-04-19
when i press x on startup nothing happens & when i press control on starup only one disk is visble with the linux penguin on it. how do i boot into os x. i dont know which partition os x is using. please help

---

### Post by SpoonMan on 2006-04-19
Try booting from the OS X installer disk. From there you can run disk utility and make sure your OS X partition hasn't been erased/damaged during the linux install.

---

### Post by namluc on 2006-04-19
i just put ubuntu on my mac mini and was convinced that the tiger had rone 4 good until I found out to press alt on hearing the chime. That brings up the screen selection

---

### Post by linear on 2006-04-19
Normally during an install, yaboot.conf would be set up to give a boot menu. So first check the contents of **/etc/yaboot.conf**.

You can make OS X the default OS by adding the line **defaultos=macosx** to yaboot.conf, then save the file and enter the command **sudo ybin -v**.

More info on yaboot configuration is [here]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.shtml").

---

### Post by SACHIN_VIJAN on 2006-04-20
I dont know which partition my mac os x is on.How should i find it out? Once I know the partition then I can go  about the commands that you have mentioned. please help

---

### Post by namluc on 2006-04-20
go to system then administration then disks. then click on partitions

after installing ubuntu i found that my mac mini had six partitions

one is to wake up the computer, another small one helps osx wake up then you've got ur ubuntu swap partition then the 2 os's.

Ubuntu takes up 7 gigs on my system (if anyone can tell me how to reduce that i'd be very happy!) and is the second biggest partition. 

The biggest partition is your mystery tiger, on mine it is partition 3.

hope that helps

---

### Post by linear on 2006-04-20
You might find it more expedient to open a Terminal window and type: **sudo fdisk -l**, then look through the list for the partition of type "Apple_HFS".

---

