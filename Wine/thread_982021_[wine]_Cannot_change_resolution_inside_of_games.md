---
title: "[wine] Cannot change resolution inside of games"
date: 2008-11-14
forum: Wine
---

### Post by bobulator on 2008-11-14
The problem I seem to be having is that inside of games which are running under wine I cannot change the game display resolution to anything other than the resolution of my desktop.

For example, Half Life 2 Deathmatch is affected by this problem. I can change the resolution outside of the game by using command line operators, but if I look in the options dialog inside of the game, the only resolution available is 1280x1024 (my screen resolution). 

This seems to be a wine problem rather than a application-specific one because other games (e.g. World Of Warcraft) are affected by this problem. I do know one workaround, that is to change the resolution of the screen to the resolution I want to play in, and then once the game has started up, I can change the resolution back to normal, but it would be far preferable to get rid of the problem at it's source.

Thanks,

---

### Post by cogadh on 2008-11-14
This is just a wild guess, but I believe that Wine passes resolution options on from the xorg.conf file, so in order for a game to be aware of the available resolutions, those resolutions have to be clearly defined in your xorg.conf. The current version of xorg.conf doesn't have to do that anymore (xorg is able to calculate the available resolutions on its own now), so they don't include specifically defined resolutions. You can still manually enter specific resolutions into your xorg.conf, so that might be a way to fix the issue.

Again, that is just a wild guess, so make sure you backup your existing xorg.conf before you decide to change anything.

---

### Post by bobulator on 2008-11-14
Thanks for the speedy reply, I'll try that and report anything I find.

---

### Post by bobulator on 2008-11-20
I've been trying to change the xorg.conf for several days now to no avail. Maybe a wine user could post their xorg.conf so I can compare?

---

