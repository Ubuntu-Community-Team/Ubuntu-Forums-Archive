---
title: "Crash as soon as login window is displayed"
date: 2009-03-20
forum: x86 64-bit Users
---

### Post by g0sp3L on 2009-03-20
I upgraded from 8.04 to 8.1. After completing the installation, I immediately rebooted. Now every time I boot up, the system crashes as soon as the login window appears. (I use the simpler login screen, with blank background and a window.) No text is displayed on the window, and the circular "not-an-hourglass" pointer freezes in the middle of the screen as well.

Part of me thinks that it has something to do with my video, because I'm using on-board video on a pretty old motherboard. It worked fine in 8.04, though. Is it possible that I may need to find and reinstall drivers? If so, how should I go about reinstalling drivers or rolling back?

Thanks, everyone.

---

### Post by baronbaron on 2009-03-22
bump (same problem)

---

### Post by lemming465 on 2009-03-22
If it crashes when it tries to start X, you definitely have a video driver problem.  There was enough churn in the X infrastructure during 8.04 -> 8.10 that various intel, ATI, and Nvidia chips broke, so you are in good company, alas.  Did you happen to try using an 8.10 live CD before trying the upgrade?  It's a recommended way to see if there are any regressions in hardware support.  You are going to have to try to repair this from the command line.  Rolling back an install is not really an option; it is by far easier back up your data, reinstall 8.04 from scratch and restore data than it is to downgrade.  Upgrades are a one-way trip.

Boot in rescue mode (single user root console), and bring up the network by```

/etc/init.d/networking start
```
First repair thing to try:```

aptitude update 
aptitude full-upgrade
dpkg-reconfigure xserver-xorg
reboot
```
If video is still broken, and you are comfortable at the command line, you may want to turn off X for a while.  There are various ways; one is```

mv -i /etc/rc2.d/S30gdm /etc/rc2.d/30gdm.nostart
```
which is easily reversed later by```

mv -i /etc/rc2.d/30gdm.nostart /etc/rc2.d/S30gdm
```

If the above doesn't fix the problem, you'll need to tell us which of reverting to 8.04, continuing to try to fix 8.10, or prematurely upgrading to 9.04 you want to try.  (I'm typing this from 9.04 alpha 6; it will hit beta next week).

Including the output of *lspci -v* and the contents of */var/log/Xorg.0.log* will provide enough more specifics that someone may be able to give you better advice.

---

### Post by baronbaron on 2009-03-23
i tried inputting this fresh update into my shell mode and it can't seem to connect to the internet despite the fact it is plugged straight in...

all this has come when i have so many deadlines...deary me.

---

### Post by NNNNNNNNNN1515 on 2009-03-23
I have a similar problem, and I'm also running 64 bit.
The actual motherboard I'm using is an intel dg43nb with a duocore processor (and I'm using the onboard video, with no proprietary drivers needed as far as I know). I just built the machine a week or two ago. Im running Ubuntu Intrepid Ibex.

I'm extremely lucky that my computer is still usable. 80 percent of the time when I turn on my computer, Ubuntu loads fine. X starts and I'm able to get in to the login screen. However once in a while Ubuntu will fail to display the login screen. The screen goes black, reports "No Signal" and the machine hangs for about 20 Seconds until it reboots itself. This also happens when trying to log on as a different user. 

I suspected X or Gnome was the problem the other day when I went to the command like (ctrl-alt-f1), and turned off x with "sudo /etc/init.d/gdm stop". I then used aptitude to update as many packages as I could, and for the hell of it, I typed "dpkg-reconfigure xserver-xorg" to see if that would make a difference. Well none of these solved my problems, but wouldn't you know it: when I tried to restart X (startx) the problem came up again. Black screen, no signal; reboot. 

I'm not worried about this problem, since 8 out of ten times, Ubtuntu works fine, and even when it fails its a matter of rebooting. However I would like to offer any help I can to get to the bottom of this. Are there any tests or logs I can post that would help anybody?

---

### Post by lemming465 on 2009-03-24
It's possible that the dg43nb problem would be helped by the [motherboard BIOS update from 2/5/09]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2979&OSFullName=&lang=eng&strOSs=38&submit=Go%21#BIO").  So you might try that.

Good log files to check: /var/log/messages, /var/log/Xorg.0.log, and *dmesg | tail -200*

---

### Post by g0sp3L on 2009-03-29
> **lemming465 said:**
> 

If the above doesn't fix the problem, you'll need to tell us which of reverting to 8.04, continuing to try to fix 8.10, or prematurely upgrading to 9.04 you want to try.  (I'm typing this from 9.04 alpha 6; it will hit beta next week).

Including the output of *lspci -v* and the contents of */var/log/Xorg.0.log* will provide enough more specifics that someone may be able to give you better advice.

Thanks for the help and the speedy response. Unfortunately, the solution doesn't seem to work. dpkg-reconfigure xserver-xorg didn't ask me about my video driver or resolution, only keyboard layout settings. Updating seemed to go smoothly, but the problem persists. Also, aside from manually typing the output of lspci -v and the Xorg.0.log file, there is no way for me to post this information, as I am using another machine. ](*,)

I think I'd like to revert back to 8.04, since it ran pretty much flawlessly with my hardware. I guess I'll just find a live CD and do a fresh install, unless there's an easier way. 

Thanks again for the help.

---

### Post by lemming465 on 2009-03-29
> there is no way for me to post (the output of lspci -v and the Xorg.0.log) 
If you can boot in single user mode to a text console, you can run the lspci from the text console, and find an older copy of Xorg.0.log, say /var/log/Xorg.0.log.old.  If you have a USB fob, you can copy the files to that, and then post them from another system.

Or if you find a live 8.04 CD, you can mount the disk partitions to get at the Xorg.0.log file, run lspci, and post directly from the live CD.

You don't want to try to retype the contents, no one would ask you to do that.

> I think I'd like to revert back to 8.04
A perfectly good choice.  Unfortunately doing a fresh install is by far the simplest way to downgrade.

Your trouble with 8.10 means that if you eventually go to 9.04 or 9.10 you'd have to that that via a new install as well.  Assuming 10.04 is the next LTS release an upgrade from 8.04 to 10.04 next year would likely be supported directly.  The key thing is to test with a live CD of the new release to see if the hardware support is good enough before committing to an upgrade.  Usually it gets better rather than worse, but that's not guaranteed, particularly with the more bleeding edge distributions such as Ubuntu or Fedora.

---

