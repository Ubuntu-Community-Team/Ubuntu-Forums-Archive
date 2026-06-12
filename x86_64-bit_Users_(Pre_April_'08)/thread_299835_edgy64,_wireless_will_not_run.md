---
title: "edgy64, wireless will not run"
date: 2006-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by velozoom on 2006-11-14
Have an HP dv9000 laptop (AMD64 Turion X2 2.0 Ghz, 1Gb ram) with a BCM4310 UART wireless nic running 64bit Edgy.  I downloaded the windows .exe and extracted the files for the wireless nic and then installed the BCMWL5.INF driver via ndiswrapper like so- 
```

# ndiswrapper -i bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2

```

ndiswrapper shows the driver as installed and the hardware as being present.  Device manager sees the hardware.  The wireless connection (eth1) shows in System >Administration >networking and is configurable.  It does NOT, however, show in System >Administration >Network Tools.  Only lo and eth0 (wired) show,  I installed gnome-network-manager and see both network connections but when I attempt to open the wireless I receive this message- 
```

SIOCGIFFLAGS error: No such device

```

I am pretty much a noob so and have no clue what that means.  Google hasn't helped figure it out either.  Where do I need to go next to get this card working?

[EDIT] FYI- I've already been all over this in the networking forum....the 64 seems to be the issue so this forum seemed appropriate

---

### Post by incubus on 2006-11-14
velozoom,

I'm ignorant in this area, but just to be sure, did you download the windows 64bit driver for the wireless card?

incubus

---

### Post by velozoom on 2006-11-15
Yup, 64bit driver.  I uninstalled the driver from ndiswrapper and then tried bcm43xx-fwcutter....I think that was mistake because it made no difference and now I can't figure out how to uninstall the driver/firmware.....

---

### Post by mavicdog on 2006-11-15
velozoom
been attentively tracking your progress - having the same issue and have tried all that you have and more with no success. I did find one link (can't find it again) that said there is trouble with wlan and latest edgy kernel. I tried another kernel still not working. I finally gave up and tried dapper - not working - here I can't even see the card. its weird actually. ndiswrapper says hardware/driver present but kernel says ndiswrapper not present when modprobed. at least in edgy I could see the card via network manager or iwconfig. 
 Here are a few links you may check out.
[URL="http://ubuntuforums.org/showthread.php?t=140257"]
[URL="http://ubuntuforums.org/showthread.php?t=285809"]
[URL="http://ubuntuforums.org/showthread.php?t=266088"]
[URL="http://bcm43xx.spugna.org/index.php?topic=110"]

Other problems:
edgy - USB devices only recognized on reboot.
dapper - crazy synaptic touchpad. 
IMHO this laptop is not ready for linux - I will keep trying and keep you posted

re; the firmware install/remove problem - try blacklisting the 43xx (its on of the links)
M.

---

### Post by elizleisndahizle on 2006-12-09
Any progress on this?  I got it to work with absolutely no problems with Sabayon Linux but I want to use Ubuntu, mainly because my Quickplay buttons work :)

---

### Post by lonniehenry on 2006-12-10
I have the amd version of the dv9000 duel booting in xp and Edgy 64 and have used fw-cutter to install firmware drivers.  I used nm-applet-gnome and then used the Hand over control to NetworkManager ("All your interface are belong to us") section of [https://help.uhttps://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.uhttps://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29) to make nm-applet-gnome work. Do the reboot and it will come up.  I am a long time linux user (since breezy) but a new laptop user.

---

