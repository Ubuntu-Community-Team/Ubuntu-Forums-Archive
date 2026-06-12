---
title: "several problems with Fiesty"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Snyper64 on 2007-04-20
Like the title says, I am having several problems since I upgraded to Fiesty. The first and biggest happened when I tried to do a system upgrade from Edgy to Fiesty and right at the end of the upgrade I got errors about not being able to install my Nvidia graphics driver that completely froze/crashed my system so bad that I had to reformat to get Fiesty to install.

After getting everything to install I still could not get my nvidia driver(9755) to install correctly either through Automatix or through Envy. I even tried to install version 9631 but it still came up about my xserver crashing? Somebody said on one of the posts i was reading to update through the Restricted Driver Manager but it just pops up saying I do not need any restricted drivers(I'm currently just running the default nv driver) and am at a loss here?

Also when I am in the text only mode when I go to restore my xorg file I keep getting the message: bcm43xx_microcode5.fw not available or load failed. Is there any way to fix this or atleast disable this? I have given up on my built in broadcom card awhile ago and am currently saving up and looking for a good pcmcia card that plays nice with Linux(I'm open to suggestions if you have any) so disabling it is no problem.

I have 2 sound cards on my pc as you can see in my lspci output:```
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
``` I only use my external soundcard so i do not need my internal to work(I lost my saved link to a post with a guy that has the same series of laptop as me and posted what items need to be blacklisted), I previously disabled this card in Edgy due to the fact that it interfered with my USBs digital output, I have not tested whether it is interfering with it now but I would rather just disable it to save some problems.

I tried to download the NTFS support update off of Automatix but it doesn't seem to work, I can mount my USB drive as usual but I still cannot write to it and for some reason it will not dismount from my pc. I went into properties to see if I just needed to change the Permissions but it sad that the user was root and had everything blanked out. Has anybody gotten this to work right?

And finally has anybody gotten their forward and back buttons to work in Firefox on Fiesty? I had them working fine on Edgy but when i added in the options to my xorg file it didn't seem to make a difference. My mouse is a Logitech MX310 and below is a copy of my xorg.conf file.```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 420 Go 32M]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 420 Go 32M]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

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

Section "DRI"
	Mode	0666
EndSection
``` I'm pretty sure the old protocol for my mouse was ExplorerPS/2 but it was labled as ImPS/2 so I just go done changing that so lets see it that was the only thing holding it back after I reboot in a few.

Sorry about all of the question but any help you can give me would be greatly appreciated.

---

### Post by Snyper64 on 2007-04-20
Never mind about my mouse, it now works after changing it from Im to Explore protocol.

EDIT: Got my internal sound card disabled and maybe I got the bcm43xx driver(I won't be sure until I have to go into text only mode) killed in the the blacklist.

EDIT2: I seem to have gotten my external hard drive to work once I noticed that there was a NTFS configuration tool in my system tools menu and that allow write access wasn't selected. Once I checked it and restarted it worked like a charm. I also got my Nvidia driver to install by downloaded several packages and starting the installation in the desktop so that they wouldn't install and checked the outputs of each one until I found a compatible driver(9631) and than I used Envy to install it and surprisingly it worked unlike earlier. Also I did not get that problem with the uninstalling driver.

---

### Post by Snyper64 on 2007-04-23
Ok, I still have one small problem, I can not get my USB drive to unmount from my laptop. When I click to unmount the drive it pops up writing data to device but than a window pops up showing the drive contents and I get an error saying that it can not unmount device. Any ideas on how to fix this?

---

### Post by DuXati on 2007-04-24
I'm having the same problem! Can't eject or unmount my external hard disk... An error message pops up saying 

"Writing data to device | There is data that needs to be written to the device ST332082 0A before it can be removed. Please do not remove the media or disconnect the drive."

In the previous version of Ubuntu, this hard disk worked fine, but in 7.04 this happens...

Any ideas?

---

### Post by Snyper64 on 2007-04-24
Same exact error message as me and yes my drive worked perfectly fine in Edgy also. Does a filder pop up on yours also that shows the contents of the drive along with an error message that says it can't eject?

---

### Post by DuXati on 2007-04-24
Yes, I've got that screen too! Exactly the same problem...

Hope there is a solution too :)

---

### Post by oxobfe on 2007-04-28
**This post could be related to an Ubuntu bug filed at**: [Bug #99538]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/99538/comments/6") [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just upgraded to feisty and my external drives won't eject either.

Although it's more of a workaround than a fix, the above bugfix makes it so that "Eject" in your right click menu becomes "Unmount Volume."  If you have more than one partition on that drive, this will change that you have to unmount each of them before disconnecting rather than the way that ejecting does it all for you.

I just added an arbitrary .bak extension to my 10-storage-policy.fdiv file just to that it will be unrecognized by what is using it rather than moving it as the bugfix up top to tells you to do,

When you restart your computer as this bugfix tells you to, I suspect that it should unmount your drives without an issue.  Just to be on the safe side, I ran a "sudo umount /media/<partition-name>" for each partition on the drives.

Related Bugs:
[Bug #107963]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107963")
[Bug #81239]("https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/81239")
[Bug #63090]("https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/63090")

Related Thread:
[ Cannot unmount USB hard disk in Ubuntu 7.04]("http://ubuntuforums.org/showthread.php?t=401591")

---

