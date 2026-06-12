---
title: "Problems with 8800 driver"
date: 2008-09-20
forum: x86 64-bit Users
---

### Post by aj_k on 2008-09-20
Hello, I hate to add to the mess of these posts but I can not find a solution. I have been reading for the past couple weeks everything I can about this subject but nothing has helped. I am new to linux, but I am pretty good with windows so I have some experience. 

 Well the first thing I did was after a clean install of Hardy 64 was to install the proprietary drivers when it offered to do so for me. After the install of the drivers I reboot and right after ubuntu finishes the loading splash it goes black. I think that this occurs when xserver tries to start.

 So after this did not work, I was able to get back to my desktop by booting in recovery mode and reconfiguring xorg. I then uninstalled the drivers, rebooted, and tried to install the driver from their website with the same result. Then through synaptic, and then I tryed envy-ng and everything led me to the same result of my screen turning black on a boot with the drivers installed and being used by xorg. 

 Now the device will not show up in the list of proprietary drivers and nothing I have done seems to work. Please someone help me

 I am running Ubuntu 64bit 2.6.24-19-generic, with an amd 4200+ x2 on a biostar nf4st-a9 mobo. graphics card is an evga 8800 gts

---

### Post by phidia on 2008-09-21
Sometimes the old drivers cause this particularly after several attempts to install the driver. I'm not running hardy but I think this should work for removing all the old driver crud:

> sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

Then start over again and either use the hardware driver method or synaptic. Hope that helps.

---

### Post by aj_k on 2008-09-21
No luck, I get the same result of a black screen when Ubuntu finishes loading. I do have nvidia x server settings in my system tools now, but it just wants me to reconfigure xorg.conf to use nvidia drivers which gives me black screen. Here is my xorg.conf that gives me black screen. Would a fresh install be better to work with?

---

### Post by davidw89 on 2008-09-21
Try EnvyNG
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by aj_k on 2008-09-21
Tried envy, gave me the same black screen after reboot. I tried the purge and it did not help. Same black screen after installing the driver. Thank you for the suggestions. 
 Here is the last section of my xorg.conf pertaining to the video. This is after I run nvidia-xconfig. 

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

When I restart with this it gives me a black screen. I will do a envy install and see if the xorg looks the same. Cause I get no error message, I cant even get a command line or restart with keyboard, has to be hard started.

---

### Post by davidw89 on 2008-09-21
Hey there mate. I am about to do a dual boot with xp and ubuntu so i'll give x64 a shot and yes i have 8800gt MSI (is that your graphic card)?

---

### Post by davidw89 on 2008-09-22
There's something wrong on your end. Please do this.

Clean install.
Update Manager (about 250mb worth of stuff)
Hardware Driver, enable, it will download.
Restart

It works fine here.

---

### Post by aj_k on 2008-09-22
Ok, yeah im sure it is something I am doing because this card is pretty well supported in my opinion. I was reluctant to do a clean install because I finally got it looking like a mac, but I need this driver to work so I will try the clean install. One question, when you say update manager, is that synaptic manager or a command to use in terminal?

 o david, yes I am running an 8800, mine is an evga gts im pretty sure that just means I have slightly different clock speeds. So it should work well for you to, provided you can get the drivers installed. 

 I am trying the clean install now, I will let you know how it went. Thanks all

---

### Post by soxs on 2008-09-22
> **aj_k said:**
> Ok, yeah im sure it is something I am doing because this card is pretty well supported in my opinion. I was reluctant to do a clean install because I finally got it looking like a mac, but I need this driver to work so I will try the clean install. One question, when you say update manager, is that synaptic manager or a command to use in terminal?

 o david, yes I am running an 8800, mine is an evga gts im pretty sure that just means I have slightly different clock speeds. So it should work well for you to, provided you can get the drivers installed. 

 I am trying the clean install now, I will let you know how it went. Thanks all

It's the restricted manager he is talking about. See System -> System... -> Hardware Drivers or Restricted Drivers

---

### Post by davidw89 on 2008-09-22
How'd you get it to look like a MAC..seriously..did you install compiz and emerald? Got a guide you could link to me?

---

### Post by soxs on 2008-09-23
> **davidw89 said:**
> How'd you get it to look like a MAC..seriously..did you install compiz and emerald? Got a guide you could link to me?

Stop highjacking threads. There is a reason for the PM system....

---

### Post by KeithWatson on 2008-09-24
I am using the following card that I bought just last week as part of a new PC that I just built.
PNY VCG88512GXEB-FLB GeForce 8800 GT 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card - Retail

Right after I installed Ubuntu I was prompted to enable the proprietary graphics driver so I did so and got the black screen whenever I rebooted. I had not yet updated the 200MB of bug fixes at that time.

I have since reinstalled from scratch and performed the updates. I am getting my courage up to try the restricted drivers again, but before I do, can anyone tell me what I could do if they don't work to get my system back to where it is now if they don't work?

If they don't work I plan to try Envy as plan B, but I would rather not have to go through a complete reinstall again. It sounds like such a simple question, but I can't seem to find the answer anywhere.

Thank you.

---

### Post by soxs on 2008-09-24
> **KeithWatson said:**
> I am using the following card that I bought just last week as part of a new PC that I just built.
PNY VCG88512GXEB-FLB GeForce 8800 GT 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card - Retail

Right after I installed Ubuntu I was prompted to enable the proprietary graphics driver so I did so and got the black screen whenever I rebooted. I had not yet updated the 200MB of bug fixes at that time.

I have since reinstalled from scratch and performed the updates. I am getting my courage up to try the restricted drivers again, but before I do, can anyone tell me what I could do if they don't work to get my system back to where it is now if they don't work?

If they don't work I plan to try Envy as plan B, but I would rather not have to go through a complete reinstall again. It sounds like such a simple question, but I can't seem to find the answer anywhere.

Thank you.

When you get a blackscreen:
before to install the drivers: setup a root password via:
```
sudo su; passwd
```
When a blackscreen appears:
Try <ALT><F1>: If that fails you are curesed and you'll have to reinstall from scratch, if you get a console, nothing is lost.
log in as root
```
nano /etc/X11/xorg.conf
```
Now you have the choice:
go to the device section, and replace the driver setup in your DeviceSection (whatever it is) to "vesa" including " " "
If that fails aswell, you can still do (which is aswell presented in the xorg.conf header, if everything fails):
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
Note: You will have to know what keyboard layout, what keyboard varaint and so on in order to get your freshinstall status back...

---

### Post by KeithWatson on 2008-09-25
> **soxs said:**
> When you get a blackscreen:
before to install the drivers: setup a root password via:
```
sudo su; passwd
```
When a blackscreen appears:
Try <ALT><F1>: If that fails you are curesed and you'll have to reinstall from scratch, if you get a console, nothing is lost.
log in as root
```
nano /etc/X11/xorg.conf
```
Now you have the choice:
go to the device section, and replace the driver setup in your DeviceSection (whatever it is) to "vesa" including " " "
If that fails aswell, you can still do (which is aswell presented in the xorg.conf header, if everything fails):
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
Note: You will have to know what keyboard layout, what keyboard varaint and so on in order to get your freshinstall status back...

Thanks, but I don't understand these directions. I think I would have to install again from scratch unless there is a guide somewhere that anyone could point me to.

---

### Post by soxs on 2008-09-25
This will allow you to start with "vesa" drivers again, without having to reinstall

---

### Post by aj_k on 2008-09-25
Ok, I have now formated and installed the current release of unbuntu 64, I started by fixing a grub error in the menu.lst ive been getting where it tries to boot the wrong disk. Then opening synaptic and clicking mark all upgrades, after those installed I rebooted, opened my restricted drivers menu and clicked to install drivers and then after reboot same problem of the black screen after ubuntu splash. Also I cannot get to a console of anything it must be hard started. And now under restricted drivers the driver is green and says in use but has no check in the box.

 I have not done anything else yet, what should be my next step?

---

### Post by soxs on 2008-09-25
post the output from:
```
sudo cat /etc/X11/xorg.conf
```
and
```
glxinfo|grep direct
```

---

### Post by aj_k on 2008-09-25
Cat gives me:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

*********  glxinfo gives me:
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

This is after I booted in recovery mode and reconfigured xorg to get my desktop to boot.

---

### Post by soxs on 2008-09-26
While installing something obviously went wrong.. I will give you some more info on that, later... I have no time atm..

---

### Post by Artemis3 on 2008-09-27
See my signature...

In addition, install nvclock and use ```
nvclock -f -F auto
``` (make sure this occurs aftear each reboot).

---

### Post by aj_k on 2008-09-27
I have installed nvclock, and im not really sure what this progam does. Something about over clocking, I am a little weary about using this program cause while Im just surfing the net I keep most of my fans off. If it is necessary I could learn to use this app. o yeah that xorg output is after I reconfigured xorg to get my desktop back.

---

### Post by soxs on 2008-09-27
> **aj_k said:**
> I have installed nvclock, and im not really sure what this progam does. Something about over clocking, I am a little weary about using this program cause while Im just surfing the net I keep most of my fans off. If it is necessary I could learn to use this app. o yeah that xorg output is after I reconfigured xorg to get my desktop back.

Nvclock is for overclocking AND (this is the part you should take usage, in case you use his install method) fan control on your gpu.

---

### Post by aj_k on 2008-09-28
When I try to hit alt f1 at the black screen nothing happens. crtl alt backspace, ctrl alt del both do nothing. The only thing that will restart the system is a hard start. So after restarting with the button I boot in recovery mode and run xfix and then I can get my desktop back, but now the nvidia driver is not checked in use.

---

### Post by soxs on 2008-09-28
> **aj_k said:**
> When I try to hit alt f1 at the black screen nothing happens. crtl alt backspace, ctrl alt del both do nothing. The only thing that will restart the system is a hard start. So after restarting with the button I boot in recovery mode and run xfix and then I can get my desktop back, but now the nvidia driver is not checked in use.

This is all crapp, I don't understand why it doesn't work. I had a 6600GT andti was just like clicking one button to make it work. Maybe you should checkout wether intrepid alpha 6 works for you ( in case you don't have a eth0 device using the e1000e, which is broken for now, any may kill your hardware)

---

### Post by Artemis3 on 2008-09-29
> **aj_k said:**
> I have installed nvclock, and im not really sure what this progam does. Something about over clocking, I am a little weary about using this program cause while Im just surfing the net I keep most of my fans off. If it is necessary I could learn to use this app. o yeah that xorg output is after I reconfigured xorg to get my desktop back.

The nvidia driver is not using the fan correctly in my 8800, it leaves it in a permanent slow rpm state, which is really bad if you leave a 3d screensaver or 3d game running, it reaches 90c degrees...

nvclock also lets you monitor gpu temp, you can do this with a nice gui for gnome called sensors-applet or issue the command nvclock -i

nvclock also lets you force fan speed, say you want to test 100% (full throttle) you issue the command nvclock -f -F 100

I never use overclocking so can't say much about that.


And to change to the consoles try ctrl alt f1 (or f2, f3, f4, f5 ,f6).

---

