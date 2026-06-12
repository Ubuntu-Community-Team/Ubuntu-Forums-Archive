---
title: "Not the way I wanted to start Xmas"
date: 2007-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by netsurfau on 2007-12-25
When I booted up my AMD X2 6000+ (Dual-core 3Ghz, 4Gb Corsair RAM, Nvidia 8600 GTS Super) on Xmas morning I got the following warning message:

[I]"Ubuntu is running in Low Graphics mode

Your screen and graphics card could not be 
detected correctly.  To use higher resolutions, visual
effects or, multiple screens, you have to configure
the display yourself."[/I]

Then, there's a check box for the option to run in low graphics mode
all the time, followed by three buttons labeled - 
*Configure....        Shut Down             Continue*

The system was working fine Xmas eve.  I shut down the system then 
headed to bed.  Got up in the morning to this.

I tried running recovery mode which, after logging in & entering "telinit 3"
was able to get back in with my original resolution settings.  But now,
26th, I can't even get telinit 3 to work now.  I checked out Nvidia's web
site for a possible updated driver but, was unable to get it installed 
(another issue for later) and found it has some problems that be fixed
till Jan some time.

I made no changes to my system on the 24th & can't work out what is
going on.  System specs are:

CPU:  AMD X2 AM2-64bit Dual-Core 6000+ (3Ghz)
RAM:  4Gb Corsair (4 x 1Gb)
Video:  Nvidia 8600 GTS Super, 512MB RAM, 128bit
OS: Ubuntu 7.10  AMD 64bit with all current updates.

---

### Post by John Jason Jordan on 2007-12-25
> **netsurfau said:**
> When I booted up my AMD X2 6000+ (Dual-core 3Ghz, 4Gb Corsair RAM, Nvidia 8600 GTS Super) on Xmas morning I got the following warning message:

[I]"Ubuntu is running in Low Graphics mode

Your screen and graphics card could not be 
detected correctly.  To use higher resolutions, visual
effects or, multiple screens, you have to configure
the display yourself."[/I]

Then, there's a check box for the option to run in low graphics mode
all the time, followed by three buttons labeled - 
*Configure....        Shut Down             Continue*

The system was working fine Xmas eve.  I shut down the system then 
headed to bed.  Got up in the morning to this.

I tried running recovery mode which, after logging in & entering "telinit 3"
was able to get back in with my original resolution settings.  But now,
26th, I can't even get telinit 3 to work now.  I checked out Nvidia's web
site for a possible updated driver but, was unable to get it installed 
(another issue for later) and found it has some problems that be fixed
till Jan some time.

I made no changes to my system on the 24th & can't work out what is
going on.  System specs are:

CPU:  AMD X2 AM2-64bit Dual-Core 6000+ (3Ghz)
RAM:  4Gb Corsair (4 x 1Gb)
Video:  Nvidia 8600 GTS Super, 512MB RAM, 128bit
OS: Ubuntu 7.10  AMD 64bit with all current updates.
1) Are you using the open source "nv" driver or the proprietary nVidia driver?
2) Check for what Linux thinks the video card is called. Get this with lspci from the command line.
3) Open your /etc/X11/xorg.conf file and look for the card. If it is not the same as what you got from lspci, you may have to edit xorg.conf yourself.
4) If you are using the open source driver, try installing the nVidia driver, or vice-versa.

---

### Post by netsurfau on 2007-12-26
G'day John,

1) Are you using the open source "nv" driver or the proprietary nVidia driver?
    **nv**

2) Check for what Linux thinks the video card is called. Get this with lspci from the command line.
    **nVidia 8600 GTS** what the card actually is
    
3) Open your /etc/X11/xorg.conf file and look for the card. If it is not the same as what you got from lspci, you may have to edit xorg.conf yourself.
     **xorg.conf showed correct card**

4) If you are using the open source driver, try installing the nVidia driver, or vice-versa.
    **unable to install.**

Have latest 64bit driver from nVidia, which requires installation with X windows NOT running.  Not very easy to do, ended up booting into "telinit 1" & eventuall got an error about missing "libc development" library.

Also tried changing existing xorg.conf with an older, known working backup.
Didn't make any difference.  Ideas?

---

### Post by John Jason Jordan on 2007-12-26
> **netsurfau said:**
> 
1) Are you using the open source "nv" driver or the proprietary nVidia driver?
    **nv**

2) Check for what Linux thinks the video card is called. Get this with lspci from the command line.
    **nVidia 8600 GTS** what the card actually is
    
3) Open your /etc/X11/xorg.conf file and look for the card. If it is not the same as what you got from lspci, you may have to edit xorg.conf yourself.
     **xorg.conf showed correct card**

What I meant here is that computers are totally literal. The exact name of the card as stated in lspci, right down to punctuation, capital letters, and so on, must be identical.

> **netsurfau said:**
> 4) If you are using the open source driver, try installing the nVidia driver, or vice-versa.
    **unable to install.**

Have latest 64bit driver from nVidia, which requires installation with X windows NOT running.  Not very easy to do, ended up booting into "telinit 1" & eventuall got an error about missing "libc development" library.

I do not have the same video card, so it's hard for me to understand why you cannot install the nVidia driver from System > Administration > Restricted Drivers Manager. Is it because the card is new and the driver is not in the repositories? And do you have all the restricted repositories enabled?

> **netsurfau said:**
> Also tried changing existing xorg.conf with an older, known working backup. Didn't make any difference.  Ideas? 

The only thing I know is that I also have nVidia video and initially had the same problem as you. This was a fresh install on a brand new laptop. Gutsy simply did not detect the video at all. I had to edit xorg.conf myself and it took several attempts before I got it working. One of the things that made it work was being sure that the video card name was exactly right. Even so, sometimes I would be booted into Vesa 1024 x 768 for no apparent reason. Eventually I installed the nVidia drivers, and that helped. Even so for a couple months I would suddenly boot into 1440 x 900 instead of the 1680 x 1050 that I had set. I haven't had any problems for a long time now (crossing fingers).

---

### Post by terminal on 2007-12-26
From terminal type sudo dpkg-reconfigure xserver-xorg . This will regenerate your xorg.conf .

---

### Post by netsurfau on 2007-12-26
Seem to have recovered original desktop setup (fingers crossed)

The updated nVidia driver I was trying to install was one I had downloaded from the nVidia
website.  New 64bit Linux driver released 20 Dec 2007.

This time I used the Restricted Drivers, and it half worked.  Had to then go change what
monitor I was using (LCD 1920 x 1200) and now back to regular resolution.

Thanks heaps for the help John, very much appreciated.

Regz

Luke

---

