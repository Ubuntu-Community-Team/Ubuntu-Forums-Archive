---
title: "Another WoW and Wine problem"
date: 2008-07-07
forum: Wine
---

### Post by zithe on 2008-07-07
Yep. I know. You've heard enough of this, and I know I'm going to be told "There are several other posts about this, yes they do have fixes for you, no we really bet you didn't try that, oh have you tried other drivers?" (etc.) none of the other stuff has worked for me. I have tried:
-OpenGL mode
-Different video cards
-Ubuntu 7.10, 8.04, Fedora core 9 (Back to 7.10 again because I didn't like 8.04) 
-registry edits
-taking WoW installs from other computers
-downloading other DLLs

For some reason all of this stuff doesn't work. I recently got my keyboard to work in game (That's actually a breakthrough for me) and FSAA x6 actually worked the first time I tried enabling it (Don't ask me why I enabled that although I was getting 20fps).

I'm using an X1800XT. I know this is an ATI card, but I've gotten well above 20 fps on max with this card at 1280x1024... My current problem is the framerate stuff, and for some reason it likes to kick me out of the game after a few seconds but the instance won't close. I can't close it manually. 

Here is a terminal displaying events starting when the game is opened until it crashes:

> joshua@ubuntu:~$ '/home/joshua/Desktop/World of Warcraft (copy)/Wow.exe' -opengl
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eccc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f518,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x65c634a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d200,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
err:bitmap:X11DRV_DIB_SetImageBits Out of memory!
wine: Unhandled page fault on write access to 0x00000000 at address 0x7dc4d8bd (thread 0009), starting debugger...
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
err:winedbg:dbg_active_attach Invalid event handle: 221c
joshua@ubuntu:~$ 




Thanks for any help. I'll be happy to supply any further information if it's required.

System: 
CPU: Celeron D 330
RAM: 1gb G. Skill DDR2 800
Video Card: Radeon X1800XT 256mb
Ubuntu 7.10
WINE version: wine-0.9.46


I know my system sounds a little unbalanced, but it's perfectly capable for running WoW with AA enabled. (Although I am replacing the Celeron D soon)

Edit: Updated to Wine 1.0 in hopes the game would perform differently. No dice.

---

### Post by upchucky on 2008-07-07
try wireshark to see the timing on the packets, i suspect the connection is dropping because the keep alive signal is getting set aside while the processor is busy with a hardware issue.

the MTU (maximum transmittable units) may be set too high or too low to keep connection active while processor is busy, there is a sweet spot for this setting, google it.

keep in mind that if the hardware issue is solved first then the rest will probably be fine.

mousespeed is directly related to graphics, there is a clue here.

unhandled pagefaults are memory address issues, they usually are somehow outta the address range they are sent to, or there is an actual memory problem.

I just noticed the memory issue may be triggered by a bitmap image it is trying to load, it may be possible to not let it load the image.

---

### Post by zithe on 2008-07-07
> **upchucky said:**
> try wireshark to see the timing on the packets, i suspect the connection is dropping because the keep alive signal is getting set aside while the processor is busy with a hardware issue.



Should I run it in the background while attempting to play WoW? This software is confusing to set up. XD
How should I set it up to get the output I need to find whatever it is you're talking about? o.o

I can't get wireshark to run. Are there any alternatives?

---

### Post by zithe on 2008-07-08
Here's my Xorg > # xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:2:0:0"
	Option		"FSAAEnable" "on"
	Option		"FSAAScale" "6"
	Option 		"Capabilities" "0x00000800"
	Option 		"UseFastTLS" "off"
	Option 		"KernelModuleParm" "locked-userpages=0"
	Option 		"UseFastTLS" "2"
EndSection

Section "Monitor"
	Identifier	"771FS-s"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"771FS-s"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"800x600"	"800x480"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"Disable"
EndSection
Section "ServerFlags"
 Option "AIGLX" "off"
EndSection

I've noticed that reducing the amount of detail stops crashing. My pc would only crash if I turned my camera view quickly with a high level of detail. When I remove the level of detail I can maintain 20fps but it's not very playable. (I know I left FSAA x6 on. Turning it off makes no difference in performance, but image quality is much nicer. Kinda strange)
Adding the second "Option "UseFastTLS"" line stopped immediate crashing. Now I just need to get normal frames. I'm looking into a new cooler for my x1800xt in case it's overheating. My temperature readouts confuse me. o.o
> 
it8718-isa-0290
Adapter: ISA adapter
in0:       +1.36 V  (min =  +0.00 V, max =  +4.08 V)   
in1:       +1.60 V  (min =  +0.00 V, max =  +4.08 V)   
in2:       +3.26 V  (min =  +0.00 V, max =  +4.08 V)   
in3:       +2.99 V  (min =  +0.00 V, max =  +4.08 V)   
in4:       +2.94 V  (min =  +0.00 V, max =  +4.08 V)   
in5:       +1.92 V  (min =  +0.00 V, max =  +4.08 V)   
in6:       +0.10 V  (min =  +0.00 V, max =  +4.08 V)   
in7:       +2.77 V  (min =  +0.00 V, max =  +4.08 V)   
in8:       +3.33 V
fan1:     4687 RPM  (min =    0 RPM)                   
fan2:     2626 RPM  (min =    0 RPM)                   
temp1:      +127°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
temp2:      +127°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
temp3:       +29°C  (low  =  +127°C, high =   +81°C)   sensor = diode   
vid:      +1.088 V

I think I did something wrong.


I know glxgears is not for benching, but I ran it and got 6,500fps.

---

### Post by upchucky on 2008-07-08
glx gears without game running should get around 12,000fps

wireshark is to be running while connected, takes a bit of reading to understand what you are seeing, but the most important part is if packets are dropping lots.

your problem now seems to be vid card related since u were able to see improvements by making a few changes, one thing that does affect frame rates is a poor isp connection but this should only be apparent while connected to a game.

your frame rates at 6,000 are very low i assume this is while not in game, so if you can get that to improve then you should be fine

---

