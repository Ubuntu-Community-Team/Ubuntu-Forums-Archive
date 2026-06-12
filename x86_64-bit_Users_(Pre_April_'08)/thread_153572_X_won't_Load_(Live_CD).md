---
title: "X won't Load (Live CD)"
date: 2006-04-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by bpat1434 on 2006-04-01
So I'm trying out Ubuntu and have an AMD64 and when I insert the LiveCD (either 32-bit or 64-bit) everything is fine, until just after it loads the HP Linux Printing stuff, it tries to start the X WIndows Server and it says that there were errors.  I thought maybe it was my screen resolution so I tried again.  Each time had the same results.

I got the free cds from ShareIt! late last year, would there be an issue with it now?  Any ideas as to why this might be happening?

[ **UPDATE** ]
Look down at the next post, I updated it with more info about my problem.  Specifically the output from X.

---

### Post by bpat1434 on 2006-04-03
*bump*

Anyone?  Seems the live CD has a lot of issues....

Narrowed it down a bit:
X-Server gives me an error saying it can't find any screens. Here are some system specs:

AMD Athlon 64 3700+
2GB RAM
(2) 160 GB ATA drives
(2) 150 GB SATA drives
MSI RX800-Pro TD256E PCI-E video-card (General ATI card)
SyncMaster910T monitor

---

### Post by bpat1434 on 2006-04-03
Crap... can't delte my own posts.... that sucks....

---

### Post by skylark on 2006-04-04
Hi bpat1434,

I haven't run into this myself, but here is some stuff from elsewhere on the forums I've rehashed for you here:

When you boot up, try CTRL+ALT+F1 to see if you can get a terminal. Then you can login and do:

sudo nano /etc/X11/xorg.conf

to edit xorg.conf.

In that file try replacing the "ati" driver with "vesa". (i.e. there is a line that reads: Driver "ati" <- replace this with Driver "vesa")

then do CTRL+X to exit and indicate that you want to save the file. When you are back at the prompt, try restarting gdm:

sudo /etc/init.d/gdm restart (for gnome)
for KDE, it might be:
sudo /etc/init.d/kdm restart (or just do startx)

If this doesn't work, you might need to play with the x.org config file a bit more:
try using the "radeon" or "fglrx" drivers instead of "ati"/"vesa". You might also have to add the following option to the file: Option "VideoOverlay" "on"
And potentially you might have to set your DefaultDepth to 24

Hope that some combination of those options works for you!

NB: vesa drivers are really slow compared to the official ATI drivers. Here is a good howto to install the full drivers: [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

---

### Post by pallaire on 2006-04-06
The modification of the xorg.conf does not work for the LiveCD.  It is as if X does not read the modified xorg.conf when restarting !

But it works fine if you install.... I did that yesterday.

---

### Post by bpat1434 on 2006-04-06
[QUOTE=pallaire]The modification of the xorg.conf does not work for the LiveCD.  It is as if X does not read the modified xorg.conf when restarting ![/QUOTE]

Yeah it does... you're not supposed to restart the system, just try and start KDE or Gnome.

The xorg.conf file workaround worked for me.  I had to modify the driver and that was it.  So it does work, but don't restart the system.  Just try and run Gnome or KDE again.

---

