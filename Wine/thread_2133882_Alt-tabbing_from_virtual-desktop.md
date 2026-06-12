---
title: "Alt-tabbing from virtual-desktop"
date: 2013-04-09
forum: Wine
---

### Post by anoldone on 2013-04-09
I'm running Twinview with two 1280x1024 monitors. I want to have the Arcanum running on one and being able to operate the other one.
The game launches fine in a 1280x1024 virtual-desktop on one of the monitors. I have to use the virtual-desktop, because otherwise I have issues with Wine shutting down one of the monitors when I exit the game. Anyway, I'm not using the -fullscreen command line as it messes up the in-game ui for me, so the game's patched to the 1280x1024 via highres11a and takes up the whole screen. It runs fine, mouse and keyboard are working, performance is fine, so is sound.
When I alt-tab to an application that's on the other desktop my mouse pointer stays in the Arcanum, that's fine, I still get the focus of the application and I can operate it with keyboard. However when I alt-tab back into the Wine Launcher I think it loses focus from the Arcanum. Mouse works as it was still "stuck" on that desktop but some keys stop being responsive. I can use "i" to open my in-game inventory or "c" to see the character's window. It looks like only letter keys are still working. ESC doesn't - I can't exit the game nor save/load because of that. F1-F12 don't work, that takes out NPCs commands (which makes my summoner build fubar). Also 1-0 numerical keys are out, so no hot-keys for spells/potions.
Any ideas?

Arcanum  v1.0.74 + uap081229 + highres11a
Wine 1.4
ubuntu 12.04 LTS

---

### Post by anoldone on 2013-04-12
Too make a quick test of this, get to Arcanum's main menu, click on any of the menu options and check if ESC is working by returning you back to the main menu. Alt-tab to Wine launcher from it and check ESC key again.
I've tried running Arcanum.exe with -fullscreen just to see if that's the issue. UI didn't mess up this time, which was weird, because it was all funky last time when I was initially testing everything to get the game running. The problem still persist, though, so it's not the issue of losing focus because of the game not being full-screened.

As a side note I've installed System Shock 2 today, and ESC also stops working there, while checking it in the menus. However once you start the game and 3d environment loads up, everything is fine, you can alt-tab all day and all keys are functional.

---

