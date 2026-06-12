---
title: "New Installation- Xserver"
date: 2006-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Quickbeam of Fangorn on 2006-01-29
I have an old gateway computer which is booged down and I needed a new computer for kids games and e-mail etc. I want to give linux a try. Haven't used a DOS command line in 12 years and that was limited.

New computer -No OS installed.

Motherboard AMD 64 K8n Neo-4-F 3500
2GB DDR 400 PC3200 Dual channel Memory
ATA 250 GB Hard drive and ATA 160 GB Hard drive (intend to run windows xp on smaller drive for games & linux on larger drive for work & internet)
ATI Radeon x1600 256MB PCI-express graphics

Installed Breezy Badger 5.10 AMD 64

First issue is the Graphics card. Prompts lead to Xserver disabled because it doesn't recognize the card.

sends me to command line ~$

I tried

sudo lspci

VGA compatible controller:ATI Technologies Inc:Unknown device 72
Display controller:ATI Technologies INC:unknown device 71e2

Then I tried

/etc/X11/xord.conf

Permission denied.

Currently I have no internet connection on new computer (going to set up wireless as the host with old computer as client) but at this point I don't want to try that and possibly lose my only home computer connection to the net unless I can get the graphics card established with a driver.

Thanks,

QB

---

### Post by RAOF on 2006-01-29
You **should** be able to get X up and running using the vesa driver.  Try running "sudo dpkg-reconfigure xserver-xorg" - you should get a (long) list of questions.  Unless you know better, you can accept the default answers.  One of the questions will be a list of video card drivers - the one you're after will be the "vesa" one.

After you've run that, try running "sudo /etc/init.d/gdm restart" to log in to the GUI.

That X1600 is a really new card - the open-source ati drivers probably don't support it yet.  Once you've got the internet up and running, you'll want to install the proprietry ATI fglrx drivers.  There's a thread in the "Customisation Tips & Tweaks" forum, called something like "Installing the latest ATI drivers"

---

### Post by Quickbeam of Fangorn on 2006-01-29
Thank you much. It worked. Figures there isn't a driver for it yet.

I look around to see where to post for host/client setup for wireless connections.

Thanks again.

---

