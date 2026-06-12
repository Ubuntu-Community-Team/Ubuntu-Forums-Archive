---
title: "Please help, busy box on start up after update"
date: 2008-08-18
forum: x86 64-bit Users
---

### Post by jeff fryett on 2008-08-18
help 
during a update I accendently hibernated my pc and when i next went to restart it went to the busy box termanal 
so i try booting in recovery mode still no go 
how ever it stalls at this point
it stalls at this text for a while before loading busybox

check root=bootarg cat/proc/cmdline
or missing modules, devices:cat/proc/modules 1s /dev 

alert! /dev/disk/by-uuid/746b81bc556e-45a0-ba92-092c87cc2df5 does not exist dropping to a shell! 

Have looked online for help and not found much at all on simaler probs one said to remove quiet splash from the boot up text line and replace with all generic ide but this did not help
any help would be great 
ps I am a realativly inexperenced linux user

---

### Post by ibuclaw on 2008-08-18
Looks like the UUID for your boot partition has changed.

You'll have to boot into the LiveCD to fix it.

Find out which filesystem device your Ubuntu Installation is on and run
```
sudo blkid */dev/sda1*
```
replacing sda1 from the above with the actual filesystem id.

This will output a series of information about the filesystem.
ie:
```
/dev/sda1: UUID="9636c69f-d0cd-4937-8e87-fa06d4583a69" TYPE="ext3"
```
Make a note of the UUID number (copy it to gedit, for example) and then open up the fstab file of your installation as root. Then change the UUID round with the apparent new one.

If you get stuck at all, don't be afraid to ask/PM me. I am around half the time, so you may have a chance of catching me while I'm here.

Regards
Iain

---

### Post by jeff fryett on 2008-08-27
problem solved 
rang a freind who knows 
solition to long and complecated to detail here
however the uuid thing mentioned was a part of the solition
thanks to tinivole for your help

---

### Post by Sef on 2008-08-27
> problem solved
rang a freind who knows
solition to long and complecated to detail here
however the uuid thing mentioned was a part of the solition
thanks to tinivole for your help 

Could you please provide the solution.  It may help someone else who has the same problem.

---

