---
title: "Farewell Bill, But still need some help Deciding on the OS"
date: 2007-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by DevilDux on 2007-03-16
Well I have decided to leave Windows behind, hopefully for good this time.   I last tried this during the early days of Breezy Badger.  I really enjoyed my experience with Ubuntu and Linux.  The only drawback was I kept switching to my Windows install to play games like WoW and Neverwinter Nights, and eventually abandoned Ubuntu all together.  It seems Linux has made substantial progress since then, in regards to running WoW through Wine. I am ready to return to Ubuntu now, but have a few questions about the best way to proceed. Here are my system specs, and also what I wish to get out of Linux.

> CPU:                	AMD Athlon(tm) 64 Processor 3200+
CPU Speed:          	2009.1 MHz
Sound card:         	NVIDIA(R) nForce(TM) Audio
Display Adapters:   	Radeon X1600 Pro / X1300XT 
Network Adapters:   	NVIDIA nForce Networking Controller - Packet Scheduler Miniport
Hard Disks:         	C:  279.5GB | D:  37.3GB
Hard Disks - Free:  	C:  143.6GB | D:  21.3GB
Motherboard:        	Gigabyte Technology Co., Ltd. GA-K8NF-9 / K8NF-9-RH

The main thing is I need to install and play WoW.  I was looking at Xubuntu for the simplicity of the desktop look, though I would also like to try out Beryl.  I understand Beryl is beta, and therefore not stable, but I would like to try it anyway.  Is Xubuntu an okay way to go for that.  Also which would be the best way to go, the AMD64 version, or should I stick with generic 386, for less problems when installing Wine and WoW?  Also how much trouble is the ATI Video card going to cause me?  Should I stick with the driver my install selects, or something else?

Thank you in advance for your time and patience regarding these questions.

*edit* Also my version preference is Edgy Eft.

---

### Post by Kilz on 2007-03-16
> **DevilDux said:**
> Well I have decided to leave Windows behind, hopefully for good this time.   I last tried this during the early days of Breezy Badger.  I really enjoyed my experience with Ubuntu and Linux.  The only drawback was I kept switching to my Windows install to play games like WoW and Neverwinter Nights, and eventually abandoned Ubuntu all together.  It seems Linux has made substantial progress since then, in regards to running WoW through Wine. I am ready to return to Ubuntu now, but have a few questions about the best way to proceed. Here are my system specs, and also what I wish to get out of Linux.



The main thing is I need to install and play WoW.  I was looking at Xubuntu for the simplicity of the desktop look, though I would also like to try out Beryl.  I understand Beryl is beta, and therefore not stable, but I would like to try it anyway.  Is Xubuntu an okay way to go for that.  Also which would be the best way to go, the AMD64 version, or should I stick with generic 386, for less problems when installing Wine and WoW?  Also how much trouble is the ATI Video card going to cause me?  Should I stick with the driver my install selects, or something else?

Thank you in advance for your time and patience regarding these questions.

If your only concern is wine and WoW there will be very little extra setup involved in the 64bit version. Following a few well known howto's will have you up in no time. But..... Please consider Cedega. For the price of $15 dollars you will save yourself loads of head banging dealing with wine.
For your setup, I would stick to Ubuntu and gnome for beryl. You can always add the xubuntu-desktop package later if you find you dont like gnome.

---

### Post by DevilDux on 2007-03-16
Thank you for that quick reply Kilz, I have started the torrent for Ubuntu 6.10 now, and will be installing it later tonight.  On the Cedega/Wine issue. A little head banging is good ever now and then, and I am broke.  I actually like challanges like that though, one of my best computer memories, is when I first got Neverwinter Nights to actually run on Ubuntu.  It just felt, "cool".

---

### Post by inCursorated on 2007-03-16
i would recommend using the x86 version and not the 64-bit to avoid issues... 

i've had a lot of problems in the past with trying to get WoW to run with ATI hardware. i actually bought an nvidia card and am now really enjoying my setup with Kubuntu Edgy and Beryl. WoW runs great for me under wine

it will install the open source ati driver. you'll prolly want to install the proprietary driver from ATI, hopefully it'll go smoothly... not sure tho

---

### Post by Kilz on 2007-03-16
> **inCursorated said:**
> i would recommend using the x86 version and not the 64-bit to avoid issues... 


Pure Fud.

---

### Post by inCursorated on 2007-03-16
> **Kilz said:**
> Pure Fud.

i made that recommendation based on experience. wine will prolly be a pain because they don't provide 64-bit binaries. u have to compile your own or use one someone else made... if u're really set on it here are some links...

[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
[http://www.ubuntuforums.org/showthread.php?t=297280](http://www.ubuntuforums.org/showthread.php?t=297280)

edit: meant to say 64-bit binaries, not 32. btw, i realize it's a 32-bit app. that's another reason gave the initial response - a lot of good programs only have 32-bit versions...

---

### Post by Kilz on 2007-03-16
> **inCursorated said:**
> i made that recommendation based on experience. wine will prolly be a pain because they don't provide 32-bit binaries. u have to compile your own or use one someone else made... if u're really set on it here are some links...

[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
[http://www.ubuntuforums.org/showthread.php?t=297280](http://www.ubuntuforums.org/showthread.php?t=297280)

You dont have to compile your own. There are a lot of packages (64bit) and information on how to install the 32bit version (ones in my signature). Either way you end up with a 32bit package, because wine is a 32bit compatibility layer. 
This is an example of someone making a mountain out of a mole hill.

---

### Post by inCursorated on 2007-03-16
i don't want to get into a thread battle here Kilz, so i'm not going to reply here again... 

> Also which would be the best way to go, the AMD64 version, or should I stick with generic 386, for less problems when installing Wine and WoW? 

sounds like the guy is looking to avoid complications... a 64-bit OS isn't really that great if it's main use is running 32-bit applications.

> You dont have to compile your own. There are a lot of packages (64bit) and information on how to install the 32bit version (ones in my signature). Either way you end up with a 32bit package, because wine is a 32bit compatibility layer.
This is an example of someone making a mountain out of a mole hill.

yeah, i saw the one in your signature. sudo apt-get install wine after adding the repository seems a lot easier ;)

> If your only concern is wine and WoW there will be very little extra setup involved in the 64bit version. Following a few well known howto's will have you up in no time. But..... Please consider Cedega. For the price of $15 dollars you will save yourself loads of head banging dealing with wine.

hahaha... lmao

---

### Post by DevilDux on 2007-03-16
Well, I have it downloaded and burnt.  Going to reboot my computer now and say good bye to Windows.  I went with Ubuntu 6.10 Edgy Eft, AMD64. I check back later to let yall know how it went.

---

### Post by DevilDux on 2007-03-17
Well I'm fully reinstalled. I work on setting up the rest of the stuff later.  Doing updates now.

*edit 1* Ok I am going to bed now, got interrupted for a bit, I am successfully updated. I did choose to install the Driver from the Restricted Repo for my video card though, as the default driver caused scrolling in Firefox to be jumpy.  (At least I believe that was the problem, as with the new driver it works flawlessly.)

---

### Post by Kilz on 2007-03-17
> **inCursorated said:**
> i don't want to get into a thread battle here Kilz, so i'm not going to reply here again... 
But your doing a good job of it, but you will learn, I dont let people spread FUD and lies.
> **inCursorated said:**
> sounds like the guy is looking to avoid complications... a 64-bit OS isn't really that great if it's main use is running 32-bit applications.
Thats just it, there is no such animal as a "easy , no setup required, "just works"" version of linux. If you think that the 32bit version is perfect and so easy. Why do we have [but this section]("http://www.ubuntuforums.org/forumdisplay.php?f=73"), [and this section]("http://www.ubuntuforums.org/forumdisplay.php?f=132"), [and this section]("http://www.ubuntuforums.org/forumdisplay.php?f=131") full of people having problems with the 32bit version?
Running 32bit applications? Exactly what 32bit applications? One of the whole 8 listed in the howto sticky? Ones that my easy scripts, simple 64 or automatix install?

> **inCursorated said:**
> yeah, i saw the one in your signature. sudo apt-get install wine after adding the repository seems a lot easier ;)
hahaha... lmao
Downloading a script , clicking on it and choosing "run in terminal" isnt easy?

---

### Post by Kilz on 2007-03-17
> **DevilDux said:**
> Well I'm fully reinstalled. I work on setting up the rest of the stuff later.  Doing updates now.

*edit 1* Ok I am going to bed now, got interrupted for a bit, I am successfully updated. I did choose to install the Driver from the Restricted Repo for my video card though, as the default driver caused scrolling in Firefox to be jumpy.  (At least I believe that was the problem, as with the new driver it works flawlessly.)

To get acceleration to play games you may need to install the proprietary driver from ATI. [Here is a good step by step howto that may help.]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.34.8_Driver_Manually")
[You may also find this WOW setup howto helpful.]("https://help.ubuntu.com/community/WorldofWarcraft")

---

### Post by DevilDux on 2007-03-17
So far so good, I have used the scripts and howtos you have linked here. I have Firefox32 With Java/Flash and such.  Wine installed, and I am running the WoW install now.  So far everything has went Extremely smooth.

*Edit 1* Jinxed my self, WoW installed fine, but errors out when I attemtp to run it.  I will do a bit more checking of Howto and Forum posts, and perhaps return here if I need help with it.

---

### Post by DevilDux on 2007-03-17
Ok I have got WoW running now,  I had to do a bit of work to get my 3d Rendering going  Had to add > Section "Extensions"
Option "Composite" "0"
EndSection

to my xorg.conf to make it work, as [I found in another thread]("http://ubuntuforums.org/showthread.php?t=292642") after I did that WoW ran fine, with one issue, some of the audio plays, but also static plays a bit too.  I am in the process of doing updates for WoW at the moment, but Ill go looking for some answers, though any help in the right direction would be apreciated in this matter.

---

### Post by manjo on 2007-03-18
Instead of wine, try vmware-player. Install all windows stuff under it. Lot better than messing around with wine etc. I have vmware-player install coz I need turbo-tax business around this time of the year.

---

### Post by lakersforce on 2007-03-19
My advise:

Use the generic 386 version of ubuntu.
Use wine.
For easy and best compatible installation of video drivers go [[COLOR="Blue"]here[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html").
For extensive guide on getting WoW installed, configured and tweaked for optimal performance go [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28world%29").

---

### Post by Kilz on 2007-03-19
> **manjo said:**
> Instead of wine, try vmware-player. Install all windows stuff under it. Lot better than messing around with wine etc. I have vmware-player install coz I need turbo-tax business around this time of the year.

Vmware is great for office applications. But it has a problem running games.

> **lakersforce said:**
> My advise:

Use the generic 386 version of ubuntu.
Use wine.
For easy and best compatible installation of video drivers go [[COLOR="Blue"]here[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html").
For extensive guide on getting WoW installed, configured and tweaked for optimal performance go [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28world%29").

Why on earth would he want to do that when he has everything almost done?

---

### Post by dptxp on 2007-03-19
Kilz, I fully agree with you that If you got a 64-bit system, use the 64-bit OS. I installed 64-bit on my ACER 5101 laptop, got scared by the Forum, downloaded the 32-bit iso, but did not install. I stuck to the 64-bit, fortunately there are some in this forum sticking to the 64-bit.
Most of the problems I see in the forum is not because of 64-bit OS. 32-bit has its own share of problems.
The 64 bit OS has to be used to grow.
I think that the beginner's team needs to put something on this as a sticky post. New users should not be misguided.

---

### Post by DevilDux on 2007-03-19
Well here I am again.  I got going pretty good but ended up running into a snag I couldnt get past.  Decided to reinstall with Xubuntu and take my time, and pay better attention to what I was doing, and hopefuly I will make it through this time. 

Oh yeah as a side note that snag that came up, while inside a building in WoW, I was fine, the moment I could get the slightest glimpse of outside the door, the textures would go haywire.  And anytime I added "SET gxApi "OpenGL"" to my config, WoW would crash imediatly when I attempted to load it.

---

### Post by Kilz on 2007-03-19
> **DevilDux said:**
> Well here I am again.  I got going pretty good but ended up running into a snag I couldnt get past.  Decided to reinstall with Xubuntu and take my time, and pay better attention to what I was doing, and hopefuly I will make it through this time. 

Oh yeah as a side note that snag that came up, while inside a building in WoW, I was fine, the moment I could get the slightest glimpse of outside the door, the textures would go haywire.  And anytime I added "SET gxApi "OpenGL"" to my config, WoW would crash imediatly when I attempted to load it.

Let me again suggest to try Cedega. The 30 day trial is free. Wine is not perfect on any version of Linux.

---

### Post by DevilDux on 2007-03-20
Well I am on to Kubuntu.  I am sticking with the 64bit version.  I believe I will stick with this one as so far,  it is the most aesteticly pleasing. Thank you everyone for the advice you have given me.

---

### Post by DevilDux on 2007-03-21
Well Finally WoW is installed and running perfectly.  Thanks again everyone for all the help.  I ended up on Kubuntu 64AMID with Wine 0.9.32 and used the Sidenet script from Kilz Wine tutorial.  I will worry about firefox32 and the plugins later, now I am off to see how well the mods for WoW work on this setup.

*edit* The mods installed perfectly fine with WoW.  I will do some Extensive "Testing" tonight and into the weekend.

---

