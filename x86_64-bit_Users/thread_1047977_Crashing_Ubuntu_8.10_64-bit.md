---
title: "Crashing Ubuntu 8.10 64-bit"
date: 2009-01-22
forum: x86 64-bit Users
---

### Post by nicknefarious on 2009-01-22
Hi all,

I need some help, please. I have installed 8.10 64-bit on my Dell XPS M1530 - T7700 Intel Core 2 Duo - NVidia 6800 GT - 4GB RAM. Immediately after install I updated everything (with updates sources set to include pre-release updates so kernel 2.6.27-11 is installed) and then installed the NVidia 180.22 driver. The installation went fine and everything seemed to be working. But now it constantly crashes. I get patches of bad graphics here and there and once this starts it deteriorates to a point where you can't see anything on the screen, though if you know where certain buttons are supposed to be you can click on them (like restart) - sometimes it will freeze totally and need a hard re-boot. At first I though it was linked to Firefox cause this was almost always present, but I have since had a number of crashes without Firefox. I have watched a downloaded HD video which was perfect no skips jumps, freezes or anything. I have scoured the log files but there seem to be many unusual things. Can anyone give me clues as to what I should be looking for? And which log files I should be looking in, and in what order? I have attached some log files from yesterday around the time it crashed and today's (23-01-2009) syslog (crash occurred 10:38am).

Please help me, I have been struggling with this for a while now. I have spent a lot of time searching many forums but didn't want to go applying changes willy nilly - I'd prefer experts' opinions.

Apologies if the formatting in the files in not correct. Can anyone point me to somewhere where I can find out the standards for formatting log files for most efficient reading?


Any help is much appreciated.

Cheers,

Nick

---

### Post by dcstar on 2009-01-25
> **nicknefarious said:**
> Hi all,

I need some help, please. I have installed 8.10 64-bit on my Dell XPS M1530 - T7700 Intel Core 2 Duo - NVidia 6800 GT - 4GB RAM. Immediately after install I updated everything (with updates sources set to include pre-release updates so kernel 2.6.27-11 is installed) and then installed the NVidia 180.22 driver. The installation went fine and everything seemed to be working. But now it constantly crashes.
........
Any help is much appreciated.


Try using previous Nvidia driver versions and/or kernel versions to see if things improve.

---

### Post by tiger.woods on 2009-01-25
I'm pretty green in Linux but this worked for me. CTRL-ALT-(F3-F6) gets a terminal and you must stop GDM on CTRL-ALT-F7 before you can proceed.

> sudo /etc/init.d/gdm stop
k=`uname -r`
sudo rm -f `find /lib/modules/$k -iname nvidia.ko`
sudo sh NVIDIA-Linux-x86_64-180.22-pkg2.run
sudo /etc/init.d/gdm start

From what I understand it removes any previous NVIDIA driver from the system which is where my problem was.

Make sure you also have the necessary headers, etc for the kernel before running the NVIDIA script.

> sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-4.4.0 xserver-xorg-dev

Check this link: [http://ubuntuforums.org/showthread.php?t=1034543&highlight=nvidia+180.22&page=3](http://ubuntuforums.org/showthread.php?t=1034543&highlight=nvidia+180.22&page=3)

TW,

---

