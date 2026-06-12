---
title: "D-link DWL-G122 usb wireless adapter"
date: 2005-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by jwhitt on 2005-12-15
Im having a hard time trying to get my d-link dwl-g122 usb wireless adapter to work with ubuntu 5.1 i have a ibook g3 800, i can go into the device manager and see it listed as a usb device, yet when i go to configure it as a network device, its not listed

---

### Post by jwhitt on 2005-12-15
wait sorry guys, temporary insanity flame on

---

### Post by OldMac on 2005-12-18
Hi there...

Did you get the USB WiFi adaptor to work?

I've just installed Ubuntu 5.10 on an old iMac DV G3 400Mhz machine and would love to have it wirelessly networked (I have a wireless ADSL router/modem for my other machines already set up).

Which would be the most stable way to go about it:

1. Buy an old airport card that fits the iMac and hope I can configure Ubuntu to use it (?driver issues?)

2. Buy a USB -> WiFi adaptor to bung in a USB port when required and hope I can configure Ubuntu to use is (again, ?driver issues?)

---

### Post by gconn77 on 2005-12-19
Yes... I would also really like to get this discussion going here. I have an Apple G3 B&W Desktop. I just purchased a Belkin Wireless G Desktop Card version 4000. After doing some research, I don't think that this paticular card will work...

So... I too would like to know what would be the best wireless product to purchase.... whether it be a PCI card, or USB... doesn't matter to me... as long as I can purchase it, install it, and have it working before Christmas.

---

### Post by jwhitt on 2005-12-19
as of right now i dont have it working, ill be home over break and plan on devoting a few good days to getting this damn thing to work, as of now im getting invalad moduule format when i mod prove rt2570, in not exactly sure what the issues is, there are several projects to get drivers working for this some ppeople have got it working ralink released their own drivers, thers a team on sourceforge etc

---

### Post by kudos2lee on 2005-12-20
[QUOTE=jwhitt]Im having a hard time trying to get my d-link dwl-g122 usb wireless adapter to work with ubuntu 5.1 i have a ibook g3 800, i can go into the device manager and see it listed as a usb device, yet when i go to configure it as a network device, its not listed[/QUOTE]

Take pity on a Linux noob........

I have a the same d-link dwl-g122. How do you get this unit working?

I see it listed in device manager, but it's not listed in network manager.

I checked the d-link site which pointed me in the direction of a download:
linux-wlan-ng-0.2.3 but I have no idea what to do with this.

I presume it's a device driver but I have no idea how to install it.

It's very frustrating starting with a new OS and not even knowing how
to install an application or device driver...please help!

---

### Post by Lambert on 2005-12-20
This is for a dwl-122 but it uses the same chipset I believe. See if this thread helps and make sure you post back if you succeed.

[http://ubuntuforums.org/showthread.php?t=25676&highlight=dwl-122]("http://ubuntuforums.org/showthread.php?t=25676&highlight=dwl-122")

---

### Post by sulobanks on 2005-12-21
dwl-g122 and dwl-122 are completely different chipsets. Don't get them confused or you'll be banging your head repeatedly. ;)  Also, I found that the ural-linux driver worked fine in hoary, but won't work in breezy.  I get an undefined symbol when I try to modprobe it.  I did a search on this and it would seem that the 80211 stuff has changed and the ural-linux driver hasn't been upgraded accordingly.  I never got the rt2570 driver to work in either system. 

OldMac, get an old airport card if you don't mind the 11mbps speed.  It's known to work as far as I remember, and without the headache of a lot of these 3rd party devices.

For those adventurous enough to play with it:
Ratech link: [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page")
Ural-linux: [http://etudiants.insia.org/~jbobbio/ural-linux/]("http://etudiants.insia.org/~jbobbio/ural-linux/")

If anyone actually gets one of these to work in breezy, please let me know how you did it. I've already spent too many hours getting the same errors.

---

### Post by Lambert on 2005-12-22
You're correct, my bad, different chipsets.

Watch the tips and tricks section of breezy. I posted a howto on the rt2570 and how to compile and install. (hasn't showd up yet at this time)

I'm looking for feedback as I know one person who has it working. I didn't have a device to double check.

---

