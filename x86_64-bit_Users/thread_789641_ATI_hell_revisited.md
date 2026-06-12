---
title: "ATI hell revisited"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by peakshysteria on 2008-05-10
Running:

Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy (64 bit)
 uname -r 2.6.24-16-generic
lspci -nn | grep VGA

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] [1002:5e4b]


It's difficult to keep away from trying to enable the right driver for my ATI X700 Excalibur Pro card. So tonight I once again gave it a shot. The whole family are in a strange limbo state since we miss our daily doze of tv out with overlay (kids are climbing the walls).

Therefore once again i tried Method 1: Install the driver the Ubuntu Way from [Ubuntu Hardy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method")

Once again everything looked good. Rebooted the machin and fglrxinfo still gives me the well known:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

Meaning I once again have done something wrong. My xorg also looks kinda strange i think:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "dri"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "no"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

So no luck this time either. Hope someone can give me some tips or tricks. I'll lay low for a while now before giving [Method 2: Manual Method ]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method")

Just for the hell of it I tried to enable the awesome Compiz again (well knowing it wouldn't work). For the first time I got the famous white screen. Ctrl+Alt+Backspace resarted X and i could once again  log in to my desktop. Phew!

Enabling the restriced drivers from system --> administration --> hardware drivers doesn't work.

[ENVY]("http://albertomilone.com/nvidia_scripts1.html") is also a dead end for me (strange since there are someone managing to make this one work for real).

Also tried to answer yes when trying to enable Compiz gives me the promt to enable the restricted driver. But this is also a nogo.

But I will NEVER give up.....not yet anyway....but now, for a couple a weeks I'll give it a rest.

Gods speed to all ATI people. I'll be back :)

---

### Post by macaholic on 2008-05-10
I would suggest trying to install the driver manually, that is what I always do, since the driver package in the repositories always screws things up for me. If you think your xorg.conf is too screwed up, you can always start fresh and reconfigure it with:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by peakshysteria on 2008-05-11
> **macaholic said:**
> I would suggest trying to install the driver manually, that is what I always do, since the driver package in the repositories always screws things up for me. If you think your xorg.conf is too screwed up, you can always start fresh and reconfigure it with:```
sudo dpkg-reconfigure xserver-xorg
```

No. In Hardy this doesn't work. If one want to reconfigure xorg in Hardy it's:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I only wanted to now from people if my xorg looks normal or not. Because I see ATI mentioned all over the place there. And it's still not working.

Any chance you have a howto for a manual install? Or is it enough to just allow executing file as program in the properties menu? I'm not to experienced with the terminal yet. Though I'm not afraid of it. But I always seem to run into some issues with root when I try to install programs, plugins or the likes manually.

And if I make the manual install of the driver I guess you'll have to make some additional changes to xorg or something. How do you proceed after a manual install macaholic??

---

### Post by Kilz on 2008-05-11
> **peakshysteria said:**
> 
Any chance you have a howto for a manual install?

[This is a manual howto.]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method") But when you go from howto to howto searching for a way to make it work it will never work.
Stick with that link, and follow it all the way down to the last word on the page.

---

### Post by peakshysteria on 2008-05-11
A bit below power there he. That's the same howto I linked to above :) So thats what's next yes. Not going to go for that one quit yet.

But it's say:

If using 64bit make sure to collect package "ia32-libs" and " libGL.so.1" before proceeding! 

Is this supposed to be from synaptic? Or is there additional terminal commands to get these? I can find "ia32-libs" in synaptic but not " libGL.so.1" Besides that it all looks almost like a walk in the park as long as the 64-bits part of the howto is right. It would be nice to have a single 64 bit howto even though there are only a few additions to the current howto :)

---

### Post by lefterist on 2008-05-11
> **Kilz said:**
> [This is a manual howto.]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method") But when you go from howto to howto searching for a way to make it work it will never work.
Stick with that link, and follow it all the way down to the last word on the page.

I followed the manual howto down to the last word but still no go. I get the same error as this: [http://ubuntuforums.org/showthread.php?t=785107](http://ubuntuforums.org/showthread.php?t=785107)

Any ideas?

---

### Post by peakshysteria on 2008-05-23
I've managed to run the installer of the latest ATI driver. Everything went smooth without any errors. After reboot all seems well. But fglrxinfo still gives me:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

Meaning something is wrong. And I have no tv out and ATI CCC wont run because either the driver isn't installed or because the driver isn't functioning properly. Can anyone help me to proceed please?

xorg output:

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0	-	65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "Extensions"
EndSection

```

---

### Post by Kilz on 2008-05-23
> **peakshysteria said:**
> I've managed to run the installer of the latest ATI driver. Everything went smooth without any errors. After reboot all seems well. But fglrxinfo still gives me:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

Meaning something is wrong. And I have no tv out and ATI CCC wont run because either the driver isn't installed or because the driver isn't functioning properly. Can anyone help me to proceed please?

xorg output:

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0	-	65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "Extensions"
EndSection

```

[This is a manual howto.]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method") 
Stick with that link, and follow it all the way down to the last word on the page. Use the installer you have that works. I can tell by looking at your xorg.conf that you didnt follow the howto.

---

### Post by peakshysteria on 2008-05-23
```
sudo sh ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/hardy
```

returns:

sh: Can't open ati-driver-installer-8-5-x86.x86_64.run

---

### Post by Kilz on 2008-05-23
> **peakshysteria said:**
> ```
sudo sh ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/hardy
```

returns:

sh: Can't open ati-driver-installer-8-5-x86.x86_64.run

Copy the terminal up to that point and paste it here. The limited info you have given makes it hard to see whats wrong.

---

### Post by peakshysteria on 2008-05-23
Sorry man. As you can see I'm not to familiar with the terminal:

```
root@peaks-desktop:/home/peaks# sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US    
Hit http://no.archive.ubuntu.com hardy Release.gpg                  
Ign http://no.archive.ubuntu.com hardy/main Translation-en_US        
Ign http://no.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://no.archive.ubuntu.com hardy/universe Translation-en_US    
Ign http://no.archive.ubuntu.com hardy/multiverse Translation-en_US  
Hit http://no.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://no.archive.ubuntu.com hardy-updates/main Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/main Translation-en_US 
Hit http://archive.canonical.com hardy Release                       
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release              
Hit http://archive.canonical.com hardy/partner Packages             
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://archive.canonical.com hardy/partner Sources
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Ign http://no.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://no.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://no.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://no.archive.ubuntu.com hardy Release 
Hit http://no.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://no.archive.ubuntu.com hardy/main Packages
Hit http://no.archive.ubuntu.com hardy/restricted Packages
Hit http://no.archive.ubuntu.com hardy/main Sources
Hit http://no.archive.ubuntu.com hardy/restricted Sources
Hit http://no.archive.ubuntu.com hardy/universe Packages
Hit http://no.archive.ubuntu.com hardy/universe Sources
Hit http://no.archive.ubuntu.com hardy/multiverse Packages
Hit http://no.archive.ubuntu.com hardy/multiverse Sources
Hit http://no.archive.ubuntu.com hardy-updates/main Packages
Hit http://no.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://no.archive.ubuntu.com hardy-updates/main Sources
Hit http://no.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://no.archive.ubuntu.com hardy-updates/universe Packages
Hit http://no.archive.ubuntu.com hardy-updates/universe Sources
Hit http://no.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://no.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
root@peaks-desktop:/home/peaks# sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
fakeroot is already the newest version.
dh-make is already the newest version.
debhelper is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
dkms is already the newest version.
linux-headers-2.6.24-16-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0 python-setuptools libgcj-bc python-pygame odbcinst1debian1
  libsdl-mixer1.2 gcjwebplugin-4.2 unixodbc gstreamer0.10-gnonlin python-qt3
  gappletviewer-4.2 python-sip4 python-zopeinterface fastjar dpatch
  python-kde3 libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@peaks-desktop:/home/peaks# sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
ln: creating symbolic link `/usr/lib/libGL.so.1': File exists
root@peaks-desktop:/home/peaks# sudo rm /usr/src/fglrx-kernel*.deb
rm: cannot remove `/usr/src/fglrx-kernel*.deb': No such file or directory
root@peaks-desktop:/home/peaks# sudo sh ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/hardy
sh: Can't open ati-driver-installer-8-5-x86.x86_64.run
root@peaks-desktop:/home/peaks# 

```

My god. The installer was in the wrong folder. I ran ```
sudo sh ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/hardy
``` and got:

```

 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/hardy
Package build failed!
Package build utility output:
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.493-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.nn7959/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.nn7959/debian/driver.$i > \
	      /tmp/fglrx.nn7959/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.nn7959/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.nn7959/debian/10fglrx.template > /tmp/fglrx.nn7959/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.nn7959/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.nn7959/debian/fglrx.default /tmp/fglrx.nn7959/debian/fglrx; \
	fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
		mkdir -p usr/share/doc/fglrx; \
		mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
		usr/X11R6/lib \
		usr/X11R6/lib64 \
		usr/share usr/src     -type f | xargs chmod -x
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.nn7959/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.nn7959/debian/driver.$i > \
	      /tmp/fglrx.nn7959/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.nn7959/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.nn7959/debian/10fglrx.template > /tmp/fglrx.nn7959/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.nn7959/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.nn7959/debian/fglrx.default /tmp/fglrx.nn7959/debian/fglrx; \
	fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
		mkdir -p usr/share/doc/fglrx; \
		mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
		usr/X11R6/lib \
		usr/X11R6/lib64 \
		usr/share usr/src     -type f | xargs chmod -x
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
		usr/lib \
		usr/sbin \
		usr/lib \
		usr/lib/xorg/modules \
		usr/lib/xorg/modules/drivers \
		usr/lib/xorg/modules/linux \
		etc/acpi \
		etc/acpi/events \
		etc/default \
		etc/X11/Xsession.d \

# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
		usr/lib32 \
		usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
		usr/bin \
		usr/sbin \
		usr/share \
		usr/share/applnk \
		usr/share/gnome \
		usr/share/gnome/apps \
		usr/share/icons \
		usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
		usr/include \
		usr/lib
dh_installdirs -pfglrx-kernel-source \
		usr/src/fglrx-8.493
dh_install
# Driver package
/sbin/ldconfig -n usr/X11R6/lib/
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "etc/ati"                   "etc"
dh_install -pxorg-driver-fglrx "debian/10fglrx"            "etc/X11/Xsession.d"
dh_install -pxorg-driver-fglrx "debian/fglrx-powermode.sh" "etc/acpi"
dh_install -pxorg-driver-fglrx "debian/fglrx-*-aticonfig"  "etc/acpi/events"
dh_install -pxorg-driver-fglrx "debian/fglrx"              "etc/default"
dh_installinit -pxorg-driver-fglrx --name="atieventsd"
# Driver dev package
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib64/*.a" "usr/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*"       "usr/include"
#Create dkms.conf
echo "PACKAGE_NAME=\"fglrx\"" > debian/dkms.conf
echo "PACKAGE_VERSION=\"8.493\"" >> debian/dkms.conf
echo "CLEAN=\"rm -f *.*o\"" >> debian/dkms.conf
echo "BUILT_MODULE_NAME[0]=\"fglrx\"" >> debian/dkms.conf
echo "MAKE[0]=\"pushd \${dkms_tree}/fglrx/8.493/build; sh make.sh --nohints; popd\"" >> debian/dkms.conf
echo "DEST_MODULE_LOCATION[0]=\"/kernel/drivers/char/drm\"" >> debian/dkms.conf
echo "AUTOINSTALL=\"yes\"" >> debian/dkms.conf
# Kernel source package
dh_install -pfglrx-kernel-source \
		lib/modules/fglrx/build_mod/*.c            \
		lib/modules/fglrx/build_mod/*.h            \
		lib/modules/fglrx/build_mod/*.sh           \
		lib/modules/fglrx/build_mod/lib*           \
		lib/modules/fglrx/build_mod/2.6.x/Makefile \
		debian/dkms.conf			   \
		usr/src/fglrx-8.493
# control panel package
dh_install -A -pfglrx-amdcccle "usr/X11R6/bin/amdcccle"				"usr/bin"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"				"usr/share/icons"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"				"usr/share/pixmaps"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.desktop"			"usr/share/applications"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.kdelnk"				"usr/share/applnk"
dh_install -A -pfglrx-amdcccle "usr/share/ati"					"usr/share"
dh_desktop    -pfglrx-amdcccle
# start the install
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
dh_compress
dh_installdeb
dh_makeshlibs
dh_shlibdeps
dpkg-shlibdeps: warning: symbol XauFileName used by debian/xorg-driver-fglrx/usr/sbin/atieventsd found in none of the libraries.
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd shouldn't be linked with libXrender.so.1 (it uses none of its symbols).
dpkg-shlibdeps: failure: couldn't find library libfglrx_gamma.so.1 needed by debian/xorg-driver-fglrx/usr/bin/fglrx_xgamma (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: *** [binary] Error 1
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.NA7876
root@peaks-desktop:/home/peaks#

```
On thin ice here......not sure how to proceed. I find the same error in several other threads. Noone solved it seems...I guess this is not the output I want at this stage in the process?

---

### Post by SledgeHammer_999 on 2008-05-23
look again [here](http://ubuntuforums.org/showthread.php?t=785107). I was able to solve it.

---

### Post by sergim on 2008-05-23
Check the dexconf command

---

