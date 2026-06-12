---
title: "USB WiFi?"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by funkychicken9000 on 2005-10-15
Right, I'm a complete newbie to linux, so apologies if any of this is nonsense.

Basically, I've been trying to get my Linksys WUSB54G working in Breezy.  No small task.  I'm kinda limited to USB here, as I have a shuttle and want to use the PCI slot (eventually) for a better sound card.

I was advised to go down the ndiswrapper route, and so I tried in vain to install that and get it working with the windows xp driver.  WLAN0 just never showed up in network options, and "modprobe ndiswrapper" seemed to go unnoticed by terminal, there was no noticeable output.

I'm now wondering (seeing as I have an amd64 and am using 64bit breezy) if i need a windows 64bit driver to use with ndiswrapper?  Or is there something else I'm doing wrong?

---

### Post by queenorych on 2005-10-24
if you are running a 64 bit kernel, you must use a 64bit wifi driver.  Good luck last I heard only broadcom and centrinos worked with ndis.  rt and atheros have native drivers that should work.  There's lot of chatter about wifi google linux 802 or linux wifi.

---

### Post by Ferrat on 2005-10-26
Im having the same problm Im using a D-link DWL-G132 USB adapter for my WLAN, now did a pretty good bit of research and found out that DWL-G132 uses two Atheros builds but can't find any native 64 drivers for Atheros. 

Most WiFi progs have tested DWL-G132 with success but I belive most of those testes where done on a 32bit system not 64, read that some people using other D-link USB WiFi adapters like 122 could make it work with the 32bit drivers.

Im new to setting up more advanced stuff in Linux, haven't use Linux in years but also read that a 64bit kernel should be able to use 32bit apps without any problems if it only hade the right libs and that you could add those libs and most of the apps would work them selfs out, is this possible also with drivers for hardware? 

Unbuntu can see the adaptor no problem but so far I have had no luck in getting it to work or ever register as a network device, currantly running Dualboot with windows until I get Unbuntu to work as I want it to, been googling and reading forums for 2 days now but have yet to find a really helpfull guide to setting it all up. 

Not having used Linux in a long time Im a bit rusty to all the commands and so on but learn as I go, how ever is there anyone who happens to know any good generic drivers for Atheros that could work? Or know of any good guides that might be able to help poor little old me? ](*,)

---

### Post by queenorych on 2005-10-27
See madwifi for atheros drivers and amd64
[http://ubuntuforums.org/showthread.php?t=38972&page=3](http://ubuntuforums.org/showthread.php?t=38972&page=3) for a page on this.  

Remeber to also search for debian amd64 atheros stuff too.

---

