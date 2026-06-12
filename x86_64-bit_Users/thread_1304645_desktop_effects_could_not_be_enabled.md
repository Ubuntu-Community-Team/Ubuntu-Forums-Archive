---
title: "desktop effects could not be enabled"
date: 2009-10-29
forum: x86 64-bit Users
---

### Post by superaktieboy on 2009-10-29
hi,
I have a problem with enabling the desktop effects.. everytime i try to enable them, it says "Desktop effects could not be enabled".. i read on other topics about this, but they all seemed to be aimed at ubuntu 8.10 and lower, however, i have 9.10 x86 .. i have a ATi mobility radeon 3470.. i saw in other topics that many asked for the output of compiz and the output of lspci.. so here they are:
lcpci:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```


the output of compiz:
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
```

anyone know what the problem is?

---

### Post by c_martini on 2009-10-29
I am having a similar problem with the exact same ati graphics chip (ATi mobility radeon 3470): [http://kubuntuforums.net/forums/index.php?topic=3107345.0]("http://kubuntuforums.net/forums/index.php?topic=3107345.0")

In order to get the desktop effects enabled, we need to install the proprietary ATI driver as that supports the 3d acceleration the desktop effects need to run.

On my new fresh install of Kubuntu 9.10 x64, there is no prompt to install the proprietary driver like there was when I evaluated the 32bit release candidate.

i'm confused here as well...

---

### Post by QIII on 2009-10-29
You can install Catalyst 9.10 (ATI ONLY made the pre-release version available for Karmic) from the repos.

But BEFORE you install it, make sure that your card is supported by dropping by ATI/AMD's website.

---

### Post by superaktieboy on 2009-10-29
actually c_martini's post helped, i deleted the drivers from ATi.. installed the proprietary drivers.. then logged out and logged in.. didn't work, however, after a restart, it worked like a charm! :) cheers!

---

### Post by c_martini on 2009-10-29
> **QIII said:**
> You can install Catalyst 9.10 (ATI ONLY made the pre-release version available for Karmic) from the repos.

But BEFORE you install it, make sure that your card is supported by dropping by ATI/AMD's website.

Ok, so is this done by downloading direct from the website and installing per instructions on the ATI site or is this to be found somewhere in the repositories?

[QUOTE=superaktieboy]actually c_martini's post helped, i deleted the drivers from ATi.. installed the proprietary drivers.. then logged out and logged in.. didn't work, however, after a restart, it worked like a charm![/QUOTE]

Glad my post was able to help someone!

---

### Post by c_martini on 2009-10-29
UPDATE:

I first removed 'xorgdriver-fglrx 2:8.660-0ubuntu4' and then just installed the proprietary driver from the ATI site: 

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.25&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.25&lang=English)

For Karmic, it needs no additional packages installed, just open Dolphin as root ```
kdesudo dolphin
``` and browse to the directory where you downloaded the driver file. Go to tools, open terminal. run the install by typing the following command with the driver script name after it: ```
./ati-driver-installer-9-10-x86.x86_64.run
``` . Restart your pc or you can alternatively just restart x.

Desktop effects can now be enabled in the desktop applet in system settings.

---

### Post by QIII on 2009-10-29
c_martini ...

What you have effectively done is exactly what would have happened if you had installed Catalyst from the repos.  The driver you used (9.10) had already been made available to Canonical for inclusion in Karmic.

In effect, the "proprietary driver" offered in Karmic is that driver.

It may be that ATI has made that driver available for public consumptions since I used the Karmic repo to install it.  They rushed it out specifically to get it into Karmic, leaving other Linux distributions in the cold.

If it is available now for public consumption, then that is great for ATI.  They've been at the back of the pack looking at nVidia's rear end for too long.

(Now if I could just get them to make a driver for OpenSolaris...)

---

### Post by c_martini on 2009-10-30
> **QIII said:**
> c_martini ...

What you have effectively done is exactly what would have happened if you had installed Catalyst from the repos.  The driver you used (9.10) had already been made available to Canonical for inclusion in Karmic.

In effect, the "proprietary driver" offered in Karmic is that driver.

It may be that ATI has made that driver available for public consumptions since I used the Karmic repo to install it.  They rushed it out specifically to get it into Karmic, leaving other Linux distributions in the cold.

If it is available now for public consumption, then that is great for ATI.  They've been at the back of the pack looking at nVidia's rear end for too long.

(Now if I could just get them to make a driver for OpenSolaris...)

Yeah, this is what I suspected. However, the driver was not being offered through the hardware drivers app in the final Karmic release like it was in the release candidate. Even searching through normal repos yeilded only the old fglrx driver.
Its nice to see ATI have caught up in the game. That was probably the easiest graphics driver install I have ever done in any Linux distro. :D

---

### Post by hagabaka on 2009-11-02
I got this problem too, with ATI Radeon 9800 Pro and "radeon" driver starting from the second boot after upgrading to Karmic. glxinfo says direct rendering is on, yet desktop effects cannot be enabled. I thought I rebooted after upgrading, but maybe I only logged off..

Before upgrading, there were no problems using desktop effects with the same card and radeon driver, so I don't know why I'd have to use flgrx...actually flgrx probably doesn't support my card any more.

---

