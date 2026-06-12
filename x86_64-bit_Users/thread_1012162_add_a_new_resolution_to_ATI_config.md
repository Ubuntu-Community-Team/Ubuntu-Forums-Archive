---
title: "add a new resolution to ATI config"
date: 2008-12-15
forum: x86 64-bit Users
---

### Post by swatsbiz on 2008-12-15
I recently had to change my home partition which caused me to have to run the recovery console, at the same time I chose to run the XServer recovery.

Now I have a little annoyance, I can't get the proper resolution for my monitor.  The closest I can get is 1600x1200, but it looks slightly blurred, as I believe it used to be 1680x1050.  I can't select 1680x1050 anywhere and all my attempts so far have failed.

I'm sure it's fairly simple solution but I'm fairly new to Linux and stuck.

Many thanks
David

---

### Post by cubeist on 2008-12-15
```
aticonfig --initial
```
that ***should*** do it, I had a similar problem with 1440x900 for my 1650x1050, but I was also running other config commands via aticonfig, so if that doesn't work, try
```
aticonfig --help
```

---

### Post by swatsbiz on 2008-12-16
Thanks for that I had to do a:

 aticonfig --help

Which then allowed me to add 1680x1050 to the Xorg.conf file - it's there just now, but even after rebooting I still don't have that option in my ATI catalyst control centre or on my ubuntu screen resolution options, I've only got the 4:3 options in a resolution approaching what what I need.

Have I missed something?

---

### Post by cubeist on 2008-12-16
ok, this should fix it:

open a terminal,

first backup your xorg.conf file, like this:
```
sudo cp /etc/X11/xorg.conf /etx/X11/xorg.conf.backup
```

next, we need to add a fixed resolution under the display section of your xorg.conf file:
```
gksudo gedit /etc/X11/xorg.conf
```
find the section called screen, and then the Subsection called display, after the *depth* line, add a line called *modes*, with the correct resolution; like this:
```
Modes      "1680x1050"

```
save and exit gedit

finally, we need aticonfig to see the changes to your xorg.conf
so in a terminal type:
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

```

logout and back in... or maybe even a full restart, and your default resolution should be 1680x1050

---

### Post by swatsbiz on 2008-12-17
Ok thanks for the above but I still seem to be struggling!

Here's my xorg.conf file:

> Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Then using:

sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

I get this:


> Warning: Option 'UseFastTLS' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-5


After Reboot, I got a blank screen, after another reboot it settled back for the 1600x1200 resolution that squashes my screen a bit.

---

### Post by cubeist on 2008-12-17
Bump - Anyone else have an idea?

Everything looks aok in the xorg.conf... After the changes does the proper 1680x1050 show up in the catalyst control?

---

### Post by swatsbiz on 2008-12-17
No there's no change in my options from my ATI control or the Screen resolution choice in System>Preferences

---

### Post by swatsbiz on 2008-12-18
I have also noticed on booting up that immediately after the grub loader, I get a message saying that there's no such "video Mode Code 318" and asks me to either choose a new one by pressing enter (and there's still no 1680x1050) or press space to continue.

Space boots me up as per normal.

---

### Post by fmb on 2008-12-18
I believe you're refering to vga parameter in grub config (/boot/grub/menu.lst). That's relevant only to framebuffer resolution (which doesn't support widescreen res, AFAIK). As soon as gdm kicks in, xorg.conf parameters are taken into account.
That being said, I think in your case it should be 0x318 (hex) or 792 (decimal), not 318 (dec). Search for string vga=318 in the file and fix it accordingly. That should take care of the lesser problem.

I'm looking forward to someone comig up with the solution to main issue... drives me crazy too...

---

### Post by swatsbiz on 2008-12-18
> I believe you're refering to vga parameter in grub config

That's why I didn't mention it until now, however it started with that error at the same time as the changes I made to my home folder.  And it comes up immediately after my grub boot list.

> That being said, I think in your case it should be 0x318 (hex) or 792 (decimal), not 318 (dec).

The code is used to select the video resolution from the list of available resolutions, as I can choose which one to use and type in an alternate code (each code of three numbers is next to a resolution and bit depth) then return continues the boot process - using the resolution for the ubuntu splash screen.

---

### Post by cubeist on 2008-12-18
Two more ideas... in *system: prefs: screen resolution*, do you have the correct resolution in the list?  If it is not there, press *detect displays* and see if the correct resolution is available.  In theory, if it is not detected, then the problem is that the monitor is not providing accurate supportable resolutions to the computer during boot.  I can't remember what the protocol is, but it may be fubar... if this is the problem, in theory, a possible fix is to switch the cable.  So if you are using dvi, try vga, or vice versa.  Again this is a long shot, but you never know...  (ps - you can also detect displays from the ati control center.  In the Display manager tab, on the far right is a little drop down next to the magnifying glass icon)

The second fix is one you probably already tried
```
aticonfig --resolution=0,1680x1050
```

---

### Post by Prusal on 2009-03-08
> **cubeist said:**
> ok, this should fix it:

open a terminal,

first backup your xorg.conf file, like this:
```
sudo cp /etc/X11/xorg.conf /etx/X11/xorg.conf.backup
```

next, we need to add a fixed resolution under the display section of your xorg.conf file:
```
gksudo gedit /etc/X11/xorg.conf
```
find the section called screen, and then the Subsection called display, after the *depth* line, add a line called *modes*, with the correct resolution; like this:
```
Modes      "1680x1050"

```
save and exit gedit

finally, we need aticonfig to see the changes to your xorg.conf
so in a terminal type:
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

```

logout and back in... or maybe even a full restart, and your default resolution should be 1680x1050

THX so much Cubeist!!!!!!!
I had a similar resolution problem and your solution did the trick :guitar::guitar::guitar::guitar:

---

