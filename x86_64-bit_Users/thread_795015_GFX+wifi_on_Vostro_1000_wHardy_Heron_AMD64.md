---
title: "GFX+wifi on Vostro 1000 w/Hardy Heron AMD64"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by tastefulasever on 2008-05-15
This is me sharing the guides I followed to get wifi and display drivers working on my Dell Vostro 1000 laptop running Ubuntu Hardy Heron AMD64.  I installed using the Hardy Heron AMD64 Alternate Installation CD.  When I first booted into the desktop after finishing the install, my display was horribly bejangled, all wavy and cross-eyed and bugging out, and my wifi didn't work.  The first thing I did was connect to my network at home through the laptop's ethernet port.

According to lspci, my wireless adapter is:
```
Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
```

And my GFX chip is:
```
VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
```


My processor is a:
```
AMD Athlon 64 X2 Dual-Core Processor TK-57
```

And my linux kernel at this time is: 
```
2.6.24-16-generic
```


To get the display drivers running properly, I followed this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

After that, to get the wifi working, I followed this guide from the Dell website:
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

The link to the driver I needed to download for wifi is:
[http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe)


Everything is running smoothly.  Hardy Heron seems even more polished than any of the previous releases.  

**Great job Ubuntu dev team!**

---

