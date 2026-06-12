---
title: "grub and L 99 99 99 ..."
date: 2006-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by thebjoern on 2006-12-09
Hi, 
  
 I started the installation of Ubuntu, then it told me to remove the CD and to reboot, then I got a problem  
 with GRUB where it doesnt give me a choice between Windows and Linux (even though it said it found a Windows)  
 and instead of just booting it gives me "L 99 99 99 99 ..." 
  
 Any idea what this is? 
  
 Also when I tried to repair a broken installation and go into a console to try look at grub/menu.1st but when  
 i open it with vi my keyboard doesnt work properly, like it detected correctly that I got a united kingdom  
 keyboard, but when i want to navigate around the file, it just puts random characters in when i use the  
 cursor keys. The normal letters and all work, but as soon as I need to move around it doesnt work. 
  
 Any Ideas on either? 
  
 Thanks in advance! 
 Bjoern

---

### Post by thebjoern on 2006-12-10
Ideas anyone? :confused:

---

### Post by RaYdOg on 2007-08-05
Well, from building LFS, I got exactly the same thing. The vi problem (I think) comes from KBD - the keyboard handling app. ... or maybe the locale for vim is set wrong. As for GRUB, yeah, that problem messed up my day. :/ The problem has something to do (again, I think) with grub having problems finding the map file. ... Try reinstalling... There has been a new ubuntu release since this post. If you haven't already, try that. best of luck. :D

---

### Post by mateuszbaranski on 2008-02-12
You have to definitelly have some problems with grub stage1 image. The most likely stage1 image (first 512 bytes of hadr disk) points to wrong location on the harddisk (it looks for stage1.5 and then goes to stage2 image). I had several times this istuation with LILO (after upgrading kernels) and with GRUB - but I don't know yet how to solve it.  - in LILO you have to boot from some liveCD and run lilo with proper parameters,

regards

---

### Post by salsafyren on 2008-03-26
I have the exact same issue after installing Hardy beta.

The weird thing is that L 99... normally comes from Lilo but this is Grub that is installed not Lilo.

I have tried everything from grub-install to running "grub" then setup in a LiveCD, nothing works.

SuperGrubDisk does not solve the issue either.

I have repartioned my disk now because I thought it had something to do with cylinder boundaries but this has not helped. This sucks so much I have to use a boot CD to boot my computer.

---

