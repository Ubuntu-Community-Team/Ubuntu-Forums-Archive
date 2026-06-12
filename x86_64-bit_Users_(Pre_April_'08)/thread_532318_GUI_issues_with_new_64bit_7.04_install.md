---
title: "GUI issues with new 64bit 7.04 install"
date: 2007-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by TheAbyssDragon on 2007-08-22
I'm running a gateway c-140x, 2.0 core 2 duo with a ATi X2300HD card. I installed the v7.04 64bit (alternate) desktop, and everything went smoothly. Now when I attempt to boot I get an error. First it says X server cannot boot, then when I view the X server output it says 'Fatal server error: no screens found'. When I continue I get the message box 'The X server is now disabled. Restart GDM when it is configured correctly,' and then I'm left at the command window.

I've searched various forums and found one person with similar difficulties, who said he was now running on restricted video drivers.

What can I do to get my GUI up and running?

---

### Post by John.Michael.Kane on 2007-08-22
ctrl+alt f1 login type you name/pass

Next:
```
sudo nano /etc/X11/xorg.conf
```

scroll down to this section
```
Section "Device"
	Identifier	"nVidia Corporation C51G [GeForce 6100]"
	**Driver		"nv"** change this to vesa
	BusID		"PCI:0:5:0"
EndSection
```

Hit ctrl x answer with Y then hit ctrl m 

reboot the machine using ctrl alt delete

If the above does not bring you to the gdm login. ctrl alt f1 login, and run the below command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ddrichardson on 2007-08-22
Have you [reconfigured]("http://ubuntuforums.org/showthread.php?t=510742") the card?

---

### Post by ddrichardson on 2007-08-22
Damnit you were quicker.

---

### Post by TheAbyssDragon on 2007-08-22
The first method didn't open a file, but actually created a new file (maybe I should try a reinstall?).

The second method showed that the driver was already set to vesa, and upon rebooting, I arrived at the same error.

I also tried setting it to ati, still no progress.

---

### Post by TheAbyssDragon on 2007-08-23
Any other advise?

---

### Post by bdoe on 2007-08-23
sudo nano /etc/X11/xorg.conf

Check the following sections:
```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver                "radeon"
        BusID                "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "8"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection
```
You're mainly concerned with "Identifier".  Make a note of it.

*Edit:  I suggest setting Driver to "vesa" until you can at least get up and running.*

Next, check:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection
```
Make a note of "Identifier" here as well.

Now, check:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
...
```
Make a note of "Identifier", and make sure that "Device" matches the identifier in the first section (Section "Device") above, and "Monitor" matches the identifier in the second section (Section "Monitor") above.

Now, check:
```
Section "ServerLayout"
	Option		"AIGLX"	"true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```
Make sure that "Screen" matches the identifier in the third section (section "Screen") above.

Once you've made sure that everything matches, save the file (CTRL-X, answer with Y, then hit CTRL-M), and reboot.

---

### Post by TheAbyssDragon on 2007-08-23
As I've already mentioned, when I try to access the xorg.conf file, nano creates a new file.

---

### Post by jpkotta on 2007-08-23
If the install didn't create an xorg.conf, something went wrong and you should reinstall.

---

### Post by bdoe on 2007-08-23
Filenames are case-sensitive.  Are you sure you're typing /etc/X11/xorg.conf and not /etc/x11/xorg.conf?

---

### Post by TheAbyssDragon on 2007-08-24
Ok so I didn't realize the cap sensitivity, so now I have access to the conf file, but everything looks alright.

Here's the first block of code if it helps:
```
Section "Device"
 Identifier  "Generic Video Card"
 Driver      "vesa"
 BusID       "PCI :1 :0 :0"
EndSection
```

Maybe PCIe is creating problems? I also have wacom (touch screen) devices listed in here, perhaps these are causing problems. Although I was doing a live run of 32bit 6.10, and everything (including touch screen) ran fine.

---

### Post by EXCiD3 on 2007-08-24
It doesnt look like it detected your video card right since it usually names it in the "Identifier" section...

Anyways, i have had that no screens found problem before...Could you post your entire xorg?

---

### Post by TheAbyssDragon on 2007-08-24
Is there an easy way to do that? Like export the file to my desktop? I r no good with terminal :confused:

---

### Post by sintranti on 2007-08-24
I think I should note that I am also having this issue with the same model of laptop. There is a difference, however, in that I am using the default integrated Intel GMA X3100 video card.

The aforementioned section in my xorg.conf log says basically the same thing:

Section "Device"
             Identifier          "Generic Video Card"
             Driver               "vesa"
             BusID               "PCI:0:2:0"
EndSection

Section "Monitor"
              Identifier         "Generic Monitor"
              Option             "DPMS"
EndSection

Section "Screen"
              Identifier         "Default Screen"
              Device             "Generic Video Card"
              Monitor            "Generic Monitor"
              DefaultDepth   24
              SubSection "Display"
                                 Depth           1
                                 Modes          "1280x768" "1024x768" "800x600" "640x480"
              EndSubSection

The subsection bit continues with depths of 1, 4, 8, 15, 16, and 24, with the same modes information.


This is also using the alternate installation of the 64 bit version of 7.04. The alternate was used as the standard would not load. It should also be noted that the live version of 5.1 (I just happened to have it laying around from when I installed Ubuntu on my desktop) came up with the same sort of error as I am getting post installation of 7.04

The input devices seem to have installed correctly, including the wacom drivers.



Hope that helps.

---

### Post by TheAbyssDragon on 2007-08-24
I installed 6.10 32bit and it worked fine, but after I updated to 7.04 using the update manager the same error occurred. There must be some conflict with 7.04 and the drivers. I'm gonna try running an older version of 64bit and see what happens.

---

### Post by TheAbyssDragon on 2007-08-24
6.06 64bit runs, but not well. The touch pad is hard to use, and both my wired and wireless got assigned eth0, so it conflicts when it tries to connect to the network.

I guess I'll just stick with 32bit 6.10 for a while, at least it runs.

---

