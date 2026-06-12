---
title: "dual screen support"
date: 2009-07-26
forum: x86 64-bit Users
---

### Post by thundaraptor on 2009-07-26
I have a new system with 9.04 on 64 bit.  I have downloaded the proprietary ati driver but when I access the catalyst interface, it says I need to have admin access to create dual display.  Can someone shed light on how to deal with this?  I have posted in some other categories here on ubuntu forums and no one is answering my threads.  Am I asking the impossible?  

thanks,

TR

---

### Post by doas777 on 2009-07-26
well, after install I found the catalyst control center in my accessories menu. I rightclicked it and selected Add to Panel. then i rclicked the panel icon, and selected properties. I added 'gksu ' to the begining of the command (without the quotes) and that got it running as root. 

I was ultimately unable to make the version of the driver from the repos work with my card, so I ended up downloading it from ATI. their install creates launchers for both normal users and superusers.

good luck,
franklin

---

### Post by thundaraptor on 2009-07-26
I am not advanced enough to know how to install from ati.  any ideas?  i have read the documentation and don't quite "get it".

---

### Post by doas777 on 2009-07-26
try adding gksu to your launcher, and hopefully everything will work for you.

gksu runs whatever command follows it as an admin. sudo does the same thing but it's for command line apps. 

also, dual monitors work a little differantly in linux. i recommend you look at ATI "Big Desktop", as that is what most people want. I prefer twin-view in nvidia, but hey, you work with what you got.

have fun

---

### Post by thundaraptor on 2009-07-26
tried that.  i am a super stupid unix/ubuntu person.  should i write amdccclegksu or something else.  as written it doesn't work, the launcher says 'failed to execute child process' no such file or directory exists.  also same message if gksuamdcccl written in command entry

---

### Post by For The People on 2009-07-26
I believe the command you are looking for is 

gksu amdcccle

you need the space in there, otherwise it tries to run a program called gksuamdcccle which I don't think exists. haha

---

### Post by thundaraptor on 2009-07-26
Sure ran it in admin mode but it still won't let me configure multiple displays.  Any help?

---

### Post by For The People on 2009-07-26
I know that when I wanted to use my svideo out to a projector ati catalyst was of little use. I installed resapplet and this was able to accomplish a mirrored desktop as well as an extended desktop.
Try out: resapplet from synaptic or

sudo apt-get install resapplet

from a terminal... 
Hope this gets you going....

---

### Post by thundaraptor on 2009-07-26
nah didn't work but thanks for the post.  somewhere i am missing some fundamental information about how the video card, xorg and the screens work togther.  anyone?

---

### Post by doas777 on 2009-07-27
well, your issue is exactly why I choose to install the driver from ATI, but I must say, my problems did not end there. it took me quite a while to get the big-desktop settings to work, and get everything at the correct res, and both monitors doing 3da, etc. 

I'll try to remember to post a copy of my xorg when i get home.

---

### Post by thundaraptor on 2009-07-27
I don't quite understand the relationship between the OS, the xorg and the video card or how to tell which drivers are in use currently.  Is there a good tutorial that will explain some of this too me?  Something like the fundamentals not just a copy paste exercise?  I don't actually want to edit the xorg file on my own but I need a better understanding of at least what is happening.

---

### Post by doas777 on 2009-07-27
> **thundaraptor said:**
> I don't quite understand the relationship between the OS, the xorg and the video card or how to tell which drivers are in use currently.  Is there a good tutorial that will explain some of this too me?  Something like the fundamentals not just a copy paste exercise?  I don't actually want to edit the xorg file on my own but I need a better understanding of at least what is happening.


that is a deep question, and is really about OS architechure (which I don't think is where you wanna go with this question). I think the thing you are missing, is that everything above teh kernel in linux is optional, so all the pieces-parts are modular. for instance many people that use ubuntu do not use X at all. as a result, each piece must be able to handle it's own configuration.

so you install a driver in the kernel so that gui window managers (like X or gnome etc) need to configure the vid card for themselves. this would allow you to use different window managers with different video configurations.
This is what xorg.conf is for; requesting the use of a specific driver, and configuring the way it works with X. if another windowmanager wants to use a different (installed) driver, or use it with different settings, then it would need similar config information.

in terms of video, your xorg has 3 sections that are important:
Devices, Monitors, and Screens.

a device is your vidcard itself. if you have a dualhead system, you'll usually two of them (one for each vid output). the device contains info about the driver used, the devices address on the system bus, and device specific options.

a Monitor contains information about your physical monitor, including logical dimensions, refresh, etc.

a Screen, is basically a "Desktop". A screen ties a monitor and a device together to create a desktop. with dualhead systems, you can use multiple screens (each monitor is it;s own desktop), have one really big screen, or with something like Xinerama or Nvidia's Twinview you can hybridize the two to get the best of both worlds (though xinerama is really showing it's age).

on nvidia terminals I use twin-view. on Ati's i use "Big-Desktop" which acts more like a single X screen.

---

### Post by thundaraptor on 2009-07-27
Ok I understand that and it makes sense.  Is there a place or document "the cook book" of all this stuff so that I can at least start learning how to control these things.  I have a dual head video card and want two seperate desktops or one extended just so long as I don't have clones or "virtual extension" which apparently limits 3d and more advanced display modes.  

Thank you for the post.

---

### Post by thundaraptor on 2009-07-27
This is my xorg.  

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Virtual   3840 1080
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Where do I being learning to disect this.

---

### Post by doas777 on 2009-07-27
before we dig too deep into xorgs, have you followed these instructions? they tell it better than i ever could.
[http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)

this is my wack at commenting your existing config. I've only worked on a couple ati builds so no expert.
 
#   sudo dpkg-reconfigure -phigh xserver-xorg 
[COLOR=Green]<resets file to defaults. if you ever really really screw it up, run this command and restart x.>[/COLOR]

Section "ServerLayout"
[COLOR=Green]<a "server" in this sense, is your entire desktop, with all it's screens. the layout defines how the screens are arranged together (how many, left or right of eachother, etc)>[/COLOR]
    Identifier     "amdcccle Layout"   [COLOR=Green]<Identifier is just a name for the configuration block.>[/COLOR]
    Screen      0  "amdcccle-Screen[1]-0" 0 0 [COLOR=Green]<puts "amdcccle-Screen[1]-0" in the layouts Screen 0, starting at 0pixels x 0pixels>[/COLOR]
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"  [COLOR=Green]<don;t mess with this.>[/COLOR]
EndSection

Section "Monitor"
    Identifier   "Configured Monitor" [COLOR=Green]<this is a default monitor section it doesn't do anything at all. you could delete it and you would not notice>[/COLOR] 
EndSection

Section "Monitor" [COLOR=Green]<this is the monitor being used>[/COLOR]
    Identifier   "amdcccle-Monitor[1]-0" [COLOR=Green]<monitor name, so we can refer to it later.>[/COLOR]
    Option        "VendorName" "ATI Proprietary Driver" [COLOR=Green] <not important, jsut a comment>[/COLOR]
    Option        "ModelName" "Generic Autodetecting Monitor" [COLOR=Green]<not important>[/COLOR]
    Option        "DPMS" "true"   [COLOR=Green]<Turns on or off power savings mode. >[/COLOR]
EndSection

Section "Device" [COLOR=Green]<this section is not being used. vestigial>[/COLOR]
    Identifier  "Configured Video Device" [COLOR=Green]<a name so we can refer to it later>[/COLOR]
    Driver      "fglrx"[COLOR=Green] <the name of your driver module. fglrx is the propreitary ati driver.>[/COLOR]
EndSection

Section "Device" <this is the active device>
    Identifier  "amdcccle-Device[1]-0"  [COLOR=Green]<a name so we can refer to it later>[/COLOR]
    Driver      "fglrx"  [COLOR=Green]<the name of your driver module>[/COLOR]
    BusID       "PCI:1:0:0" [COLOR=Green]<the sys bus address of your card. run 'lspci' to find yours if uncertian>[/COLOR]
EndSection

Section "Screen" [COLOR=Green]<this section is not being used, since "Default Screen" is not added to the server layout above>[/COLOR]
    Identifier "Default Screen" [COLOR=Green]<a name so we can refer to it later>[/COLOR]
    Device     "Configured Video Device" [COLOR=Green]<The name of the device we'll be using for this screen>[/COLOR]
    Monitor    "Configured Monitor" [COLOR=Green]<the name of the monitor being used for this screen.>[/COLOR]
    DefaultDepth     24      [COLOR=Green]<color depth. 8/16/24 "bit color">[/COLOR]
    SubSection "Display"
        Virtual   3840 1080  [COLOR=Green]<this should set the desktop to use a virtual resolution (that is probably much bigger than your screen. in this case, you would use your mouse to zoom arround the areas you cannot see)>[/COLOR]
    EndSubSection
EndSection

Section "Screen" [COLOR=Green]<this is the active screen.>[/COLOR]
    Identifier "amdcccle-Screen[1]-0" [COLOR=Green]<a name, so we can refer to it later>[/COLOR]
    Device     "amdcccle-Device[1]-0"  [COLOR=Green]<the device used by this screen>[/COLOR]
    Monitor    "amdcccle-Monitor[1]-0" [COLOR=Green]<the monitor used by this screen>[/COLOR]
    DefaultDepth     24 [COLOR=Green]<color depth>[/COLOR]
    SubSection "Display"
        Viewport   0 0 [COLOR=Green]<creates a viewport at 0 0. I'm not entirely certian why you want to.>[/COLOR]
        Depth     24  [COLOR=Green]<color depth>[/COLOR]
    EndSubSection
EndSection

---

### Post by doas777 on 2009-07-27
oh, and any good discussion of xconfig shoudl cover what to do when it goes wrong.
if you reboot, and you get a black screen or whatever, hit Ctrl + Alt + F1.
hopefully you will be presented with a terminal screen asking you to login. put in your username and password.

now you need to stop X if it is running, so run this command:
```
sudo killall gdm
```now, you can either edit your xorg by hand with a text editor like nano:
```
sudo nano /etc/X11/xorg.conf
```or you can just reset x to default with:
```
sudo dpkg-reconfigure -p high xserver-xorg 
```
if you edit and save the file, and want to test it, just run 
```
startx
```
you can reboot with 
```
sudo reboot
```

---

### Post by doas777 on 2009-07-27
heres my ati xorg for big desktop, with two monitors at 1680x1050 ea. I've hacked it a little so forgive my poor housekeeping.

```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    ModeLine     "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "false"
EndSection

Section "Monitor"
    Identifier   "amdcccle-Monitor[1]-1"
    ModeLine     "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "false"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Device"

    #Option        "HSync2" "65" #This sets the horizontal sync for the secondary display. 
    #Option        "VRefresh2" "60" #This sets the refresh rate of the secondary display.
    #Option        "Mode1" "1680x1050" #Resolution for first monitor
    Option        "Mode2" "1680x1050" #Resolution for second monitor
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
    Option        "Capabilities" "0x00000800"
    Option        "EnableRandR12" "false"
    #Option        "DesktopSetup" "horizontal"
    Option        "PairModes" "1680x1050+1680x1050,0x0+0x0"
    Option        "EnableMonitor" "tmds1,tmds2i"
    Option        "ForceMonitors" "tmds1,tmds2i"
    Option        "DesktopSetup" "horizontal" #Enable Big Desktop
    Option        "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
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

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    Monitor    "amdcccle-Monitor[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1680x1050"
    EndSubSection
EndSection


```

---

### Post by thundaraptor on 2009-07-28
Can I just go into the xorg file and make the same changes?  What if I make an error, how do I fix it?  Thanks for the detailed post.

---

### Post by doas777 on 2009-07-28
> **thundaraptor said:**
> Can I just go into the xorg file and make the same changes?  What if I make an error, how do I fix it?  Thanks for the detailed post.

you can try my xorg, if you have 2 monitors at 1680x1050, but no guarantees. be sure to backup your file first
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bu-20090728
```

if things break, follow my instructions two posts up.

---

### Post by thundaraptor on 2009-08-04
I don't know if you are still following this thread.  I had to drop off working on this for a bit because of work.  I used your xorg configuration.  It isn't working correctly but not broken either.  The screen seems to understand that it should have a big extended desktop.  One screen loads properly and the mouse can move off the edge of the screen, like it would appear on the next over screen.  the problem is that the next over screen is not receiving any signal from the video card.  I boot with a clone apperance but then once the OS loads, it logs me in with one active screen and the other screen "no signal".  thouht on differences between our setups?  Do you think this is related to my 64 bit ubuntu?  is there some type of naming or detecting issue with the difference between your xorg and mine?  also, strangely the ati catalyst control has an entire new slew of options, non of which seem to matter.

---

### Post by thundaraptor on 2009-08-04
a print of the screen is also interesting, revealing that the system thinks it has a large desktop area but I am not getting the full effect.

---

### Post by doas777 on 2009-08-04
I'm still getting the hang of ati myself, but it looks like the issue is with the monitor being enabled. I had a little trouble with that as well. The best guide i've seen on Big Desktop ([http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)), 
 has some advice on it. go to step 4, and perform steps 4 and 5. the rest of my xorg was crafted based on that tutorial, so don't do any of the earlier steps just now.

let me know how it works out. the next step would be to reset to default and try the big desktop tutorial from the top. 

also, are you still using the ubuntu version of the driver, or did you download it from ati? if its the one in the repos, perhaps installing the ati version should be next. 

have fun

---

### Post by thundaraptor on 2009-08-05
> **doas777 said:**
> oh, and any good discussion of xconfig shoudl cover what to do when it goes wrong.
if you reboot, and you get a black screen or whatever, hit Ctrl + Alt + F1.
hopefully you will be presented with a terminal screen asking you to login. put in your username and password.

now you need to stop X if it is running, so run this command:
```
sudo killall gdm
```now, you can either edit your xorg by hand with a text editor like nano:
```
sudo nano /etc/X11/xorg.conf
```or you can just reset x to default with:
```
sudo dpkg-reconfigure -p high xserver-xorg 
```
if you edit and save the file, and want to test it, just run 
```
startx
```
you can reboot with 
```
sudo reboot
```

I tried to revert back to default xorg, didn't work.  
Getting empty black screens.  Used startup mode to enter root command line (ctrl alt f1 didn't work) and still not succeeding.  error message inside root menu are...

sudo killall also tried killall no sudo since already root message "gdm: no process killed"

if i try sudo gedit /etc/X11/xorg.conf message is "Gtk-warning cannot open display"

if i try dkpk.... reconfigure... message is "xserver-xorg postinst warning: overwriting possibility-customised configuration file; backup in /etc/X11/xorg.conf.20090804213718"

Not sure what this means but I think it is something like warning won't restore default because there is a backup.  not sure how to handle.  cannot enter desktop system at this point.  need advice.

---

### Post by thundaraptor on 2009-08-05
just followed instructions on forums to cp backup xorg file but still not working.  this is a major issue.  please help.

---

### Post by thundaraptor on 2009-08-05
actually have restored a working xorg file.  still no joy on big desktop.

---

### Post by doas777 on 2009-08-05
> **thundaraptor said:**
> I tried to revert back to default xorg, didn't work.  
Getting empty black screens.  Used startup mode to enter root command line (ctrl alt f1 didn't work) and still not succeeding.  error message inside root menu are...

sudo killall also tried killall no sudo since already root message "gdm: no process killed"

if i try sudo gedit /etc/X11/xorg.conf message is "Gtk-warning cannot open display"

if i try dkpk.... reconfigure... message is "xserver-xorg postinst warning: overwriting possibility-customised configuration file; backup in /etc/X11/xorg.conf.20090804213718"

Not sure what this means but I think it is something like warning won't restore default because there is a backup.  not sure how to handle.  cannot enter desktop system at this point.  need advice.


this is perfectly normal. if you boot from recovery mode you don't have to kill gnome because it has not started yet. if you use Ctrl + Alt + F1 to get to a terminal however, you have to kill it. sorry for the confusion.

the second message you are seeing is just telling you that it made a backup of the file. a good thing.

so did you try steps 4 and 5 of the big desktop tutorial with the xorg.conf I provided? the part that asks you to run 'aticonfig --query-monitors' and the 'force monitors' commands? those settings do not affect your xorg, but another part of the ATI driver configuration, so if you start off with my xorg, we still need to enable and force the monitors.

Please try restoring your xorg.conf to the previous version (just delete the current file and rename the backed up file to xorg.conf)  and follow these steps from the big desktop tutorial.

> 

[FONT=Verdana][I][COLOR=Red][B]4. Now, you can experiment with your monitors without restarting X. First, you need to see how X identifies your monitors:

[/B][/COLOR][/I][/FONT] 	Code:
 	sudo aticonfig --query-monitor 
[FONT=Verdana][I][COLOR=Red][B]

Then based on the information provided by the query monitor command, replace STRING in the following command:

[/B][/COLOR][/I][/FONT] 	Code:
 	sudo aticonfig --enable-monitor=STRING,STRING 
[FONT=Verdana][I][COLOR=Red][B]The values of STRING should be one of these:
            [/B][/COLOR][/I][/FONT] 	Code:
 	[INDENT] none
crt1
crt2
lvds
tv
tmds1
tmds2[/INDENT] 
[FONT=Verdana][I][COLOR=Red][B] 5. If the enable-monitor command works for you, then you need to add it to the config file:

[/B][/COLOR][/I][/FONT] 	Code:
 	sudo aticonfig --force-monitor=STRING,STRING 
[FONT=Verdana][I][COLOR=Red][B]

Again replace STRING with the values given by query-monitor.[/B][/COLOR][/I][/FONT]


Now Reboot.

also there are some questions in my last post that still need answered. Please let me know what driver you are using (ubuntu repos or the ATI version).

---

### Post by thundaraptor on 2009-08-05
so strange not sure how to describe all this.  I performed enable display command.  it sets turns one display on and the other on but the other is like some crazy zoom in clone of the first.  if I then manually change display settings to 3360 i get the full big desktop working fine.  not sure what to do about all this, think it will not hold when I reboot.  current xorg file is below.  

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "ForceMonitors" "tmds1,dfp3"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal" #Enable Big Desktop
	Option	    "Mode2" "1680x1050" #Resolution for second monitor
	Option	    "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
	Option	    "HSync2" "65" #This sets the horizontal sync for the secondary display. 
	Option	    "VRefresh2" "60" #This sets the refresh rate of the secondary display.
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Virtual   3360 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

still, making progress which is good.  

Thanks,

TR

---

### Post by thundaraptor on 2009-08-05
2nd display is not large enough.  i think my display is set to 3360x1050 but should be more like 3840x1080. ideas?

---

### Post by doas777 on 2009-08-05
I'll take a look at it when I get home

---

### Post by doas777 on 2009-08-05
try this one:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    #ModeLine     "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "false"
EndSection

Section "Monitor"
    Identifier   "amdcccle-Monitor[1]-1"
    #ModeLine     "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "false"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Mode2" "1680x1050" #Resolution for second monitor
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
    #Option        "Capabilities" "0x00000800"
    Option        "EnableRandR12" "false"
    #Option        "DesktopSetup" "horizontal"
    Option        "PairModes" "1680x1050+1680x1050,0x0+0x0"
    Option        "EnableMonitor" "tmds1,tmds2i"
    Option        "ForceMonitors" "tmds1,tmds2i"
    Option        "DesktopSetup" "horizontal" #Enable Big Desktop
    Option        "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        #Modes    "1680x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    Monitor    "amdcccle-Monitor[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        #Modes    "1680x1050"
    EndSubSection
EndSection

```

if it doesn't work straight off the bat, start by uncommenting the lines in the screen sections, and work your way up. I had to do a bit of tweaking and consult some other references to get it just right for my system.

---

### Post by thundaraptor on 2009-08-11
I can't explain what I did.  I have previously installed some type of gui xorg.conf interface tool and since we have been doing so much with the xorg i didn't want the two to interrupt each other.  so I uninstalled the program, basically found its name and then uninstalled it in synaptec, I think that I uninstalled randr and everything associated with a gui interface in my system...  not good.  I have hardy on another partition but i need to fix this first and not totally sure how to proceed as I don't want to delete the information on hard drive when I reinstall.  anyways, this xorg file didn't work but I am confused because my 2nd monitor has a name that is not made reference to anywhere in the above xorg.

at any rate, thanks for your ongoing help.

---

### Post by thundaraptor on 2009-08-12
So I worked through the gui issue and just reinstalled jaunty onto another partition.  Have it up and working, used the repo fglrx driver and your last posted xorg.conf.  Interesting, I have a pseudo dual display look at the screen shot I have posted.  The system somewhere is displaying, I am getting on both screens the desired effect, but the resolution choices are a bit odd.  This is definite progress if I can just figure out how to impact the resolution choices.  Note, in your xorg.conf you had the ```
Option        "EnableMonitor" "tmds1,tmds2i"
    Option        "ForceMonitors" "tmds1,tmds2i"

``` written but for some reason my 2nd monitor is called dfp3 so I change it which made the xorg work.  I am curious if this is an important detail because in the other thread that is the main support for this topic it is written that only ```
none
crt1
crt2
lvds
tv
tmds1
tmds2
``` should be listed as possible names so maybe this is a clue.  

Cheers,

TR

---

