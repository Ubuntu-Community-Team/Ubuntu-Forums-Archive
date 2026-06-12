---
title: "[SOLVED] Mouse Sensitivity in Fixed Resolution Games"
date: 2008-07-12
forum: Wine
---

### Post by mriedel on 2008-07-12
Games like StarCraft run at a fixed resolution (640x480 in SC's case). That (at least I think it's that) messes up mouse sensitivity. Is there a way to tune it on a per-application basis?

If not, could I run the game on a different/new X display and tweak the sensitivity for that display?

---

### Post by mriedel on 2008-07-13
bump

---

### Post by mriedel on 2008-07-15
bump

---

### Post by hoagtech on 2008-07-15
Have you tried running starcraft in a previous version of wine? i know that sounds stupid, but sometimes the simplest things are the problem:)

---

### Post by mriedel on 2008-07-16
Downgrading wine would mean going back to a bugged StarCraft. Ctrl+Click wasn't supported until a short while ago, for example. Plus I've been trying this for a while and I'm pretty certain it's been the same for older versions.

---

### Post by Brebs on 2008-07-16
Use a script, e.g.:
```
#!/bin/bash

export DISPLAY=:1
export WINEPREFIX=$HOME/.wine-ravenshield
export WINEDEBUG="fixme-all,err-all"

# From http://bugs.winehq.org/show_bug.cgi?id=6971
export WINEFORCEMOUSEWARP=yes

dir="$WINEPREFIX/drive_c/Program Files/Red Storm Entertainment/RavenShield"

# Alternative is xlaunch
xauth add  :1 . `mcookie`
cd "${dir}" && xinit /usr/bin/wine system/ravenshield mod=IronWrath -- :1 &
sleep 5

# Slow down mouse
xset m 1/3 1 -display :1

# Turn nvidia vsync on
nvclock -a vsync=1 -x :1
```

---

### Post by mriedel on 2008-07-16
I won't do it exactly this way because running stuff on an additional x display makes one of the displays grab the soundcard for me, but xset is just what i was looking for. Thanks a lot.

Just gonna make a script like

```
xset m 1/2 1
padsp wine ...
xset m 2 2
```

---

### Post by kdorf on 2008-07-16
What do you mean by "grab the soundcard?"

X servers have nothing to do at all with sound cards, period. It is the programs that run which utilize the sound card (through OSS, ALSA, PulseAudio, or other means).

---

### Post by mriedel on 2008-07-17
Well, it shouldn't. Fact is though that I can hear sound from exactly one X display at a time whereas sound works fine for a multitude of applications on the same display.

---

### Post by h4mx0r on 2008-07-18
To totally pwn at fps games I use these settings in /etc/X11/xorg.conf

	Option "RenderAccel" "True"
	Option "ConnectedMonitor" "CRT"
	Horizsync	31-61
	VertRefresh	56-75
	Option	    "ZAxisMapping" "4 5 6 7"
        Option      "Resolution" "500"

Please adjust them accordingly to your system and preferences. [http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html) for more info. You might also consider using a different mouse driver. (I've been working on multi pointer custom xorg for my dual monitors :D)

---

