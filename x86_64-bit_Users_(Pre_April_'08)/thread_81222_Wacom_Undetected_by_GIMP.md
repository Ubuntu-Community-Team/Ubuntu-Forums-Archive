---
title: "Wacom Undetected by GIMP"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by crayon on 2005-10-24
Hi guys,


    This is my first time to dive into the Ubuntu realm using an iBook G3 600 (Dual USB) as my guinea pig. I'm hoping this thread will be as helpful to others as it can be to myself. I've been following through the tutorial (How-to) on getting Wacom tablets to work (with pressure enabled) with the GIMP. I've currently installed Ubuntu 5.10 Breezy Badger and I must say, it's pretty cool. 

I currently have a Wacom Graphire 1, the first of the series that came out and plugging it in, it's automatically detected and works like the real thing. Checking out the /dev/input directory through Terminal, when I plug in the Wacom, the files "event5" and "wacom" (in blue font) gets added and yes, doing a

*sudo cat event5*  **or** *sudo cat wacom*

indicates that the wacom works through those events. I've already modified my xorg.conf accordingly as indicated in the How-to instruction. My problem now is that though the graphire works out of the box and with the modifications, the GIMP's **file > preferences > Input devices > Configure Extended Input Devices ** section **does not detect the wacom**! It only says "No extended input devices". Has anyone else encountered this? Would be of big help if anyone's got a solution :). Thanks alot peeps! :) 

Cheers!
Les

---

### Post by jejones3141 on 2005-11-28
I wish I had a solution... I've just run into the same problem, though with a Graphire 3 instead of a 1.

---

### Post by jejones3141 on 2005-11-28
[This thread]("http://gug.sunsite.dk/forum/?threadid=2315") in the GUG forum shows that one possible cause is having a version of GTK that is compiled with Xinput xupport turned off. Could an Ubuntu guru let us know whether this is the case for Breezy?

---

### Post by ssam on 2005-11-28
i am not sure how you would check other than downloading the source package and reading though its build scripts.

if it was build with the option missing it would probably be true for x86 aswell. you might get a better informed answer in the ubuntu desktop help forum.

---

### Post by jejones3141 on 2005-11-28
Actually, I'm running into it on my wife's system, which *is* an x86. I'll check in the Desktop Help forum---thanks!

---

### Post by oldtree on 2005-12-06
Hi people,
Les,
              If you have not found an answer to your tablet problem yet, have a look at the xorg.conf file and specifically at the section related  to your mouse.
  Does it have the line:
Option "Device"  "/dev/input/mice" there.  I read some time ago that this causes conflicts with tablets and may need to be changed.
You can #cd /dev/input and then #ls to list options.  Run #xxd yyyy where yyyy stands for one of the options eg #xxd  mouse0
Each time you enter a new xxd command use the mouse and a stream of output will appear on the screen when you hit the right combination.  Same for stylus.
Change the line in xorg.conf in the mouse section to the one that gave you the screen output.  Confirm the correct output for the stylus by the same method.
I successfully use a graphire3 now having made these changes.  It works well.
[eMac/10.3.9/ubuntu/debian/kubuntu].  All work except Kubuntu - no gimp!
Let us know if it works or if you need more info.....
happy days,
oldtree

---

### Post by GeneralCody on 2006-09-30
Hi! I know this comes in stoneage time response, but the solution to having Gimp detect Wacom Volito2, Graphire and others lies in a kernel module, that you can download from:

[http://http://linuxwacom.sourceforge.net/index.php/chg]("http://http://linuxwacom.sourceforge.net/index.php/chg")

Follow the documentation, and you will get pressure sensitivity / eraser functionality etc. in Gimp.

Remember to set it to "enabled" in Gimp preferences. 

Wacom on Gimp rocks by the way. The only way to make true art?

Best

GC

---

### Post by irongrunty on 2007-09-30
I'm also having this problem. i have all the correct stuff in xorg.conf, and the pen works just like a mouse, but doesn't have any pressure sensitivity in GIMP and i get the "No extended input devices" message.

Also, this is what I get when searching for the devices:

irongrunty@PARADISE:~$ xidump -l
pointer                        disabled
keyboard                       keyboard
irongrunty@PARADISE:~$ xsetpointer -l
0: "pointer"    [XPointer]
1: "keyboard"   [XKeyboard]

and my xorg.conf has these in it:

[...]```

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection
```
[...]```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

if anyone can help it would be appreciated D: i miss pressure sensitivity

---

### Post by Destinatus on 2007-10-30
I got my tablet to act like a tablet (curor jumps to area on the tablet and hovering pen over the tablet works). I still have no pressure sensitivity in GIMP and I get the error "No extended input devices" when clicking "Configure Extended Input Devices" Can anyone help? I miss my sensitivity too =(

---

