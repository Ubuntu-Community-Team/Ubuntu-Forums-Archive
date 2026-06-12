---
title: "Atheros AR5007eg in Hardy AMD 64"
date: 2009-02-27
forum: x86 64-bit Users
---

### Post by rgehl on 2009-02-27
Ok. I have gone through every possible primer on how to get my Atheros AR5007eg card to consistently work in Ubuntu. I have tried ndiswrapper and I've tried madwifi. With both, I have gotten the wireless to work, but after bootup it doesn't. It sees my network, but I cannot connect.

I've tried to go through the madwifi.org site, but a) it is ugly as hell and b) a lot of its links are dead.

Anyone out there have any ideas?

---

### Post by mikespug on 2009-02-28
Here's a great step-by-step guide on compiling the drivers from source.  If things aren't working after you reboot you may need to take note of the last step which requires you to add “ath_pci” to the end of the "etc/modules” file so the driver is loaded on boot.  Keep in mind that anytime the kernel is upgraded you will need to recompile the drivers.

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

Also, if you have followed the above steps and still are unable to connect I'd suggest an, arguably, better wireless manager:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

In my experience I have found Wicd wireless manager to be much more dependable than network manager.

Good luck.

---

### Post by rgehl on 2009-02-28
Yes, and no. I went through the steps and also got Wicd. It all looks really promising; the networks appear, I can punch in my password. But then Wicd says "validating authentication" and then gives up after about 45 seconds. No connection. I have two other devices in my home connected, so it's not the network.

More details: right now I'm using basic WPA. I tried switching to WEP, and wicd gets hung on "Obtaining IP address." I cannot tell if that is progress.

I am using Ubuntu 8.4. Wonder if upgrading would help?

Second update: I can connect to an unsecured neighbor network. It works beautifully. But I cannot connect to my own. Again, another computer in the house is on that network. When I try, it says "putting network down" and fails.

Final update: Even when my home network is set to unsecured, this will not connect to it. This is very confusing.

---

### Post by mikespug on 2009-03-02
In wicd (i'm not sitting in front of my box now so this may not be entirely accurate) under the preferences menu change the "WPA supplicant driver" from wext to madwifi and see if that helps connect to a secured network.

---

### Post by rgehl on 2009-03-02
Mikespugg - Just a quick "thank you" for all the help. I am writing this via a wireless connection! I still can't figure out why it won't connect to my home network, but it will connect to public networks (which is the main way I use it). So this is workable!

---

### Post by stchman on 2009-03-02
> **rgehl said:**
> Ok. I have gone through every possible primer on how to get my Atheros AR5007eg card to consistently work in Ubuntu. I have tried ndiswrapper and I've tried madwifi. With both, I have gotten the wireless to work, but after bootup it doesn't. It sees my network, but I cannot connect.

I've tried to go through the madwifi.org site, but a) it is ugly as hell and b) a lot of its links are dead.

Anyone out there have any ideas?

Post an lspci output here in this thread.

---

### Post by rgehl on 2009-03-02
Here it is:

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I should add two things: I'm now using 8.10, and I am experiencing the startup bug described here: [https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/272247) . When Ubuntu boots up, it hangs unless I hit a key. I think this is due to nvidia OR atheros.  I don't know if this relates to my wifi troubles.

---

### Post by Melvinator on 2009-03-02
I had the same problems with my Atheros card in my Acer 7520. I beat my brains out on trying to set my card up. Then I found this.

[http://ubuntuforums.org/archive/index.php/t-766169.html](http://ubuntuforums.org/archive/index.php/t-766169.html)

It took me just a few minutes and I was up and running.It worked for me, hope it works for you.
I have Ubuntu 8.10.

---

### Post by stchman on 2009-03-03
> **rgehl said:**
> Here it is:

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I should add two things: I'm now using 8.10, and I am experiencing the startup bug described here: [https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/272247) . When Ubuntu boots up, it hangs unless I hit a key. I think this is due to nvidia OR atheros.  I don't know if this relates to my wifi troubles.

Follow this.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

---

### Post by mikespug on 2009-03-03
> **rgehl said:**
> it won't connect to my home network

The nice thing about Wicd is that it allows you to configure network settings for each "saved" (used) connection independently of one another.  I would suggest setting up a static ip as opposed to using dhcp on your home wireless connection and see if that resolves your issue of non connectivity.  You may see increased boot and/or connection times as a result also.

---

### Post by tbastian on 2009-03-03
I have the exact same problem, I've tried madwifi and never gotten that to work and I've had some success with ndiswrapper, but connecting to networks is hit-and-miss. I've found that if you do:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

```
enough times it'll connect eventually, but its a bit of a hack.

I was pointed to a fix of sorts and it helped for a while, then randomly stopped working (maybe it never worked, and it was all a coincidence) but I'm including it here in case it works for someone else!

I was also told the problem may have something to do with the order in which modules are added, and that ndiswrapper was added to early, but I don't know how to fix/change that nor if its actually the problem. if someone understands anything I just said and knows what the issue is... help?

> Thanks "mechanikking". After much pain I got to the same place that everybody else here, but I wandered... is there was a better solution?
I am using a solution based on the bug report #182716. I actually prefer it a lot, it is easier on the eye and can be turned off (to me).

Copy from Bug #182716:
To resolve the problem i crate a boot script using this steps:

1) U must create a file in /etc/init.d/ndiswrapper:

sudo nano /etc/init.d/ndiswrapper

1.a) and paste in it this text:

#! /bin/sh
### BEGIN INIT INFO
# Provides: ndiswrapper
# Required-Start:
# Required-Stop:
# Default-Start: S
# Default-Stop:
# Short-Description: enable to load ndiswrapper
# Description: enable to load ndiswrapper
### END INIT INFO

rmmod ohci_hcd
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe ohci_hcd

############# end file ############

2) then set file access permissions:

sudo chmod 755 /etc/init.d/ndiswrapper

3) check if permissions are ok. Type:

ls -l /etc/init.d/ndiswrapper

[... ]
-rwxr-xr-x 1 root root 4388 2008-02-03 14:57 /etc/init.d/ndiswrapper
[... ]

4) last, create a symbolic link call S99ndiswrapper in the folder /etc/rc2.d, from /etc/init.d/ndiswrapper:

sudo ln -s /etc/init.d/ndiswrapper /etc/rc2.d/S99ndiswrapper

END OF COPY from Bug #182716.

I also think is worth to mention that a lot of tutorials in the net speak of blacklisting ssb - all wrong. Finally my /etc/modules does not contain ndiswrapper anymore (or the turning on/off point would be wrong).

USB and bcm4328 working.


---

