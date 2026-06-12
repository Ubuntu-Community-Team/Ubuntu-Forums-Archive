---
title: "Problem with Games in Linux"
date: 2008-10-09
forum: x86 64-bit Users
---

### Post by linux4life88 on 2008-10-09
Is it just me or do a lot of open source games just not work well in Linux? For example in Ubuntu 7.10 you download Frets on Fire and it won't run after installation. You download it on 8.04 and it runs but basically crashes your computer. You download Open Arena on 8.04 and the download works but it won't work just like Frets on Fire in 7.10. AssaultCube on 8.04 is incredibly slow and lags something fierce. Basically the only games that work well in Linux is Frozen Bubble, Hearts, Same GNOME and Mahjongg. Is it just me or do other people, when trying to play games on Linux, get nothing but a head ache.

---

### Post by MedianMajik on 2008-10-09
I didn't have problems installing Frets on Fire, but the button response is sluggish.  I haven't tried Alien Arena or Assault Cube, but Nexuiz and Tremulous installed easily through synaptic and have been a lot of fun.  I've also played World of Padman (somewhat irritating to install) and Gridwars 2 (so awesome).  The biggest problem with linux games is just getting them to run.  "Frozen Bubble, Hearts, Same GNOME and Mahjongg"   are very light on system horsepower.  Could your trouble be on the hardware end?  A little more detail could go a long way

Good luck

---

### Post by linux4life88 on 2008-10-09
It's a laptop:

Gateway MX6454

AMD Turion 64bit X2 TL-50 (1.5ghz)
ATI Radeon Xpress 1150 Graphics (aka Radeon Xpress 1100 IGP) was restricted hardware but now it is in use
2gb Ram
120gb Hard Drive 4200rpm

When I had Windows on it, I didn't have any problems with any games (Rome Total War, Sim City 4). Converted the laptop to just Ubuntu back in November of 2007 because I love Ubuntu so much.

---

### Post by noerrorsfound on 2008-10-10
> **linux4life88 said:**
> AssaultCube on 8.04 is incredibly slow and lags something fierce.
Either your video card sucks, you haven't installed the proprietary drivers from the manufacturer, or their drivers suck. AssaultCube runs on the Cube 1 engine which doesn't require anything close to the latest and greatest hardware to run. It just needs a decent video card that can handle games using OpenGL and driver software that is good enough to utilize the hardware. NVIDIA's your best option by far.

You've created only one thread which was about only one game you listed above (Frets on Fire) and GNOME Hearts. You were given a suggestion; did you try it? If you did, you should have posted the output if you didn't understand it.

> ATI Radeon Xpress 1150 Graphics (aka Radeon Xpress 1100 IGP) was restricted hardware but now it is in use
For 3D games that's definitely your problem. ATI/AMD's video drivers are no good, and that's an onboard chipset which isn't good in the first place. Find a cheap video card from NVIDIA.

---

### Post by Jouke74 on 2008-10-10
"Find a cheap video card from NVIDIA." I think that won't matter much if he has a laptop... Find a new Nvidia graphic based laptop yes, but that's a drastic solution. Unfortunately indeed your videocard is the problem. 

- Make sure that you are not running the Mesa drivers, but the ATI drivers for OpenGL. If you have installed the restricted drivers this should be ok.

- Did you try to disable desktop effects before starting the game? That might Gain a few FPS (really a few). 

- Lower the screen resolution while gaming 
(also not something you wish to do I know)

- Dual boot with Windows (I basically use this).

---

### Post by Thelasko on 2008-10-10
From what I recall, I had to play with the settings in Frets on Fire to get it to work properly on my system.  It's likely because my graphics card is slow.  If playing with the graphics settings in the game doesn't work, try disabling compiz to free up some more resources.

I've also had some issues with one of the Frets on Fire addons.  I think it was called "Cold".  It completely messed up the game.

---

### Post by linux4life88 on 2008-10-10
My graphics card isn't that bad. Yes it is integrated but it can use up to 128mb shared. I shouldn't be having these problems. I have the xorg-driver-fglrx. I just can't figure how Linux games work better on Windows. This just shouldn't be.

---

### Post by linux4life88 on 2008-10-11
bump

---

### Post by linux4life88 on 2008-10-12
I went into the terminal and found out that direct rendering wasn't working. Could this be the problem? If so how can I fix it.

---

### Post by gnulogic on 2008-10-12
alien arena is an awsome game and works great.  with frets on fire just get the latest version from sourceforge, it works great. DO A LITTLE RESEARCH HOMMIE.

---

### Post by simtaalo on 2008-10-12
could you use the envy drivers for your ATI card?

---

### Post by linux4life88 on 2008-10-12
Thanks for the tip and I got rid of the other driver and downloaded the envy driver but still no direct rendering. The games are still incredibly slow. I'm hoping maybe this will be fixed in 8.10.

---

### Post by linux4life88 on 2008-10-12
I found this on ATI's site:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

I tried to open the final in the terminal under the sudo user put the terminal said:

Permission Denied

This problem is really starting to anger me. I've working on this for almost a year now and nothing works. I really really really hope this will be fixed in 8.10.

---

### Post by MedianMajik on 2008-10-12
> I found this on ATI's site:

[http://ati.amd.com/support/drivers/l...ux-radeon.html](http://ati.amd.com/support/drivers/l...ux-radeon.html)
I tried to open the final in the terminal under the sudo user put the terminal said:
Permission Denied

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

This unofficial wiki guide, linked from ATI's website link you posted above, could help.  

Below is a snippet from an old thread on installing ATI drivers.
[http://ubuntuforums.org/archive/index.php/t-908089.html]("http://ubuntuforums.org/archive/index.php/t-908089.html")

> Permissions:
Permissons can be changed via "chmod"
permissions are rwxrwxrwx
r=read; w=write; x=execute
the triple is because of free different groups:
first triple is related to the file owner
2nd triple is for the usergroup the file owner is in
3rd triple is for any other users

to make a file executable, simply type:
chmod +x ./filename (maybe with "sudo" prefix, which makes it being execute with superuser rights
This will add the "x" var to all 3 triples

There is another way to set permissions:
chmod 0755 ./filename which will set the permissions as the following: rwxr-xr-x

If you want to know more about any command, use man <command> e.g. man chmod or man chown


---

### Post by Jouke74 on 2008-10-12
If direct rendering is not working, then this is really the reason for your problems. Use: 
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Note the following things:
- "Post-Installation Tweaks" 
- If you are using the x86_64 architecture (64 bit), be sure to inst "ia32-libs" before proceeding!
- Additional 64-bit instructions
- Fix for an error:
- Removing Mesa drivers !!!!!
- Error! This module/version combo is already installed 

The easiest way is to use the restricted drivers manager. I never used Envy, but success seems to vary. 

If it says permission denied, make sure you make the downloaded file executable before running. To do this, use Nautilus, Click on the file and then "Properties". Here you can make it executable, but also change the file permissions for users if required.

Don't give-up, the only way to make Linux better is to have these reports about things not working, because no one will be bothered to change the Wiki or programs if it's working.  :lolflag:

---

### Post by linux4life88 on 2008-10-12
Thanks again for the help. I got the driver to install and the following thinks happened:

What Works:
I can now change my screen resolution. I could never do this before.

What doesn't Work:
Compiz
Direct Rendering

Random Weird Stuff:
Now when Ubuntu launches it goes in the screen where the bar is being filled and then cuts away to some random text and then the login screen shows up.

I don't get it, but oh well. I know for a fact that next time I get a laptop it is going to have a Nvidia card and not and AIT card.

---

### Post by ynell on 2008-10-14
even with the drivers etc, you'll still notice a difference. If the game is laggy etc then try lowering the resolution in game and/or taking off whatever (if any) special effects the game has to offer. 

like UT has foliage, weather effects, fog etc etc

Under windows i ran ut2004 with all max settings. and under Linux everything has to stay on normal and default resolution for me to  play without getting lag etc, and my gcard is a Radeon X850XT.



If your using an ATI and you want to game then the easiest/less stressful thing to do is just turn off compiz for now.

Edit: not saying you can't use compiz and play games with an ATI card, just that it can be pretty obnoxious to work out.

---

