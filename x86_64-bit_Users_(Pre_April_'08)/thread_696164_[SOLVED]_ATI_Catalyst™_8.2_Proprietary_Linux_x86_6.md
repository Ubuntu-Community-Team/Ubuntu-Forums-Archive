---
title: "[SOLVED] ATI Catalyst™ 8.2 Proprietary Linux x86_64 Display Driver - Released Today"
date: 2008-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2008-02-13
New driver released today...

Anyone tried it yet?

8.3 is working great for me when installed using the [[SIZE="4"]**Envy**[/SIZE]]("http://www.albertomilone.com/nvidia_scripts1.html") installer.

---

### Post by Kilz on 2008-02-13
> **crjackson said:**
> New driver released today...

Anyone tire it yet?
Why not be the first, then tell us your experiences? Perhaps you can give a warning after that in your first post so newbies with the "gata have it be cause its new" know to stay away.

---

### Post by Melcar on 2008-02-14
No drastic changes from the previous version.  No regressions neither, which is a good thing.  If you have problems with the 8.1s, try these ones, but it's very likely you will still suffer from the same problems.  As for me, most of my usage revolves around games and Compiz, and for that the current drivers do fine.

---

### Post by jpittack on 2008-02-14
> **Kilz said:**
> Why not be the first, then tell us your experiences? Perhaps you can give a warning after that in your first post so newbies with the "gata have it be cause its new" know to stay away.

I would like to hear about your experience as well.  I am awaiting the opportunity for a stable driver on my xpress 1150 so that I can start playing scorched3d out of fail safe mode.

After all of the failures, I'm afraid I will only have a stable driver by the time I'm using Hardy for my main os.

---

### Post by edantes on 2008-02-14
Upgraded from the previous version in an Gutsy AMD64 system with an onboard  X1200 GPU. 

 No problems in the installation, worked fine after reboot. 

 Didn't break anything, but didn't fix my Firefox 64 either.  I keep hoping one of these upgrades will fix  the freezes in Firefox, not this one.

---

### Post by softtower on 2008-02-14
My setup is still broken. After I installed the driver DRI won't get initialized, therefore no 3D support (yet again). I am rolling back to old driver form native Ubuntu 7.04 distribution.

ThinkPad T60p with Mobility FireGL v5250

---

### Post by _kjus on 2008-02-14
Okay I install the new driver on my ubuntu gutsy 7.1 - graphic chip:ati x1400 - system.

1. sudo dpkg -i xorg-driver-fglrx_8.455.2-0ubuntu1_i386.deb fglrx-kernel-source_8.455.2-0ubuntu1_i386.deb fglrx-amdcccle_8.455.2-0ubuntu1_i386.deb

2. sudo apt-get install -f

3. sudo aticonfig --initial

4. sudo aticonfig --overlay-type=Xv

5. sudo reboot

6. fglrxinfo or glxinfo | grep rendering

Result:
-compiz is still not working
-hibernate and suspend works (for me: better than with catalyst 8.1, because there was a small -graphical error)
-correct resolution 
-direct rendering also works

In general there is no new feature. So if you have a running system, ....

---

### Post by Páraquedas_cascais on 2008-02-14
hi again making progress here!  But need help...

> bcascais@Bruno-ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

bcascais@Bruno-ubuntu:~$ ls
ASUS-ATI_GRAFIC  Documents  file:  nautilus-debug-log.txt  Public     Videos
Desktop          Examples   Music  Pictures                Templates
bcascais@Bruno-ubuntu:~$ cd ASUS-ATI_GRAFIC
bcascais@Bruno-ubuntu:~/ASUS-ATI_GRAFIC$ LS
bash: LS: command not found
bcascais@Bruno-ubuntu:~/ASUS-ATI_GRAFIC$ ls
ati-driver-installer-8-02-x86.x86_64.run
fglrx-amdcccle_8.455.2-0ubuntu1_amd64.deb
fglrx-installer_8.455.2-0ubuntu1_amd64.changes
fglrx-kernel-source_8.455.2-0ubuntu1_amd64.deb
xorg-driver-fglrx_8.455.2-0ubuntu1_amd64.deb
xorg-driver-fglrx-dev_8.455.2-0ubuntu1_amd64.deb
bcascais@Bruno-ubuntu:~/ASUS-ATI_GRAFIC$ sudo dpkg -i fglrx-amdcccle_8.455.2-0ubuntu1_amd64.deb
[sudo] password for bcascais:
Selecting previously deselected package fglrx-amdcccle.
(Reading database ... 92790 files and directories currently installed.)
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.455.2-0ubuntu1_amd64.deb) ...
Setting up fglrx-amdcccle (8.455.2-0ubuntu1) ...

bcascais@Bruno-ubuntu:~/ASUS-ATI_GRAFIC$ 

MESA????? Now what? It would have to be ATI Radeon HD 3870 !!!

Help!! i'm getting there!

Buy the way ... after installing xorg-driver-fglrx  a checking error occurred "Couldn't verify integrity of fglrx, too many installation"
What can i do about that and about Mesa?
The Catalysm application doesn't work ether!

[COLOR="Blue"]
Machine:
P5E
Q6600
G-SKILL PC8000 4G
ASUS EAH3870
SAMSUNG 2032BW[/COLOR]

---

### Post by damneddark on 2008-02-14
I installed using [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Result:
-compiz is stopped working!, still trying to fix it

---

### Post by mad_max0204 on 2008-02-14
I changed my video card to nvidia just because of this. Only time I managed to get compiz to work and get over 10.000fps in glxgears is when I installed it how its described in that [wiki site]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").
Good luck with new drivers.

---

### Post by crjackson on 2008-02-14
> **Kilz said:**
> Why not be the first, then tell us your experiences? Perhaps you can give a warning after that in your first post so newbies with the "gata have it be cause its new" know to stay away.

Because I posted late last night from work (Windows Box) and just wanted to know if anyone else had already tried them yet before I jump in the mix...

---

### Post by softtower on 2008-02-14
I would not recommend this driver. Actually after a couple of hours I was able to solve DRI initialization issue (by generating DEBs and installing them manually with manual softlink to DRI module).

However when hardware 3D acceleration is enabled (any of OpenGL screensavers or glxgears) the video looks like garbage. 

The driver's description of "Known Issues" confirms this. They say that on "workstations", i.e. FireGL cards, horizontal resolution of the display should be a multiple of 64, like 1024, 1280 or 1600. Other resolutions will not work.

WHY????????? Why would they even consider to release a driver with a KNOWN issue like that? Why don't they supply such driver to DELL to ship it with Windows? Despite of what they say, AMD/ATI attitude towards Linux is just terrible.

---

### Post by Yellow Pasque on 2008-02-14
There's some good feedback on Catalyst 8.02 in this thread on Phoronix:
[http://www.phoronix.com/forums/showthread.php?t=7812](http://www.phoronix.com/forums/showthread.php?t=7812)

I'll try to make this as easy as possible with a little guide
**You have something earlier than a Radeon 9500:** Modern Catalyst drivers don't support your card, use the open-source "radeon" driver. If you have issues, check out [http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon)

**Radeon 9500 up to X800:** you still have the option of using the open-source "radeon" driver and I would recommend using that option unless 3D performance is a major issue for you, in which case you should use the proprietary drivers that come with Ubuntu through the Restricted Driver Manager or the 8.40.4 driver if you need TV-out.

**Radeon X1k owners:**If 3D isn't a concern for you, use the open-source "radeonHD" driver, which has full 2D support. AGP users in this category also should avoid the latest version of Catalyst because it has major AGP issues (use 8.40.4 instead). If you're just looking for 3D acceleration for games and not Compiz, go with the Ubuntu proprietary driver (xorg-driver-fglrx) or 8.40.4 if you need TV-out.

**Radeon HD 2k & 3k owners:** If you have an AGP card, you have no choice but to use the radeonHD driver, and you won't have 3D accel right now (sorry :(), but they're working on it). Otherwise, you're stuck with Catalyst 8.02

I hope that guide helps. There's a link for the radeonhd driver install in my sig if you need it.

[COLOR="Red"]Catalyst Install Guide[/COLOR]: [Click Here](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

**Release notes for 8.02**
> Resolved Issues

The following section provide a brief description of resolved issues with the latest version of the ATI Catalyst&#8482; Linux software suite. These include:

    * The Xserver no longer crashes if the screen resolution is changed in horizontal or vertical desktop setup with a monitor that does not support DDC. Further details can be found in topic number 737-32223
    * The Xserver no longer segfaults or fails to initialize DRI if a BusID was specified in an unexpected format in xorg.conf. Further details can be found in topic number 737-32224
    * The Xserver no longer freezes on shutdown if atieventsd is running. Further details can be found in topic number 737-32225
    * The first OpenGL application run after starting a session on Xserver version 1.4 no longer hangs. Further details can be found in topic number 737-32226 

Known Issues

The following section provides a brief description of known issues associated with the latest version of ATI Catalyst&#8482; Linux software suite. These issues include:

    * On workstation hardware 3D applications will be corrupted if the screen width is not an integer multiple of 64 pixels, for example with a 1680x1050 wide screen display. Further details can be found in topic number 737-31720
    * There is no support for video playback on the second head in dual head mode. Further details can be found in topic number 737-26985
    * Desktop corruption may be noticed when dragging the overlay/video when using dual-display mode. Further details can be found in topic number 737-29578
    * A black screen may be observed on some hardware when switching to the console or leaving the X window system when a Vesa framebuffer console driver is used. Further details can be found in topic number 737-30687
    * Display flicker may be noticed when the gnome screen-saver starts
    * Diagonal tearing may be noticed when playing a video file using a video player that utilizes the XVideo extension
    * Video playback may look blocky when playing a video file using a video player that utilizes the XVideo extension
    * Video Playback may display wrong colors and additional shadow images when cropping or expanding a video file using a video player that utilizes the XVideo extension 

---

### Post by Páraquedas_cascais on 2008-02-15
> **mad_max0204 said:**
> I changed my video card to nvidia just because of this. Only time I managed to get compiz to work and get over 10.000fps in glxgears is when I installed it how its described in that [wiki site]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").
Good luck with new drivers.

Thanks for the steps... restart from begining, but still got MESA in fglrxinfo! Any sugestions?

---

### Post by julian67 on 2008-02-15
I installed it yesterday for my radeon 9600 Pro on Xubuntu Gutsy. The new driver did not resolve the flicker associated with the screensaver started...not a big deal, what i really wanted was a fix for occasional complete failures of X (screen and keyboard both freeze).  Within 5 minutes of using the new driver I had a complete freeze of screen and keyboard...hard reset required with PC power switch (alt+sys Rq + reisub not possible).  The perfromance is otherwise OK but I wish I had a decent nVidia card.....

---

### Post by SorinN on 2008-02-15
damneddark

following your link - I got compiz working with Catalyst 8.2

Yap !

---

### Post by _kjus on 2008-02-15
For all those who still got the Mesa Driver:
Take a look at this page
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")
If you still got the Mesa have a look to restricted driver and enable the the new driver.

---

### Post by frogotronic on 2008-02-15
it's okay - compiz & video still flickers, but not as much.  too much to be used at the same time - but hopefully next month be solved.

- CH

---

### Post by aaaantoine on 2008-02-15
Ugh. I updated my driver from the one in the Gutsy repository, using the instructions that were linked several times in this thread. I lost compiz.

In the Appearance settings, I get a window that says, "Desktop effects could not be enabled."

And when I try it in the terminal:
```
 $ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5975 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
**/usr/bin/compiz: 379: /usr/local/bin/compiz: not found**
```

Ah, found the fix: [http://ubuntuforums.org/showpost.php?p=3993442&postcount=5](http://ubuntuforums.org/showpost.php?p=3993442&postcount=5)

---

### Post by bestguy on 2008-02-15
with the 8.2 drivers .. open GL has crippled. 

Screensaver gl dont work ..

so .. dont see any good, only one step backwards. 

i go back to 8.1 while they fix this. 8.1 seems for me most stable .

---

### Post by DavyDuke17 on 2008-02-15
I'm trying to upgrade to 8.02 from 8.01 on hardy, and I'm getting this message when I run this:
```
sudo sh ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu --autopkg
```

```
Created directory fglrx-install.hM6053
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.455.2....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu
Automatically detected hardy
Package build failed!
Package build utility output:
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 8.455.2-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture i386
echo "Using architecture: i386"
Using architecture: i386
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.fT6143/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.fT6143/debian/driver.$i > \
	      /tmp/fglrx.fT6143/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.fT6143/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.fT6143/debian/10fglrx.template > /tmp/fglrx.fT6143/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.fT6143/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.fT6143/debian/fglrx.default /tmp/fglrx.fT6143/debian/fglrx; \
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
find: usr/X11R6/lib64: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
dh_testdir
 debian/rules binary
echo "Using architecture: i386"
Using architecture: i386
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.fT6143/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.fT6143/debian/driver.$i > \
	      /tmp/fglrx.fT6143/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.fT6143/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.fT6143/debian/10fglrx.template > /tmp/fglrx.fT6143/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.fT6143/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.fT6143/debian/fglrx.default /tmp/fglrx.fT6143/debian/fglrx; \
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
find: usr/X11R6/lib64: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
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
		usr/src/fglrx-8.455.2
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "etc/ati"                   "etc"
dh_install -pxorg-driver-fglrx "debian/10fglrx"            "etc/X11/Xsession.d"
dh_install -pxorg-driver-fglrx "debian/fglrx-powermode.sh" "etc/acpi"
dh_install -pxorg-driver-fglrx "debian/fglrx-*-aticonfig"  "etc/acpi/events"
dh_install -pxorg-driver-fglrx "debian/fglrx"              "etc/default"
dh_installinit -pxorg-driver-fglrx --name="atieventsd"
# Driver dev package
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib/*.a"   "usr/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*"       "usr/include"
#Create dkms.conf
echo "PACKAGE_NAME=\"fglrx\"" > debian/dkms.conf
echo "PACKAGE_VERSION=\"8.455.2\"" >> debian/dkms.conf
echo "CLEAN=\"rm -f *.*o\"" >> debian/dkms.conf
echo "BUILT_MODULE_NAME[0]=\"fglrx\"" >> debian/dkms.conf
echo "MAKE[0]=\"pushd \${dkms_tree}/fglrx/8.455.2/build; sh make.sh --nohints; popd\"" >> debian/dkms.conf
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
		usr/src/fglrx-8.455.2
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
dh_makeshlibs
dh_installdeb
ldconfig -n arch/x86/usr/X11R6/lib
LD_PRELOAD= dh_shlibdeps
dpkg-shlibdeps: warning: symbol XQueryFont used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XEatData used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFillRectangle used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReadPad used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFreeGC used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFree used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XGetErrorDatabaseText used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XAddToExtensionList used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlsym used by debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: 22 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/bin/fglrxinfo shouldn't be linked with libXext.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: symbol XauFileName used by debian/xorg-driver-fglrx/usr/sbin/atieventsd found in none of the libraries.
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd shouldn't be linked with libXrender.so.1 (it uses none of its symbols).
dpkg-shlibdeps: failure: couldn't find library libfglrx_gamma.so.1 needed by debian/xorg-driver-fglrx/usr/bin/fglrx_xgamma (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: *** [binary] Error 1
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.hM6053
```

Any suggestions? thanks.

---

### Post by inphektion on 2008-02-15
I tried this new driver today.  I tried from directions on that wiki site, on a ubuntu wiki site, I tried every way found on the internet including using envy.  Every time when I reboot either my system hangs or reboots as it tries to load my login window.  
I'm on an Optiplex 755 with Radeon HD 2400 Pro.  I'm looking for any more suggestions.
I have to keep going back to my xorg.conf with "VESA" driver.

---

### Post by mravljica on 2008-02-16
> **inphektion said:**
> I tried this new driver today.  I tried from directions on that wiki site, on a ubuntu wiki site, I tried every way found on the internet including using envy.  Every time when I reboot either my system hangs or reboots as it tries to load my login window.  
I'm on an Optiplex 755 with Radeon HD 2400 Pro.  I'm looking for any more suggestions.
I have to keep going back to my xorg.conf with "VESA" driver.

I have the same ati card and I manage to get it work by following [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually)

Just compiz is still not working but hey, it's only the effects. If I'd like to have this I'll be using ms vista.

EDIT: just tried the fix recomended by smcintyre at [http://ubuntuforums.org/showpost.php?p=3993442&postcount=5](http://ubuntuforums.org/showpost.php?p=3993442&postcount=5) and the compiz is working fine. The file to edit is /usr/bin/compiz.

---

### Post by dark_harmonics on 2008-02-16
My reccomendation after trying this driver: Use the 8.1 previous driver. Not being able to set a 1400x1050 resolution is what did it for me. I'm not looking at 1024x768 on my two 21 inch monitors. Im not that old yet. :)

---

### Post by frogotronic on 2008-02-16
> **inphektion said:**
> I tried this new driver today.  I tried from directions on that wiki site, on a ubuntu wiki site, I tried every way found on the internet including using envy.  Every time when I reboot either my system hangs or reboots as it tries to load my login window.  
I'm on an Optiplex 755 with Radeon HD 2400 Pro.  I'm looking for any more suggestions.
I have to keep going back to my xorg.conf with "VESA" driver.


my working xorg.conf (after wiki install)


```
# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option	    "DesktopSetup" "horizontal"
	Option      "DesktopSetup" "LVDS,AUTO"
	Option	    "EnablePrivateBackZ" "yes"
	Option	    "HSync2" "31-60"
	Option	    "VRefresh2" "56-75"
	Option	    "PairModes" "1280x800+1280x800,1280x768+1024x768"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
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

---

### Post by macaholic on 2008-02-16
For anyone that is confused about the proper procedure for installing the drivers, it should look something like this:
```
./(driver_name) --buildpkg Ubuntu/(Whatever version you have, feisty, gutsy, hardy
```
Then you just need to install the xorg driver and the kernel source and reboot. I have done this on my gutsy and my hardy box, note if you are on hardy and DKMS is giving you issues, I'll be happy to help.

---

### Post by sloggerkhan on 2008-02-17
this driver is the best fglrx in ages for me. Still has some issues, but much improved over previous few.

---

### Post by ThomasNovin on 2008-02-18
> **DavyDuke17 said:**
> I'm trying to upgrade to 8.02 from 8.01 on hardy 

I also get an error. I read on [http://www.phoronix.com/forums/archive/index.php/t-7477.html](http://www.phoronix.com/forums/archive/index.php/t-7477.html) and [http://www.phoronix.com/forums/showthread.php?t=7431](http://www.phoronix.com/forums/showthread.php?t=7431) some possible fixed but I only get this far:

```

sh ati-driver-installer-8-02-x86.x86_64.run --extract ati
cd ati
ln -s arch/x86/usr/X11R6/lib/libfglrx_gamma.so.1.0 arch/x86/usr/X11R6/lib/libfglrx_gamma.so.1

$ ./ati-installer.sh --buildpkg Ubuntu/hardy
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Unrecognized parameter 'Ubuntu/hardy' to ati-installer.sh
This script supports the following arguments:
--help                      : print help messages
--listpkg                   : print out a list of generatable packages
--buildpkg package          : if generatable, the package will be created
--install                   : install the driver
$ ./ati-installer.sh --help
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Unrecognized parameter '' to ati-installer.sh
This script supports the following arguments:
--help                      : print help messages
--listpkg                   : print out a list of generatable packages
--buildpkg package          : if generatable, the package will be created
--install                   : install the driver

```

No options work! ATI absolutely sucks ***. If it wasn't that my system is a laptop I would throw away my ATI card. Next laptop will be with a Intel graphics adapter so I can have open source drivers..

Edit: I added a bug on ATI's Bugzilla, [http://ati.cchtml.com/show_bug.cgi?id=1044](http://ati.cchtml.com/show_bug.cgi?id=1044)

---

### Post by Yellow Pasque on 2008-02-18
> **ThomasNovin said:**
> No options work! ATI absolutely sucks ***. If it wasn't that my system is a laptop I would throw away my ATI card. Next laptop will be with a Intel graphics adapter so I can have open source drivers..

Hopefully, by the time you go to buy another system, AMD/ATI will have fully open-sourced their drivers. Rumor has it that they're heading in that direction anyway (thus the half-hearted resources put into fglrx). Anyway, if you have a recent ATI card (X1k, HD 2k or 3k) and you can live without 3D accelereation for the time-being, check out the open-source radeonHD driver developed by the folks at Novell.

---

### Post by Kilz on 2008-02-18
> **ThomasNovin said:**
> I also get an error. I read on [http://www.phoronix.com/forums/archive/index.php/t-7477.html](http://www.phoronix.com/forums/archive/index.php/t-7477.html) and [http://www.phoronix.com/forums/showthread.php?t=7431](http://www.phoronix.com/forums/showthread.php?t=7431) some possible fixed but I only get this far:

No options work! ATI absolutely sucks ***. If it wasn't that my system is a laptop I would throw away my ATI card. Next laptop will be with a Intel graphics adapter so I can have open source drivers..

Edit: I added a bug on ATI's Bugzilla, [http://ati.cchtml.com/show_bug.cgi?id=1044](http://ati.cchtml.com/show_bug.cgi?id=1044)

You are installing what lots of people in this thread have said is a new driver that isnt stable. You are installing it to a **ALPHA** version of Ubuntu (hardy). You dont see where the problem is?
Feel free to install the open source drivers for ATI, they are in the repositories. They will be just as functional as any version of the intel drivers.

---

### Post by edantes on 2008-02-18
> **Temüjin said:**
>  Anyway, if you have a recent ATI card (X1k, HD 2k or 3k) and you can live without 3D accelereation for the time-being

Which leads to my question.  How do I know I have 3D acceleration?

I installed the latest ATI driver under Ubuntu/Gutsy AMD64, but I am not sure of its capabilities.  This is a X1200 integrated GPU. GoogleEarth runs well (2D acceleration?),  xglgears reports  1200 FPS, but  my CPU works hard for it.  

Still no compiz.  From the Xorg log, AIGLX is loaded, but only after a ton of messages

(WW) AIGLX: 3D driver claims to not support visual 0x23
...
(WW) AIGLX: 3D driver claims to not support visual 0x72

On the plus side they fixed the black screen after a CRTL-ALT-Backspace.

---

### Post by Yellow Pasque on 2008-02-18
> Which leads to my question. How do I know I have 3D acceleration?
edante, run:
```
fglrxinfo
glxinfo
```

Resources for you
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) (follow method 2)
[http://groups.google.com/group/x1250](http://groups.google.com/group/x1250)
And, of course, the radoenHD link in my sig if you get tired of fglrx

---

### Post by edantes on 2008-02-18
> **Temüjin said:**
> edante, run:
```
fglrxinfo
glxinfo
```

Resources for you
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) (follow method 2)
[http://groups.google.com/group/x1250](http://groups.google.com/group/x1250)
And, of course, the radoenHD link in my sig if you get tired of fglrx

Unless my Firefox/Flash Plugin freezes have anything to do with fglrx :evil:, this latest version is working fines for me.  Still, I should give the radoenHD a run and compare.   

I am still curious about he 3D acceleration   Thanks for the links, I had seen the wiki already.   The most detailed attempt at explaining the fglrx mess is here:

[http://forum.compiz-fusion.org/showthread.php?t=6794]("http://forum.compiz-fusion.org/showthread.php?t=6794")

Even if most of the the setup suggestion were already the default  in my system or  messed up the display.

My *fglrxinfo* looks correct: 
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.7281 Release

```

*glxinfo* looks more complicated. Are all those  "GL_" features actually enabled at the GPU?  

```
 
# glxinfo -t
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.7281 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

Vis  Vis   Visual Trans  buff lev render DB ste  r   g   b   a  aux dep ste  accum buffers  MS   MS
 ID Depth   Type  parent size el   type     reo sz  sz  sz  sz  buf th  ncl  r   g   b   a  num bufs
----------------------------------------------------------------------------------------------------
0x23 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x24 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x25 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x26 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x27 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x28 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x29 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x2a 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x2b 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x2c 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x2d 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x2e 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x2f 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x30 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x31 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x32 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x33 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x34 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x35 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x36 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x37 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x38 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x39 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x3a 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x3b 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x3c 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x3d 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x3e 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x3f 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x40 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x41 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x42 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x43 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x44 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x45 24 TrueColor    0     32  0  rgba   1   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x46 24 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x47 24 TrueColor    1      0  0  ci     0   0   0   0   0   0   0    0  0   0   0   0   0   0   0
0x48 24 TrueColor    1      0  0  ci     0   0   0   0   0   0   0    0  0   0   0   0   0   0   0
0x49 24 TrueColor    1      0  0  ci     0   0   0   0   0   0   0    0  0   0   0   0   0   0   0
0x4a 24 TrueColor    1      0  0  ci     0   0   0   0   0   0   0    0  0   0   0   0   0   0   0
0x4b 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x4c 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x4d 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x4e 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x4f 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x50 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x51 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x52 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x53 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x54 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x55 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x56 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x57 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x58 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x59 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x5a 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x5b 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x5c 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x5d 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x5e 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x5f 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x60 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x61 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x62 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x63 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x64 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x65 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x66 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x67 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x68 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  8   0   0   0   0   0   0
0x69 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x6a 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  0   0   0   0   0   0   0
0x6b 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x6c 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  8  16  16  16  16   0   0
0x6d 24 DirectColor  0     32  0  rgba   1   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x6e 24 DirectColor  0     32  0  rgba   0   0   8   8   8   8   0   24  0  16  16  16  16   0   0
0x6f 24 DirectColor  1      0  0  ci     0   0   0   0   0   0   0    0  0   0   0   0   0   0   0
0x70 24 DirectColor  1      0  0  ci     0   0   0   0   0   0   0    0  0   0   0   0   0   0   0
0x71 24 DirectColor  1      0  0  ci     0   0   0   0   0   0   0    0  0   0   0   0   0   0   0
0x72 24 DirectColor  1      0  0  ci     0   0   0   0   0   0   0    0  0   0   0   0   0   0   0
0x84 32 TrueColor    0     32  0  rgba   0   0   8   8   8   8   0    0  0   0   0   0   0   0   0

```

---

### Post by Yellow Pasque on 2008-02-18
You definitely have 3D acceleration working. If you're not experiencing any glitches, don't mess with it.

BTW, the radeonHD driver won't have 3D acceleration code for several months, probably.

---

### Post by ThomasNovin on 2008-02-19
> **Kilz said:**
> You are installing what lots of people in this thread have said is a new driver that isnt stable. You are installing it to a **ALPHA** version of Ubuntu (hardy). You dont see where the problem is?
Feel free to install the open source drivers for ATI, they are in the repositories. They will be just as functional as any version of the intel drivers.

So there there is such a driver? Why is Ubuntu configuring my Xorg with vesa then?

Concerning 8.2, it's a released driver. It should work. I can agree that its OK that Hardy is unsupported.

---

### Post by Shampyon on 2008-02-19
Which Envy option would be best for my Gutsy setup with it's ATI Radeon X700:

Install The ATI Driver (Automatic)

Install The ATI Driver Manually: 8-01

Install The ATI Driver Manually: 8.40.4

Install The ATI Driver Manually: 8.28.8

---

### Post by Yellow Pasque on 2008-02-19
Shampyon, what are you using your computer for?
If you're using the computer for 3D gaming and no Compiz/dektop effects, then 8.40.4 would be a good option.
If you need AIGLX/Compiz support on top of 3D, then choose 8-01 (but beware, it's buggy)
If you don't care too much about 3D stuff at all, but care more about 2D stability and video playback, then the best option would be the open-source "radeon" driver.

EDIT: Also note that the radeon driver does AIGLX and 3D for the R400/X-series too, but I don't think it's as fast as fglrx.

---

### Post by Shampyon on 2008-02-19
Mostly it's for watching video and listening to music, but I have the Orange Box and an old copy of Doom 3 and would love to be able to play them on my Ubuntu partition.

If I have to give up the desktop effects for that, then so be it.

So for my purposes, you'd reccoment (with caution) the 8-01 driver?

---

### Post by Yellow Pasque on 2008-02-19
It's really hard for me to recommend the latest Catalyst at all. If you're really attached to your Desktop effects, try it, but I'd really recommend using 8.40.4 and waiting for AMD/ATI to fix the major issues with Catalyst.

---

### Post by Shampyon on 2008-02-19
Alrighty. Thanks for the assist!

---

### Post by cnr437 on 2008-02-19
on dell insp. 6400 with x1400 mobility graphics card,
it works prettier than 8.01
i can see difference with my eyes,
firefox scrolls better than past, compiz-fusion and cairo-dock work more beautiful.
Thanks to ati and cononical :)

---

### Post by surge89 on 2008-02-19
I found the ATI Catalyst for linux a few days back & decided to give it another try, it works great.

Finally got dual screen working in 7.10 =]

3D acceleration also appears to work, but im yet to test it, will do it when I'm home =]

---

### Post by inphektion on 2008-02-19
I can't install the driver from ati or fglrx from ubuntu repositories.  I don't get any errors but on reboot login screen tries to draw, goes all white and system hangs.  I've even tried envy after trying everything here [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) plus a few other places.  
Now I just followed the link that Temujin has in his sig for the radeonHD driver and that works fine but of course no 3d compiz which is what i'm after otherwise I could stick with vesa.  
So whats the deal, any chance of getting the catalyst driver going or should I wait till 3D work with the radeonHD driver?

---

### Post by Yellow Pasque on 2008-02-19
> Now I just followed the link that Temujin has in his sig for the radeonHD driver and that works fine but of course no 3d compiz which is what i'm after otherwise I could stick with vesa.
VESA can't do widescreen resolutions or resolutions greater than 1280x1024 IIRC. It also doesn't have 2D or mouse cursor acceleration.

> So whats the deal, any chance of getting the catalyst driver going or should I wait till 3D work with the radeonHD driver?
You should probably keep trying to get the Catalyst driver working. I just spoke with a radeonHD driver developer yesterday and I believe his exact words were, "several months, at least", when asked for an ETA on 3D acceleration.

Another interesting headline came out today. The crew working on the regular radeon driver just put out a new release this week (xf86-video-ati 6.8) with more support for R500/R600 products. They look to be working faster than the Novell/radeonHD team.

---

### Post by edantes on 2008-02-19
> **Temüjin said:**
> You definitely have 3D acceleration working. If you're not experiencing any glitches, don't mess with it.


For my immediate needs it is fine,  However the 3D side looks like a work in progress (so we hope):

Blender (the 3D modeler)  produces a messed up screen every time you press render or switch into full screen.

compiz  (run by brute force with compiz.real --replace) complains  about a missing feature and freezes into a black screen.

---

### Post by Yellow Pasque on 2008-02-19
> **edantes said:**
> For my immediate needs it is fine,  However the 3D side looks like a work in progress (so we hope):
Yep, that's how software development is done in Linux. Release the program and let the users find the bugs on their various hardware configurations and report back.

---

### Post by Páraquedas_cascais on 2008-02-19
Hi, i'm still geting MESA  :(

And i think the HD3870 fan is not working, on restart the machine and choosing XP the hd3870 fan goes 100% the temperature goes around 70º, returning off course to 40º 1 minute after.

Those this happen to more people? :confused:

PS: Still using XP but there is a god

---

### Post by Yellow Pasque on 2008-02-19
Try:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by edantes on 2008-02-19
> **Temüjin said:**
> Yep, that's how software development is done in Linux. Release the program and let the users find the bugs on their various hardware configurations and report back.

It would make more sense in an open source project.  Also, they are behind when compared to NVidia support.  

I made some progress.  It turns out that with some minor changes in xorg.config and /usr/bin/compiz, you can turn on the desktop effects and they work very well. Follow the instructions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects)


Too bad Google Earth doesn't work under this setup.  The map frame keeps flashing.  I am not sure if it is an fglrx problem.

---

### Post by Kilz on 2008-02-20
Just thought I would post my experiences with 8.2. Yes I decided to try it. I have a x1050 card, its an inexpensive ATI card I got for $63 about 4 months ago.
Install went ok. and for the most part it looks to be working ok. I am still running Feisty so [I used this guide.]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") I only use 1152x864 resolution. I even have compiz now enabled. 
Blender doesn't start right under compiz. Created start and stop compiz menu buttons with compiz --replace and metacity --replace for when I want to use Blender or start a game of Diablo 2 (yes I am still addicted to that ancient game).
All in all I'm quite happy, though Im sure other people will have problems being as this drivers code base is so new.

---

### Post by Páraquedas_cascais on 2008-02-20
> **Temüjin said:**
> Try:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Thks! I tried the 2 methods but still MESA, maybe you can try help me online at night?! MSN?

Thks ](*,)](*,)](*,)

---

### Post by Kilz on 2008-02-20
> **Páraquedas_cascais said:**
> Thks! I tried the 2 methods but still MESA, maybe you can try help me online at night?! MSN?

Thks ](*,)](*,)](*,)

[Did you use this part of the guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually") if so, did you follow the instructions [in this section?]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying")

---

### Post by Páraquedas_cascais on 2008-02-20
> **Kilz said:**
> [Did you use this part of the guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually") if so, did you follow the instructions [in this section?]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying")


Thks again!

i did the 2 Method all the way... then... when ...Verifying

> $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: MESA....
OpenGL renderer string: MESA....
OpenGL version string: ....


$ less /var/log/Xorg.0.log |grep EE

Returns (EE) fglrx(0):DRI not supported    !!!! :confused:

I think the grafic card fan it's no working!!! i'm gone open the desktop to see it! to nitgh 
i'm at work

---

### Post by r!ots on 2008-02-22
I installed the ATi 8.2 drivers using the 2nd method described in this [guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").
The installation was no problem and the driver seems to be running fast and stable.
Only flaw is that suspend/hibernate does not work. I only get a blank screen when waking up the computer. It did work with the OpenSource radeon driver, but I don't really need it anyway. So I'm happy with this driver.
I got an integrated ATi X1100 on an ASUS X51R notebook.

---

### Post by ThomasNovin on 2008-02-22
> **r!ots said:**
> Only flaw is that suspend/hibernate does not work. I only get a blank screen when waking up the computer. It did work with the OpenSource radeon driver, but I don't really need it anyway. So I'm happy with this driver.
I got an integrated ATi X1100 on an ASUS X51R notebook.

Have you tried the workaround?

/etc/default/acpi-support

SAVE_VBE_STATE=false
POST_VIDEO=false

---

### Post by r!ots on 2008-02-22
> /etc/default/acpi-support

SAVE_VBE_STATE=false
POST_VIDEO=false

Now it's working. Thx a lot.

---

### Post by michaelramm on 2008-02-27
> **Temüjin said:**
> There's some good feedback on Catalyst 8.02 in this thread on Phoronix:
[http://www.phoronix.com/forums/showthread.php?t=7812](http://www.phoronix.com/forums/showthread.php?t=7812)

I'll try to make this as easy as possible with a little guide
**You have something earlier than a Radeon 9500:** Modern Catalyst drivers don't support your card, use the open-source "radeon" driver. If you have issues, check out [http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon)

**Radeon 9500 up to X800:** you still have the option of using the open-source "radeon" driver and I would recommend using that option unless 3D performance is a major issue for you, in which case you should use the proprietary drivers that come with Ubuntu through the Restricted Driver Manager or the 8.40.4 driver if you need TV-out.

**Radeon X1k owners:**If 3D isn't a concern for you, use the open-source "radeonHD" driver, which has full 2D support. AGP users in this category also should avoid the latest version of Catalyst because it has major AGP issues (use 8.40.4 instead). If you're just looking for 3D acceleration for games and not Compiz, go with the Ubuntu proprietary driver (xorg-driver-fglrx) or 8.40.4 if you need TV-out.

**Radeon HD 2k & 3k owners:** If you have an AGP card, you have no choice but to use the radeonHD driver, and you won't have 3D accel right now (sorry :(), but they're working on it). Otherwise, you're stuck with Catalyst 8.02

I hope that guide helps. There's a link for the radeonhd driver install in my sig if you need it.

[COLOR="Red"]Catalyst Install Guide[/COLOR]: [Click Here](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

**Release notes for 8.02**

Ok, what about the the mobile cards...I have an x300 mobility in my ThinkPad T43.

Michael

---

### Post by Yellow Pasque on 2008-02-27
> **michaelramm said:**
> Ok, what about the the mobile cards...I have an x300 mobility in my ThinkPad T43.

Michael
It's the same for the mobile x300 as the regular x300; use the open-source driver unless you use your system for intensive 3D apps.

---

### Post by jetdog440 on 2008-03-01
> **softtower said:**
> I would not recommend this driver. Actually after a couple of hours I was able to solve DRI initialization issue (by generating DEBs and installing them manually with manual softlink to DRI module).

However when hardware 3D acceleration is enabled (any of OpenGL screensavers or glxgears) the video looks like garbage. 

The driver's description of "Known Issues" confirms this. They say that on "workstations", i.e. FireGL cards, horizontal resolution of the display should be a multiple of 64, like 1024, 1280 or 1600. Other resolutions will not work.

WHY????????? Why would they even consider to release a driver with a KNOWN issue like that? Why don't they supply such driver to DELL to ship it with Windows? Despite of what they say, AMD/ATI attitude towards Linux is just terrible.

I actually get the SAME garbage from glxgears and any opengl applications WITHOUT a multiple of 64 for screen width:

I'm running Ubuntu Linux 64-bit, with the latest 8.2 drivers installed.  I also have an ati X200M video card, and all the latest updates.  I'm running gutsy.

---

### Post by PiggiePaul on 2008-03-01
Regarding this comment:

[COLOR="Blue"]Radeon 9500 up to X800: you still have the option of using the open-source "radeon" driver and I would recommend using that option unless 3D performance is a major issue for you, in which case you should use the proprietary drivers that come with Ubuntu through the Restricted Driver Manager or the 8.40.4 driver if you need TV-out.[/COLOR]


Where is this [COLOR="Blue"]open-source "radeon" driver [/COLOR]and where do I get it from?

Thanks

---

### Post by Yellow Pasque on 2008-03-01
> **PiggiePaul said:**
> Regarding this comment:

[COLOR="Blue"]Radeon 9500 up to X800: you still have the option of using the open-source "radeon" driver and I would recommend using that option unless 3D performance is a major issue for you, in which case you should use the proprietary drivers that come with Ubuntu through the Restricted Driver Manager or the 8.40.4 driver if you need TV-out.[/COLOR]


Where is this [COLOR="Blue"]open-source "radeon" driver [/COLOR]and where do I get it from?

Thanks
The xf86-video-ati package is installed by default on Ubuntu. To use it, all you have to do is edit your /etc/X11/xorg.conf file. Look in the Device section for a line that says 'Driver'

---

### Post by PiggiePaul on 2008-03-02
> **Temüjin said:**
> The xf86-video-ati package is installed by default on Ubuntu. To use it, all you have to do is edit your /etc/X11/xorg.conf file. Look in the Device section for a line that says 'Driver'

I think I may already have this configured then.



[COLOR="Blue"]Section "Device"
Identifier "ATI Technologies Inc R420 JI [Radeon X800PRO]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection[/COLOR]

---

### Post by mobio on 2008-03-03
I installed this driver but I have huge problem. I am using thinkpad T60 with mobility FireGL V5200 (yes I know it is crappy for linux :( ). After installation things seemed to be OK but... First problem if I run glxgears you can see the image but it looks completely distorted with strange squares (like completely disturbed structure covering the main image) over it. If I try to log out the screen goes black and there is nothing I can do anymore. I am really looking for good driver or at least a way to solve this (if solvable) problem. Since I updated my Kubuntu from 7.04 to 7.10 I tested many drivers and none is working properly :

Restricted driver that I can set trough restricted driver manager (I think 8.35..) works fine, until I try to project image on external display (my InFocus projector). Than both screens goes black. 
Driver 8.443.1 works fine but I can`t set up proper resolution what ever howto I follow or whatever I do (1680X1050)
After this I tried to build custom kernel for my thinkpad, didn`t help. 
I tried suggested 8.40.4 driver, gives me message No DRI on screen... and also incompatible kernel in my xorg.log file (I am thinking that it could be due my custom kerenel but if I install different driver it seems ok). 
And least I tried 8.2 driver and glxgears or any other OpenGL application is not working due to distortion problem... 
Any suggestion would be highly appreciated.

---

### Post by Kilz on 2008-03-03
> **mobio said:**
> I installed this driver but I have huge problem. I am using thinkpad T60 with mobility FireGL V5200 (yes I know it is crappy for linux :( ). After installation things seemed to be OK but... First problem if I run glxgears you can see the image but it looks completely distorted with strange squares (like completely disturbed structure covering the main image) over it. If I try to log out the screen goes black and there is nothing I can do anymore. I am really looking for good driver or at least a way to solve this (if solvable) problem. Since I updated my Kubuntu from 7.04 to 7.10 I tested many drivers and none is working properly :

Restricted driver that I can set trough restricted driver manager (I think 8.35..) works fine, until I try to project image on external display (my InFocus projector). Than both screens goes black. 
Driver 8.443.1 works fine but I can`t set up proper resolution what ever howto I follow or whatever I do (1680X1050)
After this I tried to build custom kernel for my thinkpad, didn`t help. 
I tried suggested 8.40.4 driver, gives me message No DRI on screen... and also incompatible kernel in my xorg.log file (I am thinking that it could be due my custom kerenel but if I install different driver it seems ok). 
And least I tried 8.2 driver and glxgears or any other OpenGL application is not working due to distortion problem... 
Any suggestion would be highly appreciated.

You might want to read the [Release notes ]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_82_linux.html") for drivers you install to be aware of possible problems. Sections like Known issues give a lot of information.

Known Issues

The following section provides a brief description of known issues associated with the latest version of ATI Catalyst&#8482; Linux software suite. These issues include:

    * **On workstation hardware [COLOR="Red"]3D applications will be corrupted[/COLOR] if the screen width is not an integer multiple of 64 pixels, [COLOR="Red"]for example with a 1680x1050 [/COLOR]wide screen display**. Further details can be found in topic number 737-31720

You might want to change the resolution to a multiple of 64.

---

### Post by mobio on 2008-03-04
@Kilz

Thank you for your reply very much. It worked! I added line "Virtual etc..." rebooted and there was it glxgears work like magic.
I guess you made good point because I wasted my time by googling and trying different stuff but not looking at the right place. 

However I am left with the problem that when ever I try to switch off the session (log off, restart etc..) I get black screen and I have to push the shutdown button manually because nothing else helps. I saw some people having same issue previously and suggesting to change the value of the TerminateServer in /etc/kde3/kdm/kdmrc to True. This didn`t help. Only thing that does help is changing the driver.  So if you or anyone else have an idea how to fix it I would highly appreciate it.
Thank you again.

---

### Post by soxs on 2008-03-05
Some other question: Does this driver work with 3870? I am goning to buy ne if it does..

---

### Post by Yellow Pasque on 2008-03-06
Version 8.3 released today.

---

### Post by Kivech on 2008-03-06
Well I've tried this driver also, but had to revert to the default one that comes with Ubuntu.

The good part was that I got my direct rendering working. The bad part is that performance was horrible (this on a Radeon x1900 512Mb card), which is rediculous. Believe it or not, but my glxgears performance is MUCH better under the shipped proprietary diver that comes with Ubuntu.

Also, any type of video playback (MWV, MPG4, DVDs, etc.) was impossible. At times it completely locked up my system.

Needless to say I'm back to my old setting with xserver-xgl and no direct rendering. But at least it is stable and performs well, despite the lack of direct rendering.

It really would be time for ATI to start making decent drivers for Linux, because this is about the worst I've seen in my whole IT career. And yes, I started out when most people didn't even know what a computer was still.

Kivech

---

### Post by pmaconi on 2008-03-07
8.3 works great for me. I still have suspend / hibernate issues (my monitor suspends, but my tower keeps running and I cannot make it resume), but all of my other issues were fixed. I can now use CTRL + ALT + BACKSPACE to restart X (which would previously crash me) and my compiz / video playback work perfectly.

Edit: I use two ATI X1800 video cards.

---

### Post by crjackson on 2008-03-07
> **pmaconi said:**
> 8.3 works great for me. I still have suspend / hibernate issues (my monitor suspends, but my tower keeps running and I cannot make it resume), but all of my other issues were fixed. I can now use CTRL + ALT + BACKSPACE to restart X (which would previously crash me) and my compiz / video playback work perfectly.

Edit: I use two ATI X1800 video cards.

Good news, sounds like the state of the driver is getting better.  Perhaps 2-3 more releases and it may be a class act.

---

### Post by bestguy on 2008-03-07
> **crjackson said:**
> Good news, sounds like the state of the driver is getting better.  Perhaps 2-3 more releases and it may be a class act.


seems to me too. Running a Radeon XT 9800 on Ubuntu 7.10 with Dualscreen set to Xinerama 1280 x 1024 and 1680 x 1050 with no problems. Open GL Games and Screensavers now work flawless. Fullscreen Video performance a littel better. But Video Rendering, Dithering suckz like known. 

Because of the more open strategy from Ati, they will be soon a driver ..with near performance and better video rendering like the windoze guys have since years. 

hope dies at last :popcorn:

---

### Post by crjackson on 2008-03-10
Well I installed the ATI Catalyst&#8482; 8.3 Proprietary Linux x86_64 Display Driver on my laptop this weekend.  It's nice to see desktop effects working so well.

All my video players stopped working except MPlayer and gxine.  I had to try many different settings to get gxine to work, but MPlayer worked without issues from the get go.

VLC, TOTEM, and others won't display any video playback at all while desktop effects are enabled.  Turn them off and it's good to go.  I rather like the default desktop effects setting on the laptop, but not so much on the Desktop.

Here's something interesting...  Turning on desktop effects for the lappy doesn't change my glxgears FPS at all.  On my Desktop system listed below, I lose thousands of FPS in glxgears after enabling desktop effects.

---

### Post by deavik on 2008-03-11
> **crjackson said:**
> Well I installed the ATI Catalyst™ 8.3 Proprietary Linux x86_64 Display Driver on my laptop this weekend.  It's nice to see desktop effects working so well.

All my video players stopped working except MPlayer and gxine.  I had to try many different settings to get gxine to work, but MPlayer worked without issues from the get go.

VLC, TOTEM, and others won't display any video playback at all while desktop effects are enabled.  Turn them off and it's good to go.  I rather like the default desktop effects setting on the laptop, but not so much on the Desktop.

Here's something interesting...  Turning on desktop effects for the lappy doesn't change my glxgears FPS at all.  On my Desktop system listed below, I lose thousands of FPS in glxgears after enabling desktop effects.

Hey crjackson, do you mind sharing what steps you took to install stuff? Were you using gutsy or hardy?

I upgraded from gutsy to hardy (64 bit) recently, messing up my catalyst drivers in the process... if you're reporting that 8.3 is working I'll try that.

Did you choose buildpkg? i think that gave me errors.. i'll post more info if required (not at my home computer now).

---

### Post by Jouke74 on 2008-03-11
In order to get video output in VLC using desktop effects do: 

-> Settings > Preferences > Video > Output Modules 

Check the Advanced options in the bottom right hand corner 

Change "Video Output Module: Default" to "Video Output Module: X11 Video Output"

I followed the Ati link to the Unofficial wikki for Gutsy for the 8.3 install. 
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Notes: 
- Ia32-libs need to be installed as well.

- The only problem is that amdcccle gives errors when installing. You need to simlink the LibGL.so.1 library in AMD64 distros. This is explained, but easily overseen: sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

In the the install worked in my case after doing this :

sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb

sudo apt-get install -f

sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb (yes all of them again).

Then type "Y" when asked to overwritre the compiz files.

sudo aticonfig --initial

Note: this is how I got them to work, I assume it might make a mess out of good working things as well, so use at your own risk(!)

---

### Post by crjackson on 2008-03-11
> **Jouke74 said:**
> In order to get video output in VLC using desktop effects do: 

-> Settings > Preferences > Video > Output Modules 

Check the Advanced options in the bottom right hand corner 

Change "Video Output Module: Default" to "Video Output Module: X11 Video Output"



Thanks, I'll look into that when I get home.  I tried X11 in xine and it didn't work.  I had to select an option near the bottom (can't remember right now) befor it would work correctly...

---

### Post by crjackson on 2008-03-11
> **deavik said:**
> Hey crjackson, do you mind sharing what steps you took to install stuff? Were you using gutsy or hardy?

I upgraded from gutsy to hardy (64 bit) recently, messing up my catalyst drivers in the process... if you're reporting that 8.3 is working I'll try that.

Did you choose buildpkg? i think that gave me errors.. i'll post more info if required (not at my home computer now).

I'm using Gutsy - I used [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install.  Everything is working fine except as mentioned above.

---

### Post by bixejo on 2008-03-12
> **Temüjin said:**
> Version 8.3 released today.

OK, just a very simple question. _**[COLOR=Blue][Here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")[/COLOR]**_ it says explicitly:

> [LIST]
[*]Note: *8.471.0 does NOT work on amd64 - it conflicts with ia32-libs, which it depends on!  (they both contain /usr/lib32/libGL.so.1*[/LIST]But the rest of the page is plenty of instructions on how to install 8.03 in amd64 systems :confused:.

Is this a true problem? Any of you who already tried 8.03 have got any trouble related to this?

P.S.: Now I realized that former versions had the same problem too.. I've got currently installed 8.02, and:

> bixejo@colmena:~$ dpkg -S /usr/lib32/libGL.so.1
desviación por xorg-driver-fglrx desde: /usr/lib32/libGL.so.1
desviación por xorg-driver-fglrx a: /usr/lib32/fglrx/libGL.so.1.xlibmesa
ia32-libs: /usr/lib32/libGL.so.1
bixejo@colmena:~$


---

### Post by crjackson on 2008-03-12
> **bixejo said:**
> OK, just a very simple question. _**[COLOR=Blue][Here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")[/COLOR]**_ it says explicitly:

But the rest of the page is plenty of instructions on how to install 8.03 in amd64 systems :confused:.

Is this a true problem? Any of you who already tried 8.03 have got any trouble related to this?

P.S.: Now I realized that former versions had the same problem too.. I've got currently installed 8.02, and:

As stated above, I don't seem to have this issue.

---

### Post by bixejo on 2008-03-12
Thank you, crjackson.

I'll cross my fingers and go ahead to try this release...

---

### Post by Jouke74 on 2008-03-12
As you can see the problems I had with the manual install were also with the IA32-libs and the libGL.so.1 files. So yes. However, after my sort of forced install they seem to run fine. BTW, IA32-libs seems only required for the catalyst control center. The 8.3 (8.03) drivers are definitively running here.

---

### Post by crjackson on 2008-03-12
> **bixejo said:**
> Thank you, crjackson.

I'll cross my fingers and go ahead to try this release...

I installed my using Envy and it did install some missing dependencies and make needed adjustments automatically.  I worked like magic.  I can't speak for the manual install.  I'd try Envy 1st if I were you.  It's working really great for me on my laptop... I haven't tried my kids / wife's desktops yet, but I expect the same great results.  My laptop has a Mobility Radeon 9600.

---

### Post by bixejo on 2008-03-12
OK, I've just installed 8.03 right now, just after uninstalling all fglrx stuff I had from 8.02. Installation went OK, it only asked me whether it should replace the file **/etc/xdg/compiz/compiz-manager** (which, BTW, I had to edit and modify afterwards to comment again the line related to /etc/xdg/compiz/compiz-manager.ubuntu, which does not exist in my installation).

8.03 works quite well. It fixed the mosaic-like 3D OpenGL windows I got with 8.02 (see **_[http://ubuntuforums.org/showthread.php?t=711481](http://ubuntuforums.org/showthread.php?t=711481)_**). It persists however some other of the "classic" issues of fglrx, like blinking video playback image with Xv/OpenGL, but looks like that bug's much deeper roots and it's not that easy to fix...

Apart from the above, 8.03 compared to 8.02:[LIST]
[*]glxgears: 30% FPS faster (*)
[*]fgl_glxgears: 10% FPS faster (lost frame window when enabled compiz desktop effects)
[*]desktop cube rotation: much faster (cannot tell exactly how much, but it's sensibly faster)[/LIST](*) looks amazing, but take in mind that I lost a lot in glxgears when moved from 8.01 to 8.02, so this is not so good as it's still 10% slower than 8.01.

---

### Post by studo77 on 2008-03-12
Deleted all of my info. In short, the packages are not installable due to conflicts. They are containing the same file, and end result is that one package xorg-driver-fglrx(-dev) is missing.

I found the reason while reading this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
It is mentioned a lot in the first pages.  This is from that guide:
> 
Note: 8.471.0 does NOT work on amd64 - it conflicts with ia32-libs, which it depends on! (they both contain /usr/lib32/libGL.so.1

Envy does not care for this fact, so it is an easy tool, but not _the_ tool. So i am going back to the default in restricted drivers. A shame, as it sounds like the AMD 8-3 would have given me great improvements. (notetoself: nvidiacards are good)

---

### Post by Jouke74 on 2008-03-12
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

And with that, you link the Ubuntu LibGl as the replacement dependency for the driver. The only thing you then need to do is a "forced" install, skipping the install of the LIbGL from the driver. I wrote this now already 3 times, and it is a workaround for the cannot install because of ia32libs.

---

### Post by crjackson on 2008-03-13
I just installed 8.3 on two more of my desktops today and it's working perfectly using the Envy installer.

---

### Post by Kilz on 2008-03-14
Made a mistake  :(

---

### Post by Jouke74 on 2008-03-14
"This effects a lot more than ia32-libs imho." Yes indeed Kilz, I fully agree. In principle you're telling all programs using the LibGL.so.1 library to use the LibGL.so.1.2 instead. If I compare my secondary Xubuntu install without an ATI driver installed (Intel graphics), it shows that 1.2 is the version that came with Ubuntu 7.1. Interestingly it has the same simlink already there :confused:

[COLOR="Gray"]I am however not sure why you are referring to solving this with using a different mirror.[/COLOR] Ia-32 libs did install fine on my computer, including it's dependencies. Until now I did not have any issues with running 32 bits programs, *before* and *after* the driver install. This might however be related to the fact I am not using many 32 bit applications. 

[COLOR="Gray"]Could you please elaborate? 

Are you then looking for a mirror with an older .1 version of the library? 

Very interested, and thanks for pointing this out, JJ.

EDIT : ^ Killz removed his "mirror"-post.[/COLOR]

---

### Post by Kilz on 2008-03-14
> **Jouke74 said:**
> "This effects a lot more than ia32-libs imho." Yes indeed Kilz, I fully agree. In principle you're telling all programs using the LibGL.so.1 library to use the LibGL.so.1.2 instead. If I compare my secondary Xubuntu install without an ATI driver installed (Intel graphics), it shows that 1.2 is the version that came with Ubuntu 7.1. Interestingly it has the same simlink already there :confused:

I am however not sure why you are referring to solving this with using a different mirror. Ia-32 libs did install fine on my computer, including it's dependencies. Until now I did not have any issues with running 32 bits programs, *before* and *after* the driver install. This might however be related to the fact I am not using many 32 bit applications. 

Could you please elaborate? 

Are you then looking for a mirror with an older .1 version of the library? 

Very interested, and thanks for pointing this out, JJ.

My bad, I must have been half asleep when I read your post. I thought it wouldnt install because of not finding ia32-libs, not an internal conflict of the packages. Im going to remove my last post because it might send someone on a wild goose chase.

---

### Post by chalewa on 2008-03-15
It seems like this driver is hardly worth the upgrade...


or am i totally wrong?

---

### Post by crjackson on 2008-03-15
> **chalewa said:**
> It seems like this driver is hardly worth the upgrade...


or am i totally wrong?

It's totally subjective.  For me it was totally worth it.  It works just fantastic on the 4 machines I've installed it on.

For others it may be totally worthless.  You need to try it for yourself...

---

### Post by Jouke74 on 2008-03-15
I agree it is totally worth the update. But, given the discussion of varying results people have with it I would say it depends a lot on what you're doing with your system, what you have done already, how you install the driver, how you are able to deal with problems arising, and what side effects it might cause using for example the symlink. Briefly your mileage might vary...

---

### Post by corpsed on 2008-03-16
> **damneddark said:**
> I installed using [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Result:
-compiz is stopped working!, still trying to fix it

I followed the Method 1 instructions on this wiki, and when i get to:

> root@corpsed:~# sudo depmod -a
root@corpsed:~# sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

There obviously is a problem. I don't know what config file it needs. Help please!:mad:

---

### Post by crjackson on 2008-03-16
Have you tried the[[SIZE="4"]** Envy**[/SIZE]]("http://www.albertomilone.com/nvidia_scripts1.html") installer program?

---

### Post by Yellow Pasque on 2008-03-16
It's looking for /etc/X11/xorg.conf
You can generate it with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Or you can copy this template:
```
# xorg.conf (xorg X Window System server configuration file)
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

Section "Modules"
        Load    "dri"
        Load    "glx"
EndSection

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Option          "VideoOverlay" "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1680x1050" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Off"
EndSection

Section "ServerFlags"
        Option "AIGLX" "Off"
EndSection

```

---

### Post by soxs on 2008-03-16
... [removed] ...

---

### Post by corpsed on 2008-03-16
> **crjackson said:**
> Have you tried the[[SIZE="4"]** Envy**[/SIZE]]("http://www.albertomilone.com/nvidia_scripts1.html") installer program?

Okay, I just tried ENVY, installed the ATI drivers automatically, and it asked to reboot. I reboot, and then it starts up in "low graphics mode" because it couldn't detect my video card.

Is there something I should be doing instead?

Thanks so much.

---

### Post by Yellow Pasque on 2008-03-16
> **corpsed said:**
> Okay, I just tried ENVY, installed the ATI drivers automatically, and it asked to reboot. I reboot, and then it starts up in "low graphics mode" because it couldn't detect my video card.

Is there something I should be doing instead?

Thanks so much.
Try not using Envy :P It shouldn't be necessary for just installing the Ubuntu ATI driver. See my post a few back (#94) for directions on how to reconfigure xorg, then do the sudo aticonfig --initial -f

---

### Post by corpsed on 2008-03-16
Alright, will give that a shot, Temüjin. This will allow me to use Compiz correctly, right? and thanks!

---

### Post by Yellow Pasque on 2008-03-16
> **corpsed said:**
> Alright, will give that a shot, Temüjin. This will allow me to use Compiz correctly, right? and thanks!
You'll either need to use the new Catalyst driver and Method 2 on that wiki install guide, or you'll need to install XGL (sudo apt-get install xserver-xgl) to use Compiz. XGL tends to consume more CPU cycles and doesn't always work well with video playback. What video card do you have?

---

### Post by corpsed on 2008-03-16
ATI Radeon X1900

---

