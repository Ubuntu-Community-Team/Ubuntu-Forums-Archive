---
title: "Dual 2GHz G5 Installation Fails"
date: 2006-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by tidris on 2006-03-14
I have been attempting to install on my Dual 2 GHz G5 without success. Everything goes well up to the point the installation CD is ejected and the machine restarts into yaboot. If I select either LINUX or OSX from yaboot, a white screen follows and nothing else happens afterwards. My machine has a single internal hard disk with one partition for OSX and the other for ubuntu.

I have been able to install 5.10 successfully on a G3 PowerBook as well as on an Athlon  PC.

Can anyone confirm that it is actually possible to install 5.10 on the dual G5? I have attempted installation several times and I am almost ready to give up.

---

### Post by mtlhead on 2006-03-14
i have ubuntu on my second partition...i have yet to get it to work, it says something is wrong with the video drivers when i load and that my partition doesnt exist, and then says dropping to a shell. I have to reboot at that point

---

### Post by tidris on 2006-03-15
I have attempted installing DAPPER on the dual G5 and the problem I described in my initial post is still there. On the other hand, the live DAPPER CD was able to boot and display the Gnome desktop, so that gives me some hope.

I still would like to know if anyone has successfully installed on a dual G5.

---

### Post by tidris on 2006-03-15
I was finally able to install DAPPER on the dual G5. I had to move the serial ATA hard disk from the lower bay to the upper bay in order to fix the problem.

---

### Post by tidris on 2006-03-15
I was also able complete the 5.10 installation now that the hard disk is in the upper bay, but the Gnome desktop looks all scrambled and is unusable.

---

### Post by Volts on 2006-04-24
I was able to get 5.10 installed and working on my Dual 2.5GHz G5 this weekend.  

First, I made sure I had a partition on my disk for Ubuntu.  When installing, I first tried to have the installer look for the largest available free space.  But, since I had the empty partition formatted through Apple's Disk Utility, I had to first wipe out that formatting with the Ubuntu installer to make it into actual free space.  From there, I had it automatically configure the free space into partitions (~47 Gb for files, ~2gb for swap, maybe 1GB for boot?).  

After the installation disc ejected and the machine rebooted, the bootloader popped up, went automatically to Linux, and proceeded with the rest of the setup. 

When you were attempting to install, did you allow the installer to automatically configure the necessary partitions in your free space?  

The only hitch I found was that yaboot didn't find the correct partition for my OSX install, so I had to manually edit the yaboot.conf file.  Once that was done, my machine was set to automatically boot to OSX after the bootloader came up and sat for about 10 seconds.

---

