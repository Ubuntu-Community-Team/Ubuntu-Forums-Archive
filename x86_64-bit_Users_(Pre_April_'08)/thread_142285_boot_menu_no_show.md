---
title: "boot menu no show"
date: 2006-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by blech on 2006-03-10
Hi.

I replaced my HD in my G4 powerbook so I wanted to do dual boot OS X Tiger and Ubuntu.  I got Tiger and Ubuntu installed. After I downloaded and installed the latest updates for Tiger 10.4.5, the boot menu didn't show anymore after restarting pb or turning it on. It worked earlier. any suggestions? or do I need to reinstall ubuntu?

---

### Post by dermotti on 2006-03-10
Sounds like it re-wrote the MBR.

Ive had this happend with Windows a few time. I used Mepis live cd to reinstall grub to the MBR. Just make sure you check out the /boot/grub/menu.lst to make sure its correct or your OS wont boot properly.

you can get mepis at mepis.org

---

### Post by blech on 2006-03-10
[QUOTE=dermotti]Sounds like it re-wrote the MBR.

Ive had this happend with Windows a few time. I used Mepis live cd to reinstall grub to the MBR. Just make sure you check out the /boot/grub/menu.lst to make sure its correct or your OS wont boot properly.

you can get mepis at mepis.org[/QUOTE]
hmm, mepis is for intel/amd/etc processors. any suggestions for ppc?

---

### Post by astyanax on 2006-03-10
Use the Ubuntu Live CD for ppc.

[http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/ubuntu-5.10-live-powerpc.iso](http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/ubuntu-5.10-live-powerpc.iso)

---

### Post by linear on 2006-03-10
Read the section: "[COLOR=black]You lost the yaboot menu! Now what?" here:[/COLOR]
 
[https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot](https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot)

---

### Post by blech on 2006-03-10
Thanks, I ended up just using the full installation cd and reinstalling yaboot.

---

