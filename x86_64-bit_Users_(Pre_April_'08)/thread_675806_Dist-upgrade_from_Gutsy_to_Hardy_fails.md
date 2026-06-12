---
title: "Dist-upgrade from Gutsy to Hardy fails"
date: 2008-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by mjoenby on 2008-01-23
I am quite new to Ubuntu, but I installed Feisty (7.04) x64 from CD. I then upgraded this to Gutsy using "apt-get dis-upgrade" after modifying sources.list. That also works.
the problem is then when I run the dist-upgrade to Hardy ...!!)/T&%¤/&
The upgrade seems to run fine until the end. Some dependencies cannot be fulfilled.
PolicyKit
gnome-session
gnome-session-manager
libhal
.
.
... and a lot more. 20 in total or so ...

I did off course not write them down, but I don't even get the splash or login screen, just the creamy colored screen. The system seems to halt at that point.
I tried from command line running "dpkg-reconfigure -a", but no luck ..

Any help is appreciated. the 32-bit version works fine, but I just wanted to try the 64-bit version ...:(

---

### Post by XplOzIOn on 2008-01-23
Hi, 


I havent tried this myself so i cannot be of much help.

But that creamy screen reminds me of the problem i had in the past. 

Try
```
sudo dpkg-reconfigure xserver-xorg
```

Use vesa to try to load the GDM. Maybe theres a problem with video drivers and thats why you just get the creamy screen. I hope this can help you a Bit.

Cheers,

-DP

---

### Post by Kilz on 2008-01-23
> **mjoenby said:**
> I am quite new to Ubuntu, but I installed Feisty (7.04) x64 from CD. I then upgraded this to Gutsy using "apt-get dis-upgrade" after modifying sources.list. That also works.
the problem is then when I run the dist-upgrade to Hardy ...!!)/T&%¤/&
The upgrade seems to run fine until the end. Some dependencies cannot be fulfilled.
PolicyKit
gnome-session
gnome-session-manager
libhal
.
.
... and a lot more. 20 in total or so ...

I did off course not write them down, but I don't even get the splash or login screen, just the creamy colored screen. The system seems to halt at that point.
I tried from command line running "dpkg-reconfigure -a", but no luck ..

Any help is appreciated. the 32-bit version works fine, but I just wanted to try the 64-bit version ...:(

Since Hardy is still under development, you might want to post questions in its [development forum section.]("http://ubuntuforums.org/forumdisplay.php?f=305") That way people running it that may have fixes for your problem may be able to help you.

---

