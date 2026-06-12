---
title: "Steam issue, &quot;Could not connect&quot;"
date: 2007-12-13
forum: Wine
---

### Post by purdticker on 2007-12-13
After following this tutorial:

> [http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/](http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/)

I get the following error when I try to log into steam:
> 
Could not connect to Steam network.
This could be due to a problem with your Internet connection, or with the Steam network.  Please visit [www.steampowered.com](www.steampowered.com) for more info.


I've searched online for this problem 

> 
[http://ubuntuforums.org/showthread.php?t=463291](http://ubuntuforums.org/showthread.php?t=463291)


However, this doesn't help me.

Has anyone had this problem?

---

### Post by Fred_E _krugar on 2007-12-14
Have you installed any Ip blockers or the such??

---

### Post by purdticker on 2007-12-14
Nope

---

### Post by Nzer24 on 2007-12-14
Yeah, I've had the same issue. it worked before a couple weeks ago, so I assume it's either a wine or steam update that's causing the problem. 

I tried reinstalling gecko and steam, but it did nothing. I know the server is fine because it connects from windows. I also removed the .blob files from the steam directory. That was reported to fix it in some cases, but it didn't work for me.

If I figure it out I'll tell you.

---

### Post by purdticker on 2007-12-14
Ya weird, I'm using ubuntu on both my laptop and my desktop, I can connect with my laptop!  I'll have to see which settings are different, and which versions I'm using.  I'll report more when I get home.

---

### Post by Nzer24 on 2007-12-14
Make sure not to update anything... that might be the problem.

---

### Post by purdticker on 2007-12-17
These are my laptop settings (which *can* connect to steam.

Wine Version: 0.9.50~winehq0~ubuntu~7.10-1

winecfg:

**Applications -> **
Windows Version: Windows 2000

**Graphics -> **
unchecked -> Allow DirectX apps to stop the mouse from leaving their area
checked -> Allow the window manager to control the windows.
unchecked -> Emulate a virtual desktop

**Audio ->** (note, I get this error when I click on this tab:
> fixme:jack:JACK_drvLoad error loading the jack library libjack.so.0, please install this library to use jack
checked -> ALSA Driver
unchecked -> OSS Driver



Everything else is default

---

### Post by blaise69 on 2008-01-22
I'm having trouble connecting to a game server once, the game (Team Fortress 2) successfully loads, has anyone else experienced this problem?

The connecting to server window will pop up, and the prograss bar will start moving, but usually one or two bars before it completes with sending client info, everything freezes up, I can't even use key combinations to quite out and have to reset.

I've tested creating my own game and this works successfully, I can get into whatever map and play around without any trouble or even performance issues, so I'm sure it's not a graphics or sound issue.

---

