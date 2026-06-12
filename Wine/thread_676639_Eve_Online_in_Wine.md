---
title: "Eve Online in Wine"
date: 2008-01-24
forum: Wine
---

### Post by ClintonEv on 2008-01-24
I have read multiple forums and threads and still cannot figure out how to get EvE working in wine or the regular linux version. Can anyone help me out? I have Wine version 9.5, Ubuntu 7.10.

When I run Eve in Wine i login in, it loads the stuff it needs to, but it doesnt leave the login screen.

When I run the regular linux version I can login but it closes at the character selection screen.

For wine, I have already moved the arial files where they need to be. It is running in Windows XP. The audio is set for OSS.

I can't find anything else to do.

---

### Post by stuart.crouch on 2008-01-24
For wine - 

Keep an eye on this thread.  People far smarter than us are constantly messing with eve and wine to see how best to make them gel together.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9971](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9971)

From that link, this sounds like you....

If Eve crashes/hangs after the character selection you need to add "voiceenabled=0" to ~/.wine/drive_c/windows/profiles/username/Local Settings/Application Data/CCP/EVE/settings/prefs.ini. This is needed if you have a voice enabled account or try to test on Singularity when voice is enabled there.

For the cedega wrapped client

[http://support.eve-online.com/Pages/KB/Browse.aspx?categoryID=92&language=EN](http://support.eve-online.com/Pages/KB/Browse.aspx?categoryID=92&language=EN) - All support topics
[http://support.eve-online.com/Pages/KB/Article.aspx?id=402](http://support.eve-online.com/Pages/KB/Article.aspx?id=402) - Maybe worth trying this, doesnt sound like your problem though

Also, have you got 3d acceleration (outside of wine) working correctly?

Im going to try and get eve up and running in WINE as I want to check out the premium content.  I wont be using the cedega wrapped client as this is the old, ugly graphics version.

---

### Post by ClintonEv on 2008-01-24
Yeah I've tried everything you said and I have been to that forum and tried that too, but it still doesnt work.

About the 3d working   I typed glxinfo | grep rendering into the terminal and it said  direct rendering: Yes  as for configured correctly i dunno.

Any other Ideas?

---

### Post by buntunub on 2008-01-24
Good luck with this bud. I have been hacking at this since the Premium content was released and still most things dont work properly. However, the Official Linux Client on CCP's website works flawlessly, out of the box. As with all things wine = hit or miss.

---

### Post by ClintonEv on 2008-01-25
I am having problems with the Official linux version too.

---

### Post by stuart.crouch on 2008-01-26
OK. I just downloaded, installed and ran EVE premium using wine 0.9.53

It all seems to work. The intro screen is a bit glitchy (effects around the planet)  but the game itself plays fine. I didnt see any glitches, but Im not sure where I should be looking. All the ships and effects appeared and worked fine.

The only thing I can suggest is the equivalent of re-install windows. 
Remove wine, delete your ~/.wine directory, re-install wine, re-install EVE (premium)

If you want to use the cedega wrapped client I suggest contacting CCP for support and see if they know whats going on.

---

### Post by ClintonEv on 2008-01-26
That depends on if your computer is better than mine  I am only running an Intel Graphics Media Accelerator 950 for video. But the thing i dont get, i used to have windows vista on this machine, but then i clean installed ubuntu without changing any hardware. I used to run eve on vista just fine.

---

### Post by lilbluegremlin on 2008-01-26
i am also having the same problem as ClintonEV
here are my hardware stats:

cpu: AMD Athlon(tm)
cpu_ghz: 1.09
memory: 1011
videocard_manufacturer: ATI Technologies Inc.
videocard_type: Radeon X1950 Series
videocard_ram: 256
agp_aperture_size: N/A
videocard_driver_version: 2.0.6747 (8.40.4)
soundcard: Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xb400, irq 2
soundcard_driver: ALSA Version 1.0.13
machine_bitness: 32
kernel: 2.6.20-16-generic
x_version: Xorg Version 7.2.0
distro: Debian 4.0
GUI version: eve-000066

i have tried using wine and just the linux client and have gotten farther they the Linux client. 
i have tried reinstalling eve and using their debug feature on the eve online config. but it does not output any info.
anyone have anymore help on this?

---

### Post by stuart.crouch on 2008-01-27
Eve was written for windows,so you'd expect it to run flawlessly there.
Wine is an interpreter, it reads any calls and figures out how to make linux do them.  If a call hasn't been written in wine, then it wont work.

Its like running your diesel car on cooking oil, it will work, but your milage may vary coz thats not what the oil was meant for ;)

Im not sure whats going on with your machines I'm afraid.  Testing with the wine version (go to ccp/cedega for support with thier client) - 
Do you hear sound when the screen goes blank?
Do you have compiz installed? If so, maybe the graphics card cant do two lots of 3d and you should try turning it off.

The ATI one should work if you've got the 3d drivers installed.

---

