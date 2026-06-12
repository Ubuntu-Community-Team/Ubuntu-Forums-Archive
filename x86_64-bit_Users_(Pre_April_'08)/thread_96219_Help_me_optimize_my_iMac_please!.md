---
title: "Help me optimize my iMac please!"
date: 2005-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by neoplasticity on 2005-11-28
Hello everyone.

I've finally successfully installed Breezy on my iMac 333 with 288 megs of RAM after the 5th attempt.  For future reference of those who wish to do this on a older iMac, here are the issues i had and how to resolve them.

1.  Partitioning.  What finally worked for me is to go to shell and use parted to resize the OS X partition.  there also seems to be like 4 other small 32K to 400K partitions on my iMac.  I have no idea what those partitions were but i left them alone.   I then tried to manually partition the swap, root, and boot partition.  That didn't work out so well, so i went back and erased all the new linux partitions and left it as free space and used the guided partition in the installer and let it do the partitioning of the largest contingous free space.  that worked.

2.  Hard disk size.  I found out the minimum size of the linux partition you need for the desktop install is 1.7 gigs so do yourself a favor and make it at least 2.0 gigs.

3.  make sure the apt-get server is up.  this caused me alot of problems when i couldn't figure out why the install would crash and boot me to shell.  then i finally figured out that us.archive.ubuntu was down.  after i switched servers, all was well.


OK, now to the issue at hand.  Now that I have breezy installed, I want to make it as fast and lean as possible.  So far, i've removed open office, abiword, the non US language fonts, the gimp.   

I plan on doing whats described in this thread to remove all unneccessary services.

[http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

And I plan on installing InitNG as described here

[http://ubuntuforums.org/showthread.php?t=80423](http://ubuntuforums.org/showthread.php?t=80423)

and I want to remove GNOME and use a lighter WM and remove all the other unnessary packages.

All i want my computer to do is to browse the web with firefox, play mp3s and videos on the web, run azureus, do IM and IRC, and maybe play around with some simple java and python coding.   and i want it to do it as quickly and responsively as possible.

How do i go about removing GNOME and all GNOME applications and installing a new WM?  what other packages can i safely remove?

thanks in advance for the help and i think this thread would be really useful to everyone else wanting to make a leaner, faster version of ubuntu.

---

### Post by ssam on 2005-11-28
mac os uses those little partitions for various things. if you run
```
sudo fdisk -l /dev/hda
```
you get a list of all the partitions. There are clues in the file type as to what they do.

just removing packages will not necisarily speed up your system. it will mostly just free up harddrive space. you will get a speed up from using lighter software.
for a window manager try
xfce or fluxbox/openbox
maybe dillo or epiphany as a webbrowser

have a look through some of the older posts in this forum. getting the right graphics driver and x setting can vastly speed up some imacs. (dont bother with any mention of binary drivers, they are x86 only).

---

### Post by peter_m on 2005-11-28
Neo, how did you ger your iMAC 333 to read a CD-R? Mine wont read them reliably and I'm stuck waiting for the official CD. Also did you get your monitor to run without black borders?

Peter

---

### Post by neoplasticity on 2005-11-28
it never had any problems reading the CD R.  maybe your drive is getting a little dirty?

and yes, it runs without black borders.  well... small ones.  is there some screen adjustment tool in linux?  to change position, width, trapezoid, pincushion, etc?


and yes, to the first poster, i realize that offloading packages wont speed up the system.  but i only had 40 megs of free disk space after the install so i think i need a little more disk space and also, doesn't removing fonts decrease the startup time since it doesn't have to load as many fonts?

also, yes, im trying to go to lighter software and a lighter windows manager.  i was wondering if someone could point me to a webpage or a post that states step by step how to switch from GNOME to say xfce?

thanks

---

### Post by Rxke on 2005-11-28
hmmmm, hate to say it, but the leanest way is probably... reinstall. but use 'server' as image, and then add xfce, x-server and assorted stuff. I did this, and it went great. There's a how-to [http://ubuntuforums.org/showthread.php?t=75971&highlight=xfce](http://ubuntuforums.org/showthread.php?t=75971&highlight=xfce)  (disregard the grub stuff, that's for x86)

---

### Post by ssam on 2005-11-28
ok yeah remove stuff if you need the space. (or upgrade the hard drive. i put a 40gb in my imac for not very much money)

the font removing sounds plausible.

the sever install and then add what you need is quite a good method, as long as you know what packages you need.

[QUOTE=peter_m]Neo, how did you ger your iMAC 333 to read a CD-R? Mine wont read them reliably and I'm stuck waiting for the official CD. Also did you get your monitor to run without black borders?[/QUOTE]

if you want a cd quick then have a look at [https://wiki.ubuntu.com/forum/GiveAway](https://wiki.ubuntu.com/forum/GiveAway)

i think there are things you can put in the xorg.conf to shift the screen side to side, but you'll have to search for it.

---

### Post by neoplasticity on 2005-11-28
ok

i just reinstalled the whole thing using server install

and then installed Xbuntu desktop

however, when i do startx.  no dice

anyone know what xconfigure options i should be using for an iMac 333?

ati driver?
specify vram amount?

what refresh rate for the monitor?

etc

---

### Post by linear on 2005-11-28
Is the video ATI Rage 128, as in some later iMacs?

If so, horizontal "60-60" and vertical "75-117" work.

---

### Post by peter_m on 2005-11-29
Here is my configuration for my Debain install. Notice I am using the ati driver and look at the timing info from the "modeline" commands. Let me know if it helps. Also I'm sure the VGA is an ATI Mach 64 with 6mb. you can pop it open and look.

Also, I cleaned the lens on the CD- drive with a camera lens paper and solution. Didn't help. Any idea how to clean what's under the CD-rom's lens?

# XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"vbe"
	Load	"fbdevhw"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"macintosh"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"PS/2"
	Option		"Emulate3Buttons"	"no"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. 3D Rage Pro 215GP"
[COLOR="Red"]	Driver		"ati"[/COLOR]
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	VendorName	"Apple"
	ModelName	"iMac Rev.D 333"
[COLOR="red"]	HorizSync	60
	VertRefresh	70-121[/COLOR]
[COLOR="red"]	ModeLine	"1024x768" 77.52 1024 1061 1114 1292 768 773 775 804[/COLOR]
	ModeLine	"800x600" 60.60 800 820 900 1009 600 601 627 628
	ModeLine	"640x480" 48.12 640 640 726 802 480 481 508 510				

	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage Pro 215GP"
	Monitor		"Configured Monitor"
	DefaultDepth	16
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
#	SubSection "Display"
#		Depth		15
#		Modes		"1024x768" "800x600" "640x480"
#	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
#	SubSection "Display"
#		Depth		24
#		Modes		"1024x768" "800x600" "640x480"
#	EndSubSection
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

---

### Post by neoplasticity on 2005-11-29
peter,
hmm.. that dirty lens was a stab in the dark.  i guess the other option would be to replace the drive with another drive..  looks like it is a laptop cd drive from what i can tell.

thanks for your config file.  i'll give it a shot.  although breezy uses xorg instead of xfree86 so i dont know if that makes much of a difference or not.

i wish i would've copied my config file from my full desktop install that worked before i reinstalled the server only and xbuntu.  

if anyone has their config file from breezy on an imac 333, i'd really appreciated it cause then i'd probably just copy it verbatim.

---

### Post by neoplasticity on 2005-11-29
another thing to try would be to use another brand of cdr media.  some drives i know are picky about the type of dye used

---

### Post by peter_m on 2005-12-02
Well I have about 100 virign CDs sitting on the shelf and I am broke, I will wait for the mail to bring me the officialy pressed. But thanx for the idea.

As for the config file for Xorg, it's identical to Xfre86, look at the last post from this thread:
[http://www.ubuntuforums.org/showthread.php?t=20327](http://www.ubuntuforums.org/showthread.php?t=20327)

---

### Post by 3rdalbum on 2005-12-21
My iMac's CD-ROM drive has problems with burnt CDRs. It has more success with blue-dye discs, especially the regular TDKs. (not the Gold ones!).

If that doesn't work, try Verbatim.

I'm just about to see how good my iMac's drive really is :-)

---

