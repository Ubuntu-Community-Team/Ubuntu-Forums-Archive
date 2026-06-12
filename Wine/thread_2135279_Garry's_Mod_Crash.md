---
title: "Garry's Mod Crash"
date: 2013-04-13
forum: Wine
---

### Post by Sandvichio on 2013-04-13
I've installed steam through PlayOnLinux, but Garry's mod does not work for me. Once I click "play" my computer's resolution nearly halves and my screen zooms in practically 200%. I assume this would be caused by Garry's Mod's resolution. It flickers between my desktop and Garry's Mod once or twice before going to the blue loading screen for Garry's Mod 13. It loads for about 10 seconds, then crashes. Once it crashes, my resolution stays messed up, and I need to restart my computer.

I am using Ubuntu 12.10.
I have already tried using the launch option: -something 81 (I don't remember the exact command)

I'm not sure if installing steam with wine itself will fix anything, but considering how everything else works fine through PlayOnLinux, I'm not sure if this would help.

Most of the windows games I have installed through wine seem to work fine, but garry's mod seems to be the only one to completely not work. What can I do to fix this?

---

### Post by Sandvichio on 2013-04-14
I was able to play G-Mod with no lag at all by uninstalling PlayOnLinux's steam, and using wine to download steam via steampowered.com and selecting "windows". It lagged horribly,  but as soon as I used -dxlevel 81 everything was perfect.

---

