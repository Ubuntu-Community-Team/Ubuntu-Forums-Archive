---
title: "Team Fortress 2 from NTFS Partition. Working?"
date: 2008-11-04
forum: Wine
---

### Post by saxofoner on 2008-11-04
So I know, in the past, running steam games from my windows partition in wine has never worked.  But just for kicks, I tried it after the Ibex (and WINE) update.  To my great surprise, Steam started!  The only issues were the old text issues with chat which have always been there!  Surely tf2 won't start, I thought.  Imagine my surprise upon getting past the loading screen, to a menu, albeit without any graphics.  The menu worked, but the background image loaded.  I couldn't figure out the issue.  Then I (without the benefit of any text in the server menus) randomly clicked the blank space till I got a server with room on it, and I was playing! However, I was getting about 10 frames a minute, and all the overlays were invisible.  Any ideas?  I'd love to not have 2 copies of this massive game on my hard drive.

---

### Post by cogadh on 2008-11-04
Wine is not designed to work in that way. From the Wine FAQ:
> [B]I have lots of applications already installed in Windows. How do I run them in Wine?
[/B]
Short answer: You have to install them in Wine just like you did in Windows. Applications usually have a setup or installer program.

Long answer: Some applications can be copied from Windows to Wine and still work, but don't try this unless you like tinkering under the hood of your car while it's running.

*Wine is not designed to interact with an existing Windows installation.*

WARNING: Do not try to configure Wine to point to your actual Windows C:\ drive. We have tried to make this hard to do so you probably cannot do it by accident. If you do this, Wine may or may not continue to operate. Your Windows install will be 100 percent dead due to wine overwriting critical Windows files. The only way to fix Windows after this has happened is to run a reinstall of Windows.

---

### Post by saxofoner on 2008-11-04
Oh darn... I guess I just need a bigger hard drive then.  Thanks for the information.

---

