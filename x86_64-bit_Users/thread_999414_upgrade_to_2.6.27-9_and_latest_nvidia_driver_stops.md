---
title: "upgrade to 2.6.27-9 and latest nvidia driver stops any display"
date: 2008-12-01
forum: x86 64-bit Users
---

### Post by NickD-NLUG on 2008-12-01
I upgrade my 8.10 system to the latest kernel, nvidia driver, and other bits and pieces using the Update Manager. I rebooted... and now I have completely blank screens. No signal is being sent to them so they power off soon after booting. gdm is running, and /etc/init.d/gdm restart has no effort.

No errors in any logs from /var/log, no errors anywhere as far as I can tell.

Any suggestions on where I start on this?  Even a suggestion of what logs to look at?

Dual-headed set up, with two different X servers.  Card used is a 

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)

There's also a GeForce4 MX420 in the PC, but that's unused.

Thank you.

---

### Post by felker2 on 2008-12-02
I guess you're using the proprietary driver for you nvidia card?


I'm not sure, but first try:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```

en try starting the X server (or just restart).

If that does not work, I would boot the live CD and copy the /etc/X11/xorg.conf of the live session to your hard disk. Then reboot from the harddisk and you should be using the open source driver for nvidia.

HTH

---

### Post by m_l17 on 2008-12-02
If you where using the beta Nvidia driver[180] before the the kernel upgrade. Take a look at this: 

[http://ubuntuforums.org/showthread.php?t=835573]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by stchman on 2008-12-02
If you did not use the Restricted drivers then a kernel update will wipe them out.

---

### Post by NickD-NLUG on 2008-12-02
> **felker2 said:**
> I guess you're using the proprietary driver for you nvidia card?


Yes, version 177 iirc.

> **felker2 said:**
> 
I'm not sure, but first try:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```

en try starting the X server (or just restart).

If that does not work, I would boot the live CD and copy the /etc/X11/xorg.conf of the live session to your hard disk. Then reboot from the harddisk and you should be using the open source driver for nvidia.

HTH

Ah, unfortunately I need to leave xorg.conf exactly as it was.  After about a week, and a friend's help for an evening, I managed to get the X server working with the correct resolutions for my dual headed set up.

That said I did change the drivers to "nv" rather than "nvidia", and I got one screen back.  However the other screen is then some kind of clone of the first screen, but only about a quarter of it.

---

### Post by NickD-NLUG on 2008-12-06
So far I've tried all the different versions of the nvidia driver available using apt-get, all of them fail.

My Xorg.0.conf file also only gets this far:

= = = = =
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX

Backtrace:

Backtrace:
= = = = =

I'm struggling to find anyone with a similar issue, let along a solution... help...

---

### Post by Anonymous111 on 2008-12-06
Im having a similar issue with my two nvidia 8500 GT's, are you running SLI, or just one card?

also, when you run /etc/init.d/gdm restart or startx,  do u get an error that says something along the lines of "Primary card is not in PCI slot........No screens found..." ?

---

### Post by NickD-NLUG on 2008-12-06
> **m_l17 said:**
> If you where using the beta Nvidia driver[180] before the the kernel upgrade. Take a look at this: 

[http://ubuntuforums.org/showthread.php?t=835573]("http://ubuntuforums.org/showthread.php?t=835573")

I wasn't... but would you recommend it?  While wandering around the Interweb about this problem it did seem as though a lot of people are recommending the 180 driver.

---

### Post by NickD-NLUG on 2008-12-06
> **Anonymous111 said:**
> Im having a similar issue with my two nvidia 8500 GT's, are you running SLI, or just one card?

I don't *think* I'm running SLI, there's two graphics cards in the box... but one of them isn't used, I've just neglected to take it out.

> **Anonymous111 said:**
> also, when you run /etc/init.d/gdm restart or startx,  do u get an error that says something along the lines of "Primary card is not in PCI slot........No screens found..." ?

I've seen that issue mentioned elsewhere, but that's not the problem.

The latest state of affairs is that I can boot dual-headed by disabling GFX in xorg.conf.  That means I've got no compiz, and also to get this to work I've had to enable EDID on one of the monitors, which means it's not in as high a resoltuon as it can support, and xrandr and the nvidia programs don't give me the option to take it to that resolution.

However I am running dual headed again... so that will do for now.

I'm wondering if the problem is that I'm somehow using 32bit drivers rather than 64bit drivers, going by a quick look at the output of ldconfig -v... but I'm unsure of how to figure that out...

---

### Post by NickD-NLUG on 2009-01-10
> **NickD-NLUG said:**
> The latest state of affairs is that I can boot dual-headed by disabling GFX in xorg.conf.  That means I've got no compiz, and also to get this to work I've had to enable EDID on one of the monitors, which means it's not in as high a resoltuon as it can support, and xrandr and the nvidia programs don't give me the option to take it to that resolution.

However I am running dual headed again... so that will do for now.

I'm wondering if the problem is that I'm somehow using 32bit drivers rather than 64bit drivers, going by a quick look at the output of ldconfig -v... but I'm unsure of how to figure that out...

Anyone?

Installing the nvidia-180 driver hasn't fixed the problem.

---

### Post by NickD-NLUG on 2009-01-28
> **NickD-NLUG said:**
> Anyone?

Installing the nvidia-180 driver hasn't fixed the problem.

Uninstalling everything to do with my attempts to manually install the nvidia driver hasn't fixed the problem.

Uninstalling and reinstalling everything to do with nvidia hasn't fixed the problem.

Any ideas where I should go with this?

---

### Post by NickD-NLUG on 2009-02-07
> **NickD-NLUG said:**
> Uninstalling everything to do with my attempts to manually install the nvidia driver hasn't fixed the problem.

Uninstalling and reinstalling everything to do with nvidia hasn't fixed the problem.

Any ideas where I should go with this?

Well I've got glx working again, thanks to adding the IgnoreABI option, as seen in this thread...

[http://ubuntuforums.org/showthread.php?t=1021484](http://ubuntuforums.org/showthread.php?t=1021484)

Now to get "Visual Effects" enabled again :)

---

