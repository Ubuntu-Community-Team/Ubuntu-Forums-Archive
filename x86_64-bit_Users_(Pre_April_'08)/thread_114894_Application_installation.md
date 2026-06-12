---
title: "Application installation"
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by gdgardnerw on 2006-01-09
I am trying to install skype in my machine, but I get the following error message:

sudo dpkg -i /media/cdrom0/skype_1.2.0.18-1_i386.deb
dpkg: status database area is locked by another process

When I try to use Synaptic, I can't get access to the CD on which I have these files.

Whenever I try to use APPLICATIONS>ADD APPLICATIONS>Repositories>Add CDa, I get the following error:

"Unable to get exclusive lock. This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first."

What can I do? I also want to install a printer driver and other software, but I always run into this error.

---

### Post by welsh_spud on 2006-01-09
Close all instances of Synaptic, Terminals running Apt-get or Aptitude, or any other programs that are used to install programs using the online repositories.

Then re-open Synaptic and continue with what you were doing.


NOTE: Your posting in the Macintosh/Apple/PPC Users area, so i'm guessing your using a mac. Are you sure that the deb you have for Skype is a PowerPC binary. Binary files made for Mac (IBMs PowerPC) and binary files made for the PC (Intel, AMD, x86) platform can't work together.

---

### Post by gdgardnerw on 2006-01-09
Hmmm. 

-- 1 - Previous Instances of Synaptic, etc. --
In the case of previous instances of Synaptic, Apt-get or Aptitude...I never have any of the latter two running, because (sorry for the ignorance) I've just heard of them in passing, but don't know how to use them. In the case of Synaptic, I close out all windows of that...before doing 

Application>Add Application>Repositories>Add CD

Even after I reboot, this menu option above kicks out the same error!

-- 2 - Differing bin files for PPC and x86 / AMD 64 --

How can one tell the difference? I can now see how this is going to play out! I bet the files I need, i.e., printer driver for Samsung ML-1250, Skype, etc. are all going to be for the x86 platform and I am going to be stuck up the creek without the proverbial paddle!  (Can you detect any meloncholic / pessimistic tendencies in this preliminary conclusion?) Sorry about the frustration. It just seems that everytime I want to do something new, it takes two days to figure out. A day to get Ubuntu running on my iMac (333 MHz). Two days to figure out how to get the modem to work. I have yet to get the Palm Pilot to sync (we've been a week ,or two on that one). And now a day or so on how to install a simple program. I heard that Linux had a "higher learning curve," but I didn't realize it would require a HumVee in four wheel drive to tackle the grade.

---

### Post by welsh_spud on 2006-01-09
I think I can see what you are trying to do when you're installing skype. If the skype deb is on the CD, just copy the deb file from the CD to your home folder. Then type in command line:

sudo dpkg -i <skype filename>.deb

However, like I mentioned before this won't install skype, as it is a binary for PPC; not x86.

Oh yeah, by the way, you might not have had instances of Aptitude running, I was trying to go through all the programs that might cause that error to appear.

---

### Post by CameronCalver on 2006-03-11
Hey i have syaptic but i closed it and i want to use "add aplications" but it wont let me it says unable to get an exclusic lock

---

### Post by ssam on 2006-03-11
you can only have one package manager running at a time, otherwise they would step on eachothers toes. the package managers include apt-get, dpkg, add applications, update manager. sometimes the update manage runs in the background to check for updates.

leave the computer for maybe half an hour to be sure that any background process is completed. check that none of the programs are running. if you are really sure that none of the programs are running (restarting would be a good way to be sure or having a good look though the task manager) then you can run the command
```
sudo mv /var/lib/dpkg/lock /var/lib/dpkg/lock.old
```
to remove the lock file. it will be recreated when you next run a package manager.

with skype you will still not be able to install it because they only make a linux version that works on x86. there are a few alternative opensource VOIP clients that you could try maybe gnome-meeting (now called Ekiga)

---

### Post by CameronCalver on 2006-03-11
is this what u have to write in the termanal sudo mv 

?
sudo mv /var/lib/dpkg/lock /var/lib/dpkg/lock.old exactly like that


look at screen shot

---

### Post by CameronCalver on 2006-03-11
also when i run synaptic it says

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
 what do i have to do

---

### Post by jdp on 2006-03-12
[QUOTE=gdgardnerw]sudo dpkg -i /media/cdrom0/skype_1.2.0.18-1_i386.deb[/QUOTE]

You asked how to tell if the packages are PPC or for x86 CPUs, well the package you post about ends with **i386** which means that its for x86 processors.  i386 is the generic term for the current line of Linux compatible PC CPUs.  x86 is used more often, but could be considered to include 8086 8088 80186 and 80286, which don't generally run modern Linux distros.  The 80386 on up do, thus the i386 in the package name.

---

### Post by fatty_chris on 2006-05-15
[QUOTE=ssam]

```
sudo mv /var/lib/dpkg/lock /var/lib/dpkg/lock.old
```

[/QUOTE]

Thanks for the help.  I was having the same problem and this fixed it for me. :mrgreen:

---

### Post by gdgardnerw on 2006-05-19
> You asked how to tell if the packages are PPC or for x86 CPUs, well the package you post about ends with i386 which means that its for x86 processors. i386 is the generic term for the current line of Linux compatible PC CPUs. x86 is used more often, but could be considered to include 8086 8088 80186 and 80286, which don't generally run modern Linux distros. The 80386 on up do, thus the i386 in the package name. -- posted by jdp.

I appreciate this observation. I have had trouble distinguishing these files. This clears up a lot for me. Thanks!

---

