---
title: "Counter-strike Steam Using Wine?? Read Pleas!"
date: 2008-10-03
forum: Wine
---

### Post by saggitheman on 2008-10-03
I'm using Hardy Heron on my Dell Latitude D600. I have Wine but i don't know how to install CS Steam (1.6). Could some one pleas give me an answer were to download and instructions to install. Don't answer in an dificult way, easy pleas. I'm not so good with codes...

---

### Post by Espryon on 2008-10-03
look at [www.winehq.com](www.winehq.com) click ap db install wine and also if you dont have drivers for your video card install envyng , the instructions for both of these apps are on there websites 

envy ng - [http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html)

wine - [www.winehq.com](www.winehq.com) 

Wine - Wine is not an emulation 

i have cs source on my intrepid alpha 6 install and it works fine i play on every mapp also theres a special command for in the launch options in the steam app "launch options" i think its -dx 90

yw

---

### Post by Dark9204 on 2008-10-04
No, to play CS:S you must run it with the -dxlevel 81 tag.

But this guy runs CS 1.6, so there is no use for him to use that tag.

Saggitheman, use OpenGL when you play, it is set by default.

---

### Post by wineman on 2008-10-04
hello

here's the CS guide to linux.

COUNTER STRIKE ON LINUX:
================
tar -zxvf mozcontrol.tar.gz ~/.wine/drive_c/mozcontrol
# mozcontrol.tar.gz - google mozcontrol, it's transgaming's one
# [http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz](http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz)
# the tgz doesn't matter, tar.gz / tgz - just unzip it.
cd ~/.wine/drive_c/mozcontrol
regsvr32 mozctlx.dll
regsvr32 COMDLG32.OCX
# the next 5 files need to be downloaded, along with VB support
regsvr32 comctl32.ocx
regsvr32 mshtml.dll
regsvr32 mshtmled.dll
regsvr32 mscomct2.ocx
regsvr32 mscomctl.ocx		
#regedited it in 
# in HKCU/Software/wine/MSHTML: 
# String:[GeckoPath:"C:/Mozcontrol"])
# in HKCU/Software/wine/MSHTML/0.1.0: 
# String: [GeckoPath:"C:/Mozcontrol"])
#============
# ROUND 2
#============
#Copy these from the XP distro (home, pro, etc.) to the c:\mozcontrol folder
regsvr32 shdocvw
regsvr32 olepro32
regsvr32 dhtmled.ocx
regsvr32 urlmon.dll
regsvr32 hhctrl.ocx
regsvr32 oleaut32
#winecfg'd the following:
# the format is :
# dll (status) --> click on them, click edit.
comctl32.ocx (native)
comdlg32.ocx (native)
mscomctl.ocx (native)
mshtml (native)
mshtmled (native,builtin)
olepro32(native,builtin)
shdocvw(native,builtin)

#ran cs: IT WORKS!!! YAY.......

Got this script from my machine. I've used it sixty times, and never had any issues.
Good luck guys

---

### Post by wineman on 2008-10-04
o ya and you need to download the msttcorefonts-offline package ([http://ubuntuforums.org/showthread.php?t=646598](http://ubuntuforums.org/showthread.php?t=646598)) and tahoma font.

---

### Post by Dark9204 on 2008-10-04
No no, wait a sec, Wineman, what the hell are you doing?

To install steam, move the steam installer to your home directory and run: wine start SteamInstall.msi from terminal.

After you have logged in, wine will ask you to install gecko, just click install and it will download and install it for you.

Then just download the game and play it.

What the hell are you doing wineman? There is absolutely no use what so ever to do any of the fings you have done

In Wine App DB i found this: Solved the missing text problem with sudo apt-get install msttcorefonts Enjoy.

---

### Post by saggitheman on 2008-10-06
Thanks Dark9204 guy. I will try it in a few days... Hope it will work. But should i just download the game from anywere or? (ThePirateBay)? Anyone knows?

---

### Post by wineman on 2009-03-24
> **Dark9204 said:**
> No no, wait a sec, Wineman, what the hell are you doing?

To install steam, move the steam installer to your home directory and run: wine start SteamInstall.msi from terminal.


dude no disrespect but this is the way that i did it NON-STEAMED. At the time that i posted this my gaming PC wasn't linked to ADSL, and so i developed this method to get CS1.6 to run OFFLINE. NO STEAMING OR DOWNLOADING (except for the .dlls).

No disrespect, steam installing is the easiest method. Although i like to make my programs work the HARD way, so that others can sit back and relax instead of worrying because the easy way didn't work.

The problem most of the time is that the notorious "This program requires Gecko support" window sometimes doesn't work, and so manual tweaking is sometimes required. (i'm refering to pre-8.04 ubuntu)

But try it man, before you diss it and make a fool of yourself. You might even find that it is the first time round.

Good luck:D

---

