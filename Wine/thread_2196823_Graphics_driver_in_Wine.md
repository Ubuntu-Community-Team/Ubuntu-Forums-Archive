---
title: "Graphics driver in Wine"
date: 2013-12-31
forum: Wine
---

### Post by manudo on 2013-12-31
Simple question, if I use Wine to play a game, it uses the same graphics as Linux, I mean.
I've installed a nVidia driver in Ubuntu, can that driver be used in a Windows game using Wine? Or I have to install the same driver for Windows?

---

### Post by deadflowr on 2013-12-31
> [COLOR=#000000]I've installed a nVidia driver in Ubuntu, can that driver be used in a Windows game using Wine? [/COLOR]
It's the only way to run Windows games in wine.
Well, not the only way. But you'll need to use the linux drivers on a linux system.

---

### Post by manudo on 2014-01-01
> **deadflowr said:**
> It's the only way to run Windows games in wine.
Well, not the only way. But you'll need to use the linux drivers on a linux system.

Thanks for your reply, but you mean that WIne uses Ubuntu drivers to run Windows applications?
By the way, happy new year! :)

---

### Post by Daliz on 2014-01-01
Yes, just install graphics drivers for Ubuntu, then install the game in Wine.

Check [Wine Appdb]("appdb.winehq.org") for info which games work in Wine or what is needed to make it work, or you could use [PlayOnLinux]("http://www.playonlinux.com/en/") if your game is supported (it's way easier).

---

### Post by deadflowr on 2014-01-01
> **manudo said:**
> Thanks for your reply, but you mean that WIne uses Ubuntu drivers to run Windows applications?
By the way, happy new year! :)

Yes.
But nvidia cards can use two different drivers.
The closed-source drivers from nvidia.
Or the open-source nouveau drivers.
(Not at the same time, though)
Hence my caveat that it's not the only way statement.

But they can only use the linux drivers.
The windows drivers wouldn't do anything.

---

