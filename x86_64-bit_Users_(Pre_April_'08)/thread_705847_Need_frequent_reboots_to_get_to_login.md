---
title: "Need frequent reboots to get to login"
date: 2008-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by gfahey on 2008-02-23
I made a post a couple of days ago about this and thought it was fixed. But, upon every shutdown or reboot, I need to manually reboot several times (or more) to get to the login screen.

It will boot to grub and then appear to go to the login screen but, it never does. I just keep hitting the power button (which I hate doing) until it does so. 

Have Dell Vostro 1000 with Integrated ATI Radeon Xpress 1150 HyperMemory. Otherwise, when up and running, it runs like a champ without incident. Man, if I could just get this annoyance fixed it'd be as perfect as I'd want. 

Any help appreciated.

---

### Post by Gen2ly on 2008-02-23
Not good.  Hmmm, my best guess is that either X server is failing to start or (less likely) GDM is failing to do so.  When the desktop is loaded alright take a look for errors in the X server file:

```
cat /var/log/Xorg.0.log | grep -B 2 -A 2 EE
```

Also take a look at [COLOR="SeaGreen"]~/.xsessions-errors[/COLOR].  I believe GDM outputs to there, otherwise check [COLOR="SeaGreen"]/var/log/messages[/COLOR].

---

### Post by gfahey on 2008-02-23
> **Dirk.R.Gently said:**
> Not good.  Hmmm, my best guess is that either X server is failing to start or (less likely) GDM is failing to do so.  When the desktop is loaded alright take a look for errors in the X server file:

```
cat /var/log/Xorg.0.log | grep -B 2 -A 2 EE
```

Get this:

(==) Using config file: "/etc/X11/xorg.conf"
--
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
--
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"


Also take a look at [COLOR="SeaGreen"]~/.xsessions-errors[/COLOR].  I believe GDM outputs to there, otherwise check [COLOR="SeaGreen"]/var/log/messages[/COLOR].

Not quite sure how to go about this above.

---

### Post by Gen2ly on 2008-02-24
I think that you server is doing fine.  Compiz effects will be rendered by software but thats very likely not the issue.  I'm not using Ubuntu at the moment so find out how to stop gdm.  On my system its

```
sudo /etc/init.d/xdm stop
sudo rc-update del xdm
```

But Ubuntu uses a different init.  I'd be curious to know that by using "startx" at the command prompt if circumventing GDM would stop the problem.

---

