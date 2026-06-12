---
title: "Linksys WMP54G Wireless with WEP"
date: 2007-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by seopdx on 2007-01-29
Hi there everyone,

Just got x86_64 installed last night, but it can only boot with a noapic parameter.  Seems that every single distro is having issues with my system as far as installs and boots go, not sure why.   Having a hard time getting wireless with WEP working.  I believe it reads the card correctly, but not seeing my network.  Under the network settings, it pulls up 2 wireless interfaces;  wmaster0 and wlan0.  I have tried to fill in both interfaces to work, but this is also the first time I have tried a wireless with WEP config on any linux distro, so total noob on this hehe.  Under the "location box", nothing shows up at all.  My hardware

*Linksys WMP54G ver 4.5 pci card (device manager sees this as Ralink driver, rt61pci)
*Geforce 7600 GS PCI-E 256mb  (xorg.conf sees this as "Nvidia Default Card" with nv as the driver)
*AMD 64 x2 3800+
*2 gigs ram
*Seagate Barracuda 320gb SATA
*Nvidia nforce 550 chipset
*integrated audio

Still fairly new to Linux, so a little handholding would probably work best LOL.  Thanks for looking.

---

### Post by Vox754 on 2007-02-08
> Just got x86_64 installed last night, but it can only boot with a noapic parameter. Seems that every single distro is having issues with my system as far as installs and boots go, not sure why.
Just because you have an AMD64 doesn't mean you necessarily need to install the x86_64 version of Ubuntu, or any other distribution. You would be better with the 32-bit installation, unless you really know what you want.

To set up a wireless device you need to
```

sudo iwlist wlan0 scan
sudo iwconfig wlan0 key open 1234567890
sudo iwconfig wlan0 essid ESSID_NAME
sudo iwconfig

```
Where "wlan0" is the name of your device, It could be "wmaster0", or "eth0", "eth1".

If you have configured it properly, you may activate the interface
```

sudo ifconfig wlan0 up

```

You may need to enter the ESSID_NAME and key in the file "/etc/network/interfaces", so the changes remain.
```
man iwconfig
man ifconfig
man interfaces
```

---

