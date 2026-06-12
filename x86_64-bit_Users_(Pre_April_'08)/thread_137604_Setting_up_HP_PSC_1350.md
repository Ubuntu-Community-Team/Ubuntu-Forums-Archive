---
title: "Setting up HP PSC 1350"
date: 2006-02-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by cathy! on 2006-02-28
I have been trying to set up my PSC 1350.  So far I am able to print but the scanner and card reader will not work.  I tried installing HPLIP butgot nowhere with it (something about unable to find makefile).  If anyone could help me out with this it would be greatly appreciated.  Thanks in advance.

---

### Post by eriefisher on 2006-02-28
I also have this printer and although I have not set it up in Ubuntu I did use it with Mepis. I believe HPLIP is only the driver for printing. For scaning I think you need something like Sane. While in Mepis I never tried to get the scanner working but I believe it's possible. As for the card reader, it should just show up automatically when you insert a card. It should show as hdxxx depending which slot you use. If I get time I will try to set it up again and post back.

eriefisher

---

### Post by PaDV on 2006-02-28
hplip is installed by default in Ubuntu Breezy Badger 5.10.
But there is a bug preventing "hp" backend devices to be detected (Ubuntu bug #3841).
Please follow this HOWTO I wrote to solve the problem: [https://wiki.ubuntu.com/HPPrinterInstallation](https://wiki.ubuntu.com/HPPrinterInstallation).

---

### Post by yuvalsarig2005 on 2006-02-28
Go to web site [www.hp.com](www.hp.com)

there go to download driver. Write your
printer name and the system you want to install the driver
on.

---

### Post by cathy! on 2006-03-01
I don't know what I did but I was able to get the scanner to work through XSane.  However I am still having problems with the SD card reader.

---

### Post by 11hjpphty76lkjj on 2006-03-06
The 1350 should work fine with HPLIP.

[http://hpinkjet.sf.net](http://hpinkjet.sf.net)

Follow the install instructions for Ubuntu.

[http://hpinkjet.sourceforge.net/install.php](http://hpinkjet.sourceforge.net/install.php)

and make sure to setup the linux environment first.

else you should be able to use the hplip installed with breezy.  but the newer version is a tad easier to setup. imv.

Aaron

---

### Post by 311005901 on 2006-07-01
I have a hp psc 1350 all-in-one also.
My model is HP PSC 1350xi, I don't know if that changes anything.

I got the scanner to work through XSane.
I got the printing to work through the original GNOME printing app.
I can't get the card reader to work, however. It shows up in Nautilus, but when I click on it, nothing happens.

There's no Linux HP driver for the 1350. [http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=306888&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=306888&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us")
Or the driver for the 1350xi.
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=306892&lc=en&cc=us&dlc=en&lang=en&cc=us]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=306892&lc=en&cc=us&dlc=en&lang=en&cc=us")

So I don't know how to get the card reader to work.

---

### Post by 11hjpphty76lkjj on 2006-07-01
The HP Linux driver is at [http://hplip.sourceforge.net](http://hplip.sourceforge.net) .. 

A

---

### Post by 311005901 on 2006-07-02
Is the 1350 xi supported? I don't see it under the supported devices list.

---

### Post by 11hjpphty76lkjj on 2006-07-02
The 1350 is very similiar to the 1310 and such, so it should work fine.  I am interested why it's not on the supported devices list.  I'll look into this on july 5th.  They are in the same class of printers so I don't expect you should have any issues.

Although please let me know if you have any problems.  

Sorry for the confusion!

Aaron

---

