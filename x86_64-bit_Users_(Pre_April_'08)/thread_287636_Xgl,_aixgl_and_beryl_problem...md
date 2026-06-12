---
title: "Xgl, aixgl? and beryl problem.."
date: 2006-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by MasterHead on 2006-10-29
Hi, ill try to explain the best way the problems i have find, i guess someone has got the same problems and ive been through the forums without result.. :(

Ive been using kubuntu since Dapper was released, and a bit later i started to use compiz with amd64, nvidia( i have a Geforce6800GT ) and xgl, following this guide [http://ubuntuforums.org/showthread.php?p=845077](http://ubuntuforums.org/showthread.php?p=845077) and everithing perfect, later on i updated to cgwm and compiz-manager whitout an issue.

Now that edgy has been release ive updated my whole system to it, and add the new repositories i found :

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy-amd64
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy-amd64
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy-amd64
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy-amd64
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy-amd64

and dist-upgrade everything after reseting the changes i made in kdmrc and displayconfig-restore as from wath ive seem they where for compiz and xgl, the only thing i havent found yet its a repository with specific kernel for amd64 in 2.6.17 branch, as im using a generic kernel right now and repository nvidia drivers.

restart the system, and everithing ok, launch beryl-manager, it starts for less than a second i saw the beryl symbol in the taskbar and then the taskbar dissapears and everything feezes.... 

How can i now if i have xgl or aixgl right now? edgy is supposed to use aixgl,  so it should be install by default over the xgl install, right? thinking i should have aixgl i have followed the wiki guide for ubuntu and aixgl [http://wiki.beryl-project.org/index.php](http://wiki.beryl-project.org/index.php) … Edgy/AiGLX , which is pretty simple  but my computer hangs, should i use the beta drivers?

mi xorg.conf is the same i had before in dapper, except the "Option "AddARGBGLXVisuals" "True" " line i add just to try more options, so i have tried beryl with and without that line.. .i attach my xorg.conf as there might be something wrong...

if someone ca help me it would be really appreciated.. :) as from what ive read the best beryl option is using aixgl.. :)
Thanks a lot.. :)

---

### Post by MasterHead on 2006-10-29
one of my doubts is if iam still using xgl or with the upgrade iam using aixgl right now, how can i verify this? "ps -ef | grep xgl" should give a clue( iam at work so i cant try)?

in case iam still using xgl, how can i uninstall xgl and install aixgl... i used apt-cache search to find aixgl and found nothing.. ¿?

as you can see iam a bit lost.. xD

---

### Post by adam.skinner on 2006-10-29
Try starting beryl-manager from within a terminal session.  This will give you more detailed information about your problem.  It, for example, will let you know if it can find xgl or not, and what it looks for after that.

Also, it's "aiglx" not "aixgl" (easy to get confused on that one).

---

### Post by MasterHead on 2006-10-29
when i try to start beryl-manager it just hangs my computer, what it logs before hunging everithing is that "Xgl absent cheking for nvidia. Nvidia present" after that nothing else.. ¿?

restart the computer and try again, what ive seen is that in the session manager i can choose between start with KDE or xgl, starting with xgl and running beryl doesnt hang mi computer but it doesnt work either.
also i've seen that in kdmrc the Cmd line says "ServerCmd=/usr/bin/X -br" not sure if that is correct, i have the feeling that i dont have aixgl installed but can figure out how to install it.. ¿?

btw when upgradoing the system i cant install kubuntu-desktop as digikam is not working ok, it has unmet dependencies, maybe i need kubuntu desktop install.. dunno...

---

### Post by alek66 on 2006-10-29
I want to start configuring beryl on my edgy, I have a doubt first.
I have a nvidia, what is better: legacy or glx module... I wanted to install first the module for nvidia then set up beryl... But i never knew the difference between the modules.

---

### Post by MasterHead on 2006-10-29
i think legacy driver is for old cards, but iam not sure, if i'am right then you sshould uuse the glx and the restricted modules from the repository for the nvidia to work properly. to check if it is working fine do a "glxinfo  | grep direct", it should  value 1, to test the card you can also run ppracer or glxgears...

Once you have nvidia working you can install beryl, you can use some of the repositories i wrote in the first post and "sudo apt-get install beryl emerald-themes" it will install all the necesary files, if you are using a fresh install of edgy it is already supposed to use aixgl so you run beryl-manager and it should work out, i am having problems but becouse i have upgrade from dapper, i dont have a fresh install :(

the wiki page with tutorial : [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

hope it works for you.. :)

---

### Post by alek66 on 2006-10-29
the thing I dont understand, what engine is best? xgl or aixgl.... or its all the same and I am really confused.

So If I follow the guide that you showed me I can get beryl working?
It doesnt matter if in your guide says  > deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy because some sources you need to use the edgy main-edgy-amd64.... or thats not important because the apt takes care of that?

I installed Nvidia support, when X starts It shows the nvidia splashscreen.  glxinfo | grep direct displays "yes" and glxgears works fine.

I followed your guide: 
1)I added the repo and its key
2)I installed the packages.

> alek@darkstar:~$ beryl
XGL absent, checking for NVIDIA
NVIDIA present
Relauching bery with __GL_YIELD="NOTHING"
Xgl absent, checking for Nvidia
Nvidia present

after that Gnome crashed, top and bootom bars dissapeared, I did a alt+ctl+bckspace and restarted X.

What is wrong?

---

### Post by MasterHead on 2006-10-29
i dont really know the differences between xgl and aixgl, but from what i ve read aixgl should work better with nvidia cards... and since its now the default manager i guessed it is the right way, i really dont know the beneficts of one or another ... ¿? :)

what apt-cache shows you are the packages from official kubuntu or ubuntu repos, so i guess that you used the wrong repo for your processor type or that the repo you used is not working fine..

the sources from the guide are for 32 bit processors, if you have an amd64 processor then you should add -amd64 to the source

so any of this sources 
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy-amd64
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy-amd64
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy-amd64
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy-amd64
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy-amd64

for amd 64 or the same ones taking out "-amd64" if you gt a 32 bit processor.

so after adding this lines to the sources doing "sudo apt-get update; sudo  apt-get install beryl emerald-themes" should install them, if the repo you try doesnt work try another one.. i get this output from apt-cache search:

~$ apt-cache search beryl
beryl - Compositing window manager, decorator and theme support - Beryl
beryl-core - Compositing window manager - Beryl Project
beryl-dbus - Dbus plugins for Beryl
beryl-dev - Development files - Beryl Project
beryl-manager - Tray application launcher tool - Beryl Project
beryl-plugins - Collection of plugins for Beryl
beryl-plugins-data - Plugins data - Beryl Project
beryl-settings - Plugin and configuration tool - Beryl Project
emerald - Decoration engines for beryl

---

### Post by MasterHead on 2006-10-29
if it works out could you post your xorg.conf and kdmrc files? so i can see if i have something wrong.. ¿? thanks.. :)

---

### Post by alek66 on 2006-10-29
> **MasterHead said:**
> if it works out could you post your xorg.conf and kdmrc files? so i can see if i have something wrong.. ¿? thanks.. :)

Extract from sources.list
> ##REPOSITORIOS DE BERYL
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy-amd64


Xorg.conf
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"NVIDIA Corporation NV36 [GeForce FX Go5700]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36 [GeForce FX Go5700]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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


I editted my last post... did you read the last modification?
where can I find the kdmrc files?

---

### Post by MasterHead on 2006-10-29
kdmrm is /etc/kde3/kdm/kdmrc

and from what you say it seems as it should be working so i am not sure what might be happening, ive been looking around and the only thing i see that might help is adding this lines to xrg.conf, save your config first just in case.. :)

adding triplebuffer to your card :

Section "Device"
    [...your configuration...]
    Option "TripleBuffer" "true"
EndSection

and adding this at the end of the config file : 

Section "Extensions"
     Option "Composite" "Enable"
EndSection

i think they may help and seriusly doubt they may cause problems.. i have just installed beryl in my laptop with a intel 950 video card and it worked out at first try... lets see if get to it with nvidia.. :)

---

### Post by philetus on 2006-10-29
I was having problems with Beryl also. xserver not starting, hanging, etc.
I found this guide and it worked.

[https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy)

---

### Post by alek66 on 2006-10-29
> **MasterHead said:**
> kdmrm is /etc/kde3/kdm/kdmrc

and from what you say it seems as it should be working so i am not sure what might be happening, ive been looking around and the only thing i see that might help is adding this lines to xrg.conf, save your config first just in case.. :)

adding triplebuffer to your card :

Section "Device"
    [...your configuration...]
    Option "TripleBuffer" "true"
EndSection

and adding this at the end of the config file : 

Section "Extensions"
     Option "Composite" "Enable"
EndSection

i think they may help and seriusly doubt they may cause problems.. i have just installed beryl in my laptop with a intel 950 video card and it worked out at first try... lets see if get to it with nvidia.. :)

first there is nothing in /etc/kde3/kdm/kdmrc, i am using gnome
second, the mods didnt do anything... It still does the same thing. :???: 

look at this:
> alek@darkstar:~$ beryl-xgl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl-xgl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl-xgl: GLX_EXT_texture_from_pixmap is missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :0.0
is there something xgl... Am i missing an engine or something?
I dont recall installing nothing but what hit guide says [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)
I only installed the guide packages and the nvidia modules.
HElp... I want beryl....:(

---

### Post by MasterHead on 2006-10-29
thanks for the guide.. :)

looking alek66 config i ve seen that i had commented module dri, ive got it out and now i doesnt crash my system completely, so i can restart xserver to work, so ill try one or two thing more and if can get it to work ill go for the beta driver, as the guide says.. :)

right now with the default driver from kubuntu whath i get from beryl i : 

----------------
~$ beryl-manager doesn't autostart window-manager/decorator
any more. Please consult: man beryl-manager


(beryl-manager:9952): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(emerald:10015): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
GL Absent, checking for NVIDIA
---------------

and i loose toolbars and cant do anything but restarting xserver... guess i'am missing something.. but not everithing is lost as this last guide is another aproach through the beta drivers.. :)

i'll keep trying here now that mi computer doesnt hangs completely and tell if i get to something,., .:)

---

### Post by MasterHead on 2006-10-29
you are right, you dont have kdmrm, forgot you were with gnome.. :)

and if you have a fresh edgy install then you should have aixgl installed so beryl-xgl wont work as it is for xgl, so with beryl-manager it should work, i have no idea why it doesnt, and it starting to give me a headache.. xD

---

### Post by alek66 on 2006-10-29
> **MasterHead said:**
> 
---------------

and i loose toolbars and cant do anything but restarting xserver... guess i'am missing something.. but not everithing is lost as this last guide is another aproach through the beta drivers.. :)

So you have the same problem?
I could do anything, beryl-manager, starts but when I want to run beryl... the toolbar dissapear.

yes, i have a fresh edgy install... How do I check the aiglx thing?
...help!

---

### Post by MasterHead on 2006-10-29
actually i would also like to know.. :) so right now i am stuck at this point, so i am looking around for some solution and if i cant find something ill try the beta driver as it s my last resource.. :)

---

### Post by alek66 on 2006-10-29
> **MasterHead said:**
> actually i would also like to know.. :) so right now i am stuck at this point, so i am looking around for some solution and if i cant find something ill try the beta driver as it s my last resource.. :)

In this [guide]("http://www.guia-ubuntu.org/dapper/index.php/Xgl_y_Beryl") it says that if you want to use xgl you should install
>  sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings emerald emerald-themes
could it be this, that we are missing the xgl engines?

---

### Post by MasterHead on 2006-10-29
right, but that guide is for for xgl, with dapper and nvidia we should use aixgl which is the default manager in edgy, there are three ways of working out beryl from what i know, with xgl, aixgl or with the beta driver, from wath ive read, the beta driver will be the best way, but between xgl and aixgl the best way is aixgl( cant explain why as i dont know)... in fact what i was using in Dapper was xgl and compiz.. :)

---

### Post by alek66 on 2006-10-29
> **MasterHead said:**
> right, but that guide is for for xgl, with dapper and nvidia we should use aixgl which is the default manager in edgy, there are three ways of working out beryl from what i know, with xgl, aixgl or with the beta driver, from wath ive read, the beta driver will be the best way, but between xgl and aixgl the best way is aixgl( cant explain why as i dont know)... in fact what i was using in Dapper was xgl and compiz.. :)
I see... And what i have is XGL? because thats the engine that my Nvidia has?
and aiglx.... comes with edgy? is that correct or I missunderstood

---

### Post by oblivion on 2006-10-29
I used this [http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers](http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers) guide when i installed beryl. Don't know if it's any help...

---

### Post by MasterHead on 2006-10-29
in theory youi have aixgl as it is what edgy install, so if you havent change anything you have aixgl, to have xgl you should have to install it ... and beryl should work fine with our configs, but i have no idea what might be happening, i think that for today ive tried it enough and i ll give a try again tomorrow... and probably what i will try its the beta driver, hoping not to break something.. :)

if you want to try have a look to this two guides :

[https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy)

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

i will probably try this guides tomorrow, if they work out ill tell you .. :)

---

### Post by rjcsc on 2006-10-29
Alek66,
I had the same problem... just install the nvidia beta driver

add to source.list:
deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm

and upgrade your system

---

### Post by kleeman on 2006-10-29
A lot of my problems were solved by using the nvidia 9625 beta driver which has proper aiglx support.

---

### Post by alek66 on 2006-10-29
> **rjcsc said:**
> Alek66,
I had the same problem... just install the nvidia beta driver

add to source.list:
deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm

and upgrade your system

I and under 64bit edition... is this mirror for amd64?
does it need a key?

---

### Post by fabertawe on 2006-10-30
> **philetus said:**
> I was having problems with Beryl also. xserver not starting, hanging, etc.
I found this guide and it worked.

[https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy)

Philetus, thank you so much for this!! :D  

I'd been reading up on Beryl and waiting until I upgraded to Edgy to install it and followed one of the huge threads on installing. The repo given for the 64bit nvidia-glx was giving me a 404 so I followed the instructions for the nVidia driver from their site and it totally destroyed my X.

Following the link you have given took about 5 minutes to install, was totally painless and works perfectly!

I have to say I am blown away by Beryl, my desktop is absolutely gorgeous. Way better than I was expecting!

Cheers ... Paul

---

### Post by fabertawe on 2006-10-30
> **alek66 said:**
> I and under 64bit edition... is this mirror for amd64?
does it need a key?

I was getting a 404 for this. See my previous post about easy, painless installation. By the way, I am using an nVidia GeForce 6800 so I can't vouch for it with an ATI or other.

Paul

---

### Post by MasterHead on 2006-10-30
yeesterday before going to sleep i tried the beta driver and i blown away my system.. xD not sure why but nothing started after upgrading, so i restaed with kubuntu live cd, reset xorg config and restart, and xwindows did not start at all, after trying a while i have decided to format and install again, lucky me i could start the console, so i have saved all my data to another partitition and all my config files, so i will start over again with a fresh install ... hope everything goes fine with a fresh install... :)

in the guide there's an amd64 repository for the driver, so ill try that one and pray.. xD i also have a 6800GT, so if it work for you i guess it will do in my system.. :)

---

### Post by MasterHead on 2006-11-02
well, hello again.. :)

at last i have it working.. :)

i am using the beta driver, but not from any repository but downloading it directly from nvidia...

First of all i remove the oficial packages : 
apt-get --purge remove nvidia-glx nvidia-kernel-common, which also removed restricted modules packages... after this i did at-ctr-F1 and login as root, and stoped kdm /etc/init.d/kdm stop
and run the installer from nvidia which made the modules, then run nvidia-xconfig and Modify by hand the paramters needed for beryl in xorg.conf as said in the wiki guide : 

Section "Screen"
    [...your configuration...]
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
     Option "Composite" "Enable"
EndSection


Section "Device"
    [...your configuration...]
    Option "TripleBuffer" "true"
EndSection

Start kdm  /etc/init.d/kdm start and Voila!!!!! :) 


A new happy user for beryl... :) now everything works perfect.. :)

---

### Post by alek66 on 2006-11-02
> **MasterHead said:**
> well, hello again.. :)

at last i have it working.. :)

i am using the beta driver, but not from any repository but downloading it directly from nvidia...

First of all i remove the oficial packages : 
apt-get --purge remove nvidia-glx nvidia-kernel-common, which also removed restricted modules packages... after this i did at-ctr-F1 and login as root, and stoped kdm /etc/init.d/kdm stop
and run the installer from nvidia which made the modules, then run nvidia-xconfig and Modify by hand the paramters needed for beryl in xorg.conf as said in the wiki guide : 

Section "Screen"
    [...your configuration...]
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
     Option "Composite" "Enable"
EndSection


Section "Device"
    [...your configuration...]
    Option "TripleBuffer" "true"
EndSection

Start kdm  /etc/init.d/kdm start and Voila!!!!! :) 


A new happy user for beryl... :) now everything works perfect.. :)

So you donwloaded the beta drivers from Nvidia, unistalled the old ones, and you are running with aiglx?

---

### Post by MasterHead on 2006-11-02
yep, i took out the official ones with apt-get and installed the beta ones from nvidia page : 

[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

go to  beta drivers, and there you are, download them stop xserver as root, install the drivers, just sh NVIDIA_<driver> and it will try to download them from nvidia and as it wont find suitable ones the installer will compile them for you, then it will ask if you want 32 bit compatibility, i said yes, and thats it, run nvidia-xconfig and add the lines to xorg.conf and start gdm... 

i change nothing in the distro, and now i have a fresh install so i'm using the default config for edgy, i think, not sure, from what i've read over the internet that edgy has xorg 7.1( ¿? ) which has integrated aixgl or something like, but in order to use aixgl you have to activate it in xorg.conf and i didn't as it is not necesary with beta drivers... 

i guess i'm not being to clear with this, if you have any doubt i'll try my best to help you getting it working, also when i get home from work i can post my xorg.conf so you can see if there¡s something else you need... it would be much easier to explain it in spanish!!! xD 

As i said any doubt dont hesitate to ask, and i'll do my best to help.. :)

---

### Post by rplantz on 2006-11-02
> **philetus said:**
> I was having problems with Beryl also. xserver not starting, hanging, etc.
I found this guide and it worked.

[https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy)

Same for me. I'm running gnome and using an nvidia geforce FX5200, 128MB.

After many hours of trying other things, this guide finally did it for me. Now I see what beryl is!

---

### Post by alek66 on 2006-11-02
> **MasterHead said:**
> yep, i took out the official ones with apt-get and installed the beta ones from nvidia page : 

[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

go to  beta drivers, and there you are, download them stop xserver as root, install the drivers, just sh NVIDIA_<driver> and it will try to download them from nvidia and as it wont find suitable ones the installer will compile them for you, then it will ask if you want 32 bit compatibility, i said yes, and thats it, run nvidia-xconfig and add the lines to xorg.conf and start gdm... 

i change nothing in the distro, and now i have a fresh install so i'm using the default config for edgy, i think, not sure, from what i've read over the internet that edgy has xorg 7.1( ¿? ) which has integrated aixgl or something like, but in order to use aixgl you have to activate it in xorg.conf and i didn't as it is not necesary with beta drivers... 

i guess i'm not being to clear with this, if you have any doubt i'll try my best to help you getting it working, also when i get home from work i can post my xorg.conf so you can see if there¡s something else you need... it would be much easier to explain it in spanish!!! xD 

As i said any doubt dont hesitate to ask, and i'll my best to help.. :)
I got an error....must be all the mambo jambo thing going on
While installing Nvidia:
"you dont appear to have LIBC header file installed on your sistem"

/var/log/nvidia-installer.log shows:
vidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Nov  2 21:56:53 2006

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


help me jebus

---

### Post by kleeman on 2006-11-02
sudo apt-get install build-essentials

You need that package for any compile work

---

### Post by MasterHead on 2006-11-03
you to apt-get install :

- build-essential
- libncurses (not sure what the current version, 5 i think? )
- kernel-source 
- kernel-headers ( you probably got this one and anyway i think it's not really necesary )
- libc-dev ( not sure if it is named libc6-dev or how it's exactly named, already at work and i dont have any linux here )
- .... cant remenber if you need something else... ¿?

---

### Post by alek66 on 2006-11-03
> **kleeman said:**
> sudo apt-get install build-essentials

You need that package for any compile work
I did that and worked! the thing now is that the nvidia installer goes to 100%, displays "done". But... the program doesnt quit. The only way to get out is: alt+x or alt+c.
crapt! I cant get it to work.

---

### Post by MasterHead on 2006-11-03
i may be wrong but i think you also need to prepare the sources, i mean
 go /usr/src
there you will have the sources tar.gz so tar zxf to uncompressed the sources, and make a symbolic link to linux

ln -s /usr/src/linux-sources-2.7.10 /usr/src/linux

and run he installer, it should make the modules without problems.. if it hangs i have no idea why it miht be.. ¿?

---

