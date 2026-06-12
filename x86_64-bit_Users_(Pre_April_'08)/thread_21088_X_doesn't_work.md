---
title: "X doesn't work"
date: 2005-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by fossilsking on 2005-03-20
Hi, I've just installed 64-bit Ubuntu. My hardware is the following: CPU - AMD Winchester 3500+, MB - ASUS A8V Deluxe, Video - Ati Radeon PowerColor X800XT 256MB, 1GB RAM, HDD - S-ATA Western Digital 160GB. I'm very happy that the Ubunt did see S-ATA HDD (Windows doesn't see it...). Intallation passed OK. After the rebooting of the system I've got a message that X is not supported no any graphical enviroment is working and will not work. i saw that to install the ATI drivers I need working X. Any ideas what to do? Any help will be appreciated. Thanks in advance.

---

### Post by emperor on 2005-03-20
Did you install the "linux-restricted-modules"; this contains the ati fglrx driver that would be required for the X800. You should be able to do outside of X and would be the perfered method anyway.

apt-get update
apt-get install linux-restricted-modules   #try this!

Then run "fglrxconfig"
Note: setup to use "external AGPGART"

---

### Post by ruudiculus on 2005-12-26
Emperor,

I've installed the ATI x86_64 proprietary linux driver on my amd64 laptop and my X works fine, but my fglrxconfig doesn't work graphically (the link is present in my Gnome-menu though).

Any idea how to enable this?

Thanks in advance,

Ruudiculus

---

### Post by emperor on 2005-12-26
try running fglrxconfig from the commandline.

sudo fglrxconfig

---

### Post by datacles on 2006-01-11
[QUOTE=emperor]Did you install the "linux-restricted-modules"; this contains the ati fglrx driver that would be required for the X800. You should be able to do outside of X and would be the perfered method anyway.

apt-get update
apt-get install linux-restricted-modules   #try this!

Then run "fglrxconfig"
Note: setup to use "external AGPGART"[/QUOTE]

Major Nube here reporting for duty!
When I try these instructions I get:
E: Couldn't find package linux-restricted-modules

I edited the sources.list and ran apt-get update, no bueno

And of course:
sudo: fglrxconfig: command not found

Unfortunately I made the mistake of purchasing an ATI card.  PCI-Express 16, HD TV out, seemed pretty sweet....for holding papers down on my desk.  I'll trash it before I'll go back to Window$

I think I read somewhere in another post (I've been lurking for days) that I would also need to specify which video head I would be using.  The card has DVI and VGA and HDTV out.

Any help will be greatly appreciated.

---

### Post by emperor on 2006-01-12
The linux-restricted-modules are in the "restricted" repo.

The keyword "restricted" should be added after the lines with "main".

After editing /etc/apt/sources.list, run apt-get update and then open "Synaptics" and search for "linux" to find the available modules.

** linux-restricted-modules-2.6.12-10-amd64-k8**

  
ATI AIW cards should be avoided. ATI does not support the HD or even the TV portion of their AIW cards with their linux driver.
Their hardware does not support the standard the standard video4linux interface.

---

