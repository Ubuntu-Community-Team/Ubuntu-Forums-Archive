---
title: "[SOLVED] ATI 200M and AMD64 - got it somebody to work??"
date: 2006-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by beneedict on 2006-12-04
Hej!
I am looking for evidence, if somebody actually got the ATI 200M card (included in my nx6325 notebook) to run with the ATI drivers in Edgy AMD64?
Currently I am using the multiverse ATI drivers, but I tried on my former Edgy installation the original ATI drivers as well. Both according to the well known instructions found here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.31.5_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.31.5_drivers_in_Ubuntu_Edgy_Manually)

But I always ended up in a black screen without any response... So I had to switch back to the ati-driver.
And strange enough: The card works perfectly in Fedora Core 6 x86_64!

Help is very very welcome ;)
Benedikt

PS.: Maybe a functional xorg.conf would help?

---

### Post by zigford on 2006-12-04
mine is definately working with the latest drivers from ati. When I get home I will post my fglrxinfo output.  Of coarse there is still no composite support, but I do have 3d support :)

PS: I followed this post: [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

and add these lines at the end of the file: 

File: /etc/X11/xorg.conf  
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

---

### Post by kcallis on 2006-12-05
> **zigford said:**
> mine is definately working with the latest drivers from ati. When I get home I will post my fglrxinfo output.  Of coarse there is still no composite support, but I do have 3d support :)

PS: I followed this post: [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

and add these lines at the end of the file: 

File: /etc/X11/xorg.conf  
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
I have download the latest ati installer, and I keep getting this error:

~/tmp$ ./ati-driver-installer-8.29.6.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.29.6
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 176: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

So the debs never get built... Did you run into any issue like that?

---

### Post by zigford on 2006-12-05
> **kcallis said:**
> I have download the latest ati installer, and I keep getting this error:

~/tmp$ ./ati-driver-installer-8.29.6.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.29.6
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 176: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

So the debs never get built... Did you run into any issue like that?

kcallis, I did have that problem and I will show you the work around in my post, but I would like to start with all the changes that I have made on my system.  My system has been runing like an almost dream, only 1 issue thus far and its no major.

I have a compaq v2000 (AMDTurion64, ATI Radeon Xpress200m, BCM4318 Wireless, Texas instruments SD Card reader, firewire 1394) <---Everything working. well.

I have done a few modifications to my system so I can't say that doing one of those will make everything work, but I'll tell you them all.

Out of the box install of edgy-->No wireless, okay running 2d graphics
What I wanted to achieve-->Perfect wireless with suspend and hibernate (Previously with FC5 I had to restart Network manager after a suspend or hibernate), 3d Accell of ATI card.
What I did:

1.  Upgrade the kernel-->[http://ubuntuforums.org/showpost.php?p=1705658&postcount=668](http://ubuntuforums.org/showpost.php?p=1705658&postcount=668)
This nice fellow compwiz13 provides some .deb's to upgrade my kernel to 2.6.18.  I think this is what made my wireless work so perfectly

2.  ati-driver-installer-8.29.6
This ati-driver doesn't work for most people, but I think its a problem with our current edgy kernel, as it works perfectly runnig under 2.6.18 kernel.

I posted the link I used in my above post

kcallis: he is the answer to the problem you had:

```

$ sudo mv /bin/sh /bin/SH         #rename /bin/sh
$ sudo ln -s /bin/bash /bin/sh    #link /bin/bash to /bin/sh
$ ./ati-driver-installer-8.29.6.run --buildpkg Ubuntu/edgy
$ sudo mv /bin/SH /bin/sh         #rename /bin/SH back to /bin/sh

```

I haven't given every step I took to get where I am, but its worth it. try follow the posts, if you run into issues, go the ubuntuforums.org and paste the error message you get into the search bar, if you don't get any hits, paste it into google.

Have a good search for your errors, there are nearly always a dozen other people who have tried and posted their errors.  if all else fails, post back here or send me a PM.

Cheers

---

### Post by kcallis on 2006-12-05
Well, I followed all of you directions, and I still end up with black screen on boot. I have once again fallen back to the ati driver. I have run out of ideas, and like you, I had the same goals. 3D graphics and wireles working. It would seem that your Compaq is simular to my HP dv8040z. Would you point me to where you got your information in order to get the bcm card working.

Also anything else about the 200M would be greatly appreciated...

---

### Post by zigford on 2006-12-05
Okay, so I guess you rebooted, selected the new kernel, and then installed the ati-driver?

I got the black screen too until I added:

```

EndSection
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

Here is my xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	SubSection "extmod"
		Option	    "omit xfree86-dga"   # don't initialise the DGA extension
	EndSubSection
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "MaxTapTime" "0.05"
	Option	    "MinSpeed" "0.25"
	Option	    "MaxSpeed" "1.35"
	Option	    "AccelFactor" "0.017"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

Don't give up hope.  I think I detect that you are getting dis-heartened.  Just remember, you have never failed until you give up.
The best way to troubleshoot linux is to read and try to decipher the error messages.
When you get your blank screen, have a look at /var/log/Xorg.0.log
Logs are the key and help you learn why things aren't working.
Check the output of "dmesg"

If you can't see what wrong, post the output of these here and I'll take a look.

```
jharris@ringo:/var/log$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6065 (8.29.6)

jharris@ringo:/var/log$ 
```

NDISWRAPPER:
I think that after I installed the new kernel, I went to the ndiswrapper website and downloaded the latest: ndiswrapper-1.28

I think you can just follow the instructions in the "INSTALL" file:

```
Download the latest version of the ndiswrapper sources from here and
extract it with the command

  tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory. Change to that
directory and run

  make uninstall
  make

Login as root and run
  make install
```

Caio, good luck

---

### Post by kcallis on 2006-12-07
Zigford,

Trust me, I have not given up hope. My priority changed to me getting ndiswrapper working, and now is I not can sit on my patio with having to be connected to my D-Link portable router, I can say that I am now enjoying wireless.

But now, it is time to focus on getting my X200 working correctly. I am currently using the ATI driver, but I am going to go back through the process you layed out earlier and see where that get me.

I am curious, because I am not running the 2.6.19 kernel, and it seems to be running flawlessly. Of course, I have no idea of what is going to happen when I try to make use of the fglrx kernel against the 2.6.19 kernel. I have been trying to figure out what the differences are and see if I could patch the 2.6.19 kernel.

I will keep everyone posted!

---

### Post by beneedict on 2006-12-07
Hejhej!!
Back again :) After quite many experiments I did not get up beryl running in Kubuntu AMD64. I guess I will have to wait for ATI AIGLX drivers. or FOSS drivers... But what I got is kernel 2.6.19. and it works much better than anything else!!! my laptop was never that fast. Here the link: [http://ubuntu.secs.oakland.edu/pool](http://ubuntu.secs.oakland.edu/pool) surf for your linux kernel there. I love it ;)

If somebody can give me further hints, you are welcome :) But in the meanwhile: enjoy 2.6.19!

Thx, Bene

---

### Post by zigford on 2006-12-19
Hey Hey, just thought I'd let you know.  The new driver (released on the 13th Dec) is allowing me to run compiz perfectly and has done so since the 13th of Dec.  I highly recommend giving it a go.  My laptop is a cheaper one that forces u to use system ram (no sideport options or whatever) and I thought desktop effects would never be possible.  He :) they are now!

---

### Post by d-E-a-D on 2006-12-19
[http://www.ubuntuforums.org/showthread.php?t=321766&highlight=200m](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=200m)

---

### Post by beneedict on 2007-07-25
Feisty helps a lot ;)

---

