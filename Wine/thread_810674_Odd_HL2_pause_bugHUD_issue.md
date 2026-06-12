---
title: "Odd HL2 pause bug/HUD issue"
date: 2008-05-28
forum: Wine
---

### Post by lckeeper1 on 2008-05-28
Hey all. First a quick tech spec overview. I upgraded to the latest wine (1.0-rc2) and am running on 8.04 64bit. I have a strange bug with Half life 2 when I first log in. Starting the game is flawless, but as soon as I load and attempt to press any key (W, space, anything), the game pauses. The only way to get out is to hit ESC and click resume game.

I don't mind doing that at all. A small price to pay in my mind. The annoying part is once I do that, the hud is out of whack, and I'm not able to restore it properly.

The aux power indicator and ammo display are horribly out of position, so much so that I can't see my ammo at all. The game itself stills plays quite well, but this is just an annoying bug I can't seem to fix.

If anyone has a suggestion, please share. Thanks a bunch!

---

### Post by cogadh on 2008-05-28
I get that same odd pause bug, I think it was introduced with one of the RCs. I don't know what causes it or how to fix it, but I am also interested in getting a fix.

As for the HUD placement problem, I found that occurred when I tried to run the game a DX level that was higher than what my hardware could handle. For example, when I had a GeForce FX5200 and I tried to run the game in DX 9 mode, that would happen, but if I dropped it down to 8.1 or 8.0 mode, it wouldn't. After upgrading to a fully DX 9 card, the problem went away.

---

### Post by lckeeper1 on 2008-05-28
Thanks for the quick reply! As far as my vid card, I'm running a 7900GS, so I know it's dx9 compatible, and I usually have problems running in dx9 anyways, so I usually stick in dx8.

Oh well, I'll get it one day!:tongue:

---

### Post by guildofghostwriters on 2008-06-18
I've just installed Wine using apt-get and then the original Half Life from the original cd. I had the same problem with it pausing as soon as I pressed a control key except that hitting escape and clicking resume didn't resolve it. After much fiddling around, I found that going to winecfg, then the graphics tab, selecting the directx and window manager options and deselecting the emulate virtual desktop option has cured the pause problem and made it playable. It still has odd problems (occasionally my ubuntu desktop flickers briefly on screen and there's odd bits of corruption around the edges of the screen sometimes) but it's playable.

---

