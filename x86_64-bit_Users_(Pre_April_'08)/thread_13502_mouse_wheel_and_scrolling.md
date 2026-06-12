---
title: "mouse wheel and scrolling"
date: 2005-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by kraptor on 2005-01-31
Is there any way to enable the scroll button on my mouse :confused: . I use an optical mouse via the PS2 port. I've looked all over the forum for help, to no avail. I'm a newbie so pls keep suggestions as detailed as possible. Thanks in advance.
kraptor

---

### Post by valadil on 2005-02-01
Open a terminal and type
sudo nano /etc/X11/XF86Config

Find the InputDevice section regarding your mouse.  Make sure your protocol is "ImPS/2" and that ZAxisMapping is "4 5"

ctrl-x to save and quit.  Restart your x server (or just reboot if that's easier).

---

### Post by kraptor on 2005-02-01
I opened the config file... its blank... not too sure how to proceed...

---

### Post by kraptor on 2005-02-01
anybody out there... help :-| ! Browsing is such a headache without scrolling...

---

### Post by valadil on 2005-02-01
Might you be using xorg?  For that you'd be looking at /etc/X11/xorg.conf

---

### Post by Sye d'Burns on 2005-02-01
or you might try /etc/X11/XF86Config-4

---

### Post by kraptor on 2005-02-01
Section "ServerLayout"
        Identifier     "XFree86 Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        RgbPath      "/usr/X11R6/lib/X11/rgb"
        ModulePath   "/usr/X11R6/lib/modules"
        FontPath     "/usr/X11R6/lib/X11/fonts/misc/"
        FontPath     "/usr/X11R6/lib/X11/fonts/Speedo/"
        FontPath     "/usr/X11R6/lib/X11/fonts/Type1/"
        FontPath     "/usr/X11R6/lib/X11/fonts/CID/"
        FontPath     "/usr/X11R6/lib/X11/fonts/75dpi/"
        FontPath     "/usr/X11R6/lib/X11/fonts/100dpi/"
EndSection

Section "Module"
______________________________

thats what i have in the XF86Config-4 file... what changes should i make?

---

### Post by Sye d'Burns on 2005-02-01
[QUOTE=kraptor]
thats what i have in the XF86Config-4 file... what changes should i make?
[/QUOTE]

That's all you have in your XF86Config-4? 

As valadil said, find the InputDevice section regarding your mouse. Make sure your protocol is "ImPS/2" and that ZAxisMapping is "4 5"

It should look similiar to mine (only in format, not in content)

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"               "7"
	Option		"ZAxisMapping"		"6 7"
        Option          "Resolution"            "100"
EndSection

---

### Post by crane on 2005-02-01
[QUOTE=Sye d'Burns]That's all you have in your XF86Config-4? 

As valadil said, find the InputDevice section regarding your mouse. Make sure your protocol is "ImPS/2" and that ZAxisMapping is "4 5"

It should look similiar to mine (only in format, not in content)

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"               "7"
	Option		"ZAxisMapping"		"6 7"
        Option          "Resolution"            "100"
EndSection[/QUOTE]


His is set up for a 7 button mouse.I have mine setup for a 5 button mouse. (which is a basic mouse with a scroll whell)

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Hope this helps!

---

### Post by kraptor on 2005-02-01
you guys are the greatest... works perfect ... thanks to all :D 
kraptor

---

