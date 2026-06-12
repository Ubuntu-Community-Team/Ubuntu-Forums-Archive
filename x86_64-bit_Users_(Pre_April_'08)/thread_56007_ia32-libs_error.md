---
title: "ia32-libs error?"
date: 2005-08-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Flac on 2005-08-11
E: /var/cache/apt/archives/ia32-libs_0.5ubuntu3.1_amd64.deb:  error creating symbolic link `./usr/lib32/libGL.so.1': No such file or directory

 Im actauly not sure what this is, But the ubuntu update screen wants me to update this, but throws this error at me. I've searched for libGL.so.1 and found nothing so i dont know what its talking about... Any help would be appriciated :)

---

### Post by DancingSun on 2005-08-11
Maybe a reinstall will fix that package...

---

### Post by uniko on 2005-08-11
If you have ATI card, you need to remove ATI proprietary drivers first (xorg-driver-fglrx).  Set in xorg.conf to use ati instead of fglrx and reboot. Then you can update and after update you can reinstall ati drivers. Worked for me.

---

### Post by DerMika on 2005-08-17
[QUOTE=uniko]If you have ATI card, you need to remove ATI proprietary drivers first (xorg-driver-fglrx).  Set in xorg.conf to use ati instead of fglrx and reboot. Then you can update and after update you can reinstall ati drivers. Worked for me.[/QUOTE]Can anyone show me how to do this. I'm a noob, and i barely managed to follow the tutorial to install my 3d drivers... So i guess i need some help updating this!  :?

---

### Post by DerMika on 2005-08-17
[QUOTE=DancingSun]Maybe a reinstall will fix that package...[/QUOTE]
This didn't help for me...

---

### Post by uniko on 2005-08-17
First start Synaptic
search for fglrx,
choose xorg-driver-fglrx, 
right click Mark for Removal
click Apply

Next open terminal, type:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo gedit /etc/X11/xorg.conf

Find this section:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseInternalAGPGART" "no"
	Option		"RenderAccel"	"true"
	Option		"AllowGLXWithComposite"	"true"
``` 

Change to this (ie. comment out options and change fglrx to ati)

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	#Option		"UseInternalAGPGART" "no"
	#Option		"RenderAccel"	"true"
	#Option		"AllowGLXWithComposite"	"true"
```

Now reboot.
Update your ia32libs. Now you can install xorg-driver-fglrx thru synaptic. 
To change x-server to use fglrx driver, open terminal and type:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf 

reboot your x-server by pressing CTRL+ALT+BACKSPACE. 
Test if you got 3d by running fglrxinfo  from terminal. That shoud do it.

---

### Post by DerMika on 2005-08-17
OK I did all that you said. Now the fglrxinfo gives me this: 

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

``` 

Does this mean "all is ok"? (i certainly hope so)

Update: Well, I ran the fgl_glxgears, and the gears are going around at 676.600 FPS so i guess 3d acceleration is still OK :)

THANKS!

---

