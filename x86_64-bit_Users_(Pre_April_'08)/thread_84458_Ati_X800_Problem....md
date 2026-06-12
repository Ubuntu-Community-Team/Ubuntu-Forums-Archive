---
title: "Ati X800 Problem..."
date: 2005-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jae on 2005-10-31
I installed Ubuntu 5.10 on my AMD 64 machine, but it said failed to load X windows.  I was set to 1280 * 1024 resolution.  I still don't know what is problem with my graphic card.  If anyone have same experience with mine, please help me.  Thank you

---

### Post by wallaceb on 2005-10-31
I had problems with an X700. My solution? Bought a GeForce 6600.

---

### Post by RSX311 on 2005-10-31
I had the same problem, here's how to fix it.

run sudo dpkg-reconfigure xserver-xorg

then select Vesa as your display driver, then finish the rest out and write the xorg.conf file.  Then type startx to start up gnome and that should bring up the GUI.  Then install the fglrx drivers.  You can find the howto by searching the forums.

---

### Post by wallaceb on 2005-10-31
fglrx drivers did not work for me.

---

### Post by Elendil on 2005-11-05
off course not.........is there anything that REALLY works here????

---

### Post by RAOF on 2005-11-05
[QUOTE=Elendil]off course not.........is there anything that REALLY works here????[/QUOTE]
Yes.  The nvidia drivers :P

---

### Post by Ranime on 2006-03-17
This worked for me, I have a X800 VE chip (all in wonder). X700 isn't supported by the proprietry drivers...

[http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)

---

### Post by sporkofunk on 2006-03-17
I had the same exact problem on my x800gto, all you have to do is
sudo nano /etc/X11/xorg.conf
Capitalization is vital, or it won't find the X11 directory.
Once you are in the xorg.conf file, just edit the line that says "ati" to "vesa".

---

### Post by daradib on 2006-10-21
New topic:
[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

---

### Post by Ranime on 2006-10-22
There seems to be another thing that nobody mentioned earlier. There are 2 settings in your mainboard BIOS that have to be disabled:

for AGP users:
disable 8x AGP, set it to a max of 4x agp.
disable AGP fast writes.

also:
set the aperture size to 64MB. 128MB max if 64MB doesn't work for your system.

No more lock-ups for me :)

---

### Post by pony-tail on 2006-10-23
> . X700 isn't supported by the proprietry drivers...
That may be so but some X700 cards work - some do not I have one working with fglrx drivers on Kubuntu "dapper" with XGL and beryl the machine is a Soltek Qbic 3402 with a 2.8gig P4 Brand of card is Sapphire .
Most of my machines use Radeon cards - I have had no issues yet in "dapper" but I have had major issues with an X800XT-PE in "edgy"
The Radeons I have been able to get working under "Dapper" are 9800xt (32bit )
X800XT pci-e (64bit) X800- pro AGP (32 bit) X700 - pro AGP (32 bit ) X850XT-PE (32bit & 64bit) all "dapper" I have had an 8500LE fail under "edgy" but did not put "dapper" on It is in a PIII and I have Debian "Sarge" on it now ! 
ATI proprietry drivers do not seem to be as consistant as nVidia Drivers - but I have done fairly well with them over all . Most of our machines (not all) are SFF (Shuttle / AOpen /Soltek cube PCs ) and the newer (6800 etc) nVidia cards ran too hot in such small spaces . The nVidia 7900 series are good but we already have the Radeons . There are a couple of pretty good "fglrx" how to's on the Forum and the wikki I do it differently but they are worth checking out .

---

