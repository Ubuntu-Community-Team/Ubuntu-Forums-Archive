---
title: "[SOLVED] strange screen flashing, display completely locks up"
date: 2008-12-06
forum: x86 64-bit Users
---

### Post by LashSilence83 on 2008-12-06
So I've been doing a lot of searches and doing a bit of reading about this, but I really haven't seen anything very current about this particular problem: 

I am running intrepid 64 bit and I've been experiencing some very annoying problems while running compiz with the version 177 and 173 proprietary nvidia drivers. It happens very randomly and I have yet to find a definitive cause other than having 3d effects enabled. My screen will begin to very quickly flash and usually it will keep doing so until one of two things happens: 

1) the display will become garbled and lock up for about 1-2 minutes and then upon moving the cursor around everything will return to normal except at that point I've noticed that the system is using metacity instead of compiz and all effects are turned off. 

2) the display will become garbled and the entire system will lock up and I will be forced to either Ctrl+Alt+Backspace or sometimes it will become unresponsive to the point of me having to hard reset the machine. 

I have already tried changing refresh rates in compizconfig settings and also in the gnome screen resolution settings. I have also tried all manner of nvidia x server settings combinations. 

Like I've said I've seen a few threads about this issue but nothing exactly like this or with these circumstances. Plus most of the ones I saw were very old and had to do with the 16X.XX series of nvidia drivers. In case it helps any diagnosis, here are my main machine specs:
MSI k9a2 platinum mobo, Athlon X2 3.2ghz, 8GB ram, 8600GTS 512mb gpu, 1000w ultra X3 psu.   

Also, sorry if this is posted in the wrong category. I wasn't too sure if it had anything to do with the fact that I'm running a 64 bit ubuntu or not.

*whew* that was a lot of words. Thanks in advance to anyone who even reads this post in it's entirety. ;)

---

### Post by Melk79 on 2008-12-07
I've experienced similar issues to those you've explained.  I've been following this [thread]("http://ubuntuforums.org/showthread.php?t=832383&page=20") for now.  I thought it had to do with Flash since it generally happens to me when viewing Flash content, but I'm not sure.

In the meantime, this has been a neat approach to recovering that I didn't know about:
[http://en.wikipedia.org/wiki/Magic_SysRQ_Key](http://en.wikipedia.org/wiki/Magic_SysRQ_Key)

---

### Post by LashSilence83 on 2008-12-08
That is some highly interesting and valuable information. Thank you! :) On a side note: I found out about the 180 beta nvidia driver and implemented it yesterday. Since then, I've had only one problem with the screen flashing and the graphics getting messed up. Only difference was that it didn't crash anything, it just turned my desktop effects completely off and made me use metacity instead. Even more interesting was that I just went and turned the effects back on and it's been running fine since then. It's either a fluke or a step in the right direction...  who knows?

---

### Post by LashSilence83 on 2008-12-27
OK, I'm updating this one because I've had consistently annoying issues with the nvidia drivers (even the 180 one) on my 64 bit intrepid system. I still can't enable anything that uses 3d acceleration (desktop effects) without suffering from the same old issues of the screen locking up. 
   The main difference the 180 driver made over the 17x series was that now when I experience the problem, I dont have to restart the system. It basically just turns off the 3d effects after a 2 minute pause in screen activity. I guess this is better, but still I don't understand what is wrong here. Could it be something hardware related or am I just completely unable to config this thing correctly? 

Also, yes I know that not having the effects enabled is nowhere in the same universe as something critical, but it would be nice on this higher end system (that was anything but cheap to build) to have some pretty eye candy :biggrin:

---

### Post by LashSilence83 on 2009-01-01
ok, I've reinstalled Intrepid 64 bit and I'm having the exact same problems even with the desktop effects turned off. I even tried to just watch a movie and about an hour in, the screen started flashing and became unresponsive, ultimately forcing me to hard restart the system. I seriously can't understand what the issue is here. I'm even getting the flashing when I use any screensaver that uses any sort of 3d graphics. I tried looking at x-session errors, and see much of anything in there of interest. Should I just get a new video card ? I'm at my wit's end with this one. It's rendering my expensive system useless for most multimedia use and even everyday use. In fact, the screen is beginning to flash while I write this. Please, if anyone could just provide any insight, I would be eternally grateful. 
[B]
yet another update:[/B] I just switched video cards with another system I have running 32-bit hardy and for some strange reason, everything is working fine on both systems. I'm truly confused now. The card that I was having issues with was an EVGA 8600 gts 512mb and I switched it out with a 7200 gs 256mb. I've even tried heavily taxing both cards in both systems and had no problems yet. Does this mean there is something within the 64 bit box that isn't playing nice with the 8600? Or, is that even all that likely considering the circumstances? Both of the systems in question have similar specs. Both are very recent MSI AMD mobo's with Athlon X2 procs, OCZ platinum ram(ran memtest on both today), and WD sata hdd's. I suppose the main difference in these two systems would be the video cards. The 8600 requires external power while the 7200 does not. Not sure how or why that would make much difference in this case, but I figure any extra info would help.

---

