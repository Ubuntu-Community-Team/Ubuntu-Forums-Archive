---
title: "HalfLife 2 based games crash at loading stage"
date: 2008-06-26
forum: Wine
---

### Post by soxs on 2008-06-26
Ok, all HL2 based steam games crash silently on loadingscreen. I've tried multiple things to get rid of it (novid, defining ram amount, resolution, dxlevel, ...)

After trying to make test report for appd to rate HL2 as garbage, the report was rejected, with the comment: I should disable pulse audio.

So I am here to ask anyone, what is required to simply run hl2 or hl2* games? I tried alsa and all the other stuff as wine driver/ubuntu driver..
I have no clue atm. Plx help

---

### Post by Cappy on 2008-06-26
This is probably not your problem but I was using ```
wine steam.exe -dxlevel 81
```
when I should have been launching the app directly with the command line or using

```
-dxlevel 81 -width 1680 -height 1050
```
in the game's Properties --> Launch Options

This guide seems to show how to set graphical options in an autoexec.cfg, maybe it will help:
[http://www.gotfrag.com/tf2/forums/thread/322476/](http://www.gotfrag.com/tf2/forums/thread/322476/)

---

### Post by soxs on 2008-06-28
That's what I am allready doing. I tried all options I could get my hands on, but I still only get the loading screen and a silent crash...

---

### Post by i speak in math on 2008-06-28
I had the same problem. No source games made it past the loading screen. 

Are you also using integrated Intel GPU (X3100 here)? It seems likely that it is a driver issue.

---

### Post by soxs on 2008-06-28
Card: RadeonHD 3870 Club3D 512MB
Driver: ati 8.4/8.5/8.6 test, none of them helped me out.

---

### Post by MechWarrior001 on 2008-06-28
Have you tried killing/ending your *pulseaudio* process in the *System Monitor *app?

---

### Post by soxs on 2008-06-28
> **MechWarrior001 said:**
> Have you tried killing/ending your *pulseaudio* process in the *System Monitor *app?

Yes, no change at all.

---

### Post by kingpoiuy on 2008-10-13
Mine was crashing because of the in-game community.  Turn off in-game community in steam and restart steam.

---

### Post by drelyn86 on 2008-11-16
I have a similar problem with similar hardware... was there ever a fix to this?

---

### Post by Ameneon on 2008-11-16
Something trivial that often is forgotten; if you haven't tried this already, try disabling compiz and then start the game to see if that does the trick. Did for me at any rate (without compiz and with dxlevel correctly made a world of difference).

To disable compiz: metacity --replace
To enable it again: compiz --replace

Or you can install the compiz fusion icon application which does this and much more, great little app.

---

### Post by drelyn86 on 2008-11-17
Nope, I usually disable compiz out of habit. 

I've always had this problem with wine and Source games though... it'll play for maybe like a minute, and then the screen freezes and my keyboard doesn't work (numlock & capslock keys don't even respond), so then I have to do a hard reboot. It's pretty annoying, and I'm beginning to think it's one out of many FGLRX issues. 

Off topic and personal, but I think they should just hurry up and port the Source games over to Linux. Gaming is the only thing holding many people over to Windows, unless you want to be stuck with a bunch of Quake clones. But then again, consoles are starting to look more appealing than any Windows games as well.

---

### Post by Brynster on 2008-11-17
I may be stating the obvious. But know ATI drivers are problematic, are you certain they are installed correctly?

---

### Post by Dizzle7677 on 2008-11-17
> **soxs said:**
> Ok, all HL2 based steam games crash silently on loadingscreen. I've tried multiple things to get rid of it (novid, defining ram amount, resolution, dxlevel, ...)

After trying to make test report for appd to rate HL2 as garbage, the report was rejected, with the comment: I should disable pulse audio.

So I am here to ask anyone, what is required to simply run hl2 or hl2* games? I tried alsa and all the other stuff as wine driver/ubuntu driver..
I have no clue atm. Plx help

In the terminal change to the Steam directory....Do 'wine Steam.exe (or maybe ./Steam.exe) -applauch (whatever the hl2/whatever game appid) is. It'll give you some output of any errors or things that are going wrong somewhere. Usually it's looking for something that isn't there and silently bombs out.

---

### Post by Skripka on 2008-11-17
Steam games MUST be run in DirectX 7 mode (IIRC) -as a result of the ATi cards/drivers.

---

### Post by Dizzle7677 on 2008-11-18
> **Skripka said:**
> Steam games MUST be run in DirectX 7 mode (IIRC) -as a result of the ATi cards/drivers.
Really? Now I remember why I don't use ATI.

---

### Post by drelyn86 on 2008-11-18
Just went ahead and switched back to dual-boot again...

---

### Post by Hadron Quark on 2008-12-07
> **kingpoiuy said:**
> Mine was crashing because of the in-game community.  Turn off in-game community in steam and restart steam.

To help googlers. this fixed it for me on Debian in conjunction with:

1) Installing Steam using

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

to install Steam.

and 

2) d3dx9 DLL

[http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_34](http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_34)

Which I copied to

~/.wine/drive_c/windows/system32/d3dx9_34.dll

And then created a DLL override for it in the libraries tab of the wine config interface.

keywords : Debian half life 2 wine d3d module not initializing in game community

Lots of other info about disabling shaders, turning sound down etc were red herrings.

Oh, and be sure to make sure your wine config is set up for Alsa on teh Audio tab.

NB : this is all with an NVidia card (8800GTS) using the Nvidia-glx package. If you opt for ATI then best of luck - their support and performance is poor in comparison to NVidia's in my opinion.

---

### Post by drelyn86 on 2008-12-08
> **Hadron Quark said:**
> 
NB : this is all with an NVidia card (8800GTS) using the Nvidia-glx package. If you opt for ATI then best of luck - their support and performance is poor in comparison to NVidia's in my opinion.

Ever since AMD bought ATI, the improvements have been huge. However, because of the bad reputation ATI's Linux drivers have received in the past, most Linux applications (including Wine) do not support ATI cards.

---

### Post by Skripka on 2008-12-08
> **drelyn86 said:**
> Ever since AMD bought ATI, the improvements have been huge. However, because of the bad reputation ATI's Linux drivers have received in the past, most Linux applications (including Wine) do not support ATI cards.

Not that long ago, people didn't think well of ATi windows drivers either.

....I remember the h*ll my brother went through trying to get Half Life 2 to work on an ATi card, when the game had recently came out.  After days of trying permutations of every single game loading preference in Steam, it worked (and I do mean days)....it took many beta-quality final releases of Windows drivers before HL2 finally just worked without dicking around with individual game preference commands.



ATi has a long history of less than stable working drivers.

---

