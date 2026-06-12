---
title: "Jaunty is giving me a BIOS error !?!"
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by Slurm on 2009-04-30
Hi All,  

I upgraded from 8.10.  First 8.10 ran absolutely perfect on my machine.  This one is giving me all sort of problem and is just causing my maching to move slow.  

But more to this post,  I recently getting the following message when I boot up.

> Powernow-K8:  Your BIOS does not provide ACPI_  objects in a way that LINUX understands.  Please report this to LINUX ACPI_ Maintainers.  

I am also getting (upon startup).....

kinit: name_to_dev(dev/dsk/by-UUID/a3d33638-17a4-4bce.....
kinit: No resume image

I have never gotten a BIOS error under any other Ubuntu going back to Dapper.  

What does this mean?  

AMD-64 dual core,  2gigs MEM.  Asus AMD2 board.  

Slurm

---

### Post by hakalibre on 2009-05-14
[SIZE=2]any solution please ?
this is my motherboard: [/SIZE]
**MSI K9A2 Neo-F, Sockel AM2+**


and I had the same error message.

---

### Post by ea185028 on 2009-05-15
Well I have the same problem as you but how i got the problem was quite different from yours.

Ubuntu installation was fine it was after installing the Nvidia Proprietary Drivers that i got this error.

So what i did was i reinstalled ubuntu 9.0.4 back again and then followed this guide installing my Video Card

["Enabling nvidia drivers in Jaunty - Fixes crash to terminal"]("http://ubuntuforums.org/showthread.php?t=1139101")


Im not sure if this helps for your case, but this is mine and is up and running now

---

### Post by dcstar on 2009-05-15
> **Slurm said:**
> 
.........
I am also getting (upon startup).....

kinit: name_to_dev(dev/dsk/by-UUID/a3d33638-17a4-4bce.....
kinit: **No resume image**

What does this mean?  


Nothing, as it says it just looks for a resume image and carries on when it doesn't find it.

---

### Post by cariboo on 2009-05-15
THe BIOS error is because of changes in the kernel. I first started having this problem in Jaunty, I'm running karmic now, and created a bug report about the problem. One of the kernel devs contacted me and we went through all the logs, including a dump of the BIOS, and it turns out that it is a problem with the BIOS. I have an MSI K9NGM2-FID, that is about 2½ years old and there has never been a BIOS upgrade for this motherboard. I just ignore the error, as it doesn't seem to cause any problems.

---

### Post by hakalibre on 2009-05-15
[SIZE=2]The error was gone after I used a live CD instead of a Live Usb , Now I am using Jaunty,:) . 
for my graphic card Nvidia Geforce 9400 I used this Driver [NVIDIA-Linux-x86_64-180.51-pkg2.run]("http://us.download.nvidia.com/XFree86/Linux-x86_64/180.51/NVIDIA-Linux-x86_64-180.51-pkg2.run") and it works fine .[/SIZE]

---

