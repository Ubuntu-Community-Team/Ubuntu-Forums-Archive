---
title: "Gusy Gibbon on Acer Aspire 5020"
date: 2007-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by docnic on 2007-11-01
Hi!

I updated my system (Turion 64, ATI mobility Radeon X600, BCM 43xx) to Gutsy Gibbon. Nice!

After install the boot screen was black.
I opened as root: /etc/usplash.conf
change to:
xres=1280
yres=800
sudo update-usplash-theme usplash-theme-ubuntu


To get WLAN working I had to install [aceracp]("http://code.google.com/p/aceracpi")i. 
Load restricted driver module (fwcutter).
Edit /etc/apt/sources.list
add: deb [http://www.mumblyworld.info/ubuntu](http://www.mumblyworld.info/ubuntu) gutsy main
get the repository's key: wget [http://www.mumblyworld.info/ubuntu/depot.key](http://www.mumblyworld.info/ubuntu/depot.key) -O- | sudo apt-key add -
Open Synaptic and install aceracpi 
After that, everything essential worked fine.

Compiz Fusion isn't working.

For my other changes take a look [here]("http://docnic.blogspot.com/2007/11/ubuntu-710-gutsy-gibbon-on-acer-aspire.html").

Gutsy Gibbon is the best release ever! Use it!
docnic

---

### Post by gdp77 on 2007-11-03
very good post... 

I got a little confused about how u installed wlan. Please guide me using steps 1), 2), 3) etc...

---

### Post by docnic on 2007-11-05
Go to System - Restricted Drivers, enable Braodcom Chipset. This will load fwcutter

Go to System - Software Resources, go to Third Party Software, add: *deb [http://www.mumblyworld.info/ubuntu](http://www.mumblyworld.info/ubuntu) gutsy main*

Open an Konsole, write: *wget [http://www.mumblyworld.info/ubuntu/depot.key](http://www.mumblyworld.info/ubuntu/depot.key) -O- | sudo apt-key add -*

Go to System - Synaptic, install *aceracpi*.

Now you should be able to configure your WLAN (the sign left to the speaker and the clock)

Good luck!

---

### Post by henx77 on 2008-01-11
Thanks docnic, 
worked like a charm....

---

### Post by MrKlister on 2008-05-06
Worked for me too on Ubuntu Hardy Heron 8.04

Thanks for the more detailed description! ( newbie speaking :) )

Worth mentioning is though that a reboot is needed after installation.

---

### Post by External on 2008-07-22
> **MrKlister said:**
> Worked for me too on Ubuntu Hardy Heron 8.04

Thanks for the more detailed description! ( newbie speaking :) )

Worth mentioning is though that a reboot is needed after installation.

Just for the record: acer-acpi is already upstream, and is incorporated in the 2.6.25 kernel, the basis of Intrepid. Backport was requested and granted for it to be included in Hardy, so there is no need to be messing around finding acer-acpi any more.

References:
[http://code.google.com/p/acer-acpi-deb/](http://code.google.com/p/acer-acpi-deb/)
[http://groups.google.co.uk/group/aceracpi-announce/browse_thread/thread/76f2cb0e08c01c42?hl=en-GB](http://groups.google.co.uk/group/aceracpi-announce/browse_thread/thread/76f2cb0e08c01c42?hl=en-GB)

---

