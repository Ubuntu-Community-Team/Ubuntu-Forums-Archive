---
title: "Nividia-glx-new Screen problem"
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by TakeLifeEasy on 2008-05-01
Hi, first post so hope this is the right forum:confused:

I have a Dell Precision M90 laptop running firmware A07.  Ubuntu 8.04 installed a treat and asked me if I wanted to use the proprietary NVIDIA video driver for enhanced graphics.  I chose this and Gnome looks awesome using this driver.  However, intermittently the screen goes all fuzzy (like the picture you get on a TV without an aerial).  There is no way of bringing the screen back until I reboot when all is well.  The driver it used was the nvidia-glx-new so I uninstalled it and now back to whatever Ubuntu uses by default.  
My question is, is the nvidia-glx the same but older driver and can I use that instead to get the enhanced graphics.

Many thanks for any help provided.

---

### Post by njparton on 2008-05-01
Uninstall the driver then try envy to install it and auto configure X for you.
 
If that doesn't work you're not alone in having hardy/nvidia problems...

---

### Post by TakeLifeEasy on 2008-05-02
Many thanks for the reply.  I tried envy and it blasted my display back down to 640x480 and I could not get it to change.  May have another play with it later.  I have tried uninstalling the nvidia-glx-new driver and installing the nvidia-glx driver but when you into hardware drivers and select the NVIDIA card, it uninstalls nvidia-glx and re-installs nvidia-glx-new!

The problem I had happened when I used the nvidia-glx-new driver and set Visual Effects to "Normal".  I have now reinstalled the nvidia-glx-new driver and changed visual effects to "Extra".  I will update this thread with my findings as you mentioned others are having similar problems. 

Hope I can get this working as I have just switched to Ubuntu after using openSUSE with KDE for 2 years.  I am getting used to the Gnome interface and will probably stick with it for a while before trying Kubuntu.  I have also found the Ubuntu to be much faster than openSUSE.

Again, many thanks for your advice.

---

### Post by njparton on 2008-05-02
Have you tried editing your xorg.conf file to add in your required resolution?
 
I tried Opensuse 10.3 and Kubuntu 7.10 and opensuse was far superior, kubuntu 7.10 was very buggy for me.
 
On the flip side, community support for k/ubuntu is much better.

---

### Post by TakeLifeEasy on 2008-05-02
Must confess, I have am admit, I am personally not a command line guy and unless there is a gui front end, I leave well alone.:oops:  I compile the odd program but that is it!  I will have a a play with envy again later as I did it late last night and ran out of time to really try it properly.

Just an update, I have switched Visual Effects from "Extra" to "Normal" as I was getting a lot of flicker when moving windows around the screen.  However, it seems I am still getting the flicker in "Normal" mode as well so looks to be a driver problem.  Can anyone point me in the right direction to find out if the driver is being updated?

By the way guys, cool forum and fantastic help.  Ubuntu appears to have a great community.

---

### Post by enchantedsky on 2008-05-02
> **TakeLifeEasy said:**
> Many thanks for the reply.  I tried envy and it blasted my display back down to 640x480 and I could not get it to change.  May have another play with it later.  I have tried uninstalling the nvidia-glx-new driver and installing the nvidia-glx driver but when you into hardware drivers and select the NVIDIA card, it uninstalls nvidia-glx and re-installs nvidia-glx-new!

The problem I had happened when I used the nvidia-glx-new driver and set Visual Effects to "Normal".  I have now reinstalled the nvidia-glx-new driver and changed visual effects to "Extra".  I will update this thread with my findings as you mentioned others are having similar problems. 

Hope I can get this working as I have just switched to Ubuntu after using openSUSE with KDE for 2 years.  I am getting used to the Gnome interface and will probably stick with it for a while before trying Kubuntu.  I have also found the Ubuntu to be much faster than openSUSE.

Again, many thanks for your advice.

Yeah, Envy blasted my resolution to 640x480 also. What I did was I got Envy to undo whatever it had done, and then I tried the Nvidia driver installation a second time, and somehow it worked, because it offered my a resolution of 1440x900 (which is what my widescreen LCD monitor supports)

Anyway, I have a Dell Desktop with Nvidia graphics like yourself, and moving windows does have some flicker also. There is a new Nvidia driver coming out soon (it is currently in Beta I think) that is supposed to solve more bugs than the driver Ubuntu currently offers you with the Restricted Drivers Management.

---

### Post by TakeLifeEasy on 2008-11-15
Reference my first post, I am now on Ubuntu 8.10 and am using version 177 of the NVIDIA driver and I still get the same problem.  Is this down to NVIDIA and is there anything I can do to solve this.  It works fine for a while then just goes all fuzzy and you cannot do anything apart reboot as you cannot see a thing.

---

### Post by TakeLifeEasy on 2009-03-31
I am now running Ubuntu 9.04 beta with the NVIDIA driver version 180 and I still have the same problem with this.  Is there anyone else with this problem as I have kept with Ubuntu for some time but cannot use any of the advanced video settings.  Does the straight Debian distribution use the same drivers only I think it is time to try another distro to see if it is fixed in that :sad:

---

### Post by loomsen on 2009-03-31
I'm fine. In fact I think the driver improved a whole lot since hardy, plus there are new releases very often, betas as well as stable releases.

You can be happy you don't have an ATI device I guess ^^

To your problem.

Would you mind posting some output:

```

cat /proc/driver/nvidia/cards/0 
cat /proc/driver/nvidia/version

cat /etc/X11/xorg.conf 

cat /var/log/Xorg.0.log | grep -i "(ee)"
cat /var/log/Xorg.0.log | grep -i "(ww)"

groups

ls -alh `find /dev -name nvidiactl`

```

With the help of this, you will probably get somewhat closer towards your goals...

---

### Post by loomsen on 2009-04-01
Lol, no help eh?

Just post them, line per line, into a terminal, and copy and paste their outputs here...

---

### Post by TakeLifeEasy on 2009-04-01
Hey, many thanks for you help.  Here you go -

---------------
Model: 		 Quadro FX 2500M
IRQ:   		 16
Video BIOS: 	 05.71.22.28.04
Card Type: 	 PCI-E
DMA Size: 	 39 bits
DMA Mask: 	 0x7fffffffff
Bus Location: 	 01.00.0

-----------------
NVRM version: NVIDIA UNIX x86 Kernel Module  180.37  Thu Mar  5 18:11:54 PST 2009
GCC version:  gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4)

------------------
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---------------------

(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

-----------------------
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
clownfish@takelifeeasy:~$ cat /var/log/Xorg.0.log | grep -i "(ww)"
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
(WW) NVIDIA(0):     UBB.

-------------------------
clownfish adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev libvirtd vboxusers

----------------------

crw-rw---- 1 root video 195, 255 2009-04-01 18:35 /dev/nvidiactl

---

### Post by loomsen on 2009-04-01
OK, you're using the wrong driver...

For your device keep it with the 173 series drivers.

Remove everything related to nvidia-180 and install 173 instead. Everything else is ok, so it should work then.

(Hint, you can use 

aptitude search nvidia | grep 173

if you're stuck to a shell)

---

### Post by TakeLifeEasy on 2009-04-02
Many thanks, I will give this a go and report back.  Why does Ubuntu install and recommend the 180?  I assume the higher the number does not me the latest version?

If this works, you are a God as it has been driving me mad for ages :p

---

### Post by TakeLifeEasy on 2009-04-02
OK, everything is now stipped off apart from NVIDIA 173.  Now when I go into Appearnce Preferences - Visual Effects and click on "Normal", I get a pop up that says 

"Desktop effects could not enabled".


Any thoughts?

---

### Post by TakeLifeEasy on 2009-04-02
Just been on the NVIDIA site and entered the details of my graphics card and it comes up with the 180?

[http://www.nvidia.com/object/linux_display_ia32_180.44.html](http://www.nvidia.com/object/linux_display_ia32_180.44.html)

---

### Post by TakeLifeEasy on 2009-06-12
Another update to this thread.  I have just discovered that when my screen goes all fuzzy, if I close the screen shut and open it again, the fuzzyness disappears and I can see my desktop again!  I am still testing this to see if a single close of the screen is enough or if the screen goes all fuzzy again after the a single close.  

I guess this would indicate a hardware fault but it worked fine under Windows.

---

### Post by TakeLifeEasy on 2009-06-12
Forgot to add, I do get a lot of flickering.  The screen flickers approximately every on to two minutes.  This only happens after the fuzzy problem with the screen and I have shut and reopened the screen lid.

---

