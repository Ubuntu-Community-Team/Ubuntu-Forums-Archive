---
title: "Gutsy - Problem with Intel GMA 3100 graphics driver"
date: 2008-06-09
forum: x86 64-bit Users
---

### Post by mysticBoer on 2008-06-09
Hi all,

We have 7 machines primarily used for training. These machines had hardware trouble so we decided to replace the Motherboards/CPU's/Memory. 

We cannot re-install the OS's at this time as we have to do training on Wednesday and it takes way longer to set up the machines properly and configure our software.

```

Before the changeover the specs were as follows:
Motherboard : GA-M51GM-S2G
Chipset     : NVIDIA® Geforce 6100 + nForce 430 chipset
CPU         : AMD X2 3800+
Memory      : 2Gb DDR2 - 800

After the changeover:
Motherboard : Intel Pearl Creek
Chipset     : G31 - GMA3100
CPU         : E6650 Core 2 Duo
Memory      : 2Gb DDR2 - 800

The HDD, CDROM, PSU stayed the same. 

```

When booting the machines for the first time, the xserver was unable to start (which was expected, since it is a new chipset). I then ran 'sudo dpkg-reconfigure xserver-xorg' and selected the Intel i810 driver. When using this driver I was still unable to start xserver.

Eventually I gave up and just used the VESA driver to get the systems in a working state. This driver is inadequate however and I need to get a proper driver working since people are going to spend 8 hours a day in front of these machines and watching this fuzzy display will give anyone a headache.

Any help greatly appreciated

---

### Post by DizzyTech on 2008-06-09
If they're not using Compiz, they're much better off using the intel driver.  You might have to reconfigure their displays... which works much better in Hardy, so YMMV.

---

### Post by Thelasko on 2008-06-09
The i810 driver is WAY too old for that chipset.  Try the Intel driver.  If it's not installed on your system it's called "xserver-xorg-intel".  It's leaps and bounds better than the i810.

---

### Post by Yellow Pasque on 2008-06-09
[http://www.intellinuxgraphics.org/man.html](http://www.intellinuxgraphics.org/man.html)

---

### Post by Thelasko on 2008-06-09
I believe Temüjin sent you the wrong link.  You want [this one]("http://www.intellinuxgraphics.org/install.html") and [this one]("http://packages.ubuntu.com/hardy/x11/xserver-xorg-video-intel").
The intel site says:
>  Xorg 2D driver: xf86-video-intel
The Ubuntu site says:
> This package is built from the X.org xf86-video-intel driver module.

---

### Post by Yellow Pasque on 2008-06-09
> I believe Temüjin sent you the wrong link.
No, I was providing the xorg.conf options manual (it looks like the options are the same for both the i810 and intel drivers). I don't recommend building the latest source. Just use the intel driver included with Ubuntu.

---

### Post by Thelasko on 2008-06-09
Just to recap "intel" is the latest and best driver in the repositories.  I referenced the page above to make the point that it is the newest.  The i810 is old and should not be used (although it is still available in the repositories, which sometimes causes confusion).

In my experience, the intel driver is very easy to setup.  Just run ```
dpkg-reconfigure-xserver-xorg
``` to set your resolution and it does everything else.

---

