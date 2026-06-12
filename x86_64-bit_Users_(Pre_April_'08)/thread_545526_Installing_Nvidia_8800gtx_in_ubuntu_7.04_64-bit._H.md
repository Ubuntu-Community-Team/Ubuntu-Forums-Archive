---
title: "Installing Nvidia 8800gtx in ubuntu 7.04 64-bit. Help :("
date: 2007-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thomas64 on 2007-09-07
Hi all, I am writing to you from Vista Home Premium 64 bit (dont hate me :P)

This is my first post here, I have read around here a bit. And on [www.nvnews.net](www.nvnews.net) forums (and random sites) trying to find a -simple- and preferably short guide to installing my graphics card driver in ubuntu...but I have failed thus far. 

On my first Ubuntu install I poked around for a while before finding a shortcut somewhere in the system tab I think (writing from vista so its hard to recall) where I could auto install the nvidia driver. There were warnings that it wasnt open sources and no support etc would be provided. I tried it anyway, and it messed up my ubuntu install (I couldnt boot). Since its in my opinion is faster to reinstall ubuntu than repair it I did that.

On my second Ubuntu install I tried a long and winding readme that came with the new nvidia drivers. 100.14 I believe it was. I came more or less as far as "shutting down the x-server" whatever that is, and it made my ubuntu go blackscreened and not want to boot anymore.

I will install it a 3rd time.

I've heard a lot about the simpleness of ubuntu, and I've played around with it in a virtual machine for a bit...I really want to try it and I really want to like it... :(
I look at myself as a fairly competent pc-user. I've been around since the dos days, and gone through dos 6.22, win 3.11, 95, 98, xp and now vista. I've built all my own computers from scratch.

I am ashamed to say that I just cannot make ubuntu work. I've tried, and I've read. And dammit I've fixed up more computers in my life than I can count (windows based of course...) and I REALLY dont want to throw in the towel on this.

I want to have a real go at Linux. But if I cant even figure out how to install a graphic card driver...I'm not worth my salt. 

Is there anyone that can help me with my problem? I need an easy and preferably short way of installing the driver to my graphics card.

System specifications:

Geforce 8800gtx
OCZ 4096mb ddr2 ram running at 800mhz
intel core2 duo 6420. 2.13ghz processor
Foxconn P35 motherboard
Benq LCD 19' screen.
3x sata drives. 
Dual booting vista hp 64 bit and ubuntu 7.04 64 bit with grub.

I am a TOTAL newbie in ubuntu, please treat me like I know nothing but have a fair chance of understanding.

If there is any other info you would like, let me know. I need a shoulder to cry on. Or at least sigh on.

---

### Post by loserboy on 2007-09-07
it's not your fault, the 8800s have been giving people trouble, being so new and such.

it might be easier to start with a 32-bit install of ubuntu (if kilz is around he's gonna yell at me for saying that)

next we need to know where you get stuck at. Can you run the LiveCD at all?, have you tried using the Safe mode option when you boot the livecd.

edit: just so you know the 32-bit version will work fine for you, in a perfect world you would want the benefit of having a 64-bit OS though

---

### Post by Thomas64 on 2007-09-07
Thanks for the speedy reply!

Bah, I guess I'll try a 32 bit ubuntu for now...and I finally got my 4gb of ram to work properly in vista... :P ah well

I'll try 32 bit in the morning I guess. Good night for now.

edit: I can run the live cd and the install just fine, it boots up perfectly before I install any "extra" nvidia drivers.

---

### Post by loserboy on 2007-09-07
so it works fine until you try to use different driveres?

is there a problem with the default drivers, is it running the slower "vesa" drivers and you are trying to get better ones

---

### Post by Thomas64 on 2007-09-07
I boot from the livecd, choose start/install, and install fine. After that I've tried going to I believe it was System->administration->some sort of driver. There was an option to use a non-supported nvidia driver, I tried that and it messed everything up. I'll explain this better tomorrow when I reinstall.

Second time I tried installing the drivers from [http://www.nvidia.com/object/linux_display_amd64_100.14.11.html](http://www.nvidia.com/object/linux_display_amd64_100.14.11.html) and following the instructions in the readme. But I only got as far as closing the x-driver. Then I got a black screen and my install was messed up again. 

Now I'm really going to bed :P see you tomorrow, and thanks for all help so far :)

Edit: Update.

I booted into Ubuntu from grub. Seems my x-server thingy was not messed up by me stopping it after all. The thing that messed up my install on my second try was going into system->administration-> management of non-free drivers (translated roughly from norwegian). I activated the "nvidia accelerator driver" and then everything went bad and I had to reinstall.

Main Problem: I need an easy and short way of installing the driver from nvidias homepage. It says that my 8800 card is supported so there should be no problem. I just cant manage to install it :|

---

### Post by loserboy on 2007-09-10
I was hoping someone would hop in and help us out here.

It seems you are saying that when you activate the Driver in the restricted driver manager that things get messed up, if that's true then that gives me a place to start to find the answer.

it's true the 8800 is supported, it's just not perfected yet


one program you might be interested in is Envy, it automatically installs the proper video drivers for you.  - [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html). now if you install this program you will want to do it before you do anything else on a fresh install don't even activate the restricted driver as far as i can remember, but don't just go by what i said here, read the howto or even ask alberto, he's a great guy.


other than that, I will start looking for other ways to get the good drivers for your card

---

### Post by CaptainInsaneO on 2007-09-10
Have you tried using Envy to install your drivers? I don't use the 64-bit version but I DO use an 8800gts card (soon to upgrade to gtx :)) and I installed the latest driver very easily using Envy.

Edit: Sorry about that loserboy, didn't see that you already suggested Envy.

Thomas, that link that loserboy gave is the same one I used just a couple days ago to install the drivers for my vidcard after a new install. I can't stress enough to install your video card drivers before everything else. Do that if at all possible.

---

### Post by loserboy on 2007-09-10
thanks for the input captain, I've known that envy was great I just hadn't talked to anyone that used it with an 8 series card yet so thats good to know.  I also just want to put my agreement in for installing the video drivers via Envy before doing anything else, getting the internet to function would be the only exception... hopefully that already works out of the box though.

---

### Post by Thomas64 on 2007-09-12
Hi, and thanks to both of you for your advice and help :)

I actually stumbled upon Envy myself, and tried it out, and sure enough its good advice to install 
the video driver before anything else (internet works out of the box btw). I tried envy, and it worked, more or less. Then I ran the updates, and nothing worked again :P

Seems I'm destined to fail. I have a clean install of ubuntu atm, and I believe my graphics driver is installed, but I dont think the 3d acceleration works. After using envy I can go into the restricted driver manager, and my card is listed as "active". I can still activate it by putting a "v" in the square menu there, but if I do it gets messed up again. 

Woe to me. I'm a bit tired of reinstalling ubuntu, so I'll take a break and do some math (I'm behind in my studies :). But I thank you both for the input, and I'll be checking back on the thread in case any of you think of any more advice.

Thanks a lot for now, I'll update if I try something else (odds are I will since I really want to have ubuntu running ;)

---

### Post by CaptainInsaneO on 2007-09-12
If you use Envy to install your drivers, you should never have to touch the Restricted Drivers Manager.

You  DO have to edit your xorg.conf though if you want all the resolutions available to you. If you happen to be using a Dell 2407WFP I can give you the config you need to put in your xorg file.

---

### Post by Thomas64 on 2007-09-12
I'm using a BenQ 19" LCD FP93GX atm. Bah, now you've given me hope again, guess I'll have to try this out tomorrow :P

If you could post an example of the editing in the xorg file I might be able to figure out how to customize it to my own monitor? Or is that a long shot? :)

---

### Post by CaptainInsaneO on 2007-09-12
I'm at work right now but I'll post my xorg.conf (mostly hand made because the reconfigure command never works for me) when I get home tonight. :popcorn:

---

### Post by loserboy on 2007-09-12
one of the reasons the updates may have broken your X, could have been a kernel update in there and that can sometimes break certian settings, fortunately Envy is made with that in mind and if you do a kernel update and find that X is broken then you can just run a command and it will fix it.... i forgot the command atm but I'll bet captain knows


edit: straight from albertos page


> E) What happens if the kernel is upgraded (e.g. via system updates)?

You will only have to follow these steps:

1) Restart your computer and the Xserver will crash (since it will lack a module).

Say No if the system asks you whether you want to see the output of the error to debug.

NOTE: press ALT+F1 if all you can see is a black screen

Then launch Envy's textual interface from the command line by typing:

(if you're using Ubuntu)

sudo envy -t

(OR, if you're using Debian)

su -c "envy -t"


---

### Post by CaptainInsaneO on 2007-09-12
> **loserboy said:**
> i forgot the command atm but I'll bet captain knows


lol you flatter me. Good boy *gives cookie*

---

### Post by loserboy on 2007-09-12
> **CaptainInsaneO said:**
> lol you flatter me. Good boy *gives cookie*


lol, i t's not flattery, surely someone as handsome and intelligent as you can see that......


:lolflag:

---

### Post by CaptainInsaneO on 2007-09-12
lmao sure sure. I totally see that :lolflag:

Ok, here's my xorg.conf in full, pay special attention to the "Screen", "Device", and "Monitor" sections. Remember to make a backup of your working xorg.conf before making changes in case something goes wonky on you.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
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
    Screen         "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"dbe"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option      "Name"          "Razer Copperhead"
    Option      "Vendor"        "Razer"
    Option      "CorePointer"
    Option      "Protocol"      "ExplorerPS/2"
    Option      "ZAxisMapping"  "4 5"
    Option      "Device"        "/dev/input/mice"
    Option      "Buttons"       "7"
    Option      "ZAxisMapping"  "6 7"
    Option      "ButtonMapping" "1 2 3 6 7"
    Option      "Resolution"    "2000" 
    Option      "SampleRate"    "1000Hz" 
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"2407WFP"
	VendorName	"Dell"
	ModelName	"2407WFP"
	Option		"DPMS"
	Modeline	"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

Section "Device"
	Identifier	"nVidia GeForce 8800GTS"
	Driver		"nvidia"
	Option		"XAANoOffscreenPixmaps" "true"
	Option		"AllowGLXWithComposite" "true"
	Option		"TripleBuffer" "true"
	Option		"NoLogo" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia GeForce 8800GTS"
	Monitor		"2407WFP"
	Option		"AddARGBGLXVisuals" "true"
    DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Enjoy!

---

### Post by tza on 2007-09-12
I'm (probably) having a similar problem - selecting the 2.6.20-15 kernel loads up just fine with an 8400 card, but choosing any newer kernel gives me the black screen.  I'm going to try the black screen Envy update method suggested - I'll post back in a few minutes and update my results.

---

### Post by tza on 2007-09-12
I got nuthin'

selecting any kernel newer than 2.6.20-15 results in no signal at the monitor.  After CTRL +F1, if I have a terminal, I wouldn't know it.

I tried to 'login' with a blank screen, but there was no activity on the disk and I certainly didn't reach the desktop.

However, Thomas64, choosing the .20-15 generic kernel at the grub menu loads up for me with no problem.

Anybody else?

---

### Post by CaptainInsaneO on 2007-09-13
Maybe try switching your drivers in xorg.conf back to nv instead of nvidia? That might make it work for the time being until you can find a more permanent solution.

---

### Post by tza on 2007-09-13
HAHAHAHa!  ha

other maniacal cackling.  Problem is between the user and the chair.  

driver module is built kernel-specific.  I didn't realize this.

using generic driver to boot newer kernel, use Envy, clean the install, reinstall, reboot, pick the correct resolution, reboot, problem solved.

this all started because I worked hard to break stuff that didn't want or need to be broken.

Everyone feel better today knowing that you're smarter than at least one other person on the planet!!

thanks for all the fish:lolflag:

---

### Post by CaptainInsaneO on 2007-09-13
Well, I'm not sure but I think I helped you so you're welcome. :lolflag:

---

### Post by easyease on 2007-09-14
its best to use envy AFTER updating other packages on a fresh install as you will most likely get a new kernal and headers during that first big update and you are supposed to uninstall restricted nvidia drivers before updating. 
I found it best to do the auto update first, then i go to install automatix2 which also installs the appropriate nvid drivers and many other good 64 bit apps and codecs.

---

### Post by handy on 2007-09-14
> **easyease said:**
> its best to use envy AFTER updating other packages on a fresh install as you will most likely get a new kernal and headers during that first big update and you are supposed to uninstall restricted nvidia drivers before updating. 
I found it best to do the auto update first, then i go to install automatix2 which also installs the appropriate nvid drivers and many other good 64 bit apps and codecs.

I always customize the repository choices, then do a full automatic update immediately after an install & before I install *anything* else. 

I don't use automatix anymore but that was always my next step after the updates, & was used to install the nVidia restricted drivers, amongst other things.

---

### Post by praxis22 on 2007-09-14
This may be redundant if you've already got it working but this comes from the August edition of Linux Format (UK) 

**Nvidia GeForce 8800GTX/GTX**

> As for Linux support, it's back to where the 5950 was when it launched - you need to boot into VESA  mode and install the Nvidia binary driver by hand. Some older distros, including Ubuntu 6.10, seem to have issues with running the GTX card in VESA mode, but this was fixed in 7.04 and never seemed to be a problem in SUSE.

    Installing the binary driver on Ubuntu 7.04 wasn't easy, because it needs to be installed when X isn't running. For some reason , killing GDM and X to get to a command line left us with a blank screen as did pressing Ctrl+Alt+F1. Our solution was to open up an X terminal and run **sudo rm /tmp/.XO-lock** - without that file, the Nvidia installer wont realise X is running, so you can install the driver safely. We did have one further problem that was the result of trying to use the Ubuntu restricted driver installer, because it turns out that the driver Ubuntu helpfully installs for you is too old to support 8800 cards! Our solution: don't touch the restricted driver installer

The August issue is the "HARDWARE GUIDE 2007" issue

Hope that helps.

---

