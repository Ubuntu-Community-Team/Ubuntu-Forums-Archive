---
title: "Ati Driver problem"
date: 2004-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by tr0nic on 2004-11-10
First, if you think this thread is not in the right place here, feel free to move it to the 'Hardware issues' section, or I will do it by myself...

I downloaded Ubuntu 64 and installed it on my machine (Athlon64 3500, 1 Gb RAM, Ati X800 Pro, SATA HD). Everything worked fine, so I rebooted. Note that I chose the Vesa Driver for my X800. However X does not start, instead the system hangs up totally (in 5 of about 8 attempts). I thought that it would be better to choose the ati driver, but after editing Xfree.conf it still did not work. I tried to get the offical ati drivers by apt-get install fglrx-driver, but these drivers does not seem to be in the repository (even after adding universal etc. to sources.list). The only driver that works is vga, obviously... Remember that my graphics card was correctly supported under MEPIS Linux 2004.3 (vesa drivers)

Think it could be related to the 64-bit version I tried to install, dunno...

Kudos

---

### Post by tr0nic on 2004-11-10
Oh sorry dudes...
I didn't see that my question was already partly answered in a previous thread. I still wonder though why the vesa driver does not work, maybe also a problem related to the 64-bit thingie...

---

### Post by Rink on 2004-11-10
You could try looking at the [Instructions here](http://wiki.ubuntu.com/BinaryDriverHowto) .

They may help you to install your card properly, but there is also a section on configuring your /etc/XF86Config-4 file. ie by typing 'sudo dpkg-reconfigure xserver-xfree86'

Cheers

---

