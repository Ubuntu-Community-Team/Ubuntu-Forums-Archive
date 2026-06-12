---
title: "Configuration of Broadcom Dell 1390 on an hp pavillion 2000"
date: 2007-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by GodaHale on 2007-07-07
Used 
Feisty AMDx64
ndiswrapper v.1.47
Had to open an EXE file so I used a windows box
About an hour of headache


Okay, let me start this by saying that the MAIN reason I am posting this at all is that I couldn't personally find much help on the matter for myself.  It got so bad that I went out and bought a USB dongle (D-link) and then found out that it didn't even have a 64bit driver.

Okay here goes in the order I found worked for me.[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=us&dlc=en&product=3193476&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=us&dlc=en&product=3193476&os=228&lang=en)


The Ubuntu installation procedure installed the bcm43xx driver, there does not function with the Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01) that comes in the dv2000 I needed to un-load it and black list it, so it not will be loaded in the future. Then I had to install the ndiswrapper and the Windows driver for the chip. To un-load the bcm43xx driver do:  sudo rmmod bcm43xx. To black list the driver, open the file /etc/modprobe.d/blacklist and add the following to the end of the file: blacklist bcm43xx.

Get the latest release of ndiswrapper (at this time 1.47)
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

You can follow the install instructions that come with the file, but in case you want a one-source approach I will include them here too.

# cd to the directory that the archive was downloaded to.
$ cd [directory]
$ tar zxvf ndiswrapper-[version].tar.gz

# This will create ndiswrapper-version directory change to that next
$ cd ndiswrapper-[version]
$ sudo make uninstall

#This uninstalls the old version of ndiswrapper that comes with Ubuntu
$ sudo make
$ sudo make install


Now you need to install the specific driver.
My internal card reported itself as a Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

Drivers for this pc can be found at hp.com/support 
**SPECIAL NOTE** 
Even though the XP x64 doesn't have the driver the one that is listed with the normal XP has a x64 driver in the file.  That being said I did have to open the .exe on a windows box I had.  If you need me to send you the file just email me at derek.hale(at)gmail.com and I will send you a special link.

To make sure you have the same...
$ lspci

$ ndiswrapper -i bcmwl5.inf (Installing Windows INF driver in ndiswrapper)
$ ndiswrapper -l (See Driver installed)
$ ndiswrapper -m (Write configuration for modprobe)
change the wlan0 aliais to eth1 in /etc/modprobe.d/ndiswrapper
add ndiswrapper to the file /etc/modules to load it at boot time.
$ modprobe ndiswrapper 
# (Load driver)

At this point I restarted my laptop and was able to turn on my wireless card (with the switch) and connect using Ubuntu's network utilities.

---

