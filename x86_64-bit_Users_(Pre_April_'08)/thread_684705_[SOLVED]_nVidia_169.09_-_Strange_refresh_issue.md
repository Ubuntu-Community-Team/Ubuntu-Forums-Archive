---
title: "[SOLVED] nVidia 169.09 - Strange refresh issue"
date: 2008-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2008-02-01
My monitor is NORMALLY set at 1152x864 at 85 Hz.  After installing the new driver, I launched nvidia-settings and set my refresh from 54 Hz (that's what the default install left me with) back to 85 Hz with no problem.  **HOWEVER...  **If I go to the Ubuntu screen resolution applet, it tells me I running 1152x864 @ 121 Hz. 

What's up with that?  Which one do I trust.  I'm guessing it's at 85 Hz because that's the highest I'm aware this monitor can support at the current resolution, but what gives?

Thanks

---

### Post by crjackson on 2008-02-01
Really, no one wants to help?

---

### Post by crjackson on 2008-02-02
bump...

---

### Post by Black Magix on 2008-02-02
theres been a lot of problems with the Nvidia Drivers latley.....it destroyed me wireless card interface and  GNOME. I can't drag, minimize, maximize, or close windows anymore.

---

### Post by crjackson on 2008-02-02
> **Black Magix said:**
> theres been a lot of problems with the Nvidia Drivers latley.....it destroyed me wireless card interface and  GNOME. I can't drag, minimize, maximize, or close windows anymore.

Really, I haven't heard of that one...

---

### Post by crjackson on 2008-02-02
Well, I've just tried again from a clean install and it made no difference.

---

### Post by Sockerdrickan on 2008-02-02
There is a new driver it might help but I doubt it.

---

### Post by crjackson on 2008-02-02
> **Tux0r said:**
> There is a new driver it might help but I doubt it.

Newer than 169.09?

---

### Post by Sockerdrickan on 2008-02-02
[ftp://download.nvidia.com/XFree86/Linux-x86_64/171.05/NVIDIA-Linux-x86_64-171.05-pkg2.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/171.05/NVIDIA-Linux-x86_64-171.05-pkg2.run)
171.05

---

### Post by crjackson on 2008-02-02
Dang, I'm always running behind.  How long do you think it will be, before Alberto includes this one in the Envy project?

---

### Post by Sockerdrickan on 2008-02-03
Why not just install it?

```
GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start
```

---

### Post by crjackson on 2008-02-03
> **Tux0r said:**
> Why not just install it?

```
GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start
```

I'll prolly do it later today and see how it goes.  Are you using this driver?  What is your impressions of it?

---

### Post by Sockerdrickan on 2008-02-03
I am using the 169.09 currently since this new one hasn't been released officially yet. I don't have any kind of troubles with my 8800 :KS

---

### Post by Toffeeapple on 2008-02-03
> **crjackson said:**
> . 

What's up with that?  Which one do I trust.  I'm guessing it's at 85 Hz because that's the highest I'm aware this monitor can support at the current resolution, but what gives?

Thanks

Hi..

if it's any consolation my ubuntu Screen resolution applet has never coincided with what the actual refresh rate of my monitors is.. They are both at 60 according to both their own OSD and Nvidia-settings.. while ubuntu tells me they are at 51.

---

### Post by crjackson on 2008-02-03
> **Toffeeapple said:**
> Hi..

if it's any consolation my ubuntu Screen resolution applet has never coincided with what the actual refresh rate of my monitors is.. They are both at 60 according to both their own OSD and Nvidia-settings.. while ubuntu tells me they are at 51.

It was actually reporting perfectly with the older driver.  Perhaps something in the driver has changed and Ubuntu just doesn't read the setting correctly anymore.

---

### Post by Toffeeapple on 2008-02-03
> **crjackson said:**
> It was actually reporting perfectly with the older driver.  Perhaps something in the driver has changed and Ubuntu just doesn't read the setting correctly anymore.

I'd be inclined to believe what your monitors OSD tells you.. and go from there : ) for example, compiz for me detects 50 and I get tearing when I move windows about.. If I set it manualy to 60 in General Options (within CompizConfig) the tearing goes away.

---

### Post by crjackson on 2008-02-03
> **Tux0r said:**
> I am using the 169.09 currently since this new one hasn't been released officially yet. I don't have any kind of troubles with my 8800 :KS

I think I'll just stay with 169.09 since I'm having no other issues.  I'll wait for an official release...

---

### Post by crjackson on 2008-02-06
After running the Ubuntu updates that came out today (or lastnight), I noticed there seem to have been some kernel updates.  I rebooted and I was in low graphics mode.

I re-ran the Envy script to reinstall my graphics driver and it seems okay at this point.  Running the script did un-do any of the Ubuntu updates did it?

```
charles@MSI-K8N-Neo4-SLI-Platinum:~$ uname -r
2.6.22-14-generic

```

Just hoping that envy didn't reverse the update somehow to fix itself. 

Is there a way to install a graphics driver so that when these types of updated come through that it won't require reinstall of the driver?

---

### Post by dabl on 2008-02-06
Two clarifications/suggestions:

1. When running the downloaded driver installer, at the end of the installation routine where it asks if you want it to write a new xorg.conf file, say "no".

2. When you're back to the CLI, run ```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
``` to set up the xorg.conf file for compiz.

THEN you can start the X server.  If you don't like the first screen resolution that you see, open a console window on your desktop and (depending on whether your are running Gnome or KDE) do ```
gksu nvidia-settings
``` or ```
kdesu nvidia-settings
``` to run the nvidia settings utility in Super User mode.  On the "X Display Configuration" panel, click "detect displays" then set the resolution the way you want it, leave "refresh" set to "auto", and click the "Save to X Configuration File" and then "save" to make this the default desktop resolution.

You're done!  :)


p.s.  In Hardy Heron, just install the "nvidia-glx-new" package -- it has driver 169.09 already packaged.  :)

---

### Post by Anubis on 2008-02-06
> **Tux0r said:**
> [ftp://download.nvidia.com/XFree86/Linux-x86_64/171.05/NVIDIA-Linux-x86_64-171.05-pkg2.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/171.05/NVIDIA-Linux-x86_64-171.05-pkg2.run)
171.05

[http://www.phoronix.com/scan.php?page=article&item=987&num=1](http://www.phoronix.com/scan.php?page=article&item=987&num=1)

Last night NVIDIA quietly uploaded a new Linux display driver to their FTP server. This new driver is tagged 171.05, while the latest public driver has been 169.09. Having already three releases in the 169.xx series, this is a moderate update to 171.xx, but according to NVIDIA it's not for everyone. There is no official change-log that NVIDIA has published for the 171.05 driver, and the change-log that ships with the driver hasn't been updated (whether it be intentional or not). The only word that has come out of the NVIDIA camp on this new driver is from Christian Zander and he has said that this driver is only intended for use with the Tesla S870 GPU Computing Systems. The legacy NVIDIA Linux drivers have also been updated this week.

---

### Post by crjackson on 2008-02-06
> **dabl said:**
> Two clarifications/suggestions:

1. When running the downloaded driver installer, at the end of the installation routine where it asks if you want it to write a new xorg.conf file, say "no".

2. When you're back to the CLI, run ```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
``` to set up the xorg.conf file for compiz.

THEN you can start the X server.  If you don't like the first screen resolution that you see, open a console window on your desktop and (depending on whether your are running Gnome or KDE) do ```
gksu nvidia-settings
``` or ```
kdesu nvidia-settings
``` to run the nvidia settings utility in Super User mode.  On the "X Display Configuration" panel, click "detect displays" then set the resolution the way you want it, leave "refresh" set to "auto", and click the "Save to X Configuration File" and then "save" to make this the default desktop resolution.

You're done!  :)


p.s.  In Hardy Heron, just install the "nvidia-glx-new" package -- it has driver 169.09 already packaged.  :)


Excellent information dabl - Thanks for jumping in.

---

