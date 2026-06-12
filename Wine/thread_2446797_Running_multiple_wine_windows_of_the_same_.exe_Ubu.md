---
title: "Running multiple wine windows of the same .exe Ubuntu 20.04"
date: 2020-07-07
forum: Wine
---

### Post by mariannagr1 on 2020-07-07
Alright, I managed to get my game running with wine (not supported). Now I am trying to figure out how to run multiple clients of the same game. ''New window'' minimizes existing window in a corner and I cannot restore it/freezes wine. Any help with that? Tried searching but no luck.
The game runs in fullscreen only, 800x600. So it occupies the entire (windowed) wine desktop. I want to be able to expand the wine desktop... I don't know if I make sence, I am new to this.
[https://pastebin.com/HhpPBRAi](https://pastebin.com/HhpPBRAi)

Is the problem: [COLOR=#333333][FONT=Consolas]0009:fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16 ?[/FONT][/COLOR]

---

### Post by mastablasta on 2020-07-07
in winecfg you can set the resolution of wine dekstop. 

in playonlinux it's found in *wine tab* in *configuration window*: [http://wiki.playonlinux.com/index.php/The_Configuration_Window](http://wiki.playonlinux.com/index.php/The_Configuration_Window)

> [h=3](1) - Configure Wine[/h][FONT=sans-serif]This opens **winecfg** in the selected virtual drive. This is where you can set the version of Windows for the virtual drive, as well as set the virtual desktop settings and disks reported to Wine. [/FONT]


winecfg information: [https://wiki.winehq.org/Winecfg](https://wiki.winehq.org/Winecfg)
or this one is good with pics: [https://linuxconfig.org/configuring-wine-with-winecfg](https://linuxconfig.org/configuring-wine-with-winecfg)

you will find settings in dekstop integration tab.


supported or not if it runs it's all good.

---

### Post by mariannagr1 on 2020-07-10
Thanks for your reply, mastablatsa. I have been on holiday and just came back.

I studied the guides you recommended and played around with various settings; however,  cannot seem to manage the settings I need. The game folder has a txt that specifies what mode you want the game to run. It only works with wine if the setting is FullScreen. If i change that to WindowScreen, the game just won't run. So I keep the setting in Full Screen and configure wine to treat the game as a virtual desktop, in 800x600 mode. Then the game runs just fine, in a wine window.
The issue is that I need to be able to open multiple clients of the same game, but the first client occupies the entire wine desktop (window). So, if I try to open a new window, the first one cashes at the bottom corner and I am unable to restore it. 
I don't know if I make sense... What I need is a big wine window-big as my desktop, that can fit multiple clients of the game in it. Do I need a VM?
Thanks!

---

### Post by mastablasta on 2020-07-11
ah i see what you want and also this is a multiplayer game. you need to run multiple applications within single prefix. you could tray to run the program (another client) form virtual desktop. however i am not sure if you could easilly switch between them. say you set virtual deskotp to be larger and then run inside it in widnowed mode with windows 800x600 in size.

see issues with that plan here: [https://forum.winehq.org/viewtopic.php?t=14002](https://forum.winehq.org/viewtopic.php?t=14002)

 yeah VM would be an easier choice in this case. what windows does this game need? Win98?

---

