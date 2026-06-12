---
title: "ubuntu 64 and evga geforce 7600 gt"
date: 2007-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by saru411 on 2007-03-12
hello there
   i have been introduced to ubuntu by a close friend. i dont know much about linux or ubuntu but i can follow the simple instuctions given in alot of the posts on the forums and main page. my problem is that im running edgy 6.10 64 bit and have a newly built system also running evga geforce 7600gt. now ive installed the drivers from the sources ive found on these forum and all ive recieved are x server not found errors. since im new to this i have no idea how to fix those errors and have reinstalled edgy 4 times now. ive been working on this problem and also my on board wifi for well over a week. i dont mind reading to learn what to do........but i really need something to go right to cheer me up on "linux"

---

### Post by bender5788 on 2007-03-12
hey buddy ive got a 7600gt on my system right now if you want some help though you will need to give a little more info.

Here are a few things that could help
1. Kernel Version.
To get this in the terminal or tty type ```
uname -r
```
 (I use the 2.6.17.10 generic kernel (because the nvidia-glx breaks my X in the 17.11 kernel))
2.What are the packages you are installing to get your nvidia stuff going.
3. any error logs would be great if could.

and don't stress some times its something simple

---

### Post by saru411 on 2007-03-12
uname -r
 gives
2.6.17-11-generic

[http://www.nvnews.net/vbulletin/showthread.php?t=87714](http://www.nvnews.net/vbulletin/showthread.php?t=87714) is a driver that looks up to date but its not packaged correctly for me to run in terminal.

ive installed the drivers 3 times now all resulting in an error that sends me straight to a terminal(looks like im running dos) and i have no access to my gui. well i might have access but im a linux newb and have no idea how to revert to the back up driver other than reinstalling ubuntu for a 5th time. last time i did this i saved the file and then saved the name of it as a folder name on the Desktop. i could get to that file on the Desktop but had no way of restoring it.

---

### Post by saru411 on 2007-03-12
ok now im trying the how to in [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) .

 im a little confused about what i should do in step 2.) Find the appropriate module for your kernel. For example, if you have linux-image-amd64-k8 installed, then you should install linux-restricted-modules-amd64-k8. Selecting one will also install nvidia-kernel-common. (Note: you have to select the restricted modules first because the nvidia-glx package automatically installs the i386 one - and if you have a generic kernel image, the X will not work.

this is telling me generic kernel wont work? i dont wish to go further in this how to until i understand what i should or shouldnt be doing since my kernel is 2.6.17-11-generic

all help is very much appreciated. 

your friendly newest newb

---

### Post by bender5788 on 2007-03-12
Ok good well i know know your running the 2.6.17.11 kernel (which is not compatible with the nvidia common modules).
Try booting to the 2.6.17.10 kernel in the grub/boot menu you should have roughly 6 entries (if your using windows as well) it should be about the third. Once there run this commmand 
```
sudo aptitude remove nvidia-kernel-common
```followed by this one 
```
sudo aptitude install nvidia-glx
``````
sudo nvidia-glx-config enable
```Thats should give you access to the supported nvidia drivers which do work for my 7600gt albeit a gigabyte one it is still the same architecture and is just a nvida card with a few different features.
now a simple one line command ```
startx
```From there do your self a favour and ask about getting the drivers to work in the 2.6.17.11 edgy kernel most likely they will tell you to use a script called ENVY.

Which can be found here [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb)

give that a try and if still doesnt work just do what i did and remove the 17.11 kernel and continue using the 17.10 for the shear sake of it actually working with almost everything.


Also if you just need your GUI back to be able to get your head around it run this command
```
sudo dpkg-reconfigure xserver-xorg
```
When your in there you will see Nvidia and NV(the open source drivers) for the sake of even having a GUI in the meantime use the NV also at some point itll ask about modules make sure you uncheck the glx module.

---

### Post by saru411 on 2007-03-12
ok im about to try your instructions but i have a few questions first...
how do i get/install/boot the older kernel you are reffering to
im not running another o/s on this system, its a fresh install on a fresh system
should i install another copy of ubuntu on one of my other hdds so i can boot from it to solve these issues easier?
also should i continue the howto i mentioned in the earlier post or just forget it and follow our instructions.....again thanks for your time

---

### Post by bender5788 on 2007-03-12
ok first of WOW that was a quick reply
Ok to boot to the older and would say more reliable in the case of ubuntu.
At any stage during the boot process does it come up with a textual menu with something like this
Ubuntu.........................2.6.17.11
Ubuntu/........................2.6.17.11 (safe mode)
Ubuntu........................2.6.17.10 (the little blighter you want to use
yad yada yada

if it doesnt shortly after post keep hitting esc and itll bring the menu up
as for uninstalling them use synaptic. The exact steps are fairly long to detail but it entails removing something which sounds way more important than it really is.
The other option is you could just remove the option from your GRUB
But this involve editing the config fiel  for grub (well actually a menu list)
To try that type this 
```
sudo nano /boot/grub/menu.lst
```
look for somethng similar to this
```


title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```
```

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot
```

and quite simply delete that line and save it. It wont delet the Kernel just make it so you can't boot to it

---

### Post by saru411 on 2007-03-12
ok i booted with the stable kernel and ran most of the commands you asked me to....

i input the startx command and got this

 startx
xauth:  creating new authority file /home/saru/.serverauth.5327

X: user not authorized to run the X server, aborting.
Couldnt get a file descriptor referring to the console

---

### Post by bender5788 on 2007-03-12
hmm that is rather strange as if it has set the permissions to be root only never mind try```
sudo startx
``` Thats about all i can think of in the short term.
I guess you could try askng some of the more experienced people but they can become rather frustrated with people asking about the X server because it is such a common problem... hmm im genuinly puzzled by that x error though i may try and replicate it using my server. (dont need the GUI anyhow)

---

### Post by Mau on 2007-03-13
Hi,
I have a 7600 GT card running 64bit and I installed the drivers using Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It worked quite well and I recommend it. 

Good luck,

---

### Post by saru411 on 2007-03-13
ok so i used envy and ran it. it would still crash saying it couldnt detect screens. 

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
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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
	Identifier	"Generic Video Card"
	Driver		"nv"
	BusID		"PCI:6:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
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


yes i changed nv to nvidia and rebooted and now im running it with nv so i can respond here.

when i installed using envy i did notice it added the pci bus


lspci command gives 

00:00.0 Host bridge: Intel Corporation 975X Express Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 975X Express PCI Express Root Port (rev c0)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controller RAID (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
06:00.0 VGA compatible controller: nVidia Corporation Unknown device 0391 (rev a1)


hope that helps fix my problem

---

### Post by rajeev1204 on 2007-03-15
Hi

i use evga 7600 gt on dapper 64 .

The best way of installing anything is via the synaptic package manager since it takes care of dependencies also .But anyway since u have already installed with envy here are a few tips on ur problem ( i hope )

type in terminal sudo dpkg-reconfigure xserver-xorg

now it will take u through a list of options.

in the first option it will show a selection of drivers , eg nv , mesa ,nvidia

select nvidia

IMPORTANT - for the rest of the options just press enter ( select the default values)

That should be enough ,

When u reboot u will see the nvidia splash screen just before u log in.

Do u have onboard graphics also? Then u have to set the 7600 gt ( PCI -E) as the primary graphics adapter .I have onboard disabled so iam not sure how to set up both simultaneously.  I 



regards

rajeev

---

### Post by saru411 on 2007-03-16
> type in terminal sudo dpkg-reconfigure xserver-xorg

now it will take u through a list of options.

in the first option it will show a selection of drivers , eg nv , mesa ,nvidia

select nvidia

IMPORTANT - for the rest of the options just press enter ( select the default values)

That should be enough ,

sorry but that just made my xserver crash again. i then reditted xorg.conf back to "nv" and im back up and running.....still not running the correct divers but im now looking into a fresh install. i have a p5w dh and i know about all of the jmicron issues going around. thanks for the help but unless i reinstall edgy, which is unlikely, i will be restarting from a fresh install(dapper 64 or feisty 64)...then i will try your suggestion again.

looks like im stuck using generic drivers :(

---

### Post by rajeev1204 on 2007-03-16
hi

what version of drivers r u using?

i have the nvidia glx 8776 version from repos for dapper.

Anyway if u r going for a fresh install , this time install from repos .There is absolutely no need for newer drivers .Iam a gamer and playing quake 4 fine with version 8776 .

OK one more step in case u do a fresh install which we tend to forget . 

After installing nvidia-glx from repos , which btw also automatically selects the appropriate restricted drivers and kernel modules , dont forget to enable the driver

Type this -- sudo nvidia-glx-config enable

After this step u have to change nv to nvidia in xorg.cong

i.e sudo gedit /etc/X11/xorg.conf

So basically is a 3 step process.

After this doesnt seem to work out only then u need sudo dpkg-reconfigure xserver-xorg

P.S Stick to the official drivers from repos unless there is update available through repos . Running scripts aint necessary at all .

---

### Post by saru411 on 2007-03-19
ok, i still haven't  reinstalled but i took your advice with using the command 

> sudo nvidia-glx-config enable

then i changed the nv to nvidia like you stated.....after reboot i got this

fatal : Could not open ' /lib/modules/2.6.19-7-generic/volatile/nvidia.ko' No such file or directory
(EE) NVIDIA(0):Failed to load NVIDIA kernel module!
(EE) NVIDIA(0):***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

after this there was another page with alot of information(is there a way for me to cut and paste or save this log without writting it all down on paper?). i did notice it had alot to do with the following section of xorg.conf

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

the error report stated that all of these files weren't found. i feel this is most likely my issue......again thanks for your continued support ubuntu community

---

### Post by rajeev1204 on 2007-03-19
hi

ok iam also new to linux ( learning ) why dont u try re installing the nvidia glx drivers?

It may correct errors caused by installing the envy script i guess.

sudo apt-get install nvidia-glx

In dapper , after i select this , it automatically selected linux restricted modules and kernel version. If u have 2 versions listed at boot up in grub , then i say u try another version of kernel . 


for example , when i fisrt installed dapper from live cd , it installs the 2.6.15.26 kernel version . After that when i use synaptic and install nvidia-glx , it also automatically installs 2.6.15.27 kernel and similar version restricted modules ( probably cos the default glx install is version 2.6.15.27 . (newer)

So on boot up i have now 2 linux kernels and when  i select lower version , nvidia doesnt start (xserver ).

So try that and we will see how it goes 


regards

rajeev




Meanwhile iam trying to check what exactly is the envy script !


regards

rajeev

---

### Post by sdman on 2007-03-19
> **Mau said:**
> Hi,
I have a 7600 GT card running 64bit and I installed the drivers using Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It worked quite well and I recommend it. 

Good luck,

Yea I double that same here check my sig I have same card aswell. tseliot GUI driver compilation is working great for me..if your doing a manual install it revision 1.0-9755(I looked up my card on the nvidia site and this is the version it recommends). The GUI does everything automatically sounds like that would be right up your alley.

edit btw my motherboard is the same as yours this was really tricky but this is the way I did it. 

-You wont be able to boot consistently with your pcie video card in the slot so take that out.

- Goto Ihttp://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb download the installer.

- Double click the deb package that will put it in your application>>systemtools menu (dont run the installer just yet, the installer has to be ran while x-server is shutdown).

- Now your ready to reboot your system. when it starts back up enter the bios with the delete key.

-Your in your bios go to the advanced tab and navigate down to chipset. You want to disable  'Initiate Graphic Mode Select'<--this is your onboard video. 

-You want to set your Initiate Graphic Adapter to IGD or PCI/...   (Igd works in tandum with your cpu so that is why I have IGD enable<--optional with maxium DVMT). As long as your have PCI/.. enabled your good to go. Save your setting and get ready to cut off your system.

-with your system cut off install your PCIE graphic card. Now reboot.

-x-server is gonna crash so dont worry. Go through the ok messages and you will come to command prompt.

-login using your user id and password. In command prompt you want to type the following line

sudo envy -t

-depending what nvidia drivers you have on your system its a safe bet to pick option 6 for starters. I think that is uninstall all nvidia drivers not sure but pick that one for starters.

-now click number 1 and go through the prompts and click yes to all the questions.

Your good to go from there on out. I wouldnt have given my input so dont mean to step on anyones toes. I just so happen to have the same motherboard and video as he does. Good Luck.

I left my onboard disabled becuase I use the adapter to run my second monitor. It is just taking up needed resources if you keep it enabled.

---

### Post by saru411 on 2007-03-19
> **sdman said:**
> Yea I double that same here check my sig I have same card aswell.

edit btw my motherboard is the same as yours this was really tricky but this is the way I did it. 



actually you dont have the same mobo as me...i have a p5w dh....which does not have on board video, but thanks for trying

---

### Post by sdman on 2007-03-19
It should still work never the less with that driver. That driver revision is for your card. The glx driver comes with that package and even if you do try to uninstall the glx driver it will automatically download via updates.

This is what is installed on my system :

nvidia-glx-dev
NVIDIA binary XFree86 4.x / Xorg driver development files

nvidia-glx
NVIDIA binary XFree86 4.x driver

with the envy driver. try downloading opengl. All I know it was a pain but was worth it to have the right drivers. Good Luck hope you get it going.

---

### Post by kuja on 2007-03-20
--First, run envy in the kernel you are going to use, keeping in mind the video driver is very, very, very kernel specific, even the smallest subversion change is a problem.
--Second, assuming you're running edgy, run "sudo nvidia-xconfig", then start the x server.
--Thirdeither you're good to go, or you should attach the file /var/log/Xorg.0.log so we can figure out what's going on :P

---

### Post by FrozenFOXX on 2007-03-20
Have to admit, I'm using a 7800GT on Edgy and it worked without issue.

All I did was got the nvidia restricted modules (believe it's nvidia-glx, shows up as a regular package in your favorite manager) and modified the xorg.conf where it says "Device" from "nv" to "nvidia." Restart the X server, it works.

---

