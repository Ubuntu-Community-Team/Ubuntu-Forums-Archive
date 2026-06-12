---
title: "Inexplicable Counter-Strike Crashes"
date: 2008-05-15
forum: Wine
---

### Post by Burstaholic on 2008-05-15
I am having a very irritating issue with CS in WINE. After the first install, it worked beautifully, for about five minutes. Then it crashed. Hardcore. Had to power off the computer. 

This seems to happen every time I run it, at completely random intervals. The last test, just after yesterday's WINE update, lasted for a full hour before crashing. After the reboot, it would not play for more than a few seconds.

This is an extremely frustrating bug, thank you in advance for any help you can give.

---

### Post by Brynster on 2008-05-16
can we have some hardware details please.

---

### Post by Burstaholic on 2008-05-17
Ok, hardware details. I was worried I wasn't going to get any replies for a while there O.o.

First, it better not be an overheating problem. The entire guts are brand new. Also, it has no such issues in Windows.

I'm running onboard graphics graphics ATI x1200, with the default drivers Ubuntu downloaded. Same for sound: pure onboard, no separate card. AMD64 4200 2.2 ghz processor, gig of ram.

---

### Post by Muffinabus on 2008-05-17
Same thing for me, though I've never made it past 5 seconds.  Sometimes I just have to alt-tab and close the program, but most of the time I have to do a hard reboot and hold down the power button.  The whole operating system becomes unresponsive.  I have tried the game in quite a few settings as well.  Forcing DX8 with all settings at low had absolutely no effect on the problem whatsoever, it crashed like normal.

My hardware includes:
Pentium 4 at 2.8 Ghz
2 GB PC 3200 ram
ATI 1950GT

Also not an overheating problem, Windows runs the game perfectly, Ubuntu and Wine does not.  I have the latest ATI drivers as well.

Also, it's not an issue with ATI cards, as I have seen someone with a Nvidia card reporting the same exact problem.

---

### Post by YokoZar on 2008-05-17
This isn't a Wine bug - crashing the entire system is something Wine shouldn't be able to do as a user-level application.  Rather, Wine is just exposing a much deeper issue with your system, likely in your video drivers or even the hardware itself.

So, don't worry about "fixing Wine" here - the problem lies elsewhere

---

### Post by Burstaholic on 2008-05-26
Very interesting. Any ideas how I might go about finding what this underlying issue is?

---

### Post by Muffinabus on 2008-05-27
> **YokoZar said:**
> This isn't a Wine bug - crashing the entire system is something Wine shouldn't be able to do as a user-level application.  Rather, Wine is just exposing a much deeper issue with your system, likely in your video drivers or even the hardware itself.

So, don't worry about "fixing Wine" here - the problem lies elsewhere

I also find this quite interesting.  I know 100% that it's not a hardware issue on my end and I am fairly certain I have my drivers installed correctly.  I would really like to know what you think the problem is.  If Wine can't crash my computer as a user level app, then why is it doing so?  Is this a flaw with Ubuntu?  As I have heard previous versions of the OS were able to actually run this game.

---

### Post by jmesquita on 2008-06-08
Has anyone solved this problem? I am assuming we are talking about CS 1.6. I have the same problem with my system at a very different system configuration. Here is my setup:

** Hardware Settings **

Intel MOBO + P4 Core 2 Duo
Video Card: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

** Software Settings **

Wine Version: 1.0-rc4 (.deb downloaded from wine's official repo)
```

glxinfo | grep direct
direct rendering: Yes

```

Things I tried with Wine: Setting OSS as sound driver and running as virtual desktop

Another interesting point is that I found out that the problem only happens running the game with OpenGL. D3D runs fine, but too slow. Only solution for now has been running the game with software configuration on the game (not sure what that uses) but its been hard to do great with that bad graphic quality.

My suggestion is, can we involve someone from the wine community on this? I am not even sure on how to get more information since my system always halts completely.

Thanks,

Mesquita

---

### Post by karth on 2008-06-09
I had hard lockups when trying to play CS:S in WinXP mode.
Setting "Win98" mode on hl2.exe in winecfg stopped the lockups.

---

### Post by jmesquita on 2008-06-09
No luck here. I still get those weird freezes at random times.

I must say that we are talking about cs1.5 here, meaning that it uses hl.exe, not hl2.exe.

M.

---

### Post by RESID3NT on 2008-06-09
is it the steam version?

---

### Post by jmesquita on 2008-06-09
Yes, it is. In Brazil, for all servers I know with low latency, we have to have Steam to play online.

---

### Post by jmesquita on 2008-06-12
I dont mean to be pushy or anything, but is anyone else having this? If not, what am I doing wrong?

Regards,

Mesquita

---

### Post by karth on 2008-06-12
I read you found the D3D mode too slow to be playable (previous page)

Did you try to force the dx 8.1 mode? To achieve this, open Steam, then right click on your game and go to properties, and then press "Launch commands" or something like that (not sure, since I use the french version)

You'll see a blank text field, you'd just have to type "-dxlevel 81", minus the quotes.

DX9 under wine is often considered too slow, and DX8.1 often speeds up the games a lot.

---

### Post by jmesquita on 2008-06-21
I have finally solved this problem. Not the good way tho. Seems like there was something wrong with the intel video driver because I changed the card to a Nvidia and now all works smooth.

Thanks a lot,

Mesquita

---

### Post by mihaid on 2009-03-26
this seems to work for me :)

---

### Post by skateracl on 2010-05-05
I have same problem.  My counter-strike crashes, I have a dell 8400 3.2ghz, 4gb ram, 256mb nvidia 8600 pci express.  I used latest nvidia drivers and cs freezes in 5-30 min.  I tried using older drivers, update bios, same problem.  Can't seem to find the source of this problem, also crashes when i use a torrent program called vuze.  The pc will freeze and i have to hold the power button and restart.

---

### Post by beastrace91 on 2010-05-06
> **skateracl said:**
> I have same problem.  My counter-strike crashes, I have a dell 8400 3.2ghz, 4gb ram, 256mb nvidia 8600 pci express.  I used latest nvidia drivers and cs freezes in 5-30 min.  I tried using older drivers, update bios, same problem.  Can't seem to find the source of this problem, also crashes when i use a torrent program called vuze.  The pc will freeze and i have to hold the power button and restart.

[img]http://www.osnn.net/attachments/green-room/3923d1094252491-osnn-irc-channel-irc-freenode-net-holythreadresbatman.jpg[/img]

What Wine version? If you aren't using the latest try upgrading.

~Jeff

---

