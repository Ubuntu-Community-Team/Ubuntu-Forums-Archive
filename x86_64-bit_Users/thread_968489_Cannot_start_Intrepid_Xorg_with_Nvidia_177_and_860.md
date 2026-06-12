---
title: "Cannot start Intrepid Xorg with Nvidia 177 and 8600 card"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by Mouth on 2008-11-02
I cannot get Intrepid Xorg to start with Nvidia binary 177 drivers (or 173) with my 8600M video (ASUS laptop). It worked fine with Hardy :(

I have tried removing nvidia*, compiz*, dkms*, and even jockey* and purging all config files. Then installing the 177 drivers from repo and using hardware drivers(jockey) to install and activate.

Once Xorg loads with the nvidia driver I see the Nvidia logo, but then the screen flashes a few times and Xorg reverts to failsafe.

I have tried using the repo provide Xorg.conf and a barebones Xorg.conf.

I can use the nv drivers without any problems. Even if I use the same Xorg.conf for 'nv' and only change the driver to 'nvidia' I still get the same result - nvidia logo, a few screen flashes, and then failsafe starting.

The Xorg log in /var/log/ doesn't reveal anything (to me) or give any module load errors/problems.

Anyone else experience the same/similiar problem? I search the forums and google, but nothing I found has allowed me get Xorg starting with nvidia 177 (or 173) binary drivers.

Any tips/suggestions?

---

### Post by red_team316 on 2008-11-02
I didn't even get the NVIDIA logo. I killed KDM, logged in via terminal, compiled the 177.80 driver for my 8800GTS 512, and now it's borked. My guess is that NVIDIA is going to come out with another driver. . .

---

### Post by Mouth on 2008-11-02
> **red_team316 said:**
> I didn't even get the NVIDIA logo. I killed KDM, logged in via terminal, compiled the 177.80 driver for my 8800GTS 512, and now it's borked. My guess is that NVIDIA is going to come out with another driver. . .

Have you tried the new beta? [http://www.nvnews.net/vbulletin/showthread.php?t=121763](http://www.nvnews.net/vbulletin/showthread.php?t=121763)
Has a lower revision number than 177.80, but was released/announced after 177.80 !?!

---

### Post by Viranh on 2008-11-02
I'm a little curious about this. I have an Nvidia 8600M GT 512 and I did a clean install of Kubuntu 8.10 when it was beta and booted, selected the 177.8 driver and have had no real problems since. I experience slow down in plasma, but that's a common problem.  Did you upgrade or do a clean install? Maybe that has some effect on things.

---

### Post by red_team316 on 2008-11-02
I did a clean install. 

I have not tried any beta drivers.

---

### Post by Mouth on 2008-11-03
> **Viranh said:**
> I'm a little curious about this. I have an Nvidia 8600M GT 512 and I did a clean install of Kubuntu 8.10 when it was beta and booted, selected the 177.8 driver and have had no real problems since. I experience slow down in plasma, but that's a common problem.  Did you upgrade or do a clean install? Maybe that has some effect on things.

Thanks, your confirmation that it's working spurred me to try again.

I had network upgraded from Hardy through to Intrepid beta, Intrepid RC, and Intrepid final. I also did a re-install using final desktop CD, but keeping my home partition. Under both, I had the problem in my OP and couldn't get it to load/work.

So, after reading your post, tonight I tried the re-install again from Intrepid final desktop CD. Only this time, before rebooting for the install, I moved all ~/.* files into another directory (~$ mv .* ~/OldDotFiles/) beforehand so I would have no X or application setting/configuration files remaining through the re-install.

Now I was able to install nvidia 177 and Xorg successfully loaded with the nvidia binary driver and only the repo's Xorg.conf.

---

### Post by red_team316 on 2008-11-03
Can you explain that step by step? I did a clean install and still borked it.

---

### Post by Goofee691 on 2008-11-03
i am having the same problem with my 2 7900gs cards in my desktop. i just never get to a failsafe x configuration i end up at a terminal login

---

### Post by loomsen on 2008-11-03
Guys, what about posting your xorg.conf files instead of reinstalling and praying for automatic reconfigurattion?

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CPT"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "1440x900 +0+0" "nvidia-autoselect"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

This will work with the 8600.

Should you have 2 cards, or should your card not be found, do this to locate it:
```

me@tiffany:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
me@tiffany:~$ 

```

and change the BusID path of the Device section. And stop reinstalling. It will just delete your current files replacing them with exactly the same ones. You should adjust your Resolution as well...

By the way, it's useful to post your xorg.conf if you got problems configuring it...

---

### Post by Mouth on 2008-11-04
> **red_team316 said:**
> Can you explain that step by step? I did a clean install and still borked it.

1. Open a terminal
2. "cd ~/"
3. "mkdir HardyConfigFiles"
4. "mv .* HardyConfigFiles/"

5. Boot from install CD, and install Intrepid from text boot menu (ie. don't go into 'LIVE CD' mode)
6 (i) If you have separate /home and root(/) partitions, use the partition manager in manual mode to ensure you mount and keep (NOT format) your current /home partition. Mount and format you current root(/) partition. *This is what I did, as I have a separate /home partition*
6 (ii)  If you only have a single partition, then mount it as root(/) and choose to format it. **Make sure you have backed-up any important files elsewhere (eg. DVD(s), USB key, server drive, etc.)

After install is completed...
7. Open a temrinal and "sudo apt-get update"
8 "sudo apt-get upgrade"

9. Open Hardware Drivers
10. Select Nvidia 177 drivers. It will take a few minutes to download and install.
11. Reboot, and voila I had a working Xorg with nvidia binary drivers.

Here is my Xorg.conf after the above ...
> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


---

### Post by Mouth on 2008-11-04
> **loomsen said:**
> Guys, what about posting your xorg.conf files instead of reinstalling and praying for automatic reconfigurattion?

Because many Xorg.conf files posted have more than is required for the Intrepid versions of Xorg. Eg. The mouse and keyboard are not configured by HAL, and not used/required within any Xorg.conf

Other peoples Xorg.conf's can also contains module loads or screen types etc. that means it won't work for other people.

---

### Post by loomsen on 2008-11-04
> **Mouth said:**
> Because many Xorg.conf files posted have more than is required for the Intrepid versions of Xorg. Eg. The mouse and keyboard are not configured by HAL, and not used/required within any Xorg.conf

Other peoples Xorg.conf's can also contains module loads or screen types etc. that means it won't work for other people.


So, you encourage hoping for magic?

More than REQUIRED, not more than allowed.

I prefer using over being used, but if you wanna let yourself get configured... Gogogo.

---

### Post by randalotto on 2008-11-04
I'm having the exact problem described by the OP, albeit with a 7900 card.

Doing a fresh install isn't really an option - I was upgrading and have a lot of stuff that I don't want to have to reconfigure. 

Any more insight on this problem?

---

### Post by Mouth on 2008-11-05
> **loomsen said:**
> So, you encourage hoping for magic?

Using other peoples Xorg.conf files, a "sudo dpkg-reconfigure -phigh xserver-xorg", disabling and re-enabling nvidia drivers, and even re-installing nvidia drivers failed for me.

Using the Xorg.conf that you suggest (and claim that it works - it did not!) also goes against the Ubuntu 8.10 release notes ('X.Org Input Devices')

The solution I gave is one that worked for me, and 2 others, when all others failed - including your Xorg.conf.

Don't go rubbishing working solutions when you have nothing helpful or a working solution to add.

---

