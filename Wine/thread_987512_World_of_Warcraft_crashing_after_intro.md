---
title: "World of Warcraft crashing after intro"
date: 2008-11-19
forum: Wine
---

### Post by Gary13579 on 2008-11-19
WoW downloaded and installed fine under Wine, but it crashes after the opening intros.

My notebook is a Thinkpad X31 (I LOOOVE this thing by the way, it's fast enough, amazing battery life, pretty small/thin, and built like a truck. I wouldn't be worried if I dropped it tbqh). It has a 1.4 GHz Pentium M (Pentium M chips are fast, faster than Pentium 4, so that's not the problem), 1 GB RAM, and an ATI Mobility Radeon 7000 graphics chip with 16 MB VRAM. [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000)


Here's the terminal output:

> gary@fluffy:~$ wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c250000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c250000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x32ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ece0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f05c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f540,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f05c,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x20028, 0x1390c8): stub

Doesn't appear to be any errors, it just closes after the intros, or if I try to skip them.

Ubuntu 8.10, wine 1.1.8.

---

### Post by Gary13579 on 2008-11-19
Up.

---

### Post by Gary13579 on 2008-11-20
After upgrading to WotLK, it's even worse. WoW won't even start, it just returns to the shell after a few seconds.

---

### Post by Sammi on 2008-11-20
Try the troubleshooting section from the community WoW/Wine guide: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Gary13579 on 2008-12-14
Up, and I've only tried those like 500 times.

---

### Post by hikaricore on 2008-12-14
Just curious, try this from a console and post the result here:

> glxinfo | grep rendering

Also have you tried not running in OpenGL mode?  I seem to remember some ATI users
having trouble when running in this mode.  Also be sure you have properly installed
the video drivers for your card and if you can try a few 3d games from the repos to
see if hardware rendering is working properly for those titles.

---

### Post by Gary13579 on 2008-12-14
direct rendering is enabled, yes.

gary@fluffy:~$ glxinfo | grep rendering
direct rendering: Yes

I've tried OpenGL and D3D in just about every single possible wine configuration I can manage. OpenGL is much faster at playing the intro, but both crash after that. Here is my current Config.wtf:

```
SET ffxDeath "0"
SET ffxGlow "0"
SET gxApi "OpenGL"
SET M2UseShaders "0"
```

The ONLY possible solution I have found is here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329) . Search for "ubuntulistener". He had the exact same problem, but got it working. Same ThinkPad as well. I've been trying to track him down...

---

### Post by hikaricore on 2008-12-14
Perhaps we try disabling the intro?

expansionMovie "0"

---

### Post by Gary13579 on 2008-12-14
Does nothing, it still even plays the intro, then exits afterwards.

---

### Post by hikaricore on 2008-12-14
They may have changed the config setting in woltk, I don't know the new one.

Look in your conf file for any other line with the word movie in it, perhaps wotlkmovie or something like that and set it to 0.

---

### Post by Gary13579 on 2008-12-14
*sighs*

SET movie "0"
SET readTOS "1"
SET readEULA "1"

Copied that from my Windows desktop install, yet it still plays the intro. It does not play it on my desktop.

Edit: Does Wine cache any files?

---

### Post by hikaricore on 2008-12-14
Not in the way I think you're imagining.

There should be no reason for it to be playing the movie at this point.
Sorry I don't know how else to help. :/

---

### Post by Gary13579 on 2008-12-14
Up.

---

### Post by Gary13579 on 2008-12-20
Up.

---

### Post by Amof on 2008-12-20
Did you try outright deleting the WTF folder? Was this a new install or a copy from a windows system?

---

### Post by jinxi on 2008-12-21
I had some problem to.
If I login before the lich king dragon stands and spits fire, it's OK.
I think it has something to do, with the new grafik from lich king... 
Just try to login very fast ;)

---

### Post by Gary13579 on 2008-12-24
> **Amof said:**
> Did you try outright deleting the WTF folder? Was this a new install or a copy from a windows system?

New install.

> **jinxi said:**
> I had some problem to.
If I login before the lich king dragon stands and spits fire, it's OK.
I think it has something to do, with the new grafik from lich king... 
Just try to login very fast ;)

If you could READ, you'd know the login screen doesn't show up at all, and that this existed before WotLK. But you know, thanks for the useless spam.

---

### Post by Zargoon on 2008-12-24
What ATI driver are you using?  Even the new ATI drivers have had problems.  If you aren't running 8.12 I would suggest upgrading to it.  I like this guide a lot if you need some help: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

This dirver currently works on my system with my ATI card, although it's not the same as yours.

---

### Post by Zargoon on 2008-12-24
Also have you added the OpenGL disabledextensions tweak.  For me it had a MASSIVE increase in performace.  As in going from 8 fps at 800x600 rez to 30 fps at 1280x1024 rez.

---

### Post by Gary13579 on 2008-12-29
> **Zargoon said:**
> What ATI driver are you using?  Even the new ATI drivers have had problems.  If you aren't running 8.12 I would suggest upgrading to it.  I like this guide a lot if you need some help: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

This dirver currently works on my system with my ATI card, although it's not the same as yours.

I've tried running fglrx a couple times, just did again and spent an hour trying to get X to work properly again.

Every time I try and install it, it segfaults on aticonfig --initial -f, and X breaks until I completely remove fglrx.

Anyone else want to take a shot at it :/ ?

---

### Post by EnderEcho on 2009-01-02
Have you tried running it in a virtual desktop? If so what rez?

---

### Post by utnubuuser on 2009-01-04
Hey Gary -- I noticed you answered "new install" to the question about whether you copied a windows install or did a new install.

I never tried that route on my X31 because my machines are running Ubuntu exclusively.  I do remember reading in some of the how-to's that copying all the folders from a Windows install was the way to go.
Don't suppose you tried that route?

---

### Post by Gary13579 on 2009-01-05
> **EnderEcho said:**
> Have you tried running it in a virtual desktop? If so what rez?

As said in the first post, notebook is a 1.4 GHz 1 GB RAM 16 MB VRAM machine. Virtual machines are hardly a solution, when the game would barely run on the normal PC.

> **utnubuuser said:**
> Hey Gary -- I noticed you answered "new install" to the question about whether you copied a windows install or did a new install.

I never tried that route on my X31 because my machines are running Ubuntu exclusively.  I do remember reading in some of the how-to's that copying all the folders from a Windows install was the way to go.
Don't suppose you tried that route?

This should be unrelated, as it's installed fine on my desktop via Wine. I don't have a Windows machine any more, so can't copy from there.

---

### Post by Eviljim on 2009-01-06
Im pretty sure that this card wont be able to support the game unfortunatley. Here is some info I found for you.

1. Your card is not supported by the ATi proprietary driver therefore you can only use the fglrx driver.

2.[http://www.thinkwiki.org/wiki/Fglrx]("http://www.thinkwiki.org/wiki/Fglrx")

Support for cards earlier than 9200 stopped at version 8.29.6.

It also states that the 7500 card is not supported at all - may be related as yours is in the same series.

3.Min spec for WoW from [http://www.wow-europe.com/en/requirements/technical.html]("http://www.wow-europe.com/en/requirements/technical.html")

states ATi 7200 with **32MB VRAM**, on a windows box, which should be fairly similar requirements for a linux/wine box.


Hope that is of use to you.

---

### Post by Gary13579 on 2009-01-11
> **Eviljim said:**
> Im pretty sure that this card wont be able to support the game unfortunatley. Here is some info I found for you.

1. Your card is not supported by the ATi proprietary driver therefore you can only use the fglrx driver.

2.[http://www.thinkwiki.org/wiki/Fglrx]("http://www.thinkwiki.org/wiki/Fglrx")

Support for cards earlier than 9200 stopped at version 8.29.6.

It also states that the 7500 card is not supported at all - may be related as yours is in the same series.

3.Min spec for WoW from [http://www.wow-europe.com/en/requirements/technical.html]("http://www.wow-europe.com/en/requirements/technical.html")

states ATi 7200 with **32MB VRAM**, on a windows box, which should be fairly similar requirements for a linux/wine box.


Hope that is of use to you.

I appreciate your research, but the game installs and launches fine in Windows. Yes, it is not enough VRAM for the minimum requirements, but it WILL run on it.

Just not in Wine...

---

### Post by hikaricore on 2009-01-11
While your hardware may be able to offload half of the demand on ***dows using DirectX, it may not be able to properly do the same under WINE using OpenGL.
This may be an issue of hardware under Linux specifically due in part to the manufacturer dropping the card from their driver support.

Just because something works in ***dows does not mean it will work in Linux, especially with dodgy hardware as the case may be.

You may be able to accomplish something more using the lowest resolution and disabling all effects in the Config.wtf file as well as doing various WoW related performance tweaks under WINE, however you may not be able to get it running as well as it does on ***dows **ever**.

---

### Post by Juggercat on 2009-01-29
I was having a similar problem, Have you tried setting teh visual effects to none?

Thats what solved my problem, hope you good luck :D

---

### Post by johnl on 2009-01-30
I'm not sure if the entries in the Config.wtf are case sensitive or not, but I see the crash your are mentioning only when WoW is trying to run using DirectX.

Try also passing "-opengl" to WoW when you run it from the console.


Just a shot in the dark :)

---

