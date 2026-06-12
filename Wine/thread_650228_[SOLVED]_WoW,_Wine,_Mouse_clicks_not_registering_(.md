---
title: "[SOLVED] WoW, Wine, Mouse clicks not registering (errors in terminal)"
date: 2007-12-26
forum: Wine
---

### Post by regret on 2007-12-26
I apologize in advance if this is a really stupid question that has been answered before, but a lengthy search of the terminal error and several different keyword configurations in google netted me mostly nothing. I see the error frequently but people are always talking about different problems, and not this error in particular. Anyway, that being said...

I installed Wine and WoW flawlessly. I followed all the steps in the How-To and had zero problems setting everything up, which was really very nice and the game runs beautifully. I get anywhere from 70-150 FPS which is miles ahead of what I was seeing in Windows Vista (I spontaneously installed Ubuntu a few days ago). There's no graphics problems, my keyboard functions perfectly, and as far as mouse movement goes it's flawless as well.

But now we get to the problem: frequently my mouse button clicks won't register in-game. The mouse cursor will still be flying around the screen but neither button will register. It happens for a very brief period of time. I'd say 2-5 seconds at most, but I PvP a lot so this is very noticeable. If you play WoW and hold the right-mouse button to strafe you will understand what an issue this is.

In my searches I discovered that running from terminal will show me errors, so I did that and found that every time I had a mouse button issue I'd also receive this error in the terminal:

```
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

```

So is there a simple fix for this I'm somehow missing?

Using a logitech g5 laser mouse plugged directly into my motherboard, in Ubuntu 7.10, under Wine 0.9.51, having tried both Windows 98 and XP mode. I can include more info if needed but this seems to be more of a software/system issue than anything on the hardware end.

I would appreciate any help that can be given. This is the only problem I've had with Ubuntu but it's a pretty major one... I have no desire to boot back into Windows.

---

### Post by regret on 2007-12-27
So I reinstalled Windows Vista, believing that the only difference between my old WoW and my new WoW was Ubuntu. But this wasn't so, apparently, because the problem transfered itself to Windows Vista. I began to suspect it's a mouse problem, but that makes no sense: my mouse works perfectly in every other application. So, WoW? An addon? Why does it only seem to have problems in the center of my screen? I went through every single addon I had and discovered that -- surprise, surprise -- the one new addon I'd downloaded was causing this dead zone in the middle of my screen.

The culprit: warrior alert fu

Incoming reinstall of Ubuntu. /sigh

I guess I should have known better than to jump to conclusions.

---

### Post by c1rcu17 on 2008-01-25
Wow, thank you so much! I was having the exact same problem, and I too have warrior alert. You just saved me soo much time!

Cheers!!!!

---

