---
title: "TF2 Black Overlays"
date: 2008-06-08
forum: Wine
---

### Post by yekim on 2008-06-08
Hi all,

I did some searching on this issue, and seems some people have found similar problems while running Wine / Team Fortress 2 under DirectX 9.  I've tried changing to 81, but it did not help.  The problem I'm having is best seen in the screenshot below, in which all the overlays (names, health, ammo, etc. are black)

[http://bayimg.com/lajahAaBO](http://bayimg.com/lajahAaBO)

My launch command for Steam is below, but even when I launch it this way, in the "Video" options it lists DirectX 9 instead of 8.1.

env WINEPREFIX="/home/mike/.wine" wine "C:\Program Files\Steam\Steam.exe" -dxlevel 81

Any ideas? Thanks!

---

### Post by Fazer2 on 2008-06-08
You're doing it wrong ;-) You don't want to set this command to Steam, but to HL2.exe (because technically, TF2 is a Half-Life 2 mod).

You have run Steam, go to My games tab, right click on Team Fortress 2, Properties, Set launch options and type -dxlevel 81

Then run Team Fortress 2, set your video options, exit, delete what you've just typed in the launch options - this way your video settings won't reset each time you run the game.

---

### Post by yekim on 2008-06-08
Hi Fazer -- thanks for the tip.

Unfortunately I just tried that, and with the -dxlevel 81 switch, it does not even display the menu.  The entire screen is just black.  Any thoughts?

I'm going to try a few other dxlevels and see if any of them work.

---

### Post by L1nchp1N on 2008-06-08
I get this as well.  I set the -dxlevel 81 from within steam, so that TF2 starts with it.  Then when it goes blackscreen on me, I Alt-Tab a few times and it brings the screen back with the full menu.

Not an ideal fix, but a simple work around that is reasonably effective.

---

### Post by yekim on 2008-06-09
That's quite a strange fix indeed.

In any case I played around a bit more,and am now running WINE in Vista mode, with DirectX 81.

Still not perfect - the games in the My Games list take a good 45 seconds to show up after starting STEAM, and I've been seeing some really horrid black-screen crashes where my only recovery is to power-cycle (3 times in about 6 hours), but for the most part everything else is working.

Thanks for everyone's help!

---

