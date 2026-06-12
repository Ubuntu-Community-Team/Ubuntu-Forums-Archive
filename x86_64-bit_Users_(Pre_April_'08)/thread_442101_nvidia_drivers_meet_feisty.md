---
title: "nvidia drivers meet feisty"
date: 2007-05-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by IFailAtLinux on 2007-05-13
I have NVIDIA GeForce FX 5500 card, which is listed as supported on nvidia site. After installing ubuntu feisty few days ago one of first things I did was trying to install nvidia driver trough restricted drivers manager. As easy as that could be, after rebooting PC(which it told me to do) I found X unable to start giving following errors:

> 
NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0
Scren(s) found, but none have an usable configuration.

Fatal server error:
no screens found

And info about API conflict, because my NVIDIA kernel module was 9755 and X module was 9631. I managed to get around that with using following commands before trying to install drivers again(I'm installing them manually now):

```
sudo apt-get --purge remove nvidia-glx nvidia-glx-legacy nvidia-settings nvidia-kernel-common linux-restricted-modules-`uname -r` linux-restricted-modules-common
sudo rm /etc/init.d/nvidia-*
```

After that I'm going with installation of drivers from nvidia homepage and I don't get info about API conflict, but I still get those errorsabout not being able to initialize graphics device. I tried to installing nvidia-glx-new, but that didn't help as well.

Every time I installed nvidia drivers I couldn't start x so I used
sudo dpkg-reconfigure -phigh xserver-xorg
to set nv driver back, so I could at least get GUI. I'm complete begginer when it comes to linux, so I just did what other people suggested.

Anyway, with few days of browsing net for many different solutions(of which none helped and I don't even remember most) I still get those quoted errors. I let 2 people mess up a bit with that trough ssh, but they failed to do any good as well.

I'll just note that I have ACPI set to off, because otherwise my system wouldn't run at all. I get a warning about that when nvidia driver is installed, but that shouldn't by any means stop x from working as far as I know.

I don't know what additional info you might want and need, so in any case just ask(and tell me how to get that info, I'm completely green).

---

### Post by ronacc on 2007-05-13
I have been using an FX5200 for several years with the drivers from nvidia.com (currently 9755) and can assure you they work . you can also use the ubuntu provided version of the driver ( I believe nvidia-glx for the 5200) .I think from the message about 9631 that you have the "legacy" driver installed somehow. try this .
make sure you have build-essentials and the headers for your kernal installed.

go to /etc/x11/xorg.conf and edit the driver from nv to nvidia.
reboot 
when X fails to start hit control>alt>F1 to get a terminal and login
cd to the dir where you have the pkg*.run ( make sure you only have 1 in that dir)
sudo sh NVIDIA"tab" 
answer yes to everything except the last (the configuration)
when the installer exits type  startx and hit return , you should shortly be at the desktop.

---

### Post by expatCM on 2007-05-13
I have the same card .....   I used Envy to install the drivers  ...  easy :)

You will find Envy here
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by IFailAtLinux on 2007-05-13
I tried envy already. Failure:/ (gives the same errors)

I tried the method of ronacc, that didn't help as well, but I didn't know how to check if I have headers of my kernel installed. That method gave me usuall error.

Then I tried installing the drivers from restricted driver manager yet again. Well, I managed to break it nicely and get error message like that:

> 
Failed to initialize NVIDIA kernel module! Please ensure that there is supported NVIDIA GPU in this system and that the NVIDIA device files have been created properly


---

### Post by ronacc on 2007-05-13
to check for the headers open a terminal and type uname -r  . that will give you the name of your kernal.

then go to /usr/src and look for a folder named linux-headers-"that exact name" . if that folder exists you have the headers.

in a terminal run sudo lsmod  and see which nvidia driver is actualy being loaded.


edit  see also this post      [http://ubuntuforums.org/showthread.php?t=435447](http://ubuntuforums.org/showthread.php?t=435447)

---

### Post by IFailAtLinux on 2007-05-13
Well, I have kernel-headers then.

I don't get an error about kernel and x module missmatch anymore, instead I get

> NVIDIA: Could not open the device file /dev/nvidia0 (Input/Output error)

After doing lsmod with grep for nvidia I get:

> 
nvidia  7761464 0
i2c_core 26624 2 nvidia, i2c_nforce2


I hope it is what I was to check.

I tried following instructions in the link from the thread(which didn't work), I tried adding those 2 modules to DISABLED_MODULES, but that didn't help as well.

---

### Post by ronacc on 2007-05-13
I am at a loss your driver "should" be working . I did see some posts about the nforce2 , although the fx5200 should override that. if it isnt mabye that is causing the problem . Have you run update-manager recently ? if not do so , also open synaptic and check the status section and see if you have any broken packages  if you do select edit>fix broken packages . You definately have something wierd going on since that card normaly works very well with linux and the steps you have taken should have fixed any problems.
 I'm almost ready to say try a reinstall.Anyone else out there got any ideas ?

edit : post your /etc/x11/xorg.conf  and the output of lspci

---

### Post by IFailAtLinux on 2007-05-13
I ran synaptic and clicked custom filters->broken. Nothing there.

lspci:
> 
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:07.0 Network controller: RaLink RT2561/RT61 rev B 802.11g


xorg.conf(without hashed stuff):
> 
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"Generic Video Card"
	Driver		"nvidia"
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
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection
 
Section "DRI"
	Mode	0666
EndSection


---

### Post by expatCM on 2007-05-13
I seem to recall that I also saw the error message you mention.  Before discovering Envy I had also been following the best route I could find along the lines you have been describing.

To move forward I used Automatix to uninstall the nvidia driver and then went to synaptic and search for nvidia and also remove everything installed.  I then ran Envy and it worked for me.  I may have rebooted before doing so but I cannot remember .....

That is what I did.  For me it worked but ...  hey it may work for you or it may lead you into other deeper water ...  :)

---

### Post by ronacc on 2007-05-13
Its correctly identifying your card and your xorg.conf looks ok . Youve got some stuff in there you dont need but that shouldn't keep the nvidia driver from working. I'm posting my xorg.conf for reference ,yours will be different because of different hardware . about the only thing I can think of at this point is try a reinstall ( I really hate to say that its so "windows").  by the way which cd did you use to install from ?



Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#   InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by IFailAtLinux on 2007-05-13
@expatCM
Well, I tried removing everything nvidia related and then using envy, but that didn't work:/

@ronacc
I used ubuntu 7.04 for 64bit AMD and Intel computers live CD to install. I don't have the image anymore so I can't be more specific, but those are choices I made on [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Edit: Oh yeah, and I'll look trough my Xorg.conf tommorow, today it's too late already.

Edit 2: So I tried doing fresh install of ubuntu on another partition and then let envy try installing nvidia drivers. Guess what? It didn't work.

Well, now I'll try putting my PC apart and try to figure out if it's not some hardware problem. I don't even know if there's possibility like that, but I guess it's still worth a try.

---

### Post by rjwboys on 2007-05-14
i had the same problem and i uninstalled nvidia compleately with apt-get remove --purge nvidia* then i rebooted into recovery and ran envy in text mode and let it run and it worked it didnt work in the gui for some reason lol

---

### Post by IFailAtLinux on 2007-05-14
Amazingly doing it like that let me make some progress... I think.

Now I don't get blue console graphics pseudo-gui with x error anymore! Instead I just get black screen, so I guess X is loading. I've gotta google out how to go around that... Unless someone knows and posts here before I eat my late dinner.

#somehow I'm happy with... things not working right. At least they are not working in different way than before.

Edit: So, Ok, I'm still getting errors in my Xorg.0.log(but I at least get black screen! yay). From black screen I can't get to console though, so it makes me reboot even more to test stuff :/ 

When X runs(nv drivers):
> 
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success


When it does not(nvidia drivers):
> 
(EE) Failed to load module "wfb" (module does not exist, 0)
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.


When I try to use envy I get errors about GLX module and kernel module mismatch, so I guess installing it manually is better:/
Again, it's how I install it now(in text mode, with X off):

```

apt-get remove --purge nvidia*
reboot

```
then after reboot, even though it's probably not necessary to reboot here
```

apt-get install avm-fritz-firmware
apt-get install nvidia-new-kernel-source
apt-get install nvidia-glx-new
nvidia-glx-settings enable
reboot

```
And after reboot I stand on my head and pray X would load, but I get black screen:/ So I get back to recovery mode and 'nvidia-glx-settings disable', which changes back to nv driver.

avm-fritz-firmware and nvidia-new-kernel-source are suggested when installing nvidia-glx-new, or at least it says so.

---

### Post by kybishop on 2007-05-14
I am having the EXACT same problem as you
well a little different, my card works if I choose the nv driver, but not nvidia driver

If i change the nv driver to nvidia, I just get a black screen
thing is, I can't even go back to the console, it's like my whole computer freezes if I try to load with the nvidia drivers

---

### Post by IFailAtLinux on 2007-05-14
So it is EXACTLY like my problem. Right now I still can work with nv drivers, but I get that freeze thingy if I try to use nvidia ones :/

---

### Post by ronacc on 2007-05-14
We are missing something here but I cannot see what it is . that card and driver combo (either the ubuntu or nvidia one) work for most people. I am afraid I have given all the help I can ,I hope someone more knowledgeable than me chimes in with the answer. You seem to be doing everything correctly, it just isn't working.

---

### Post by kybishop on 2007-05-15
I've got a theory

I've heard of people having difficulty with the geforce fx 5500 cards when they're using an intel motherboard that has an integrated graphics card

I don't have an intel board, but my motherbaord does have an nvidia geforce 4 mx integrated graphics card

If someone could show me how, maybe disabling the integrated graphics card will allow the pci card to work

---

### Post by plun on 2007-05-15
Well, nVidias support says that this probably is a Kernel bug.

I have exactly the same problem with a nVidia 7600GS card and Gutsy Gibbon.

[http://ubuntuforums.org/showthread.php?t=445222](http://ubuntuforums.org/showthread.php?t=445222)

Its several unsolved bugs and no comments from Ubuntus developers.

Drivers hell...:---)

---

### Post by IFailAtLinux on 2007-05-16
Yeah, nvidia guys told me the same thing - BIOS or kernel problem.

---

### Post by verytwisted on 2007-05-16
Hi I have just recovered from the same problem, it happened after trying to install the nvidia-glx-new package.  After changing to "nv" driver in /etc/X11/xorg.conf I managed to get Gnome back but whenever I tried to install the standard nvidia-glx X would crash with the mismatch kernel module/x module error.

Thanks to this thread I have fixed it, hopefully you can too!

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217")

Basically after uninstall the driver leaves behind a file,

 "/lib/linux-restricted-modules/.nvidia_new_installed"

If you have this file then delete it (you will need root privileges, I used sudo nautilus to browse and delete it) after deletion install your chosen driver an things should work ok.

I have a nvidia fx 5500 and i used the nvidia-glx driver that ubuntu first chose for me and I'm now back to full openGL support, lesson learned, if it ain't broke don't fix it! ;)

Good luck folks

---

### Post by John Jason Jordan on 2007-05-17
> **verytwisted said:**
> Hi I have just recovered from the same problem, it happened after trying to install the nvidia-glx-new package.  After changing to "nv" driver in /etc/X11/xorg.conf I managed to get Gnome back but whenever I tried to install the standard nvidia-glx X would crash with the mismatch kernel module/x module error.
Thanks to this thread I have fixed it, hopefully you can too!
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217")
Basically after uninstall the driver leaves behind a file,
 "/lib/linux-restricted-modules/.nvidia_new_installed"
If you have this file then delete it (you will need root privileges, I used sudo nautilus to browse and delete it) after deletion install your chosen driver an things should work ok.
I have a nvidia fx 5500 and i used the nvidia-glx driver that ubuntu first chose for me and I'm now back to full openGL support, lesson learned, if it ain't broke don't fix it! ;)
Good luck folks
I had the same problem and found the same fix. I reported it on Automatix forum and the Automatix folks later posted that they had fixed Automatix so it would make sure that file is not left there when it is not needed.

---

### Post by ronacc on 2007-05-17
Good find , now I know what I was missing , I never install anything from linux-restricted (no wireless and always use the Nvidia installer) I didn't have that file and so I never have the problem.

---

### Post by IFailAtLinux on 2007-05-19
Even if I deleted the file nvidia-glx wouldn't work for me :/

Well, I'll try getting help yet again.

To specify: I am not getting version mismatch problem. Versions are all right, so there's nothing to fix here.

When I install nvidia drivers(nvidia-glx or nvidia-glx-new) I get that PCI couldn't initialize error in xorg.log file, mentioned in my first post.

When I install legacy drivers I get even worse error so I guess they are not for me.

Based on my xorg.conf nvnews guys said it could be kernel or bios bug, but from that sentence I have no idea what to do further.

I'm uploading my nvidia-log file from when I could boot(so with nv driver). One of errors mentioned by nvnews person was the one about aperture conflicting with PCI mapping, but adding 'iommu=memaper=2' to kernel boot line doesn't make this to disappear. I tried adding some other parameters to kernel that my friend proposed, but I don't remember them and they did not help at all.

The other lines they wrote about were 2 NVRM messages:
May 19 17:15:43 TheL kernel: [   87.777865] NVRM: RmInitAdapter failed! (0x25:0xffffffff:1039)
May 19 17:15:43 TheL kernel: [   87.777887] NVRM: rm_init_adapter(0) failed
But I don't have an idea what to do with those as well.

So basically, it seems I have to fix those 2 things in order to fix the error from first post. So, is there any linux magician around who is able to tell me what exactly should I do to get rid of aperture and rm_init_adapter errors? Any proposition is good as long as it's not "Change your hardware".

As for hardware I have GA-K8NS motherboard with newest BIOS.

---

### Post by kybishop on 2007-05-19
Where's the location of the xorg.log file, I want to see if or problems still match up

---

### Post by IFailAtLinux on 2007-05-19
It's in: /var/log/Xorg.0.log

---

### Post by kybishop on 2007-05-19
I couldn't find the same errors in my log, but I want to try installing an old kernel, if its a kernel problem maybe the problem doesn't exist in older kernels.

Could someone show me how to install an older kernel (in such a way i can still choose the newest kernel in grub)

---

### Post by ronacc on 2007-05-20
first look in /boot you may have some older kernals still there , it will be called vmlinuz-*.*.*-* and the associated initrd and system map.  if they are there pick one and edit your /boot/grub/menu.lst to add a section for that kernal , look at the existing entries and you will see how to do it, the easiest way is to clone your existing boot choice and change the #'s. backup your menu.lst first.

---

### Post by IFailAtLinux on 2007-05-28
I finally got nvidia working!~

Well, solution was so scarily simple, but I found info about it just today.

It was all due to AGP aperture being set to 32MB on my BIOS settings, while nvidia drivers just won't work with anything less than 64MB. After changing it in hidden settings of my BIOS everything work nice.

Why did it work with release from 1 year ago? There was some changes in kernels since then and one thing that used to be kept in module and was optional now is hard-implemented into kernel. Before it would turn off itself when installing nvidia with 32MB AGP aperture and X would start. Now it couldn't do that.

So, if you get black screen and freeze when X should start check your nvidia bug report and if it says your AGP is set to 32MB you might have a solution~

---

