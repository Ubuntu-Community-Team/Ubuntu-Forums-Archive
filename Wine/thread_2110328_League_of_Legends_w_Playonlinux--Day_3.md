---
title: "League of Legends w/ Playonlinux--Day 3"
date: 2013-01-29
forum: Wine
---

### Post by Sequoia Bird on 2013-01-29
I know this question comes up frequently. I've been reading forums and working on it for three days now, with little to no success. Time to bring in the experts.

I've tried this:
[http://www.playonlinux.com/en/topic-8738-Test_How_to_install_League_of_Legends.html](http://www.playonlinux.com/en/topic-8738-Test_How_to_install_League_of_Legends.html)

...7 times, changing variables based on other forum suggestions. It ran once on Win XP, Wine v1.5.22 . but I couldn't launch it from the PlayonLinux GUI. I had to navigate through ```
~/PlayOnLinux's virtual drives/LoL/drive_c/Riot Games/League of Legends
``` to get it to launch. Otherwise, I got a message along the lines of "Playonlinux has encountered a serious error and needs to close." I assume making a shortcut to this isn't difficult, but it may be part of a larger problem.

During installation no. 6, I got the game running with this issue:
[http://www.playonlinux.com/en/issue-1364.html](http://www.playonlinux.com/en/issue-1364.html)

I went through this page:
[http://www.playonlinux.com/en/topic-9095-League_of_Legends__TexturesFonts_missing.html](http://www.playonlinux.com/en/topic-9095-League_of_Legends__TexturesFonts_missing.html)

With no luck. It seems like LoL was running without anything to do with playonlinux, which I assume is what 
```
force_s3tc_enable=true playonlinux 
```is supposed to affect.

I have a feeling that installing the (proprietary) FGLRX graphics drivers might be a step in the right direction, but they do not work in 12.10.

With the current installation, I can attempt to launch the game through PlayonLinux, but it pops up with the league of legends starting banner which stays frozen and stuck in the middle of the screen until I log out/in again. 

This (combined with a temperamental Ubuntu install on my own computer) has caused me to pull the Monday Morning Classic on a Tuesday evening; I put OJ in my corn flakes.  Things are getting kind of grim...

Thanks for the help, please ask any questions you have.

(12.10 32 bit on an HP DV6)

---

