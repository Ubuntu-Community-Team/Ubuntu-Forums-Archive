---
title: "Should I install the xorg update?"
date: 2006-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Wafflesomd on 2006-08-23
Well, the recent xorg update seemed to fubar my install, so after readin ghte fixes, I'm wondering if I should dl the xorg update along with the rest of the big ubuntu update.

One issue I seemed to have trouble with, is that, even w/out the xorg update installed.  After I configured and ran the xorg setup, then rebooted, it would just go to a code screen,

I would tell it to run xorg, but it gives me the error "No screen"

So idk what to do.

---

### Post by encompass on 2006-08-23
Alwasy discribe your computer...
What is your graphics card and other what not.
With out that basic information we have no where to start.

---

### Post by richard53 on 2006-08-23
Similar problem with (barebones) AMD 64 laptop and (Aopen) Pentium 4 laptop. I have avoided loading the update on my desktop (Celeron 900) and Nvidia TNT2. I cannot afford the risk. I would like to reload Ubuntu on the AMD machine, but worry that automatic updates will crash the machine anyway.

How do I use the Live Cd and avoid the new x.org?

---

### Post by Wafflesomd on 2006-08-23
AMD Opteron 148
DFI Ultra-D
Nvidia 7800gt
Crucial Ballistix Tracer, 1 gig
WD 74gig raptor.

There's my specs.

---

### Post by encompass on 2006-08-23
interesting how tou go that error... are  you saying you don't have any mouse or graphics?  If not... do this at the prompt...(if no prompt press ctrl alt F1
```
sudo dpkg-reconfigure xserver-xorg
```
then select everything as your defaults EXCEPT when it comes to the driver to use... don't use the nv driver select the vesa driver.  Does that help.
And no... don't do the update of the xorg.  And if you don't know how to leave it out.. don't update yet.  They should be getting that fixed soon.
Wait till the warning is down at ubuntuforums.org before doing any updates.

---

### Post by Wafflesomd on 2006-08-23
Well, the alst time I went to do the xorg setup, there was an actual driver selection named "nvidia" its not there anymore.

I'm afraid to run the setup, as it is the only way I can get proper resolutions, but it will probly just kill my isntall.

---

### Post by spacepirates on 2006-08-24
My comnputer crashed with the Xorg error "no screen" as well. I foudn the fix, but I don't have internet on Ubuntu yet (I need to work around the AEGIS client that lets me access the network still). Does anyone know of a way to get the update by other means?

I can run windows (and access the net), have a cd/dvd burner, no floppy drive, and i have a 512mb cruzer usb drive.

AMD Athlon X2 4400
Biostar TForce4U board
NVIDIA 6800 GS

help?

---

### Post by edistar on 2006-08-24
I have the same problem, and only with my 64-bit dapper. I have a 32-bit version installed too and that one works..
Is there a fix yet? Or does anyone know a work-around?
doing dpkg-reconfigure xserver-xorg doesn't help...
Greetings,
Edistar

[Edit]
Fixed! I just had to do an "apt-get update" and "apt-get upgrade" in text mode, then it worked again! :)

---

### Post by Wafflesomd on 2006-08-24
Can you please explain in detail what you did?

I just got a nice dual boot setup working, and I dont want to kill my linux install by configuring my xorg.

---

### Post by cell-gfx on 2006-08-24
I have had the same problem twice. I've got XGL and Compiz running on an AMD 64 with a GeForce GT 6600 and each time the automatic update updates xorg, I can't start X; I just get failure errors.

---

### Post by thoffland on 2006-08-25
I installed the new Xorg 10.4 today... 10.3 was the one with the problem. It shouldn't be a problem anymore, but I did upgrade to the 10.3 a couple of days ago and had the same problems. 

I'm on 64bit too.

---

### Post by Ausus on 2006-08-26
Hi All,

I did the update and all is well.
Mobo Asus A8N32 Sli deluxe.
It was mentioned it was fixed on the fourums.(Mark Shuttleworth):-o 

Regards

---

### Post by Wafflesomd on 2006-08-26
Well, I reconfigured, and did update it, as I now know the problem isnt the update.

It seems when I use the "nv" driver, and set my values right, I get a scrambled screen upon ubuntu's loading.

When I use vesa, I log in, and it just puts me right back to the log in, wierd huh.

---

### Post by Ausus on 2006-08-26
Hi Wafflesomd,

It could be screen resolution that might be wrong.
I also had once on a reboot the my screen resolution went beyound my LCD screen resolution settings.

I updated my driver, it is now using nvidia driver and tot nv.
Use Tseliot guide to update.

regards

---

### Post by Wafflesomd on 2006-08-26
It's not a resolution issue, my crt easily handles 1600x1200@85hz.

And can you point me in the direction of the guide.

---

