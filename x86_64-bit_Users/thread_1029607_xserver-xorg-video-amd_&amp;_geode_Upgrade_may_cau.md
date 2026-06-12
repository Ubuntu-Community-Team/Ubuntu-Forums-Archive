---
title: "xserver-xorg-video-amd &amp; geode Upgrade may cause Multiple Problems"
date: 2009-01-03
forum: x86 64-bit Users
---

### Post by MaindotC on 2009-01-03
Today I ran automatic upgrades on my desktop (listed in my signature) and I seem to be experiencing some problems.  I tried to find the name of the packages buy my Synaptic Package Manager won't list any history for January.  I also conducted the upgrades on my laptop, which for some reason Synaptic does have January history, and these two packages accompanied Wine in the upgrade:
```

xserver-xorg-video-amd (2.9.0-1ubuntu2.4) to 2.9.0-1ubuntu2.5
xserver-xorg-video-geode (2.9.0-1ubuntu2.4) to 2.9.0-1ubuntu2.5

```
I recall seeing two packages named xserver something updated on the desktop as well.  Since I've had this system, I've always installed the ATI driver by downloading it from ATI's site and installing it; **I do not** go to *System -> Administration -> Hardware Drivers* and check the box to enable the ATI restricted driver.  I don't know if there's even a difference, but just wanted to let you know.

The problems I'm having: 

First, the login splash displays even after I'm logged into the system.  It goes away after a while.  While the login splash is displaying any applications I open like calculator, NetworkManager, or Monitor Resolution Settings can't be seen unless I double click on the associative Window List - almost like minimizing then maximizing an application from the bottom panel.

If I disable desktop effects, they do cease but when reboot or ctrl + alt + backspace desktop effects are re-enabled without me selecting them.

I can't change the Monitor Screen Resolution.  It seems to be stuck in 1600x1200 mode and when I try to change it and click "Apply", nothing visibly happens.

How I discovered it:

The ATI Catalyst Control centre couldn't seem to detect my tv, so I tried different physical connections (s-video, RGB Composite, and finally RCA).  It still didn't work even though RCA usually works so I deleted the ati directory with:
```

sudo rm -r /etc/ati

```
and I reinstalled the driver.  Now I have output to my TV, but the other problems I mentioned remain.

Is anyone else having any problems and if not, can you please help me troubleshoot this?  Thanks!

Edit: Now all of a sudden Firefox isn't working properly.  AdBlock Plus disappeared and when I tried to reinstall it, FF closed unexpectedly.  I tried reopening it, and now FF doesn't have any of my bookmarks, and it won't let me log into UF.  When I enter the username and pw, I click "Login" and nothing visibly happens.  That can't be related to xserver updates can it?

---

### Post by MaindotC on 2009-01-03
No one has experienced any similar problems?

---

### Post by sherriesyo on 2009-01-03
woo!good!MONEY-RUNESCAPE provide good and safe [runescape money](http://www.money-runescape.net/) ,[runescape gold](http://www.money-runescape.net/),[runescape power leveling](http://www.money-runescape.net/) and [Runescape Gold](http://www.mmonice.com/Runescape-c-50.html).want to buy them,come here.

---

### Post by Taollan on 2009-01-06
I am having similar problems
After upgrading the same two packages:
xserver-xorg-video-amd (2.9.0-1ubuntu2.4) to 2.9.0-1ubuntu2.5
xserver-xorg-video-geode (2.9.0-1ubuntu2.4) to 2.9.0-1ubuntu2.5
on my laptop (running a ATI mobility radeon 9600) my dual monitor no longer works.  In ATI catalyst control center I can enable the external monitor and set it to "big desktop".  From just the perspective of the laptop, that seems to work (see screenshot), but the external monitor is black. This just started after I performed the two upgrades above.  I could be missing something really obvious, so go easy on me.

---

### Post by MaindotC on 2009-01-07
*sigh* video and wireless threads are tough. I hope someday I can understand linux drivers so I can help others with these problems...

---

### Post by Taollan on 2009-01-12
Update on my problems:
On Friday I did an update which included:
xorg-driver-fglrx (1:7.1.0-8-3+2.6.24.14-22.53) to 1:7.1.0-8-3+2.6.24.16-23.56

Since this update, all my dual monitor problems are no more.

---

### Post by MaindotC on 2009-01-13
I've kind of/sort of not had any problems in a while either.  I can't go to a tty and then go back to tty7 but other than that it's ok.  Very depressing is the lack of interest or help in resolving this issue.  Guess I'll just have to wait till I learn the inner workings of drivers.

---

