---
title: "After changing resolution I can't see screen"
date: 2006-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by lonrot on 2006-06-23
Hello people, this is my first post.

I'm very new to linux, this is my first distro.

I managed to change the screen resolution though xconfig commands, cause my resolution was 800x600 and I wanted to switch to 1024X768, I simply added 1024X768 to all the screen resolution stuff.

When I rebooted with ctrl+alt+delete (I think) I got a black screen with a message saying: Refresh rate not compatible 85Hz.

My monitor is an AOC 26, in windows xp my default refresh is 75hz.

I don't know how to fix this problem since I can't see anything, right now I'm typing through live cd. Is there a way to fix this problem using this cd. I can't access the partition :(

Thanks in advance!

---

### Post by incubus on 2006-06-23
lonrot,

You can get it back from the CD or probably from your setup too. When you see that problem you can press Ctrl+Alt+F1 to go to a Terminal. From there you can fix the problem. (to go back to Xserver it's Ctrl+Alt+F7)

If you want to do it from the Live CD, you have to mount your partition somewhere. I don't know what your partition is, but suppose it's "hda1". 

So open a terminal and:
```

$ sudo mkdir /mnt/hda1
$ sudo mount /dev/hda1 /mnt/hda1

```

Now all your files are in the directory /mnt/hda1, so if you need to edit something like "/etc/X11/xorg.conf", make sure you open "/mnt/hda1/etc/X11/xorg.conf" instead.

About the refresh rate, check this thread:
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

What you have to do is edit "xorg.conf" and add the lines for "HorizSync" and "VertRefresh" in the Section "Monitor".

Let us know if you can't figure it out. It's a good idea if you can check the refresh rates from your monitor's manual.

incubus

---

### Post by vigleik on 2006-06-23
It's generally not a good idea to edit the /etc/X11/xorg.conf file by hand, and if you do you should at least make a backup first. There is a better way, which is to type "sudo dpkg-reconfigure xserver-xorg" in a terminal window. That helps you reconfigure all that stuff. You can give the default answer to most of the questions, but you should pay attention to two things. The graphics driver, and when you get to the resolution stuff. You can probably leave the driver as the default first, but if you have a nvidia or ati graphics card it helps (sometimes a lot) to install the nvidia or ati driver and then choose the corresponding driver.

Anyway, a way to fix this is to boot from your hard drive again, press ctrl+alt+F1 (which should give you a text login), and then do what I described.

Another way to get you up and running again is to boot from the live CD, and copy the /etc/X11/xorg.conf file from the live CD to you hard drive (for example after mounting it as incubus describes). Of course, manually editing the xorg.conf file back to what it was (if you remember) should also work.

Vigleik

---

### Post by lonrot on 2006-06-23
Thanks a lot for the quick replys.

I´ve tried all the steps here. 

First the live cd stuff, I did everything just fine till I got to the file and unluckily the page was blank. No idea why, tried several times an the file was blank.

Rebooted and then used the ctrl+alt+f1 logged in and typed > sudo dpkg-reconfigure xserver-xorg i found myself in this blue screen, I just wanted to fix the problem, not to reconfigurete all the options there. 

I could probably fix this out using that feature but I´m a bit scared about screwing things up. I checked in windows my linux partition and I have a xorg.conf backup next to the edited one. Is there a way to revert the process with that backup file.

And one more question, is there a way to to read/write linux through windows? Unfortunaly being a windows former user I´m very familiar with graphical interfaces, and not command lines, but I´ll try to do my best in the learning process :D

---

### Post by incubus on 2006-06-23
lonrot,

Make a copy of the current xorg.conf somewhere (just in case), then copy the backup you have over it.  If it doesn't work you can revert.

But that doesn't solve your problem: you still don't have 1024x768.

vigleik was absolutely right in pointing that it's a better (safer) idea to use "dpkg-reconfigure". The downside of it, as you noticed, is that you will be asked some questions that you may have no idea. With the working backup, you could try to answer them and come here if you need help.

By the way, do you get the correct resolution in the Live CD?

Can you post your xorg.conf?

incubus

PS: How did you access your linux partition from windows? What's the filesystem? If it's ext2/ext3, there is a driver that you can use to read/write.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by lonrot on 2006-06-23
> Edited, I managed to fix the problem with the blue-screen its very simple, even though I coundn´t change the resolution to 1024X768

Now that I know how to get back working I could try several times if I get black screens ^^

---

### Post by lonrot on 2006-06-23
Back then I was typing in my old computer but now I can finally use ubuntu 8) 
So here is my xorg.conf tha I just fixed with the blue-screen

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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV36.2 [GeForce FX 5700]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"CT520n"
	Option		"DPMS"
	HorizSync	30-54
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36.2 [GeForce FX 5700]"
	Monitor		"CT520n"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I have already installed the nvidia drivers.
My monitor is an AOC CT520n
And for now my best resolution is 800X600 at 60Hz. 
Still looking for a way to view the screen on 1024X768 though :P

---

### Post by incubus on 2006-06-24
So you still get the bad screen if you change it like this?
```

Modes		"1024x768" "800x600" "640x480"

```

By the way, you're using "nv" which probably doesn't give you 3D acceleration. It's not necessarily a bad thing, but you could get 3D rendering by using "nvidia". (first you have to make sure you installed the driver and loaded it [restart will do]).

Check that through:
```

$ glxinfo |grep direct

```

You'd want "direct rendering: yes".
I don't know if using "nvidia" would solve the resolution problem.

incubus

---

### Post by lonrot on 2006-06-24
Yes, I'm still getting black screen if I add 1024X768 that way.
Added "nvidia"

Tried to sudo glxinfo |grep direct and...
```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

I think the installation of nvidia is not fully complete, I downloaded the file NVIDIA-Linux-x86_64-1.0-8762-pkg2.run and I followed instructions that I found on a site. Is there a way to check if the drivers are correctly installed?

---

### Post by incubus on 2006-06-24
lonrot,

I strongly recommend you to try the Ubuntu driver before installing "manually", because the ubuntu package has been troubleshooted by many people. When that doesn't work, then you go for the latest driver.

Check these sites:
[http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver](http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

But maybe your installation is working.

Can you run:
```

$ glxgears

```

incubus

PS: The dollar sign ($) means you run as a user. The number sign (#) means you run as root (using sudo).

---

### Post by vigleik on 2006-06-24
[QUOTE=lonrot]
Still looking for a way to view the screen on 1024X768 though :P[/QUOTE]

I still think the easiest way to do that is with dpkg-reconfigure. If you have nvidia drivers installed, be sure to choose the nvidia driver when you do this. And be sure to choose 1024x768 when it comes to that part (by pressing space).

I know it will ask you some questions you don't know the answer to, but you can just choose the default for each of them. Besides, what do you have to lose? You'll make a backup of a working xorg.conf file first, so if you screw up you can always just restore the backup.

Vigleik

---

### Post by lonrot on 2006-06-24
Yup I followed the instructions over the webpage you gave me, some stuff was already taken and other missing. Everything worked fine, now I have the Nvidia settings in system tools, I can see the gears and I switched to direct rendering. ^^

Still having the same issue with the 1024x768 tho.

---

### Post by lonrot on 2006-06-24
Thank you vigleik. As I said before, I have already used the blue-screen several times, it helps a lot cause now I can reconfigure it whenever the black screen comes out.

Everytime I choose 1024X768 (selected all posible Hz) I get black screen, if I don't select it I can see the screen again with 800x600 resolution. You can check my xorg.conf [here]("http://www.ubuntuforums.org/showpost.php?p=1175602&postcount=7").

Thank you all for your interest.

---

### Post by vigleik on 2006-06-24
I'm sorry to hear it's not working for you. Usually dpkg-reconfigure works, especially with the nvidia driver.

There is one other thing you can do. You can try another distro (for example the latest simplymepis release candidate, they have a live CD and good hardware detection) and see if you have better luck there. If you do, you can either install simplymepis instead or copy the xorg.conf file it makes for you to your ubuntu install.

But I can understand if you're tired of trying. It's things like this that prevents linux from being "ready for the desktop". I think the monitor is set correctly by default in 95% of the cases, and after the amount of work you've done in 99% of the cases. It doesn't help those in the last 1% though....

Vigleik

---

### Post by incubus on 2006-06-24
EDITED: Sorry, I didn't read your post saying that you already tried all frequencies. If you haven't tried sticking it to 60Hz, give it a shot.

Yeah, I again agree with vigleik. At least get another Live CD to see if it can get your resolution working right. If it can, either check what configuration it used, or consider switching. It's sad, but it's also great that we have plenty of options when it comes to Linux! :) 

Mepis is famous for having a terrific hardware detection (I used it before switching to Ubuntu).

incubus

==============================
Before giving up, can you try changing

```

Section "Monitor"
(...)
	VertRefresh	50-85

```

to

```

Section "Monitor"
(...)
	VertRefresh	60-60

```

And adding "1024x768"?

incubus

---

### Post by lonrot on 2006-06-24
This is quite anoying ](*,) I like Ubuntu a lot but I wont be able to use it with this horrible resolution. So my last question is if there is another Ubuntu distro version that could fix this problem. If I'm going to switch from distro I would like something as good as Ubuntu or better, if not... I guess I'll have to go back with windows :(

And thanks again incubus, I'm in debt with you.

---

### Post by incubus on 2006-06-24
lonrot,

I completely agree with you. That is terribly annoying and if I had the same problem I would be disappointed too. I use Kubuntu but I don't think installing the CD with Gnome or XFCE would make a big difference.

If you don't mind me asking, what is this AOC monitor that you have? Is it CRT? Is it an old/new model? Is that error message from Xserver or from your monitor? It's so strange that it can't handle 1024x768 at 60Hz.

No debt, my friend, I still hope we can figure this out.

incubus

---

### Post by incubus on 2006-06-24
I found some information here (googling your configuration):
[http://www.deremate.cl/accdb/ViewItem.asp?Data=12303572%7C23486](http://www.deremate.cl/accdb/ViewItem.asp?Data=12303572%7C23486)

I know Portuguese, not Spanish, but anyway it says that the maximum resolution is 1024x768 at 60Hz. If this is correct, it's not a good idea to run it at 75Hz, it can damage the device.

But again, I see no reason why it wouldn't work. You've tried VertRefresh 60-60, right? What about something like 59-60?

incubus

---

### Post by lonrot on 2006-06-25
Tried 60-60, 59-60 and nothing. So I think this is goodbye to ubuntu.

Can you recomend me a distro with this characteristics:user friendly, accesible and solid for beginer users and pros aswel. Cause I wanted to stay with Ubuntu for a long long time, I don't like switching OS all the time.

Ubuntu has a great community support that's what I like too.

---

### Post by incubus on 2006-06-25
lonrot, that's really sad. Good to hear that you will still give linux a chance.

I come from a Debian background, so I'm very biased in favor of it and its derivatives.  When deciding for a distribution, the most important thing for me is package management. It's hard to beat the wonder of not having to worry about zillions of libraries and programs necessary to make one application run.

Mepis also uses the same package system, so you would feel at home. Plus, it seems that Mepis is migrating to use Ubuntu's packages, I don't know if this has already happened. (funny I remember when Mepis was higher than Ubuntu at Distrowatch). Check this out:
[http://ubuntu.wordpress.com/2006/03/28/mepis-embraces-ubuntu/](http://ubuntu.wordpress.com/2006/03/28/mepis-embraces-ubuntu/)
[http://www.mepis.org/node/9970](http://www.mepis.org/node/9970)
[http://www.desktoplinux.com/news/NS6045116609.html](http://www.desktoplinux.com/news/NS6045116609.html)

The other two that I have experience with (very good, indeed) are Gentoo and Arch. I love them, but because time became very scarce for me, I've been using Ubuntu only.

But lonrot, try some live distro like Mepis or Knoppix to see if they get your resolution right. Maybe from there you can figure out what's going wrong.
By the way, I'm downloading simplyMepis right now to see its shape.

incubus

---

### Post by lonrot on 2006-06-25
Okay, I'm downloading mepis. I'm also a little confused about the distros, I've heard mepis is a little too simple in some ways, also I have heard good stuff about suse and fedora. And yes probably I want something similar to Ubuntu 64bit.

---

### Post by incubus on 2006-06-25
lonrot,

I just downloaded simplyMepis and I confirm that it's using Ubuntu's repositories. That's pretty cool because to a large degree you would be using Ubuntu.

Knoppix is famous for hardware detection. But it's not a good choice for installing.

I also hear good things about Fedora and SUSE, but I confess I never tried them. I can't offer much advice there.

I will install Mepis and check how it behaves if I try to install Ubuntu programs.

incubus

---

### Post by lonrot on 2006-06-25
Typing in mepis, and yes it's pretty familiar! I think I'll use it if there is no choise. The funny part is that when I booted the cd the distro used by default 1024x768! I'm checking the xorg.conf...

```
Section "ServerLayout"
  Identifier "XFree86 Configured"
  Screen 0 "Screen0" 0 0
 #Screen 0 "ATIScreen" 0 0
  InputDevice "Keyboard0" "CoreKeyboard"
  InputDevice "PS/2 Mouse" "CorePointer"
 #InputDevice "USB Mouse" "CorePointer"
 #InputDevice "Touchpad" "CorePointer"
 #InputDevice "Stylus" "CorePointer"
 #InputDevice "Eraser" "CorePointer"
 #InputDevice "Cursor" "CorePointer"
 #InputDevice "Serial Mouse" "CorePointer"
EndSection

Section "ServerFlags"
  Option "AllowMouseOpenFail" "true"
EndSection

Section "Files"
  RgbPath "/usr/X11R6/lib/X11/rgb"
  ModulePath "/usr/X11R6/lib/modules"
# True type and type1 fonts

    FontPath 	"/usr/X11R6/lib/X11/fonts/misc:unscaled"
    FontPath 	"/usr/X11R6/lib/X11/fonts/Speedo"
    FontPath 	"/usr/X11R6/lib/X11/fonts/PEX"
    FontPath 	"/usr/X11R6/lib/X11/fonts/cyrillic"
    FontPath 	"/usr/share/fonts/truetype/ttf-xfree86-nonfree"
    FontPath 	"/usr/share/fonts/truetype/java"
    FontPath 	"/usr/share/fonts/truetype/arphic"
    FontPath 	"/usr/share/fonts/truetype/freefont"
    FontPath 	"/usr/share/fonts/truetype/openoffice"
    FontPath 	"/usr/share/fonts/truetype/ttf-bitstream-vera"
    FontPath 	"/usr/share/fonts/ttf/western"
    FontPath 	"/usr/share/fonts/ttf/decoratives"
    FontPath 	"/usr/share/fonts/type1/gsfonts"
    FontPath 	"/usr/X11R6/lib/X11/fonts/Type1"
    FontPath 	"/usr/X11R6/lib/X11/fonts/defoma/CID"
    FontPath 	"/usr/X11R6/lib/X11/fonts/defoma/TrueType"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
    FontPath 	"/usr/local/share/fonts"
    FontPath 	"/usr/share/fonts"
    FontPath 	"/usr/X11R6/lib/X11/fonts"
    FontPath 	"/usr/share/fonts/afms"
    FontPath 	"/usr/share/fonts/bitmap"
    FontPath 	"/usr/share/fonts/truetype"
    FontPath 	"/usr/share/fonts/ttf"
    FontPath 	"/usr/share/fonts/type1"
    FontPath 	"/usr/X11R6/lib/X11/fonts/defoma"
EndSection

Section "Module"
  Load "GLcore"
  Load "bitmap"
  Load "dbe"
  Load "ddc"
  Load "dri"
  Load "extmod"
  Load "freetype"
  Load "glx"
  Load "int10"
  Load "record"
  Load "speedo"
  Load "type1"
  Load "vbe"
  Load "synaptics"
EndSection

Section "InputDevice"
  Identifier "Keyboard0"
  Driver "keyboard"
  Option "CoreKeyboard"
  Option "XkbModel" "pc105"
  Option "XkbLayout" "us"
  Option "XKbOptions" ""
EndSection

Section "InputDevice"
  Identifier "Serial Mouse"
  Driver "mouse"
  Option  "Protocol" "Microsoft"
  Option  "Device" "/dev/ttyS0"
  Option  "Emulate3Buttons" "false"
  Option  "Emulate3Timeout" "70"
EndSection

Section "InputDevice"
 Identifier "Touchpad"
 Driver "synaptics"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 Option "LeftEdge" "1700"
 Option "RightEdge" "5300"
 Option "TopEdge" "1700"
 Option "BottomEdge" "4200"
 Option "FingerLow" "25"
 Option "FingerHigh" "30"
 Option "MaxTapTime" "180"
 Option "MaxTapMove" "220"
 Option "VertScrollDelta" "100"
 Option "MinSpeed" "0.06"
 Option "MaxSpeed" "0.12"
 Option "AccelFactor" "0.0010"
 Option "SHMConfig" "on"
 Option "Repeater" "/dev/input/mice"
EndSection

Section "InputDevice"
  Identifier "PS/2 Mouse"
  Driver "mouse"
  Option "Protocol" "auto"
  Option "Device" "/dev/psaux"
  Option "Emulate3Buttons" "false"
  Option "Emulate3Timeout" "70"
  Option "ZAxisMapping" "4 5"
  Option "Buttons" "5"
EndSection

Section "InputDevice"
  Identifier "USB Mouse"
  Driver "mouse"
  Option "Device" "/dev/input/mice"
  Option "Protocol" "ExplorerPS/2"
  Option "ZAxisMapping" "4 5"
  Option "Buttons" "5"
EndSection

Section "InputDevice"
  Identifier "Stylus"
  Driver "wacom"
  Option "Mode" "Absolute"
  Option "Type" "stylus"
  Option "Device" "/dev/input/wacom"
Endsection

# Settings for wacom eraser
Section "InputDevice"
  Identifier "Eraser"
  Driver "wacom"
  Option "Mode" "Absolute"
  Option "Type" "eraser"
  Option "Device" "/dev/input/wacom"
Endsection
# Settings for wacom cursor (mouse)
Section "InputDevice"
  Identifier "Cursor"
  Driver "wacom"
  Option "Mode" "Absolute"
  Option "Type" "cursor"
  Option "Device" "/dev/input/wacom"
Endsection

Section "Monitor"
  Identifier "Monitor0"
  VendorName "unknown"
  ModelName "unknown"
 #Option "DPMS" "true"
  HorizSync    30.0 - 82.0 # Warning: This may fry old Monitors
  VertRefresh  50.0 - 70.0 # Very conservative. May flicker.
  Modeline "640x480"     25.175 640  664  760  800   480  491  493  525 #60Hz
  Modeline "800x600"     40.12  800  848  968 1056   600  601  605  628 #60Hz
  Modeline "1024x768"    75    1024 1048 1184 1328   768  771  777  806 -hsync -vsync
  Modeline "1024x768"    85    1024 1056 1152 1360   768  784  787  823
  ModeLine "1152x864"    65    1152 1168 1384 1480   864  865  875  985 Interlace
  Modeline "1152x864"    92    1152 1208 1368 1474   864  865  875  895
  Modeline "1152x864"   110    1152 1240 1324 1552   864  864  876  908
  Modeline "1152x864"   135    1152 1464 1592 1776   864  864  876  908
  Modeline "1152x864"   137.65 1152 1184 1312 1536   864  866  885  902 -HSync -VSync
  Modeline "1280x768"    80.14 1280 1344 1480 1680   768  769  772  795
  ModeLine "1280x800"    80.58 1280 1344 1480 1680   800  801  804  827 -HSync -VSync
  Modeline "1280x1024"   80    1280 1296 1512 1568  1024 1025 1037 1165 Interlace
  Modeline "1280x1024"  110    1280 1328 1512 1712  1024 1025 1028 1054
  Modeline "1280x1024"  126.5  1280 1312 1472 1696  1024 1032 1040 1068 -HSync -VSync
  Modeline "1280x1024"  135    1280 1312 1456 1712  1024 1027 1030 1064
  Modeline "1280x1024"  135    1280 1312 1416 1664  1024 1027 1030 1064
  Modeline "1280x1024"  157.5  1280 1344 1504 1728  1024 1025 1028 1072 +HSync +VSync
  Modeline "1280x1024"  181.75 1280 1312 1440 1696  1024 1031 1046 1072 -HSync -VSync
  Modeline "1440x900"   106.47 1440 1520 1672 1904   900  901  904  932 +HSync +VSync
  Modeline "1400x1050"  129    1400 1464 1656 1960  1050 1051 1054 1100 +HSync +VSync
  Modeline "1600x1200"  162    1600 1664 1856 2160  1200 1201 1204 1250 +HSync +VSync
  Modeline "1600x1200"  189    1600 1664 1856 2160  1200 1201 1204 1250 -HSync -VSync
  Modeline "1600x1200"  202.5  1600 1664 1856 2160  1200 1201 1204 1250 +HSync +VSync
  Modeline "1600x1200"  220    1600 1616 1808 2080  1200 1204 1207 1244 +HSync +VSync
  Modeline "1680x1050"  147.14 1680 1784 1968 2256  1050 1051 1054 1087
  ModeLine "1800x1440"  230    1800 1896 2088 2392  1440 1441 1444 1490 +HSync +VSync
  ModeLine "1800x1440"  250    1800 1896 2088 2392  1440 1441 1444 1490 +HSync +VSync
  Modeline "1920x1200"  230    1920 1936 2096 2528  1200 1201 1204 1250 +HSync +VSync
EndSection

Section "Monitor"
  Identifier  "ATIMonitor"
  VendorName "unknown"
  ModelName "unknown"
 #Option "DPMS" "true"
  HorizSync    30.0 - 82.0 # Warning: This may fry old Monitors
  VertRefresh  50.0 - 70.0 # Very conservative. May flicker.
EndSection

Section "Device"
  Identifier  "Card0"
  Driver "vesa"
  BoardName "unknown"
  
 #BusID  "PCI:1:0:0"
 #Option "sw_cursor" # needed for some ati cards
 #Option "hw_cursor"
 #Option "NoAccel"
 #Option "ShowCache"
 #Option "ShadowFB"
 #Option "UseFBDev"
 #Option "Rotate"
 #Option "NoUseBios" # needed for some Savage cards
  Option "UseInternalAGPGART" "no"
  
# nvidia special options, use with care
  Option "CursorShadow" "1"
  Option "CursorShadowAlpha" "63"
  Option "CursorShadowYOffset" "2"
  Option "CursorShadowXOffset" "4"
  Option "FlatPanelProperties" "Scaling = native"
  Option "NoLogo" "false"
  Option "IgnoreEdid" "true" # needs to be true for some nvidia cards
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Card0"
  Monitor "Monitor0"
  DefaultColorDepth 16
  
  SubSection "Display"
  Depth 8
  Modes "1024x768"
  EndSubSection
  SubSection "Display"
  Depth 15
  Modes "1024x768"
  EndSubSection
  SubSection "Display"
  Depth 16
  Modes "1024x768"
  EndSubSection
  SubSection "Display"
  Depth 24
  Modes "1024x768"
  EndSubSection
  SubSection "Display"
  Depth 32
  Modes "1024x768"
  EndSubSection
  
  # Only the official NVIDIA driver supports twinview
  # these setting are an example
  Option "TwinView" "false"
  Option "SecondMonitorVendorName" "unknown"
  Option "SecondMonitorModelName" "unknown"
  Option "SecondMonitorHorizSync" "30-82"
  Option "SecondMonitorVertRefresh" "50-70"
  Option "MetaModes" "1024x768, 1024x768"
  Option "TwinViewOrientation" "RightOf"
  Option "ConnectedMonitor" "dfp,dfp"
EndSection

Section "Screen"
  Identifier "ATIScreen"
  Device "Card0"
  Monitor "ATIMonitor"
  DefaultColorDepth 24
  
  SubSection "Display"
  Depth 24
  Modes "1024x768"
  EndSubSection
EndSection

Section "DRI"
  Mode 0666
EndSection

```

I'm wondering what happens if I replace the Ubuntu xorg.conf with this one?
Something interesting might happen :-k

---

### Post by lonrot on 2006-07-01
It worked but only in the Log in screen. When I entered to the main screen I got the command screen, at least I'm getting close. Can you help me out to know what's wrong?

---

### Post by dschulz on 2006-08-07
Hi all, 

I was in the same scenario, a fresh Dapper install, Nvidia FX5200 vga, and an AOC CT520n monitor.

It was impossible for me to get a decent 1024x768 screen resolution with the Nvidia driver. Curiously, I just connected another 15" AOC monitor (about 2 years older than the CT520n), and it worked perfectly with my config.

So, my (PROVISORY!) solution to this problem is just swapping monitors :mrgreen:  (not throwing away *my precious.. my precious* Ubuntu installation) 

I think switching the distros won't solve this. Nearly all the available distros uses the same software :-k

---

### Post by lonrot on 2006-08-12
Well I have tried several distros and none worked with me. So I installed the 32 bits Ubuntu and everything worked well.

Yeah, switching monitors or forgetting the 64bits.

---

### Post by Kilz on 2006-08-12
> **lonrot said:**
> Well I have tried several distros and none worked with me. So I installed the 32 bits Ubuntu and everything worked well.

Yeah, switching monitors or forgetting the 64bits.

If it works in 32bit, it should work in 64bit. Have you filed bug reports?

---

### Post by lonrot on 2006-08-13
> **Kilz said:**
> If it works in 32bit, it should work in 64bit. Have you filed bug reports?

Well maybe it should work but not on all monitors. And this is not a problem of Ubuntu, Fedora never worked. But trying on the 32bits like MEPIS and Ubuntu does the trick.

Threads regarding the same issue (by myself):
[http://www.linuxforums.org/forum/ubuntu-help/65423-nvidia-1024x768-black-screen.html](http://www.linuxforums.org/forum/ubuntu-help/65423-nvidia-1024x768-black-screen.html)
[http://www.linuxforums.org/forum/linux-desktop-x-windows/64900-nvidia-drivers-wont-work-under-1024x768-resolution.html](http://www.linuxforums.org/forum/linux-desktop-x-windows/64900-nvidia-drivers-wont-work-under-1024x768-resolution.html)
[http://www.mepislovers.org/modules/newbb/viewtopic.php?viewmode=flat&topic_id=17057&forum=29](http://www.mepislovers.org/modules/newbb/viewtopic.php?viewmode=flat&topic_id=17057&forum=29)
[http://www.fedoraforum.org/forum/showthread.php?t=115768&page=2](http://www.fedoraforum.org/forum/showthread.php?t=115768&page=2)

As a result there still a long way to make 64bit a proper distribution.

And nope I haven't filled bugs reports :-k

---

