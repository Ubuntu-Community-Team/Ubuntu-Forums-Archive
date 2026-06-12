---
title: "[SOLVED] ATI - Fresh Install Help!!"
date: 2007-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-07-30
Here's the deal.  I installed a new SATA HD to replace my IDE Ubuntu install.  There was nothing wrong with the IDE install and I wanted a faster drive for U.  On my old install, the downloaded ATI driver worked PERFECTLY the 1st time.

It instantly gave me all my screen resolutions and refresh rates.  Now here is the problem.

After installing my New Raptor drive, I was doing a fresh install of ubuntu and the driver wouldn't install.  I quickly found that installing all my software packages installed the dependencies needed for the ATI driver.  I got the driver installed, but I didn't get my screen resolutions or refresh rates.

I have spent the whole weekend doing apporx. 30 fresh installs with the same result.

How come it worked the 1st time for me, and how do I duplicate this again.

I actually managed to clone the IDE drive to the SATA, and after editing the fstab/device map, and removing/reinstalling ntfs-3g, I now have my old install working with a good ATI driver.

I would still like to do a CLEAN install, but I can't figure out what I did right the 1st time that I'm doing wrong now.

Any help would be appreciated.

---

### Post by praxis22 on 2007-07-30
sudo dpkg-reconfigure xserver-xorg

---

### Post by crjackson on 2007-07-30
> **praxis22 said:**
> sudo dpkg-reconfigure xserver-xorg

Thanks I'll do that when I get home.

Does that make it reconfigure for the newely installed driver or something like that?

---

### Post by praxis22 on 2007-07-30
It asks you all the setup questions again, then forces the drivers to rediscover the hardware, etc. If ever you change any hardware, (keyboard, mouse, VGA card, monitor) you have to do to configure the new stuff. X is tweaky about new hardware.

---

### Post by crjackson on 2007-07-30
> **praxis22 said:**
> It asks you all the setup questions again, then forces the drivers to rediscover the hardware, etc. If ever you change any hardware, (keyboard, mouse, VGA card, monitor) you have to do to configure the new stuff. X is tweaky about new hardware.

Excellent!  I can't wait to give it a shot.

---

### Post by crjackson on 2007-07-31
> **praxis22 said:**
> sudo dpkg-reconfigure xserver-xorg

This didn't work out.  I must have done something wrong.  I'll try again tomorrow in the wee hours when I get home from work.

I went through the selections but when I reloaded X it dumped me into CLI.  I had to restore the HD from a backup image.

---

### Post by praxis22 on 2007-07-31
Odd, all it does is rewrite you xorg.conf

Look up your monitor specs, especially the refresh frequencies, etc. Then try it again, that part is rather vital. then you need to edit you modelines, etc.

This describes in detail how to do it:

[http://ubuntuforums.org/showpost.php?p=454217&postcount=1](http://ubuntuforums.org/showpost.php?p=454217&postcount=1)

Then there's this:

[http://jeremy.sunriseroad.net/2007/05/command-line-x-modeline-generator/](http://jeremy.sunriseroad.net/2007/05/command-line-x-modeline-generator/)

a web front end for it:

[http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

Wiki entries:

[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)
[https://help.ubuntu.com/community/DebuggingXAutoconfiguration](https://help.ubuntu.com/community/DebuggingXAutoconfiguration)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

google is your friend :)

---

### Post by crjackson on 2007-07-31
> **praxis22 said:**
> Odd, all it does is rewrite you xorg.conf

Look up your monitor specs, especially the refresh frequencies, etc. Then try it again, that part is rather vital. then you need to edit you modelines, etc.

This describes in detail how to do it:

[http://ubuntuforums.org/showpost.php?p=454217&postcount=1](http://ubuntuforums.org/showpost.php?p=454217&postcount=1)

Then there's this:

[http://jeremy.sunriseroad.net/2007/05/command-line-x-modeline-generator/](http://jeremy.sunriseroad.net/2007/05/command-line-x-modeline-generator/)

a web front end for it:

[http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

Wiki entries:

[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)
[https://help.ubuntu.com/community/DebuggingXAutoconfiguration](https://help.ubuntu.com/community/DebuggingXAutoconfiguration)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)



Okay, looks like I've got several things to try.  I really like that gtf script - One thing I couldn't find was the exact placement in the xorg file.  Does it matter where in the file I place the output of this script?

---

### Post by Kilz on 2007-07-31
> **crjackson said:**
> Okay, looks like I've got several things to try.  I really like that gtf script - One thing I couldn't find was the exact placement in the xorg file.  Does it matter where in the file I place the output of this script?

xorg.conf goes in /etc/X11
I recently solved my ATI problems once and for all, with a nvidia 7100 gs.  :D

---

### Post by praxis22 on 2007-07-31
> **crjackson said:**
> Okay, looks like I've got several things to try.  I really like that gtf script - One thing I couldn't find was the exact placement in the xorg file.  Does it matter where in the file I place the output of this script?

No, just make sure they're all linked, (that one references another, etc.) I think the modelines have to be in the screen section (from memory)  but just follow what's there and you'll be fine. look up a few on google, they all look alike, most of the good stuff goes at the bottom :)

---

### Post by crjackson on 2007-07-31
> **Kilz said:**
> xorg.conf goes in /etc/X11
I recently solved my ATI problems once and for all, with a nvidia 7100 gs.  :D

It's tempting kilz, but I have 8 systems in my house - all have ati except 2 (nvidia).  I'm not spending that kind of dough.  I don't have endless time BUT - I do have more time than money....:)

---

### Post by crjackson on 2007-07-31
> **praxis22 said:**
> No, just make sure they're all linked, (that one references another, etc.) I think the modelines have to be in the screen section (from memory)  but just follow what's there and you'll be fine. look up a few on google, they all look alike, most of the good stuff goes at the bottom :)

Like everything else Linux - It'll probably take 5 times longer to figure this out than anyone else, and once I think I've got it....  I'M WRONG AGAIN :)

I'll work on it until I get it, but this thing is crazy (video card thing I mean).  I just don't get how it worked perfect the one time.  I installed the driver, it did it's thing, and BANG!  I couldn't understand what all the fuss was.  The next 30-35 attemps were nothing but a way to piss off the wife (back at the keyboard at every chance I got).

You know, ATI lists dependicies needed for this thing and I can't find the exact ones in the repositories.  I find what I THINK are possibly newer versions but somehow I don't think they are quite right.

If I understood how to apt-get or whatever for those EXACT libs, and if I knew how in the H to write a script, I'd make one so that all the ATI people (especially me) could have less stress.  I don't see why ATI can't make an installer that will check for the dependicies and install them when needed.  Also why can't the thing put in the entries needed for the xorg file correctly ALL THE TIME?

I don't mind tweaking and fiddling and learning - but the ATI crap, and the wireless card crap - really drags a person down.

Right now, I finally have a FAIRLY decent OS config on MY system and one of the kids' systems.  They use it more that I do and UBUNTU is not hard for a new user at all.  It's just us older users who are having a hard time catching on (I Think).  Once it's all set up you can forget about it for the most part, but getting it setup PROPERLY with hardware support is rough in my house.

---

### Post by crjackson on 2007-08-05
I hate to say it, but I'm about to give up on ubuntu...

Thanks for all the help - You guys here are great, but after approx. 60 installs now, I can't get the ATI driver installed/configured on a fresh install.

Thanks again for the help.

---

### Post by praxis22 on 2007-08-05
Sorry to see you go.

Have you thought of using another distro?

---

### Post by crjackson on 2007-08-05
Not really.  I liked this one. not so much interested in the others...  I've learned a lot about ubuntu, but the ATI driver thing has really burned me out.

I even purchased a new hard drive just for this OS, but the rest is history...

---

### Post by Kilz on 2007-08-06
> **crjackson said:**
> It's tempting kilz, but I have 8 systems in my house - all have ati except 2 (nvidia).  I'm not spending that kind of dough.  I don't have endless time BUT - I do have more time than money....:)

Welllll, after a week, the board died. So I took it back, and got another ATI card. Best Buy had a x1050 for $63 bucks, vast improvement over the x200 on board. I also got more ram. After fooling around with my Dapper install trying to get the new board to work. I backed up dapper, wiped, and installed Feisty.

I just took a look at the entire post again.
With fiesty and thge new drivers, dont use 
```
sudo dpkg-reconfigure xserver-xorg
```
It will mess up the xorg.conf every time, I got the cli myself, use
```
sudo aticonfig --initial
```

[I used this]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.39.4_Driver_Manually") page. [But I took a few things from this page as well]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

What did I use from the Ubuntu page?

I edited the xorg.conf by adding 
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```
to the bottom.
I also got a command from some other page, that I cant remember. But I got them from the terminal log
```

sudo mkdir -p /usr/X11R6/lib/modules/dri
sudo ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri 
```
And added this to the bottom of xorg.conf
```
Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

---

### Post by crjackson on 2007-08-06
> **Kilz said:**
> Welllll, after a week, the board died. So I took it back, and got another ATI card. Best Buy had a x1050 for $63 bucks, vast improvement over the x200 on board. I also got more ram. After fooling around with my Dapper install trying to get the new board to work. I backed up dapper, wiped, and installed Feisty.

If you figure out the magic to making the ATI driver work on 7.04 please let me know.  I haven't killed the latest install yet...  If I could get a solid solution I'd stay with Ubuntu.

---

### Post by Kilz on 2007-08-06
> **crjackson said:**
> If you figure out the magic to making the ATI driver work on 7.04 please let me know.  I haven't killed the latest install yet...  If I could get a solid solution I'd stay with Ubuntu.

I just added a lot to the last post.

---

### Post by crjackson on 2007-08-06
> **Kilz said:**
> I just added a lot to the last post.

Does this give you all your resolutions, refresh rates, and 3D?

Also does you CCC work? 

I found that on the occasion where the driver installs (or seems to, I get a GUI during the install), the CCC only works if the restricted drivers are enabled.  This has happened on 2 instances of testing. The thing is that if I enable that, it downloads and uses the MESA code instead of the ATI code.  The difference is way noticable on my card.

---

### Post by Kilz on 2007-08-06
> **crjackson said:**
> Does this give you all your resolutions, refresh rates, and 3D?

Also does you CCC work? 

I found that on the occasion where the driver installs (or seems to, I get a GUI during the install), the CCC only works if the restricted drivers are enabled.  This has happened on 2 instances of testing. The thing is that if I enable that, it downloads and uses the MESA code instead of the ATI code.  The difference is way noticable on my card.

All the resolutions I use, I cut it down quite a bit and only use 1152x864, refresh up to 100hz. CCC works, I darkened the colors a little. Give it a try, my fglrxinfo gives
```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6650 (8.39.4)

```

The howto I linked to is all cut and paste.

---

### Post by crjackson on 2007-08-06
Okay I'll give it another try.  Just a few questions about your install procedure.

Prior to and during the install, are the restricted drivers disabled or enabled?  Mine are disabled

During the install, does the ATI GUI installer launch?  Mine won't, I get terminal feedback only.  This leades me to think that some dependicies are not installed, but I can't figure out which one(s).

What is your command line code for launching the installer?

I used    sh ./<drivername>

and

sudo -i ./<drivername>

They both do the same thing as far as I can tell.

---

### Post by Kilz on 2007-08-06
> **crjackson said:**
> Okay I'll give it another try.  Just a few questions about your install procedure.

Prior to and during the install, are the restricted drivers disabled or enabled?  Mine are disabled

During the install, does the ATI GUI installer launch?  Mine won't, I get terminal feedback only.  This leades me to think that some dependicies are not installed, but I can't figure out which one(s).

What is your command line code for launching the installer?

I used    sh ./<drivername>

and

sudo -i ./<drivername>

They both do the same thing as far as I can tell.

Disabled is fine while you do the howto.
No, the gui will not create ubuntu debs for Feisty. Its all in the terminal. Dont even try and run the gui. 
[The howto is a series of cut and paste commands,]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.39.4_Driver_Manually") read it and just follow the copy and paste instructions.
```
sudo bash ati-driver-installer-8.39.4-x86.x86_64.run --buildpkg Ubuntu/feisty
``` is the command that creates the debs, but it is only one step in the howto, after finishing the howto, add the extra steps I added to post #16 before you restart the computer.

---

### Post by crjackson on 2007-08-06
Thanks kilz - I'll give it a shot in a day or so.

---

### Post by crjackson on 2007-08-07
Okay kilz - Once again you have come to the rescue.  It all seems to have worked.  Please look in your CCC information tab and see if the 3D drivers says it was provided by MESA.  It all seems to work correctly, but it used to say ATI there.

Also, is there a cli command I can issue that confirms everything is as it should be?

---

### Post by Kilz on 2007-08-07
> **crjackson said:**
> Okay kilz - Once again you have come to the rescue.  It all seems to have worked.  Please look in your CCC information tab and see if the 3D drivers says it was provided by MESA.  It all seems to work correctly, but it used to say ATI there.

Also, is there a cli command I can issue that confirms everything is as it should be?

Mine says ATI, try ```
fglrxinfo
```. But at least we are getting closer.

---

### Post by crjackson on 2007-08-07
> **Kilz said:**
> Mine says ATI, try ```
fglrxinfo
```. But at least we are getting closer.

I'll try this when I get home tonight.

Mine does give an ATI driver version on one or two of the info lines listed in the CCC info page, but it also lists MESA at the 3D provider for GL.  I don't know what gives now.  It did this on my other machine too...

---

### Post by crjackson on 2007-08-08
[B]charles@MSI-K8N-Neo4-SLI-Platinum:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

charles@MSI-K8N-Neo4-SLI-Platinum:~$ 
[/B]

---

### Post by Kilz on 2007-08-08
> **crjackson said:**
> [B]charles@MSI-K8N-Neo4-SLI-Platinum:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

charles@MSI-K8N-Neo4-SLI-Platinum:~$ 
[/B]

Is the ATI accelerated graphics driver box checked in the Restricted Drivers manager in the System > Administration menu? If not, check it and reboot.
Secondly, just to make sure, you did the 2 commands and the 2 sections were added to your xorg.conf file from post 16. Go back and make sure everything is still there.

---

### Post by crjackson on 2007-08-08
> **Kilz said:**
> Is the ATI accelerated graphics driver box checked in the Restricted Drivers manager in the System > Administration menu? If not, check it and reboot.
Secondly, just to make sure, you did the 2 commands and the 2 sections were added to your xorg.conf file from post 16. Go back and make sure everything is still there.

It won't let me get to the check box in the restricted driver section.  It gives me a pop up that says "Your Hardware Does Not Need Any Restricted Drivers"

Here is the xorg.conf file:

[B]
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
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
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver      "ati"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
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

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
[/B]

---

### Post by Kilz on 2007-08-08
In this section, 
Section "Device"
Identifier "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
Driver "ati"
BusID "PCI:5:0:0"
EndSection

Replace "ati with "fglrx"

---

### Post by misfitpierce on 2007-08-08
I honestly got no problems witth my ATI card in laptop. Yes ATI could do better graphics wise... but in time im sure they will for linux. Till then I use Envy to install my drivers... Works fine everytime

---

### Post by crjackson on 2007-08-08
> **Kilz said:**
> In this section, 
Section "Device"
Identifier "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
Driver "ati"
BusID "PCI:5:0:0"
EndSection

Replace "ati with "fglrx"

I'll try this tonight when I get home.

---

### Post by crjackson on 2007-08-08
> **misfitpierce said:**
> I honestly got no problems witth my ATI card in laptop. Yes ATI could do better graphics wise... but in time im sure they will for linux. Till then I use Envy to install my drivers... Works fine everytime

That's great.  Doesn't help me though.  I've tried Envy and fails for me everytime so far.

---

### Post by crjackson on 2007-08-08
> **Kilz said:**
> In this section, 
Section "Device"
Identifier "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
Driver "ati"
BusID "PCI:5:0:0"
EndSection

Replace "ati with "fglrx"

[B]kilz, I'm at work right now so I haven't had a chance to make any changes but I have a basic question perhaps you can throw some light on.

I would like to know how come when I open up my screen resolution applett there are MANY resolution / refresh settings (all correct for my card / monitor), but I don't find them anywhere in the xorg.conf file.

We keep making changes to this file, and it would seem to be the correct place, but how come I don't see the rest of the information.  Where is it being stored?

Could there be another file some place that stores all this information?  Perhaps I should be looking there too.[/B]

---

### Post by crjackson on 2007-08-09
Okay, I changed the ati to fglrx.  Same result, I even asked ATI for help.  That was a mistake.  Here's what they said.

[B]The Linux drivers available from ATI are provide are "as is".
You may be able to get further assistance from the Linux community
at the links below:


[http://www.linux.org/help/index.html](http://www.linux.org/help/index.html)

[http://www.linuxdoc.org/](http://www.linuxdoc.org/)

[http://www.xfree86.org/](http://www.xfree86.org/)


Customer Care
ATI Technologies Inc.
ati.com
[/B]

---

### Post by Kilz on 2007-08-09
> **crjackson said:**
> Okay, I changed the ati to fglrx.  Same result, I even asked ATI for help.  That was a mistake.  Here's what they said.

[B]The Linux drivers available from ATI are provide are "as is".
You may be able to get further assistance from the Linux community
at the links below:


[http://www.linux.org/help/index.html](http://www.linux.org/help/index.html)

[http://www.linuxdoc.org/](http://www.linuxdoc.org/)

[http://www.xfree86.org/](http://www.xfree86.org/)


Customer Care
ATI Technologies Inc.
ati.com
[/B]

Now that you have changed the ati to fglrx, will the restricted driver manager allow you to enable it?

---

### Post by crjackson on 2007-08-09
> **Kilz said:**
> Now that you have changed the ati to fglrx, will the restricted driver manager allow you to enable it?
[B]
No Difference.  It doesn't let me select anything.[/B]

---

### Post by Kilz on 2007-08-09
> **crjackson said:**
> [B]
No Difference.  It doesn't let me select anything.[/B]

Ok, we have mesa installed. Are you getting ```
glxgears
``` to run? Are you having problems running anything? Are all your resolutions and refresh rates showing? Because if they are, then you may not need to get the proprietary driver to say its the driver. 
If you think something is not working my next suggestion will be to wipe out all existing video drivers and start from the beginning. This may lead to starting at the cli.
If you think you might  I will give you the commands in the next post.

---

### Post by crjackson on 2007-08-09
> **Kilz said:**
> Ok, we have mesa installed. Are you getting ```
glxgears
``` to run? Are you having problems running anything? Are all your resolutions and refresh rates showing? Because if they are, then you may not need to get the proprietary driver to say its the driver. 
If you think something is not working my next suggestion will be to wipe out all existing video drivers and start from the beginning. This may lead to starting at the cli.
If you think you might  I will give you the commands in the next post.

I'll try the glxgears when I get home, I'm at work right now.

Everything runs fair, but I do get video corruption after running 3D games and such.  I have to reboot to fix the problem.

I actually have a backup image of my HD with a good ATI driver (38 not the 39) installed.  I was having other issues because this image was made on an IDE drive, and I now use all SATA drives, so I wanted to do a CLEAN install to make sure I got everything behaving properly.  The clean install is where the problems started.

When I use the image with the properly installed ATI drivers, my system is much more responsive and 3D is WAY faster without any corruption afterwards.

I would like to work through this thing so that I KNOW how to make a clean install with a good video driver installation.

---

### Post by Kilz on 2007-08-09
In that case
```
sudo apt-get remove fglrx-kernel-source fglrx-kernel fglrx-kernel-$(uname -r) 
``` will remove everything. But it will leave you at the cli if you reboot.
I would recommend downloading the ati installer to your desktop if you reboot. Write down all the instructions, or print them out. You might also want to backup the xorg.conf file. You might also want to delete the /etc/ati folder.
Make sure you have the following installed
build-essential
module-assistant
fakeroot
dh-make
debconf 

[Make sure to do the preinstall checks]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Pre-Installation_Checks") Then [follow this method]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.39.4_Driver_Manually").

---

### Post by crjackson on 2007-08-09
> **Kilz said:**
> In that case
```
sudo apt-get remove fglrx-kernel-source fglrx-kernel fglrx-kernel-$(uname -r) 
``` will remove everything. But it will leave you at the cli if you reboot.
I would recommend downloading the ati installer to your desktop if you reboot. Write down all the instructions, or print them out. You might also want to backup the xorg.conf file. You might also want to delete the /etc/ati folder.
Make sure you have the following installed
build-essential
module-assistant
fakeroot
dh-make
debconf 

[Make sure to do the preinstall checks]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Pre-Installation_Checks") Then [follow this method]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.39.4_Driver_Manually").

No problem.  I'll do this later when I get home.  I'll back up the whole partition as it now is, it's very easy to restore it if something goes worg.

I have 7 other computers in the house to access the forum for instructions if needed.  Seldom do I have a disaster I can't recover from.  I backup backup backup, and then i backup some more.  No worries....

---

### Post by crjackson on 2007-08-09
> **Kilz said:**
> In that case
```
sudo apt-get remove fglrx-kernel-source fglrx-kernel fglrx-kernel-$(uname -r) 
``` will remove everything. But it will leave you at the cli if you reboot.
I would recommend downloading the ati installer to your desktop if you reboot. Write down all the instructions, or print them out. You might also want to backup the xorg.conf file. You might also want to delete the /etc/ati folder.
Make sure you have the following installed
build-essential
module-assistant
fakeroot
dh-make
debconf 

[Make sure to do the preinstall checks]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Pre-Installation_Checks") Then [follow this method]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.39.4_Driver_Manually").

[B]kilz,

Do you think it would work just as good if I do a clean install?  I'm not worried about the loss of data or settings.

If a clean install would do just as good, then should I do the driver procedure after getting the 99 updates it's going to alert me to, or should I do the driver thing first?

I already have a new image of a clean install with only the automatic updates added.  No software or drivers have ever touched this install.  It takes me 1m 38s to restore from this image as compared to 20m from an install CD.

Your advice...[/B]

---

### Post by Kilz on 2007-08-09
> **crjackson said:**
> [B]kilz,

Do you think it would work just as good if I do a clean install?  I'm not worried about the loss of data or settings.

If a clean install would do just as good, then should I do the driver procedure after getting the 99 updates it's going to alert me to, or should I do the driver thing first?

I already have a new image of a clean install with only the automatic updates added.  No software or drivers have ever touched this install.  It takes me 1m 38s to restore from this image as compared to 20m from an install CD.

Your advice...[/B]

If your willing to do a clan install, go for it. As for what kind of clean install, thats up to you. As long as you didn't install any graphics drivers it shouldn't matter. At least then you will be doing the work from a gui.

---

### Post by crjackson on 2007-08-09
> **Kilz said:**
> If your willing to do a clan install, go for it. As for what kind of clean install, thats up to you. As long as you didn't install any graphics drivers it shouldn't matter. At least then you will be doing the work from a gui.

**Cool, I'll do that then.  So you don't think having the updates installed or not play any role in the issue then?**

---

### Post by Kilz on 2007-08-09
> **crjackson said:**
> **Cool, I'll do that then.  So you don't think having the updates installed or not play any role in the issue then?**

No, I install all updates as the fist thing on install, and my install went ok when I installed Feisty this last week.

---

### Post by crjackson on 2007-08-09
Okay, I'll start from there then on my next attempt.  This puts me at approx. 63 installs of ubuntu now.](*,)

---

### Post by Kilz on 2007-08-09
> **crjackson said:**
> Okay, I'll start from there then on my next attempt.  This puts me at approx. 63 installs of ubuntu now.](*,)

ouch!

---

### Post by crjackson on 2007-08-09
Going out of town after work tonigh, so I won't get a chance to work on this again until Monday or Tuesday.

Thanks for hanging in there with me...):P

---

### Post by crjackson on 2007-08-10
How do I fix this?

[B] charles@MSI-K8N-Neo4-SLI-Platinum:~$ debconf libstdc++5 linux-headers-generic
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Can't exec "libstdc++5": No such file or directory at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of libstdc++5 linux-headers-generic failed at /usr/share/perl5/Debconf/ConfModule.pm line 58
charles@MSI-K8N-Neo4-SLI-Platinum:~$ 
[/B]

---

### Post by Kilz on 2007-08-10
> **crjackson said:**
> How do I fix this?

[B] charles@MSI-K8N-Neo4-SLI-Platinum:~$ debconf libstdc++5 linux-headers-generic
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Can't exec "libstdc++5": No such file or directory at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of libstdc++5 linux-headers-generic failed at /usr/share/perl5/Debconf/ConfModule.pm line 58
charles@MSI-K8N-Neo4-SLI-Platinum:~$ 
[/B]

Im not sure if its a bad install, or it cant find the package. You might want to run ```
sudo apt-get install -f
``` To see if it clears up the problem. If not you can get [the package here.]("http://packages.ubuntu.com/feisty/base/libstdc++5")

---

### Post by crjackson on 2007-08-10
Okay, I ran through it again and got past that point.

Problem is I'm now running on MESA drivers just like the last time except that I can use the restricted driver check box.  On or Off it doesn't seem to matter, it still reports the MESA drivers again.

Going to call it for the night.  I'm getting tired of ATI...

---

### Post by Kilz on 2007-08-10
> **crjackson said:**
> Okay, I ran through it again and got past that point.

Problem is I'm now running on MESA drivers just like the last time except that I can use the restricted driver check box.  On or Off it doesn't seem to matter, it still reports the MESA drivers again.

Going to call it for the night.  I'm getting tired of ATI...

Did you edit the xorg.config to replace the ati with fglrx?

---

### Post by crjackson on 2007-08-12
> **Kilz said:**
> Did you edit the xorg.config to replace the ati with fglrx?

Yes, it's there.

---

### Post by Kilz on 2007-08-13
> **crjackson said:**
> Yes, it's there.

Im going to attach my xorg.conf file to this post. Then you can at least make sure they match.

---

### Post by crjackson on 2007-08-13
It's clear to me that there is somewhere else these settings are being stored.  My xorg.conf doesn't even show my resolutions / refresh rates that are actually available to me.

I have them all at my fingertips by using the screen resolutions applett but they do not show in the /etc/x11/xorg.conf file.

Is there another copy of this file possible being loaded from somewhere else on the system?

---

### Post by Kilz on 2007-08-13
> **crjackson said:**
> It's clear to me that there is somewhere else these settings are being stored.  My xorg.conf doesn't even show my resolutions / refresh rates that are actually available to me.

I have them all at my fingertips by using the screen resolutions applett but they do not show in the /etc/x11/xorg.conf file.

Is there another copy of this file possible being loaded from somewhere else on the system?

The only one I know about is in /etc/X11/xorg.conf

---

### Post by mobad on 2007-08-13
OK... you are the second person (not including me) that I've seen with this problem... its remarkably easy to fix and I'm really disappointed no one has fixed it yet.

Use this xorg.conf and make sure you have the ATI driver installed before you use this xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "Files"

# path to defoma fonts
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection


Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection


Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "aticonfig-Monitor[0]"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection


```
It had two Monitor sections, it had two Device sections and it had two Screen sections so to fix it you simply have to remove one of each.  Hopefully this should work.

P.S. I feel sorry for you ... 63 INSTALLS!!! thats just crazy.

---

### Post by crjackson on 2007-08-13
> **mobad said:**
> OK... you are the second person (not including me) that I've seen with this problem... its remarkably easy to fix and I'm really disappointed no one has fixed it yet.

Use this xorg.conf and make sure you have the ATI driver installed before you use this xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "Files"

# path to defoma fonts
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection


Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection


Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "aticonfig-Monitor[0]"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection


```
It had two Monitor sections, it had two Device sections and it had two Screen sections so to fix it you simply have to remove one of each.  Hopefully this should work.

P.S. I feel sorry for you ... 63 INSTALLS!!! thats just crazy.

Thanks - I'm getting ready for work right now, so I'll have to do this tomorrow.  I'll report back with my results later.  Thanks for you help.

63 installs was just about to turn me back to windows :mad:

---

### Post by crjackson on 2007-08-14
**@mobad**

I made the changes however it didn't effect anything with the system.

**kilz or mobad - anything else I can try**?

---

### Post by mobad on 2007-08-14
OK, type "fglrxinfo" in the terminal and post the results.  Post your current xorg.conf.  Post what resolution and refresh rate you want your screen to be.  Make sure the ATI restricted driver is installed.

---

### Post by crjackson on 2007-08-14
[B]charles@MSI-K8N-Neo4-SLI-Platinum:~$ fglrxinfo
Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

charles@MSI-K8N-Neo4-SLI-Platinum:~$ [/B]

Resolution and refresh rate are no longer a problem - 1024x768 100Hz

Problem is that it's still using the MESA driver and I want the ATI driver.  I get screen corruption w/3D games using MESA.  On previous install I had the ATI driver working properly (I don't know why it worked, It just did).  3D was faster and without any screen corruption.

I'm starting to think that it has something to do with using an SATA drive.  When I did a fresh install on the previous IDE drive, the driver (38 not 39) from ATI installed perfectly the first time.

All the subsequent installs have been an effort to get a good install going on my new SATA drive.  Could this be causing the problem?

---

### Post by mobad on 2007-08-14
Try "sudo depmod -a" then Ctrl+Alt+Backspace.
I don't think that SATA or IDE would make a difference, at least I can't think of a reason for it to make any difference.
I would still like to see you current xorg.conf if the above does not work.

---

### Post by crjackson on 2007-08-14
I'll do this when I get home from work and see what gives.

Can you tell me where all the information is stored that contains the resolutions and refresh rates.

The xorg.conf file isn't the only place, it can't be.  I have resolutions and refresh rates available to me using the screen resolution applet that aren't reflected in that file.

There is some other place this information is being stored and I feel like this is where the answer lies.

What do you think?

---

### Post by mobad on 2007-08-14
Well it IS all in xorg.conf.  You can choose other resolutions because your driver allows you to select up to the maximum available for you card unless otherwise stated in xorg.conf.  Resolutions and refresh rates have nothing to do with why it's using Mesa.

---

### Post by crjackson on 2007-08-14
> **mobad said:**
> Well it IS all in xorg.conf.  You can choose other resolutions because your driver allows you to select up to the maximum available for you card unless otherwise stated in xorg.conf.  Resolutions and refresh rates have nothing to do with why it's using Mesa.

It's pretty confusing.  My xorg.conf file shows a low refresh range and only a maximum of 1024x768.  The applet lets me chose very high resolutions and refresh rates (all valid for this card).  If the driver keeps all this information and the xorg.conf doesn't reflect the same, then it seems the driver overrides the xorg.conf entries.

I understand what you are saying about it not having anything to do with using either MESA or ATI.  It just seemed strange and I wanted to know how this works.

---

### Post by crjackson on 2007-08-14
> **mobad said:**
> Try "sudo depmod -a" then Ctrl+Alt+Backspace.
I don't think that SATA or IDE would make a difference, at least I can't think of a reason for it to make any difference.
I would still like to see you current xorg.conf if the above does not work.

WOW! All this time....
[B]
sudo depmod -a and IT'S ALL WORKING CORRECTLY NOW![/B]

Please tell me exactly what that did...

---

### Post by mobad on 2007-08-15
Well "sudo depmod -a" basically loads the unloaded kernel modules and I figured fglrx wasn't loaded properly because I've had those sorts of problems many times when playing around with Compiz Fusion.  But, even that wouldn't have worked if you hadn't of replaced xorg.conf with the fixed one I supplied (I think I pointed out the problems with your xorg.conf in my post with the fixed xorg.conf).  If you be more specific about what you want to know about then I can help. 
Glad I could help!

---

### Post by crjackson on 2007-08-15
Thanks, that's what I wanted to know depmod told it to load modules and -a flagged it for ALL modules.  I think that's correct.

I downloaded and even installed the latest driver that came out yesterday and it worked like a charm.

Thanks again...

---

