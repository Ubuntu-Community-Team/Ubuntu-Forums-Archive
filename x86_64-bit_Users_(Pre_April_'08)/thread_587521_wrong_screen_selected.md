---
title: "wrong screen selected"
date: 2007-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by thirtyfiftyone on 2007-10-22
Alright, I'll be honest; I'm a complete NEWB when it comes to Linux. I installed 7.10 64 bit on my computer (which was already tri-booting: Vista, XP, OSX). After getting through all of that and jumping through more than a few hoops, I was disappointed to see that my video drivers apparently hadn't loaded properly. I managed to download adequate video drivers, however my video was still in the 800X600 resolution and there was no option to change it to something higher. I found an option to change my monitor type. My monitor was not listed, so I selected one that was similar to it. From there I was able to get up to 1024X768. However I wanted more resolution, so I tried to select another one that was similar to it. After I restarted to make things apply, my video was completely distorted. Now I am stuck not being able to see ANYTHING. Is there some sort of safe mode in Ubuntu that I can utilize? Or is there another solution?

---

### Post by John Jason Jordan on 2007-10-22
> **thirtyfiftyone said:**
> Alright, I'll be honest; I'm a complete NEWB when it comes to Linux. I installed 7.10 64 bit on my computer (which was already tri-booting: Vista, XP, OSX). After getting through all of that and jumping through more than a few hoops, I was disappointed to see that my video drivers apparently hadn't loaded properly. I managed to download adequate video drivers, however my video was still in the 800X600 resolution and there was no option to change it to something higher. I found an option to change my monitor type. My monitor was not listed, so I selected one that was similar to it. From there I was able to get up to 1024X768. However I wanted more resolution, so I tried to select another one that was similar to it. After I restarted to make things apply, my video was completely distorted. Now I am stuck not being able to see ANYTHING. Is there some sort of safe mode in Ubuntu that I can utilize? Or is there another solution?
Yes, there is a safe mode (called Recovery Mode in Linux-land). Right after the BIOS screen you should see a line at the top of the screen saying that Grub is loading. If you hit Esc quickly before Grub starts it will display the Grub boot menu. The second item is the Recovery Mode. This will boot you to a command line where you can fix problems.

Regarding what to fix, the file you need to repair is called /etc/X11/xorg.conf. It is a rather daunting thing to fix, however, because you'll be at the command line. Having said that, there is a utility called nano that will give you the ability to edit the file without needing a degree in computer science. The command you'll want is "sudo nano /etc/X11/xorg.conf." At least you can look at the file and get some idea of what might be wrong.

Another way to fix things is to use the live CD. It will mount your existing filesystem so you can use the text editor to repair things. Another advantage of the live CD is that it will be running as a Linux operating system on your hardware, therefore it will have generated an /etc/X11/xorg.conf file in RAM. You can look at this file and compare it to the one on your hard drive. In fact, you could even rename the one on your hard drive and copy the one from the live CD there to replace it.

Those are just a few suggestions. If none of that gets you working, post back with more information, like what video card it is, what kind of monitor you have, and so on. If you don't know, from the command line do "lspci," which will list all your devices.

---

### Post by thirtyfiftyone on 2007-10-22
Alright I'll try that. BTW, I'm not computer illiterate lol. I'm just a hardcore windows guy that's taken a soft side lately.

---

### Post by thirtyfiftyone on 2007-10-23
I ended up editing the file from the terminal and got things working. Thanks for the tips. Do you have any idea why my video would look fine on the live cd but not after a fresh install?

---

