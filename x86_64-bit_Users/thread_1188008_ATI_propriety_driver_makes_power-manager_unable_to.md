---
title: "ATI propriety driver makes power-manager unable to switch off monitor"
date: 2009-06-15
forum: x86 64-bit Users
---

### Post by zelhar on 2009-06-15
Greatings all,

I am running ubuntu 9.04 64bit (and also kubuntu installed). I noticed after enabling ATI propriety driver for my HD3650 (fglrx packs I believe), the power-manager just can't switch off the monitor when the set time is due. Instead it just blanks it (It is not a blank screen saver cause I set up deliberately a non-blank screen-saver to rule it out). 

I also tried using kde's power mangermant with gnomes, I also removed gnomes power manager, installed xfce-power management, and tried any combination of them to no avail. I also switch from gdm to kdm.

The same problem occurs with xubuntu 64bit. 

The only 'solution' I could find is to remove the ATI driver. 

Anyone faced the same bug, any suggestions ?

---

### Post by Yellow Pasque on 2009-06-15
Perhaps fglrx doesn't work with power-managers?

You can still use DPMS. Try enabling it and controlling it with xset command. You can also set it permanently in xorg.conf:

```
Section Monitor
...
Option "DPMS"
EndSection
```

```
Section Serverflags
...
Option "BlankTime" "time"
Option "StandbyTime" "time"
Option "SuspendTime" "time"
Option "OffTime" "time"
EndSection
```

> BlanktTime sets the inactivity timeout for the blanking phase of the screensaver. time is in minutes. This is equivalent to the Xorg server's `-s' flag, and the value can be changed at run-time with xset(1x) . Default: 10 minutes. 

StandbyTime sets the inactivity timeout for the "standby" phase of DPMS mode. time is in minutes, and the value can be changed at run-time with xset(1x) . Default: 20 minutes. This is only suitable for VESA DPMS compatible monitors, and may not be supported by all video drivers. It is only enabled for screens that have the "DPMS" option set (see the MONITOR section below). 

SuspendTime sets the inactivity timeout for the "suspend" phase of DPMS mode. time is in minutes, and the value can be changed at run-time with xset(1x) . Default: 30 minutes. This is only suitable for VESA DPMS compatible monitors, and may not be supported by all video drivers. It is only enabled for screens that have the "DPMS" option set (see the MONITOR section below). 

OffTime sets the inactivity timeout for the "off" phase of DPMS mode. time is in minutes, and the value can be changed at run-time with xset(1x) . Default: 40 minutes. This is only suitable for VESA DPMS compatible monitors, and may not be supported by all video drivers. It is only enabled for screens that have the "DPMS" option set (see the MONITOR section below). 

---

### Post by zelhar on 2009-06-15
Thank you I will try it, however I think there is a problem with this solution- it blanks the screen when a movie is played, isn't it ?

So is there a way to avoid this undesired effect ?

---

### Post by zelhar on 2009-06-15
update: i reinstalled fgrlx and now xset **doesn't** work either. Even when I run xset as root, it only blanks the screen rather than turn it off.

---

### Post by grege on 2009-06-17
I have the same issue with my HD3450 card on an Intel G33 motherboard. If I plug that video card into my old computer with an AMD CPU on an Nvidia chipset the ATI card switches the monitor off as it should.

I do not think that there is any solution. I reported the bug to ATI a long time ago and I am sure many others have as well.

If you have no need for 3d or desktop effects then the open source driver with give you accelerated 2d and video playback, and send the monitor to sleep when it should.

---

### Post by Yellow Pasque on 2009-06-17
Perhaps this will help: [http://ubuntuforums.org/showthread.php?t=1137576](http://ubuntuforums.org/showthread.php?t=1137576)

---

### Post by grege on 2009-06-17
> **Temüjin said:**
> Perhaps this will help: [http://ubuntuforums.org/showthread.php?t=1137576](http://ubuntuforums.org/showthread.php?t=1137576)

Wish I had read this 6 months ago before I chucked the ATI card and bought an Nvidia. Too late to try it now.

---

### Post by zelhar on 2009-06-17
> **Temüjin said:**
> Perhaps this will help: [http://ubuntuforums.org/showthread.php?t=1137576](http://ubuntuforums.org/showthread.php?t=1137576)

That fix works !

Thank you very much Temüjin.

---

