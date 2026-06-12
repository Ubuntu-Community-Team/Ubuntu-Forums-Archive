---
title: "Problems with installing Ubuntu 5.10(64)"
date: 2006-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by shadowmaster on 2006-02-15
Greetings,
While installing unbuntu, the installation of the base system fails and gives the following:
"failed getting release file /cdrom/dists/breezy/Release,  I tried checking the integrity of the disk itself and there were no problems.  I am really at a road block as no other 64 bit linux I've tried has been able to install on my laptop.  Any help would be greatly appreciated.



Thank You


System Specs:
hp pavilion zv6000 notebook
AMD 64 processor
ATI Raedon express 200M
80 GB Hard drive
512 MB RAM
Windows XP pro installed on 50 GB partition
30 GB partition left over for Ubuntu

---

### Post by Heretic Monkey on 2006-02-15
Did you download the Iso of the release, or order a printed Disc from Ubuntu?

---

### Post by Spudly on 2006-02-15
I had major dramas getting Breezy (5.10) to install from CD. I think I must have downloaded the image from a number of different Ubuntu mirrors, but the install kept freezing because it couldn't find a package... i checked the CD for integrity and it checked out fine. MD5 sum also checked out...

This also happened once when i tried to install Hoary, and happened to a friend who tried to download and install on completely separate hardware.

Has anyone else had unexplainable problems where the install simply hangs at a particular point? My guess is the file was corrupt in some way, but I cannot explain 'how' or 'why'... that and the fact that the latest version of 'kino' for Breezy is buggy (latest version for Hoary-security works fine!) almost put me off installing Ubuntu completely!

---

### Post by ricka on 2006-02-15
as Spudly mentioned breezy installer is buggy, I aswell could not install breezy so installed older ubuntu version and dist-upgrade'ed to breezy
you can try to install ubuntu dapper flight 3(development version of next release), its quite stable (and imo much better then breezy) but you might run into some problems 
you can download iso images to install from [http://cdimage.ubuntu.com/releases/dapper/flight-3/](http://cdimage.ubuntu.com/releases/dapper/flight-3/)

---

### Post by shadowmaster on 2006-02-15
I downloaded the iso file from one of the mirrors.

---

### Post by Spudly on 2006-02-15
Ricka, what problems have you experienced with Dapper flight-3? I'm keen to upgrade, but I've found Hoary much more stable than Breezy so am reluctant...

---

### Post by ricka on 2006-02-15
[QUOTE=Spudly]Ricka, what problems have you experienced with Dapper flight-3? I'm keen to upgrade, but I've found Hoary much more stable than Breezy so am reluctant...[/QUOTE]
i did not have any problems, except few small issues(like time changing to uk timezone, few gui issues), 
it is stable enough too am sure there will be some kind of problems later but just for few hours before devs fix it, also nautilus is way more stable on dapper, firefox1.5 and totem(imrpoved greatly) and Xgl:)

---

### Post by StuartCarter on 2006-02-16
Hi Shadowmaster,

I had a complete nightmare install failure on my AMD64 laptop - the 3 shipit U64 CDs reported corrupt / missing files (and the error message "CD may be upside down"!).

I have been getting around it by:
boot from install cd
at boot: prompt  type
server
(if install screen looks weird, try server vga=771)

Allow basic install to complete. Login as you, then follw the instructions in italics in the following thread:
[http://ubuntuforums.org/showthread.php?t=128369](http://ubuntuforums.org/showthread.php?t=128369)

Next, sudo apt-get install synaptic, and reboot once synaptic has installed.
Once you are logged into the (somewhat broken!) GUI you can remove the CD from the repositories and install all the goodies, including ubuntu-desktop, without using the b0rked CD.

Hope this helps.

---

