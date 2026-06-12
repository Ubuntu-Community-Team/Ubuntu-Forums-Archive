---
title: "Cannot install Ubuntu but can install Kubuntu"
date: 2007-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by timgerr on 2007-02-01
Hey all, have a problem  I have a new 3200 AMD 64bit computer that I want to run Linux under.  When I use the Ubuntu 64 bit GUI boot disk I can get to the desktop but when I try to install I get this mount error during the beginning of the install.  I am able to install Kubuntu.  

The other problem is that I have Kubuntu installed and I go to install Gnome, 
```
apt-get install ubuntu-desktop
```

I get error during the install of ("I think") power or apci.  It just hangs at that install spot and when I reboot my computer, the Kubuntu install is hosed.  I get a fsck error for some reason.  I know the drives are good, they are new.  Like I said I have been running Kubuntu for about 2 months now, I want to have the Gnome desktop installed.  Anyone seen these problems or know what I am doing wrong?

Thanks for the help.

Timgerr

---

### Post by anuradha.d on 2007-02-04
hello pal,

did you check your repositories before you install gnome?. check whether you have the right repos, plus use uptitude instead of apt-get in this matter. 

> #sudo aptitude update
            #sudo aptitude install ubuntu-desktop


if you just want gnome but not all the ubuntu desktop, just do,
> #sudo aptitude install gnome

after installing you have to select the session GNOME in the login window.

good luck.

---

