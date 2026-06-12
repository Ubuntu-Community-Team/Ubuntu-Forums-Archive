---
title: "Having Blank Screen Issues"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by StitchedChin on 2008-04-30
When I hit ctrl-alt-F1 or F2, my screen goes blank and my monitor goes to sleep mode.  I hit ctrl-alt-F7 it wakes back up and I get back to X Server.  I'm trying to update my Nvidia driver for my 7600 GTs because I've also had problems while running Planeshift back in Gutsy and now in Hardy.  Once the game is on, either in windowed or non-windowed mode, any other application I load is completely black.  I can even just minimize a program I had opened before I started PS and it'll go black on me when I restore it.  The program is still functional if you know areas to type, but it stays black and does not come back to visible until I shut down Planeshift and then minimize and restore it.  I've seen some VGA additions that worked for others, but they didn't seem to be having similar issues.  Here is what my xorg file looks like.  I turned off SLI to see if that helped, but I'd like to keep it on if I can figure out what the issue is.  I was trying to install the beta of the latest 7 Nvidia drivers and can't get to a prompt to turn the X server off to install run the package.  I'm a bit new to Linux, so let me know what else you need and how to do it, and I'll get going.  I'm running and installing everything 64 bit.  Thanks.

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "auto"
    Option         "7"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
    Option         "ButtonMapping" "1 2 3 8 9 10 11"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "VX924"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    Option	   "RenderAccel"  "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "VX924"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600"
    EndSubSection
EndSection

Section "Extensions"
    Option  "Composite" "Enable"
EndSection

---

