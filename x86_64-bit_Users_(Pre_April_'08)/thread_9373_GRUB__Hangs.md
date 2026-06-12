---
title: "GRUB  Hangs"
date: 2004-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by vswr31 on 2004-12-27
The install goes pretty smoothly, seems like all my hardware will work.
But on the reboot after the first stage of installation GRUB just hangs.
I read in the other forum where someone  chose the expert installtion and just used the LILO bootloader which worked .....but Ubuntu 64 didnt give me the option to use lilo during the install.  
Just got a brand spanking new PC and can't use it until  I get this OS loaded.

---

### Post by diebels on 2004-12-28
How is your partitions laid out?

---

### Post by vswr31 on 2005-01-13
Whatever was leftover from a prior install, but nothing to exotic as I was just going o use this as my workstation.  I have sinced moved to Suse 9.2 as I just wanted one computer in my house to work with all my devices without hours of configuring them.
I am not done with Ubuntu only the 64 bit version.

---

### Post by warpengi on 2005-01-18
I have exactly the same problem.  I get the following

GRUB loading stage 1.5

GRUB loading, please wait....

and it just hangs there.  I am using an Asus SK8N motherboard and a Maxtor 80G IDE harddrive.  Don't know if that has anything to do with it.

So when I did the expert install, still using GRUB as bootloader, it booted just fine.

Problem with Grub being written to the MBR in the handsfree install??

---

### Post by agds on 2007-09-13
Although no one's touched this thread in a while, for the record, I've seen the same problem on a legacy machine I have, specs as follows:

Pentium II at 450MHz
ECS/Elitegroup P6BX-A+ motherboard
256MB RAM
40GB Western Digital Caviar SE WD400JB HDD

The first time the machine boots from a powered-off state, it never successfully passes "GRUB loading, please wait..."  If I do a hard reboot from there, it works the second time.  I'm not sure what the cause is, but I'm going to play with LILO.

---

