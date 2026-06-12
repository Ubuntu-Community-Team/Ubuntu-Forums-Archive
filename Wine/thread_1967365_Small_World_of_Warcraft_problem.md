---
title: "Small World of Warcraft problem"
date: 2012-04-28
forum: Wine
---

### Post by skxc on 2012-04-28
Hello,

I've managed to get WoW working smoothly through wine (quite impressed), but the Alt key seems to be behaving weirdly. I've disabled the "drag window" feature so it wouldn't interfere anymore, but it still has some weird behavior.

When playing, to walk I hold W and control direction with the mouse while keeping my finger on right click. If I press the Alt key while doing this (W+RightClick), my camera direction is being released and I'm controlling the cursor instead of the character direction.

Any idea if there's a fix for this kind of thing ?

---

Managed to fix this.

Compiz Settings > Unity > change the key to show HUD from Alt (it was grabbing focus)

---

### Post by kalkems on 2012-04-28
I have 2 people that are interested in Ubuntu but mean they cannot make the move because WoW does not work.  I would appreciate instructions on how to set it up in wine.

---

### Post by skxc on 2012-04-28
Quite easy, I have dual-boot and WoW was installed on the windows partition already, didn't have to bother with that. The only problems that may arise with emulation are the updates that come through the launcher, you may have to do that on windows.

Install wine (the microsoft windows compatibility layer package) from the repository, then you can simply run the exe (right-click, open with > wine loader).

---

### Post by kalkems on 2012-04-29
I got WoW running through wine for my son when he lived at home.  The problem he had then was graphics and laging.  He wasn't able to run in fullscreen mode.  How does this work for you?  What makes having it in mswin better when using wine?

---

### Post by skxc on 2012-04-29
> I got WoW running through wine for my son when he lived at home. The problem he had then was graphics and laging. He wasn't able to run in fullscreen mode. How does this work for you?

It depends mostly on your PC/Laptop's specs, a low-end system won't be able to run games smoothly with emulation (wine) as it generally requires more power. Be sure to have the proper drivers installed for your graphic card (usually in restricted packages).

> What makes having it in mswin better when using wine

Having it already on Windows doesn't make it run smoother or anything, it's just simpler because this way it's already installed, from my previous experiences running an installer through wine is harder. And since WoW has its own launcher/autopatcher, problems may arise when running that through wine (don't take my word on that though, haven't tried it myself).

---

### Post by kalkems on 2012-04-30
Thanks I'll have try again when I have some time over.

---

