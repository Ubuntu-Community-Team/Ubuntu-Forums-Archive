---
title: "login screen missing"
date: 2008-05-22
forum: x86 64-bit Users
---

### Post by hvacr on 2008-05-22
This is very strange, I have my system set up to auto login, which is fine. When I choose log out in the shut down screen, when the new login screen should appear, I get nothing. The only way I know it at the screen is by the tone it makes. I can login by typing my info, but I see nothing.

---

### Post by warp99 on 2008-05-22
> **hvacr said:**
> This is very strange, I have my system set up to auto login, which is fine. When I choose log out in the shut down screen, when the new login screen should appear, I get nothing. The only way I know it at the screen is by the tone it makes. I can login by typing my info, but I see nothing.

Try reinstalling the login screen to replace any files that may be missing:
```
sudo apt-get install --reinstall gdm
```
if that does not work you can purge the original files then reinstall:
```
sudo apt-get remove --purge gdm && sudo apt-get install gdm
```
Don't worry if the package manager wants to remove 'ubuntu-desktop' since this is only a meta-package and will not remove the actual desktop.

---

### Post by hvacr on 2008-05-22
Thanks

I tried both options, but either one worked, still left with no login screen.

I have found out what my problem is. I have dual monitors, one which I do not use when I run ubuntu. Seems the primary monitor has been switched to the one I do not use. The login screen shows up there. Catalyst control center shows the screens as my main monitor is 1, and the secondary as 2. When I click on identify monitors, it shows my main one as number 2. Not sure what will fix this, mat remove the driver and try again.

---

### Post by hvacr on 2008-05-22
Seems to be a bug with the ATI drivers, with the vesa drivers, the login screen appears on both monitors. Very strange.

---

### Post by warp99 on 2008-05-22
You can manually set the force-monitors option in your xorg.conf by using the aticonfig tool that is included with the restricted drivers. Open a terminal and type 'sudo aticonfig --help | more' for additional information. Some more information on settings the options manually can be found here:

[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)

Edit:

**Don't** remove the driver and reinstall since it's a configuration issue and not a driver issue.

---

### Post by hvacr on 2008-05-23
I will look into this tonight. I still say it is an ATI drivers issue, when the Vesa driver is used this does not happen. Seems many people with Ati are having this same issue.

---

### Post by warp99 on 2008-05-23
> **hvacr said:**
> I will look into this tonight. I still say it is an ATI drivers issue, when the Vesa driver is used this does not happen. Seems many people with Ati are having this same issue.

If you set the force-monitor option as the following:

```
sudo aticonfig --force-monitor=crtl1,nocrtl2
```

The second monitor is disabled regardless of the physical connection as per the help guide:
```
--force-monitor=STRING[,STRING...]
        Describe all displays that are to be enabled and/or disabled regardless
        of physical connection.  STRING can be one or more of the following
        set, separated by commas:
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            tmds2i
            nocrt1
            nocrt2
            nolvds
            notv
            notmds1
            notmds2
            notmds2i

```

Since you do not use the second monitor with Ubuntu it can be disabled. You can also disable the second monitor real time with the following string:

```
aticonfig --enable-monitor=crtl1 --effective=now
```

You may have to place this command as an autostart if your other operating system turns on dual monitor support but the Linux ATI driver somehow ignores the force-monitor setting. Most likely you need to experiment a little with the settings until you have the desired setup.

---

### Post by hvacr on 2008-05-24
Thanks

I disabled the second screen, all is well.

---

### Post by jonez176 on 2008-12-26
> **warp99 said:**
> Try reinstalling the login screen to replace any files that may be missing:
```
sudo apt-get install --reinstall gdm
```


Thanks!  This worked for me after trying soo many other "fixes"...  My problem was that x wasn't even starting at all.  I would boot up my computer, and it would just take me to the command-line login.  I would then have to log in via command line and use startx to get Gnome running.

I started having this problem when my laptop failed to come out of sleep mode, and I was forced to hard-reboot it.  I could be wrong, but that's really the only thing I think could have caused the problem.

---

