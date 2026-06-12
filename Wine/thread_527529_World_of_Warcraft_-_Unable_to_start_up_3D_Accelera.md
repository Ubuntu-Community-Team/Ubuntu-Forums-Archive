---
title: "World of Warcraft - Unable to start up 3D Acceleration"
date: 2007-08-16
forum: Wine
---

### Post by JesseEklund on 2007-08-16
Whenever i start WoW i get this error:

```
World of Warcraft was Unable to start up 3D Acceleration
```

That is when i use opengl, If i don't use opengl the game opens and i can log in all that stuff. Only problem is the game gets really choppy and colors and stuff mess up. Its playable but its more hassle then fun. I think i have tried almost every possible solution i could find. I have run out of ideas and would like some suggestions anything is welcome.

When i run glxinfo |grep direct i get direct rendering: Yes, Just thought i would put that in as i saw many people were asked to do that with this similar problem. If you need anything else from me just ask. 

My Specs:
```
Intel(R) 82845G/GL/GE/PE/GV Graphics Controller
Intel(R) Pentium(R) 4 CPU 2.00GHz
768MB RAM
60 GB Hardrive (40GB To XP/20GB to Ubuntu)
```

---

### Post by Nkari on 2007-08-16
Ah the very error message that has me stuck using windows.

---

### Post by dublinfireman on 2007-08-16
Same problem here....

---

### Post by cogadh on 2007-08-17
The problem is probably due to the Intel driver. When Intel stopped supporting it and it went open source, it never really improved much and still has significant problems running games. You'd be better off getting a cheap Nvidia card and running your games with that. Nvidia's drivers are incredibly robust and easy to install, plus Nvidia actually actively supports and updates the Linux drivers.

---

### Post by dougfractal on 2007-08-17
Hi JesseEklund
I'm tring to help a few people with your chipset.How did you get direct rendering?
can  you get compiz running?

---

### Post by Nkari on 2007-08-17
I Think it is probably more of a generic unhelpful error message, I'm using nvidia hardware and drivers not intel.

---

### Post by hikaricore on 2007-08-17
> **Nkari said:**
> I Think it is probably more of a generic unhelpful error message, I'm using nvidia hardware and drivers not intel.

Which NVIDIA hardware?
How did you install your drivers?
What version are the drivers you are using?
What colour depth is set in your xorg.conf file?
Do other 3D applications/games work well?
Most importantly, are you attempting to launch WoW while running a 3D desktop envioronment such as beryl or compiz?

---

### Post by JesseEklund on 2007-08-17
> **dougfractal said:**
> Hi JesseEklund
I'm tring to help a few people with your chipset.How did you get direct rendering?
can  you get compiz running?

To tell you the honest truth i have no clue at all. All i can remember is running the install and it auto detected it or something. Sorry i know thats not much help lol. And yes i do have compiz running and it works fine. If you need me to get any info off my install just ask and ill grab it for you.

As for the stupid error message i only get it when i attempt to run wow without the -opengl as i said. When i hope on ubuntu later ill get you guys a SS of what it looks like its not really pretty lol.

> Do other 3D applications/games work well?
Most importantly, are you attempting to launch WoW while running a 3D desktop envioronment such as beryl or compiz?

Wow i just saw that part of your post. I know you were talking about Nvidia but do you think it could be a problem with me running compiz and trying to start it?

---

### Post by dougfractal on 2007-08-17
> If you need me to get any info off my install just ask and ill grab it for you.  cheers :)

**system spec grabber**

paste this in terminal
```
mkdir ~/Xinfo
cd ~/Xinfo
echo 'touch X.info # create file
lsb_release -d > X.info # version
uname -r >> X.info # kernel
lspci -nn >> X.info # list hardware
glxinfo | head -4 >> X.info
script -c " glxgears &  sleep 11 ;  pkill -15 glxgears"   
cat typescript | grep FPS >> X.info
cp /etc/X11/xorg.conf ./   # graphics file
cp /var/log/Xorg.0.log ./
cp /etc/modprobe.d/blacklist ./
aptitude search ~imesa ~ixorg  ~idbus ~icompiz -F "%1p %10v %10V %20d" > installed.txt
tar -czf xinfo.tar.gz X.info xorg.conf Xorg.0.log installed.txt blacklist ' | tee xinfo.sh
sed -i '1i#!/bin/bash' xinfo.sh
chmod a+x xinfo.sh
./xinfo.sh
echo -e "\nplease attach $PWD/**xinfo.tar.gz**"

```
please attach **xinfo.tar.gz**

---

### Post by hikaricore on 2007-08-17
> **JesseEklund said:**
> Wow i just saw that part of your post. I know you were talking about Nvidia but do you think it could be a problem with me running compiz and trying to start it?

Accelerated desktops can cause many issues with other 3D applications, even more so using WINE.

I suggest disabling compiz with the tray icon prior to attempting to launch WoW.

---

### Post by JesseEklund on 2007-08-17
> **dougfractal said:**
> please attach **xinfo.tar.gz**
Hope this is what you wanted :)


Ok on to the wow thing now. I attached some photos of what it looks without the opengl thing selected. It probably wont make a difference but i just wanted to show what it looked like. I have to try a couple more things then ill get back with what happened,  Also is there a package that i have to install to get opengl support or something?

---

### Post by Nkari on 2007-08-18
Regarding getting the OpenGL unable to start 3D acceleration with Nvidia gear the following info is what you were after.

2x 512M 7600GT, however pulling one out and running with a single card has no effect on WoW problems.

Driver is 100.14.11 as set up by Envy, could not get Ubuntu GUI prior to fixing divers with Envy.

Have not tried any other games under wine as of yet, but GL screen savers work, GL Gears works and the command line test to see if direct rendering is functioning says it is. 

I am not using any 3D desktop effects or enhancement packages, just using the standard Gnome GUI one gets given, I haven't even changed the wall paper.

According to the Nvida control panel I am in 32Bit colour, but that particular application does not even offer 24bit, it jumps from 16 to 32, most likely this will mean it is really set to 24, not sure where to find the xorg config file to confirm this .

Might just see what happens if I set to 16 through the Nvidia panel later, that is not an area I have messed with yet.

Getting it to work, even if badly would at least give a starting point to see where the problem lies and I have a feeling that once I can get it to work with GL it will just work for me.

Anyone that seems to get the the point I can get to with D3D usually just ends up running in it in openGL and happily playing basically problem free.

---

### Post by graigsmith on 2007-08-18
ati's cards suck.  except for the ati 9200.  i play using the open source drivers with it. never had any problems with this card under linux. no crashing ever.  the only thing, it's quite slow. but i much prefer the stability.

nvidia's drivers are better.  yet i still had problems with them, it worked, and was pretty stable.  however 3d would black out for a second. every once in a while.

---

### Post by JesseEklund on 2007-08-18
After i tried running WoW without compiz i still am coming across the same problem. It's not life or death if it doesn't work on ubuntu but it would be plus as then that is one more thing i don't have to use windows for. Anyone else got some ideas?

---

### Post by dougfractal on 2007-08-18
from Gentoo 
[http://docs.huihoo.com/gentoo/resources/document-listing/dri-howto.html](http://docs.huihoo.com/gentoo/resources/document-listing/dri-howto.html)
> Section "Device"
  Option     "AGPMode" "4"
  // This increased FPS from 609 to 618.
  Option     "AGPFastWrite" "True"
  // This had no measurable effect, but it may increase instability of your computer.
  // You may also need to set it in your BIOS.
  Option     "EnablePageFlip" "True"
  // This improved FPS from 618 to 702. It also is "risky" but few people have reported problems.
  ...
EndSection
normally for radeon driver but I've googleed it and its been done with i810

[http://www.free3d.org/](http://www.free3d.org/)
some interesting stats and fps

other tweaks

---

### Post by dougfractal on 2007-08-23
I came across the thread

[http://ubuntuforums.org/showthread.php?t=533086](http://ubuntuforums.org/showthread.php?t=533086)
**HOWTO fix Intel GMA 3D issues by backporting Mesa 7.01**
> In some games and 3D applications (notably for me, Neverwinter Nights), the Intel GMA 950 has graphical errors that are caused by a bug in the version of Mesa that ships with Feisty. This bug is resolved in version 7.01 of Mesa, but unfortunately that version is only available in 7.10 Gutsy Gibbon. Therefore, the solution is to backport it. This would normally be a complicated process, however it is greatly simplified by the use of a program called prevu ........

---

### Post by Seraed on 2007-08-23
I'm sorry to get off topic, but I find your Void Walker's name hilarious... even more so because I knew a Warlock named Pheobe ><

Also, you might not want to post screen shots with your account name in them.

---

### Post by stuismad on 2007-09-03
Sorry to bump this but we need a solution.
Thanks.

---

### Post by dougfractal on 2007-09-03
stuismad tell me about your system

run this script. (copy and paste into terminal)
```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by stuismad on 2007-09-04
voila.

---

### Post by Allysan on 2007-09-14
I too am having this issue.  I'm running an NVIDIA GeForce Ultra on Ubuntu Feisty.  I installed the proper Nvidia drivers, reconfigured Xorg, and installed the nvidia-settings package.  Unfortunately when I try to use nvidia-settings, i get a box with only one set of options in it, none of them pertaining to 3d acceleration -- "Display tooltips, show status bar, slider text entries, include x display names, and show "really quit?" dialog" is all I get for options.  I'm assuming there should be more.  Running nvidia-settings as sudo does nothing.  Please help!  I want to play some WoW!

---

### Post by dougfractal on 2007-09-14
> NVIDIA GeForce Ultra
which type of ultra
please run
> lspci | grep -i vga


I have script. Can you use my diagnostic tool as it will tell me lots of things about your setup.

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```

please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by Allysan on 2007-09-15
Thank you sir, I don't have access to that computer right now but I will post it up as soon as I get back to campus tomorrow.

---

### Post by Allysan on 2007-09-17
Output of lspci | grep -i vga:

```
01:00.0 VGA compatible controller: nVidia Corporation NV15BR [GeForce2 Ultra, Bladerunner] (rev a4)

```

*xinfo.tar.gz is attached.  Thank you so much for your time.

---

### Post by dougfractal on 2007-09-17
from Xorg.0.log
> (EE) GLX is not supported with the Composite extension


make a xorg.conf backup
add this to the bottom of xorg.conf
> Section "DRI"
        Mode    0666
EndSection

Section "ServerFlags"
       Option  "AIGLX" "off"
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection


in the screen section
> Option		"AddARGBVisuals"	"True"
Option		"AddARGBGLXVisuals"	"True"

add Section "Module"
> Load    "dri"

Try with XGL
> sudo apt-get install xserver-xgl

restart

---

### Post by Allysan on 2007-09-17
Dougfractal, you are a GOD.  A GOD, I say.  Thank you so much.

EDIT: Garrr I'm afraid I spoke too soon.  It works... kind of.  I can sign in and get to the select character screen without a bit of lag, but then it hangs at about 66% of the loading bar after clicking "Enter World".  Anyone got any ideas?

**EDIT v2.0: SOLVED by upgrading to the newest version of Wine.  That's a big DOH on my part.  Thanks to all who helped :)**

---

### Post by sgnlfive on 2007-09-20
Hey everyone, sorry to bump up this post but I seem to have run into the mentioned problem. The card is a Radeon 9600.

here.s the file you requested in previous posts

please bare with me, as i am a linux noob.

Much thanks.

---

### Post by dougfractal on 2007-09-20
sgnlfive
> (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II(EE) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb733c000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

You've been "Envyed" or similar.
Uninstall flglx with envy if that what you used.

Then reinstall fglrx

> sudo apt-get install --reinstall xorg-driver-fglrx linux-restricted-modules-2.6.20-16-generic

---

### Post by sgnlfive on 2007-09-20
Appreciate the help dougfractal. Did what ya said and now it is working great. Much thanks. :)

---

### Post by dougfractal on 2007-09-20
Can you run the Xinfo script again so that I can add you to the list.  ;-)

[http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml](http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml)

cheers
Doug

---

### Post by sgnlfive on 2007-09-20
No problemo!

---

### Post by Nkari on 2007-09-21
Just spotted this diagnostic script you have been using in response to what seems to be the exact error message I am experiancing trying to run wow in OpenGL Mode under wine.  

I have never managed to get it working, I just keep trying again every time there is a wine update just in case somethng changed that will allow me to play in either D3D (no error message, almost works but not quite) or OpenGL.(unable to start 3d acceleration error)

Anyhow, mind if I give it a go and post my file? Might solve problems for multiple people if there is something hidden in plain sight there that is being missed.

Because either there is just no way for it to work at this point in time with the way my machine is set up and WoW will be the saviour of a loneley windows partition, or something has been missed

---

### Post by dougfractal on 2007-09-22
Nkari  run the script. Then I can help see what the problem is.

[http://ubuntuforums.org/showpost.php?p=3303634&postcount=19](http://ubuntuforums.org/showpost.php?p=3303634&postcount=19)

---

### Post by corndogs on 2007-09-23
I need help too,  I have the info in the attachment.

I get the same graphical issues as the guy who posted the screens.

---

### Post by Nkari on 2007-09-24
Ok, I'll do that when I get back on the machine, I ran the script already, so the file will hopefully have been created and just needs to be uploaded when I get home.

---

### Post by Nkari on 2007-09-24
File uploaded, thanks in advance.

---

### Post by dougfractal on 2007-09-24
**corndogs**   and** Nkari** 

You both have good frame rate and DRI, so I don't think I can help you.
It may be a Wine issue, I think there is a special version of wine for WoW but i'm not sure.


Are you running Destop effects? if so try with them off.

Nkari enable Destop effects , this will add some line to you xorg.conf which might help.

What wine version have you got and where did you get it from?

---

### Post by Nkari on 2007-09-24
That is what is really confusing, it looks like my 3d acceleration is working fine, WoW just thinks I don't have any when I try GL mode, it makes no difference if I have one or both of my video cards plugged in. D3D is super jerky on the swirly smoke animation on the login screen, and can't get into the game properly anyway. 

My wine is via the repositry that was mentioned in the "WoW with Wine" howto, so now that it is added I get updates to it from the Ubuntu Updater frequently.

By turning on desktop effects do you mean the standard ones in Ubuntu/Gnome desktop, or something like Beryl? Currently I have nothing like that turned on, but it is worth a go.

---

### Post by dougfractal on 2007-09-26
Can you tell me how you setup your WoW
did you follow this guide ?
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

do run WoW with this command?
**wine ~/.wine/drive_c/Program Files/World\ of\ Warcraft/WoW.exe -opengl**

Have you seen this guide
[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

---

### Post by LordAlvinMangrim on 2007-10-02
I am having the same troubles, only when i go to start wow without the opengl, it takes about a minuet until the login boxes appear. And in advance no im not using any special desktop addons or anything of that nature. 
Plz halp im starting to go into withdrawal from wow

---

### Post by LordAlvinMangrim on 2007-10-02
/facepalm never mind, i got it working just fine now, just needed some graphix updates... i feel like an idiot.

---

### Post by Warfire on 2007-10-13
I have much the same problem using OpenGL

My file is attached.  This is an old laptop so I wouldn't be surprised if it didn't work but I'd like to try.

Thanks!

---

### Post by dougfractal on 2007-10-14
Warfire  I don't think you are going to get DRI running on your trident CyberBlade/i1 :-(

---

### Post by Warfire on 2007-10-15
DRI wiki: [http://dri.freedesktop.org/wiki/Trident?highlight=%28CategoryHardware%29]("http://dri.freedesktop.org/wiki/Trident?highlight=%28CategoryHardware%29")

I have no idea how to grab the component from CVS - if this is worth trying I'll give it a go but am also happy to give up if it's not likely!!

Thanks for the response!

---

### Post by packamac on 2007-10-16
i am having the same 'unable to start up 3d acceleration ' problem. However- i am on a mac, any ideas? :( ( powerbook g4 12 inch tiger )

---

### Post by bogeangles on 2007-10-18
hi, 

i have the same problem, with the 3d acceleration.
I dissabled the 3d desktop, run the script.

using wine 0.9.47

thank you in advance

---

### Post by dougfractal on 2007-10-25
do run WoW with this command?
**wine ~/.wine/drive_c/Program Files/World\ of\ Warcraft/WoW.exe -opengl**

whats your output?

---

### Post by Nkari on 2007-10-26
Interestingly, the update to Gutsy through the updater somehow fixed the problem for me. Not sure exactly how.

---

