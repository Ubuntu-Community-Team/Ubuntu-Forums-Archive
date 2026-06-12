---
title: "Help Driver"
date: 2008-08-26
forum: x86 64-bit Users
---

### Post by kyo007 on 2008-08-26
Hi, i have wacom bamboo tablet, i want to install wacom driver, so i have download wacom driver (file name: linuxwacom-0.8.0-3), when i was installing, it show some error; what can i do ?

```
kyo@kyo-desktop:~/Desktop/prebuilt$ ./install
This installer must be run as root
kyo@kyo-desktop:~/Desktop/prebuilt$ sudo ./install
[sudo] password for kyo: 
Installing Wacom man page......
Installed under /usr/share/man/man4

Installing wacom_drv....
wacom_drv.so installed under /usr/lib64/xorg/modules/input

Installing utility programs (wacdump, xidump, xsetwacom....)
Installed under /usr/local/bin

Installing wacomcpl......

Warning: wacomcpl requires tcl/tk being installed

./install: line 105: yum: command not found
./install: line 105: yum: command not found

Please install tcl/tk then run this script again

You need to compile and install wacom.(k)o manually if your kernel is out of date.

After adding your Wacom tools into /etc/X11/xorg.conf, please restart X server or simply reboot your system to run the new Wacom X driver.
kyo@kyo-desktop:~/Desktop/prebuilt$ 
```

NK: Wacom works on USB, i plug it and it's working but it's very very slow moving and it's not working correct (working only when i press to table,) Right and Left click also working.

Thanks.

---

### Post by Thelasko on 2008-08-26
No No No!

Don't get files from random places on the internet!

[Read this!]("http://www.psychocats.net/ubuntu/installingsoftware")
Download [this]("http://packages.ubuntu.com/hardy/wacom-tools") and [this]("http://packages.ubuntu.com/hardy/xserver-xorg-input-wacom").

From now on, use the repositories!

---

### Post by kyo007 on 2008-08-27
hi sir, i have downloaded and installed from links, for some packet when i want to install, it wrote: you have some verison of this, so i don't re-install this, but now i have still problem, it's now working correct, maybe it's about tablet setting but i can't find anything for contol tablet on my pc, what can i do ?

Thanks.

---

### Post by Thelasko on 2008-08-27
[Here is a thread about settings for tablet PCs]("http://ubuntuforums.org/showthread.php?t=852574")

---

### Post by Crafty Kisses on 2008-08-28
Look at the RDM because usually they'll be there.

If they're not then look at alternatives.

---

### Post by kyo007 on 2008-08-30
i have found this page [http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133), when i make sudo install, i have error;

Installing Wacom man page......
Installed under /usr/share/man/man4

Installing wacom_drv....
/usr/bin/install: cannot stat `wacom_drv.so': No such file or directory
/usr/bin/install: cannot stat `wacom_drv.so': No such file or directory
wacom_drv.so installed under /usr/lib64/xorg/modules/input

Installing utility programs (wacdump, xidump, xsetwacom....)
Installed under /usr/local/bin

Installing wacomcpl......
Installed under /usr/local/bin


You need to compile and install wacom.(k)o manually if your kernel is out of date.

After adding your Wacom tools into /etc/X11/xorg.conf, please restart X server or simply reboot your system to run the new Wacom X driver.
kyo@kyo-desktop:~/wacom/linuxwacom-0.7.9-7/prebuilt$ 

what is problem, i can't found .. and also when i do gksudo gedit /etc/X11/xorg.conf

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection


it's not include this :

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection


[IMG]http://viperfs.com/Webb/t.jpg[/IMG]

---

