---
title: "[SOLVED] Pro Evolution Soccer 2008 Demo and DirectX in Wine"
date: 2007-10-23
forum: Wine
---

### Post by SDL on 2007-10-23
Hi. I have a question regarding running PES2008 Demo in Wine. Before I start I should say that I'm completely new to Wine but have read Cogadh's excellent document, '[Stuff I've learned about Wine]("http://ubuntuforums.org/showthread.php?t=497332").'

My question is, according to the information regarding PES 2008 Demo on the [AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9271"), I should install Direct X. As I understood from Cogadh's document, this is a bad idea?

Assuming that I shouldn't install Direct X, which files do I need to move where and how exactly do I configure them with Wine? So far I understand how to open Winecfg and add an override to the library but after that I get quite confused as to what load order I should specify and which directory I should put the overriden files in?

Thanks for reading this. I'd love PES2008 to work as PES is one of the final applications which I really want to keep Windows for!

Stephen.

---

### Post by cogadh on 2007-10-23
That is not the real DirectX installation, that is just the d3dx9_##.dll files, which you can copy from Windows into Wine and set DLL overrides for (set the load order for native first and you should be fine). The files should be placed in .wine/drive_c/windows/system32.

Installing the actual DX will overwrite some of the Wine "fake" DX libraries and break DX functionality.

---

### Post by SDL on 2007-10-23
Thank you very much. Problem solved... for now!

---

### Post by eaglesfan17 on 2007-10-25
> **SDL said:**
> Thank you very much. Problem solved... for now!

So does the demo work for you? Because I couldn't get passed the menu screens. As soon as I would get to team selection, the game would crash back to the desktop on me.

---

### Post by jackietreehorn on 2007-10-26
Hey, this is my first post on here. I'm relatively new to linux/ubuntu, and I'm trying to use Wine to install and run the demo for pro evo 2008. However, I'm having trouble installing the game. I was wondering if someone could run through the process step by step or if there was a website with a good description of installing/running programs on Wine.?

---

### Post by cogadh on 2007-10-26
I wrote a basic Wine usage document that might help. Just click on the "Stuff I've learned about Wine" link in my sig.

---

### Post by jackietreehorn on 2007-10-26
> **cogadh said:**
> I wrote a basic Wine usage document that might help. Just click on the "Stuff I've learned about Wine" link in my sig.

Thanks. I'll give that a try and let you know how it goes.

---

### Post by SDL on 2007-11-03
No, the game didn't work for me. Sorry, I should have been paying more attention to this thread... I played the demo on Windows in the end and didn't really like it compared to PES6 so I couldn't really be bothered to spend too much time trying to get it working in Ubuntu. Although, I'm slightly more tempted now as the full game is only £13 on Amazon!

*Edit - price is back up to £18 now - boo!

---

