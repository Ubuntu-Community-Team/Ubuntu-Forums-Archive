---
title: "[SOLVED] xserver-xgl very slow I tried #compiz-fusion"
date: 2008-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lukasz Tarkowski on 2008-02-04
Dear Support
I can't seem to get the Ati Radeon 200 Integrated Mother Board to work.
It slows my laptop like alot :(
The xserver-xgl and I did install compiz fusion :(

---

### Post by prince_niceguy on 2008-02-06
use the latest drivers from ati and use aiglx instead. xgl makes your comp slow with the effects. aiglx is better. however since these are newly implemented by ati the driver might have some issues.

having said that, i am using ati driver with aiglx on my laptop and it is working fine except for watching movies in full screen.

---

### Post by Lukasz Tarkowski on 2008-02-07
Where can I download aiglx?
I can't seem to find it in apt-cache search aiglx

---

### Post by jocko on 2008-02-07
> **Lukasz Tarkowski said:**
> Where can I download aiglx?
I can't seem to find it in apt-cache search aiglx

AIGLX is already part of xorg. No need to install anything extra to get that running.
But you need to install the latest drivers from ATI.
[Here's a link]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually") to some helpful instructions.

---

### Post by Lukasz Tarkowski on 2008-02-07
Thank You Jocko :)

---

### Post by prince_niceguy on 2008-02-07
sorry was not checking my emails.. the solution given by jacko is the perfect one.. i too used the same site for installing ati's latest driver.

so, how is your aiglx working now?

---

### Post by Lukasz Tarkowski on 2008-02-07
Jocko said its already in there configured _but still no effects?_ or I misunderstood
_I have the driver installed and Control Center they both work _
Ati drivers work ow but no Visual Effects :( Says Not able to enable 
_System/Preferences/Appearance Visual Effects_

---

### Post by Lukasz Tarkowski on 2008-02-07
Her is my error
```
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:9074): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:9074): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
/usr/bin/compiz.real (core) - Fatal: No composite extension

```

---

### Post by Lukasz Tarkowski on 2008-02-07
by the way I typed in Alt-F2 and put in compiz and screen flickerd once maybe twice and came back to Normal
Is that working now?
Don't forget to read logs on top of this reply

---

### Post by prince_niceguy on 2008-02-08
have you installed the restricted drivers? if yes, then comment the composite option.

also post the file /etc/X11/xorg.conf file too.

also type the command

```
compiz --replace
```

---

### Post by Lukasz Tarkowski on 2008-02-08
Here is my xorg conf
w System server configuration file)
```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
        Option  "Composite" "1"
EndSection

```
Error one more time
```

Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:9074): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:9074): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
/usr/bin/compiz.real (core) - Fatal: No composite extension

```

---

### Post by prince_niceguy on 2008-02-08
Follow the second method of installing the ati drivers from the amd site which are not in the repository. Repository has non aiglx drivers.

Take a back up of your xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now, run the following
```
sudo gedit /etc/X11/xorg.conf
```

In your xorg conf change the line
```

Section "Extensions"
        Option  "Composite" "1"
EndSection

```

to 

```

#Section "Extensions"
#        Option  "Composite" "1"
#EndSection

```

Note that there is a # in front of all lines given above. This will remove composite which is not required with aiglx.

Now press ctrl + alt+ backspace and X server will restart and you can login again and try enabling the desktop effect from the preferences --> appearance.

Also, please post the output of

```
fglrxinfo
```

---

### Post by Lukasz Tarkowski on 2008-02-08
It didn't work :(
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)
glxinfo | grep rendering
direct rendering: Yes 
```
Rendering says yes I used that command 

_I made a screenie :)_

---

### Post by prince_niceguy on 2008-02-08
seems you have not installed the proprietory driver from ati's site. it is showing the older version of the driver from the repo.

download the drivers from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

and follow the instructions in [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)

just replace the file name for the .bin with the one you downloaded from ati's site.

after that follow each and every line in the install and you should have something like this below when you type fglrxinfo

ubuntu-laptop% fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.4 (2.1.7276 Release)

After that just run desktop effects and they should come up...

---

### Post by Lukasz Tarkowski on 2008-02-08
I will do that Saturday :)
Hope it workx :)

---

### Post by Lukasz Tarkowski on 2008-02-08
The flgrxinfo now
lukasz@lukasz-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

By the way visuals go Blank afte rI change them
then I have to press Ctrl-Alt Backspace
[http://wiki.cchtml.com/index.php/Ubu...river_Manually](http://wiki.cchtml.com/index.php/Ubu...river_Manually)
I followed number 2

---

### Post by Lukasz Tarkowski on 2008-02-08
New Ati Code
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7276 Release
_reboot was needed_

yeyyeyey The Visual Effect work :)

_It doesn't logout cleanly it goes blank evrything Logout System it just blank after second logout First one is ok but the SECOND TIME LOGUT IS BAD_
It doesn't wonna work now so I have to format
I messed it up and what if I can't logout

---

### Post by prince_niceguy on 2008-02-09
press ctrl + alt + backspace and you should be able to log out without issue in that case.

---

### Post by Lukasz Tarkowski on 2008-02-09
I think I have to start from new install cause ctrl-alt backsapce didn't work heh
From the clean install i shouldve Followed those insructions
It has crashed cause I messed it up heh
Im gonna reinstall it now, its not so bad heh
It doesn't even wonna start so format time

---

### Post by prince_niceguy on 2008-02-09
oh oh... good luck...:-)

---

### Post by Lukasz Tarkowski on 2008-02-09
They don't work
I did the way i supposed to and set Compiz to keep default
I did from clean install
Preferences/Apperance/Visual Effects

```
lukasz@lukasz-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5955 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found
```

FGLRX
```
lukasz@lukasz-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7276 Release
```

---

### Post by prince_niceguy on 2008-02-09
can you post your xorg.conf and also run the following command

```
locate compiz
```

have you done upgrade after doing clean install?

---

### Post by Lukasz Tarkowski on 2008-02-09
yeah holdon

---

### Post by Lukasz Tarkowski on 2008-02-10
Whenever i follow these Instructions 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)
It crashes on me :(
I can't do Ctrl-Alt-Backspace either just freezes Normal Logout as well freezes
Now I have to format cause I messed it up :(
By the way when I'm doing it asks me
sudo dpkg -i xorg-driver-fglrx_8.452.1-1*.deb fglrx-kernel-source_8.452.1-1*.deb fglrx-amdcccle_8.452.1-1*.deb
Should I install The compiz maintainer edition I for install N for default?
By the way I was messing around and messed it up

---

### Post by Lukasz Tarkowski on 2008-02-10
Evrything is fine now :)
I can logout as well :)

New list

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5955 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

```

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7276 Release

```

---

### Post by prince_niceguy on 2008-02-10
glad to know it is working now...:-)

---

