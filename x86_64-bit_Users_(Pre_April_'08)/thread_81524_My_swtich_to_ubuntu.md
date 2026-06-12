---
title: "My swtich to ubuntu"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by calcioguy9 on 2005-10-24
Hi, I'm an undergrad majoring in math and econ.  I'm trying to switch over to ubuntu for several reasons now.  A large reason is I want to start using statistical and mathematical programs, but I don't have the money to pay for them.  I also want to learn more about my computer, be able to customize it for what I want, switch to a more stable and secure OS, start learning some programming, and so on...and linux seems to be my answer.

Anyway, here's my issue.  I have an iBook G4 that is dual booting in Mac OS X 10.3 and ubuntu 5.10.  Everything is working fine, well except for my wireless.  And I use my wireless a lot, that is a necessary requirement for me to completely, or at least mostly, switch over to ubuntu.  But, as you guys know, there is not yet a linux driver for airport extreme.  I know one is in the works, but I have no idea how close that is to being functional.  So would I be best off buying a new wireless card and having that installed, should I just wait for the completion of the driver, or should I work on using MOL to access my wireless card?  If a new wireless card would be best, which one?

Also, if any of you know good programs for econ, stats, and math, that would also be a great help.  I've looked around and found some for math and science, but maybe there are some more out there more oriented toward what I'm into.  I've read that a few math programs work better with KDE, so maybe I should consider switching to kubuntu?

Thanks for any and all help,

Kevin

---

### Post by Rxke on 2005-10-24
Good thing you looked at the options and found MOL. 
I'd give it a try, but it's not always straightforward to set up. But if it works, it saves you the money for another wireless card, so always worth a try!

---

### Post by jdp on 2005-10-24
For an iBook you wouldn't get another WiFi card, but rather a WiFi USB adapter.  There are several that work in Linux, and some may well work in MacOS as well.  Airport Cards tend to work only in Airport slots, and there are a few cards that need some mods but can work in the old (slower) pre-Extreme slots.  I'm not sure if there is anything that is known to work in an AP Extreme slot.

---

### Post by sulobanks on 2005-10-24
A USB adapter with a prism 2 chipset would be most likely to work. You can just install the wlan-ng package to run it. D-Link made the DWL-122, which you'll have to pick up second hand.  The DWL-G122 uses the ratech chipset and there is a linux driver for it, but it still causes kernel panics from time to time. However, it's under active development and ratech has released the source for the driver. I've only tried those two.  122 is solid and won't crash your machine, but is 802.11b. G122 is still a little flaky, but likely to be ready long before the broadcom driver and is 802.11g.  I know there are others that work, but I've not tried them.

There is a tried and true statistical application called R. You can install it from synaptic or apt-get. It has a lot of modules to it as well for doing all sorts of things. Gnumeric includes some basic statistical functionality in a graphical way. OpenOffice 2 has a math component (can't remember if version 1 did or not). And I know absolutely nothing about econ. ;)

---

### Post by oswaldkelso on 2005-11-01
[QUOTE=sulobanks]A USB adapter with a prism 2 chipset would be most likely to work. You can just install the wlan-ng package to run it. D-Link made the DWL-122, which you'll have to pick up second hand.  The DWL-G122 uses the ratech chipset and there is a linux driver for it, but it still causes kernel panics from time to time. However, it's under active development and ratech has released the source for the driver. I've only tried those two.  122 is solid and won't crash your machine, but is 802.11b. G122 is still a little flaky, but likely to be ready long before the broadcom driver and is 802.11g.  I know there are others that work, but I've not tried them.


CWD-854 is CNet's 802.11g wireless USB2.0 dongle capable of transferring data at up to 54Mbps. Enjoy the power of instant connectivity by using the CWD-854 in your home, office or any public wireless hotspot. Using this fast, flexible and easy to use adapter makes networking of hard to wire areas a done deal. The CNet Wireless-G USB Dongle connects with Wireless-G networks at an incredible 54Mbps! And for added versatility, it is also capable of inter-operating with all the Wireless-B products found in homes, businesses, and public wireless networks around the country.  re:

[http://www.cnetusa.com/product/specs/wl_CWD-854.htm](http://www.cnetusa.com/product/specs/wl_CWD-854.htm)

This usb works **well **on my mac and there are linux drivers here

[http://www.ralink.com.tw/supp-1.htm](http://www.ralink.com.tw/supp-1.htm)

---

