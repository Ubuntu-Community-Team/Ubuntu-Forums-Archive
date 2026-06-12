---
title: "opera browser"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by dickpuller on 2005-10-20
Opera do a .deb for debian i386.....how do I install on my kubuntu 64 bit system? DPKG craps out saying the package is i386 and the system is amd64.
opera is a good browser and I want it. Any words of wisedom would be appreciated!

---

### Post by aysiu on 2005-10-20
I don't know. It doesn't look good:

[http://ubuntuforums.org/archive/index.php/t-40449.html](http://ubuntuforums.org/archive/index.php/t-40449.html)
[http://ubuntuforums.org/archive/index.php/t-75940.html](http://ubuntuforums.org/archive/index.php/t-75940.html)

---

### Post by hammett111 on 2005-10-20
[QUOTE=dickpuller]Opera do a .deb for debian i386.....how do I install on my kubuntu 64 bit system? DPKG craps out saying the package is i386 and the system is amd64.
opera is a good browser and I want it. Any words of wisedom would be appreciated![/QUOTE]

OKAY HERE YOU GO:D 

Go to the Opera site and download the Static-qt "OTHER" package, this contains all the operwrappers and plugins so that Opera (which is only available in 32bit can run on your machine).

When you go to install it type as root 

dpkg -i -force--architecture "opera-qt-static file". 

The -force--architecture command will overide the i386 problem and install it onto your machine. DO NOT WORRY!! This will not harm your system.

Have fun, from your friendly SuSe Crew

---

### Post by nux on 2005-11-15
Alternatively you could try the more correct...

dpkg -i --force-architecture opera*


:p

---

### Post by rplantz on 2005-12-06
There is a thread on this under gnome:

[http://ubuntuforums.org/showthread.php?t=75940&highlight=opera](http://ubuntuforums.org/showthread.php?t=75940&highlight=opera)

I'm running xfce, and it works quite well for me.

The trick is to install the 32-bit static version. Then you don't need chroot.

This is my first experience with Opera. I really like it.

And I'm using its email client, m2. There was a learning curve, but I'm glad I did it. Seems to fit my thought patterns better than most other mail clients.

---

### Post by GameManK on 2005-12-13
I'm upgrading to 64-bit soon and i hope I won't have issues with this.  I always use opera.  I don't see why they can't make a 64-bit compatible package, seems about time.

---

### Post by freedom on 2005-12-20
I second you... :KS 
But as I see on Opera forums, 64bit version is not planed very soon. I really don't know why they delaying with this... 
:confused:

---

