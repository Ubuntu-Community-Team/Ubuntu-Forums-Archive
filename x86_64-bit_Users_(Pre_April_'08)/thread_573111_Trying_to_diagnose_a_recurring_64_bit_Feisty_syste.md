---
title: "Trying to diagnose a recurring 64 bit Feisty system freeze"
date: 2007-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by ggathrig on 2007-10-11
My system freezes periodically.  By this I mean that the system does not respond to keyboard or mouse, and I cannot SSH into the machine.  

If I do a hard reboot, the system boots up but fails to connect to the network.  A second reboot gets me up and running for another couple of days to a week.  

I cannot detect a pattern in which software I am running when it crashes.  Does that suggest a hardware issue?  

How should I proceed to diagnose the problem?

Many thanks.

---------------------------------------------------------------------------------

My system specifications are as follows:

Hardware: 
ASUS P5K LGA 775 Intel P35 ATX Intel Motherboard
Intel Core 2 Quad Q6600 2.4GHz 2 x 4MB L2 Cache LGA 775 Processor
EVGA 256-P2-N615-TX GeForce 7600GT 256MB 128-bit GDDR3 PCI Express x16 SLI Supported Video Card
Mushkin 4GB(2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)

Software:

Ubuntu 7.04 AMD64
Restricted video drivers

---

### Post by soxs on 2007-10-11
This is actually not related to x86_64 or not...
It is cross-distro, cross-kernel bug (tested linux mint 3.1, fedora 7, ubuntu 6.10, 7.04, 7.10)
nor is it related to graphics drivers/card manifacturer

See also:
[http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)
Note: Monsterthread alert!

---

### Post by ggathrig on 2007-10-12
Thanks for the reply soxs.  I had perused that thread some and thought it did not apply because I did not get any response from the mouse and could not ssh into the system.  

After getting your response, I read some more of the 78 pages of posts on the thread you mentioned and then disabled my restricted drivers--still got a crash.  After rebooting, I issued a "sudo killall gdm" and then just accessed the machine via ssh.  When I checked from home this morning, the machine was down again.

Incidentally, when it is running I periodically get "general protection fault" messages in the terminal (without a freeze).  A while back, I inquired about this in the forum and someone suggested that I try reseating the memory and recompiling the kernel.  I tried reseating the memory, but have not tried recompiling the kernel yet.  I have never compiled a kernel before but will follow the "master kernel thread" and give it a try.

---

### Post by Jouke74 on 2007-10-12
It maybe wise to rule out bad memory first (causing the same issue of random freezing), by testing it using the 3rd Grub option in the menu : MEMTEST. Leave this on for a while and see if it crashes or shows errors after about 3 to 4 hours of testing.

---

### Post by ggathrig on 2007-10-12
> **Jouke74 said:**
> It maybe wise to rule out bad memory first (causing the same issue of random freezing), by testing it using the 3rd Grub option in the menu : MEMTEST. Leave this on for a while and see if it crashes or shows errors after about 3 to 4 hours of testing.

I did run it for about 2.5 hours yesterday and didn't find any errors.  The last two columns (labeled with error in the column header) remained at zero.  I plan to let it run through the night tonight.

If it passes the memtest does that rule out all types of memory problems or just some possible memory problems?

Thanks.

---

### Post by steveneddy on 2007-10-12
BIOS update, maybe?

---

### Post by ggathrig on 2007-10-12
Update:  when I came into the office this morning the message on the screen said:
```
<0> Kernel panic - not syncing: Aiee, killing interrupt handler!
``` 
I will go search for what has been discussed about "kernel panic".  

steveneddy, indeed, I should probably look into updating the BIOS.  I suspect that I could try that fairly easily before undertaking the kernel recompile.

In fact, I think I will start with flashing the bios.  Next I will do a fresh install.  Then, I will recompile the kernel.

---

