---
title: "ATI problem"
date: 2006-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by deathbyswiftwind on 2006-03-02
hey guys yet again another ati thread. Alright Ive tried using the howto for the newest drivers. I get no errors or anything but when I restart my computer the xserver fails to start. Ive tried the install 3 times and cannot get it to work. The howto works great for my ubuntu 32bit partition. Any help anyways?

---

### Post by cronholio on 2006-03-02
What is the output of:

```
grep '(EE)' < /var/log/Xorg.0.log
```

---

### Post by deathbyswiftwind on 2006-03-02
this is what I get when enter the command

rob@ubuntu:~$ grep '(EE)' < /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

---

### Post by cronholio on 2006-03-03
Umm... this means there are no errors. It's strange though. You might want to check for warnings:

```
grep '(WW)' < /var/log/Xorg.0.log
```

What happens if you use the "radeon" driver instead of "fglrx"?

---

### Post by Defector on 2006-03-03
Well I got some errors for ya: ( i have to copy this from another screen so don't quote me on ALL the spelling):

The Directory "/usr/share/X11/fonts/cyrillicc" does not exist.
The Directory "/usr/share/X11/fonts/CID" does not excit.
'fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttvidfont-conf.d/dirs/CID
Open APM failed (/dev/apm_bios) (no such file or directory)
Ignoring request to load module GLcore
ATI: PCI Mach64 in slot 4:0:0 could not be detected
ATI: PCI Mach64 in slot 4:0:1 could not be detected

So there are my errors.  Any assitance would be GREATLY appreciated. 
I am new to ubunto but i'm not totally green to unix. 
Thanks! 

General Info:
mobo asus p5gd2-x
PowerColor GTO 256mb
lga 775 3.2ghz 
1gb patrit ram

---

### Post by cronholio on 2006-03-03
```
ATI: PCI Mach64 in slot 4:0:0 could not be detected
ATI: PCI Mach64 in slot 4:0:1 could not be detected
```

These seem unusual, you can ignore the rest. Do you have a Mach64 graphics card? What does it say if you do:

```
lspci | grep ATI
```

---

### Post by Defector on 2006-03-03
Thanks for the reply!
Here is my output:
0000:04:00.0 VGA compatible controller: ATI Technologies Inc: unkown device 554d
Hopefully this helps?

---

### Post by cronholio on 2006-03-03
In your /etc/X11/xorg.conf, there should be 2 lines in the "Device" section like these:

```
Driver "vesa"
BusID "PCI:1:0:0"
```

What exactly does it say in your case?

---

### Post by Defector on 2006-03-03
Ah Yes, thanks for all your help, device says
driver "ati"
BusID "PCI:4:0:0"

---

### Post by reh4c on 2006-03-11
[QUOTE=Defector]Well I got some errors for ya: ( i have to copy this from another screen so don't quote me on ALL the spelling):

The Directory "/usr/share/X11/fonts/cyrillicc" does not exist.
The Directory "/usr/share/X11/fonts/CID" does not excit.
'fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttvidfont-conf.d/dirs/CID
Open APM failed (/dev/apm_bios) (no such file or directory)
Ignoring request to load module GLcore
ATI: PCI Mach64 in slot 4:0:0 could not be detected
ATI: PCI Mach64 in slot 4:0:1 could not be detected

So there are my errors.  Any assitance would be GREATLY appreciated. 
I am new to ubunto but i'm not totally green to unix. 
Thanks! 

General Info:
mobo asus p5gd2-x
PowerColor GTO 256mb
lga 775 3.2ghz 
1gb patrit ram[/QUOTE]
I finally have direct rendering saying "Yes," but I have those same errors about detection.  Also, if I run glxgears, my screen slowly starts to bleed into darkness (quite scary actually).  My video card is an ATI Rage Mobility P/M with 8 MB of VRAM.  Any luck on fixing this problem?

---

### Post by jecos on 2006-03-11
I would reccommend dist-upgrading to dapper or just install dapper. [http://www.ubuntu.com/testing/flight5](http://www.ubuntu.com/testing/flight5)
 Your graphics card is officially supported in dapper.

once dapper is installed..


run these commands to get the driver and setup xorg.conf.

sudo apt-get install xorg-driver-fglrx linux-amd64-generic

sudo aticonfig --initial

---

### Post by reh4c on 2006-03-11
I've already been using Dapper for several months.  Also, the fglrx package doesn't work for my old 8MB ATI Rage Mobility P/M laptop card.  It works with the newer Radeon cards.  My laptop is i386 not an AMD64, so why do I need the package "linux-amd64-generic"?

I'm downloading Dapper Flt 5 right now, so I may just do a complete reinstall.  Then, I plan to change the default color depth to 16 instead of 24.  A depth of 24 does not allow my 8MB video chip to work with DRI, since 9600KB is required.  If this small modification to the xorg.conf file successfully enables DRI without installing any additional packages, then I'll report a bug to the developers.  Basically, a color depth of 16 with DRI enabled is more beneficial to me than a color depth of 24 bits and no DRI.;)

---

### Post by deathbyswiftwind on 2006-03-25
just a question on the ati page is says for the 64bit drivers you need to install both the 32bit and the 64bit drivers. is this true?

---

### Post by mellanon on 2006-03-26
I hope that this is the right place to post this question?
Anyway, Hi everyone! 
I installed Ubuntu a couple of days ago, and I am very impressed (Even erased windows completly), but I must admit that I've had second thoughts... I didn't think it would be this hard to install a driver. 
My goal is to be able to use Xgl and Compiz, but first I have to mange to install the fglrx driver. This leads to the problem.

I haven't been able to get the fglrx driver to work with my ATI 9800 PRO. The Xserver wont start...I have searched the web for additional information on how to install the ATI drivers. These two tutorials gave the best result for me:
[Ubuntu installation guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)
[BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

It feels like I'm very close to succeed just one error (+a couple of warnings) in the Xorg.0.log. :-k 

Hardware:
AMD 64 3200+ Socket 754
DFI LanParty nFORCE 3 250 GB
ATI 9800 PRO

lsb_release -a:
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu (The Dapper Drake Release) Development Branch
Release:        6.04
Codename:       dapper
```
uname -a
```
Linux ubuntu 2.6.15-19-amd64-generic #1 SMP PREEMPT Mon Mar 20 16:44:40 UTC 2006 x86_64 GNU/Linux
```
ATI driver:```
ati-driver-installer-8.23.7-x86_64
```
/etc/X11/xorg.conf:
```
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
	Load	"dbe"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"type1"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Hercules Pro"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor		"Hercules Pro"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```
lspci | grep ATI```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
```
It seem like the driver is loaded because the:
```
sudo modprobe fglrx
```
command give no output and
lsmod  | grep fglrx:
```
fglrx                 522976  7
```
kern.log:
```
Mar 26 14:06:23 localhost kernel: [   43.446557] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Mar 26 14:06:23 localhost kernel: [   43.448826] [fglrx] Maximum main memory to use for locked dma buffers: 922 MBytes.
Mar 26 14:06:23 localhost kernel: [   43.449202] [fglrx] module loaded - fglrx 8.23.7 [Mar  6 2006] on minor 0
Mar 26 14:06:28 localhost kernel: [   54.596349] [fglrx] Internal AGP support requested, but kernel AGP support active.
Mar 26 14:06:28 localhost kernel: [   54.596357] [fglrx] Have to use kernel AGP support to avoid conflicts.
Mar 26 14:06:28 localhost kernel: [   54.596360] [fglrx] Kernel AGP support doesn't provide agplock functionality.
Mar 26 14:06:28 localhost kernel: [   54.596364] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
Mar 26 14:06:28 localhost kernel: [   54.596471] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
Mar 26 14:06:28 localhost kernel: [   54.600358] [fglrx] free  AGP = 121909248
Mar 26 14:06:28 localhost kernel: [   54.600361] [fglrx] max   AGP = 121909248
Mar 26 14:06:28 localhost kernel: [   54.600363] [fglrx] free  LFB = 116387840
Mar 26 14:06:28 localhost kernel: [   54.600365] [fglrx] max   LFB = 116387840
Mar 26 14:06:28 localhost kernel: [   54.600367] [fglrx] free  Inv = 0
Mar 26 14:06:28 localhost kernel: [   54.600368] [fglrx] max   Inv = 0
Mar 26 14:06:28 localhost kernel: [   54.600370] [fglrx] total Inv = 0
Mar 26 14:06:28 localhost kernel: [   54.600371] [fglrx] total TIM = 0
Mar 26 14:06:28 localhost kernel: [   54.600372] [fglrx] total FB  = 0
Mar 26 14:06:28 localhost kernel: [   54.600374] [fglrx] total AGP = 32768
Mar 26 14:06:28 localhost kernel: [   55.194011] [fglrx] Flat panel plugged out
Mar 26 14:06:28 localhost kernel: [   55.215896] [fglrx] Flat panel plugged in
Mar 26 14:06:31 localhost kernel: [   58.304361] [fglrx] Flat panel plugged out
Mar 26 14:06:31 localhost kernel: [   58.326237] [fglrx] Flat panel plugged in
Mar 26 14:06:37 localhost kernel: [   63.558871] [fglrx] Flat panel plugged out
Mar 26 14:06:37 localhost kernel: [   63.580755] [fglrx] Flat panel plugged in
Mar 26 14:06:41 localhost kernel: [   67.635661] [fglrx] Flat panel plugged out
Mar 26 14:06:41 localhost kernel: [   67.657545] [fglrx] Flat panel plugged in
Mar 26 14:06:46 localhost kernel: [   73.212300] [fglrx] Flat panel plugged out
Mar 26 14:06:46 localhost kernel: [   73.234195] [fglrx] Flat panel plugged in
Mar 26 14:06:51 localhost kernel: [   77.530703] [fglrx] Flat panel plugged out
Mar 26 14:06:51 localhost kernel: [   77.552587] [fglrx] Flat panel plugged in
Mar 26 14:06:56 localhost kernel: [   82.443029] [fglrx] Flat panel plugged out
Mar 26 14:06:56 localhost kernel: [   82.464924] [fglrx] Flat panel plugged in
Mar 26 14:07:00 localhost kernel: [   86.519830] [fglrx] Flat panel plugged out
Mar 26 14:07:00 localhost kernel: [   86.541715] [fglrx] Flat panel plugged in
Mar 26 14:07:04 localhost kernel: [   91.099989] [fglrx] Flat panel plugged out
Mar 26 14:07:04 localhost kernel: [   91.121873] [fglrx] Flat panel plugged in
Mar 26 14:07:08 localhost kernel: [   95.055967] [fglrx] Flat panel plugged out
Mar 26 14:07:08 localhost kernel: [   95.077852] [fglrx] Flat panel plugged in
```
less /var/log/Xorg.0.log | grep '(WW)' 
less /var/log/Xorg.0.log | grep '(EE)'

```
------------------------------------
WARNINGS
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): Bad V_BIOS checksum
(WW) fglrx(0): Specified desktop setup not supported: 8
------------------------------------
ERRORS
(EE) fglrx(0): === [R200DALSetControllerConfigForRemap] === CWDDC ControllerSetConfig failed: 6 - 0
```
I've searched the web for information about the error, but I haven't found any solution to the problem.
I hope that you can help me with this...
If you need the whole output of the Xorg.0.log, I can post it for you...

---

