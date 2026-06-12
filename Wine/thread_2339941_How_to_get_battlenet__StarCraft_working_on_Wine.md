---
title: "How to get battlenet / StarCraft working on Wine?"
date: 2016-10-14
forum: Wine
---

### Post by jcllings on 2016-10-14
I've seen and tried several HOWTO's but I'm not able to get it to the point where I can launch StarCraft. The existence of these howtos implies that somebody has it working. 
Anybody willing to lend a hand? I can go through it again this evening. If you have a method that you prefer and/or are most familiar with, I can start with that if you let me know what it is.

---

### Post by jcllings on 2016-10-15
Woohoo! I got SC working.  Basically what you do is install BattleNet using PlayOnLinux. Oh but just BattleNet. Not StarCraft yet. Change to the latest version of Wine available. 1.9.15 at the time of this writing. Set your video memory size, 1024 in my case. Then you select the Wine tab in the PlayOnLinux Configuration window. Click the Configure Wine button. Select the libraries tab and add the libraries listed here: 


[LIST]
[*]api-ms-win-crt-runtime-l1-1-0 
[*]api-ms-win-crt-stdio-l1-1-0 
[*]api-ms-win-crt-math-l1-1-0 
[*]ucrtbase 
[*]vcruntime140 
[/LIST]

Apparently these are a work-around for this issue:  [https://bugs.winehq.org/show_bug.cgi?id=40905](https://bugs.winehq.org/show_bug.cgi?id=40905)
THEN you install StarCraft. I have noticed that it doesn't go full screen but I think that is because I'm using Synergy right now. I already know StarCraft on Wine hates Synergy.

---

### Post by jcllings on 2016-10-15
Alrighty there's an additional issue but it's an easy fix. You have to open the wine config and in the Graphics tab uncheck everything.  You'll notice that the check boxes that are checked by default on this screen all pertain to the emulators control of the window.

---

