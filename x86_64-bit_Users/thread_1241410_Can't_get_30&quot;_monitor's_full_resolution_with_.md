---
title: "Can't get 30&quot; monitor's full resolution with nvidia drivers, 6800xt on ubuntu 9.04"
date: 2009-08-15
forum: x86 64-bit Users
---

### Post by hjdivad on 2009-08-15
Hi,

I have the following motherboard, graphics card and monitor:

[Gigabyte GA-EP45-UD3P]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128358")

[XFX GeForce 6800XT]("http://www.newegg.com/product/product.aspx?Item=N82E16814150130")

[Samsung SyncMaster 305T]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824001098")


I cannot get resolutions above 1280x800.  nvidia-settings and Xorg.0.conf report the connection link as single link TMDS.  I have a DVI-D cable connecting the monitor and the graphics card, and I've tried both DVI ports.

I'm running Ubuntu 9.04 for x86_64.

I have tried the beta drivers (190.18) as well as the current drivers for Ubuntu 9.04 (180.44) and the current official release (185.18.31).

Please find attached my Xorg.0.log, xorg.conf and output of nvidia-bug-report.sh.




What I would like is to get the monitor's native resolution (2560x1600) or at least 2048x1536.  Please let me know what else I can provide to help debug this problem.


Thanks in advance

---

### Post by bford16 on 2009-08-18
Did you try booting into recovery mode and running nvidia-xconfig?  Also, did you try to reconfigure X? (also in recovery mode) ```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by PatrickVogeli on 2009-08-18
You've said you have a DVI-D cable, have you checked if it actually is a DVI-D dual link cable? 

[IMG]http://www.playtool.com/pages/dvicompat/sldldvi.jpg[/IMG]

Check you have a DL-DVI-D o -I cable.

---

### Post by hjdivad on 2009-08-18
@bford16

I have indeed reconfigured x by running ```
dpkg --reconfigure
``` and ```
nvidia-xconfig
```.


@PatrickVogeli

Yes, I have a DVD-D Dual Link, with three rows of eight pins and no gap.  It's actually the one that came with the SyncMaster and works as I used to have this monitor attached to a different machine.


So it turns out the card is somewhat old, and apparently only supports 2048 x 1536 resolution (per the newegg page).  Of course, that's a lot more than 1280x800, but is it possible that the monitor simply doesn't support resolutions other than 1280x800 and 2560x1600?

---

### Post by hjdivad on 2009-08-21
Well, that seems to have been it.  I moved the 6800 XT to the second PCI slot and put in an 8600 GT to run the Samsung on and now all is well.

Thanks to both of you for the help.

---

