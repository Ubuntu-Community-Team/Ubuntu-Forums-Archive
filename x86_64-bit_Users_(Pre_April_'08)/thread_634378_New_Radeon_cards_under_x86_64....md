---
title: "New Radeon cards under x86_64..."
date: 2007-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by caitscheverst on 2007-12-07
Hello all,

We have a ATI Radeon HD 1850, and can't get the fglrx, radeon hd, ati or plain radeon drivers to recognise it. We're stuck with the generic vesa drivers and can't get the resolution right, and bits of desktop keep falling off the side of the monitor.

Does anyone know the best driver to use to solve these problems, or how to solve these problems independent of drivers?

Many thanks,

Jason

---

### Post by crjackson on 2007-12-07
Go to this [**[COLOR="Red"]_website_[/COLOR]**]("http://albertomilone.com/nvidia_scripts1.html") and read about the driver installer and use it if you think it meets your needs.  Many Ubutu users swear by it.  I've not tried it myself.

---

### Post by Yellow Pasque on 2007-12-07
Radeon HD 1850? What's that? Did you mean X1850 or HD 3850?

Can you run:
```
lspci | grep "VGA"
```

---

### Post by MrDigital1 on 2007-12-07
I have a friend I was trying to get his ATI Radeon HD 2600 working in x64 Ubuntu and could not get any drivers other than Vesa to work.  Including the "restricted" drivers that Ubuntu automatically can install, nor the envy system.  Nothing worked.  Told him to dump the ATI and get something from nVidia.

---

### Post by flyer40r on 2007-12-25
yep, after 18 hours of pain and uncovering tidbits of info scattered about the net, I've come to the conclusion: ATI HD series cards WILL NOT WORK with AMD64 platform and Gutsy 7.10_amd_x64.

The video card I got for xmas was an ATI HD-2400. I downloaded the correct latest linux drivers from the ati site, built the packages, followed all instructions carefully and got "no screens found" in the /var/log/Xorg.0.log file. Not only would X not start, the machine locks up completely.

One fix was supposedly that the link in rc2.d to start the driver before kdm (I'm using kubuntu) kept getting deleted on boot. Another long and arduous command line adventure followed to no avail. dmesg says the drivers are loading ok, but still black screen and frozen box.

Then I find a page where it was stated a bug in xorg 1.3.0 exists where it will not render from these cards with these drivers. Only solution is to downgrade xorg or get another card.

hhhmmmm let me think, do I spend another 10 hours of screwing around in the command line or...just get an nVidia card (and maybe spend only another 2-3 to get it working)?

I realize this forum isn't intended for rants and I am trying to restrain my frustration. I am posting this as advice to anyone going down this hardware path. Apparently xorg 1.4.0 where this bug has been fixed, is not built for the x64 platform (correct me on this). 

Anyway, back to the store for me.

Hope this saves someone some time.

Mike

---

### Post by caitscheverst on 2007-12-26
To crjackson: many thanks - that website looks like it might be useful!

To Temujin: HD 3850. That was a bit stupid of me - I just typed in the number without looking at the box. <_< Also, the command gives me:
[INDENT]01:00.0 VGA Compatible Device: ATI Unknown Device 9505[/INDENT]

To MrDigital1: Gonna call that the last resort. 'Specially since I'm dual-booting into XP and the graphics card's a true beauty there, where it's needed for games.

To flyer40r: I can believe it. The HD cards are pretty recent, so I figured that just pushing the system to working condition and then waiting for tailored drivers would be my best bet. I have no pressing need to see beautiful graphics in Linux. :P

Thankyou, everyone - I've botched the job for now, but I'm going to look at this Envy page and try a couple of other things before leaving it to Time.


Yours,
-Jason

---

### Post by Yellow Pasque on 2007-12-26
Try the open-source radeonhd driver then. Support was just added for the 3k series. You should at least be able to access all of the 2D resolutions with it.
[http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

Also, if you haven unknown PCI devices, you might want to run:
```
sudo update-pciids
```

---

