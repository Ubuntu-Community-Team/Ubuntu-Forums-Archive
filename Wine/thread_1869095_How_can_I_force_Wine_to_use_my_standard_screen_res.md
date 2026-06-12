---
title: "How can I force Wine to use my standard screen resolutions?"
date: 2011-10-25
forum: Wine
---

### Post by colobix on 2011-10-25
Hi. I use 1920x1080, but it changes to 800x600 on some games.
Is there a way to force the resolution to stay in full HD?
Because now I have to change the nVidia settings, and that's annoying.

---

### Post by dino99 on 2011-10-25
there are some race conditions:
- is the game able to play like you ask (full screen, 24 bits) ?
- is your graphic card able to do so ?

its not a wine issue.

---

### Post by ubupirate on 2011-10-25
Like dino stated, not an issue with Wine.

Wine will use up to whatever the resolution the game allows, so if you have a game that can only be max 800x600 (for example) then that is the max resolution Wine will use.

---

### Post by colobix on 2011-10-25
@ubupirate Then why is this not happening when I play it in windows?
It doesn't happen with Linux games. Plus, they cover the whole screen including the gnome panel.
Some wine games doesn't. Such as GTA San Andreas, Sonic Mega Collection Plus, Dead Island and Portal 2.

---

### Post by ergo-proxy on 2011-10-26
> **colobix said:**
> Hi. I use 1920x1080, but it changes to 800x600 on some games.
Is there a way to force the resolution to stay in full HD?
Because now I have to change the nVidia settings, and that's annoying.

Not really if it's not supported by a games. What I can advise is use emulate desktop resolution (winecfg)

---

### Post by colobix on 2011-10-26
> **ergo-proxy said:**
> Not really if it's not supported by a games. What I can advise is use emulate desktop resolution (winecfg)
Thanks. What's winecfg and how do I use an emulate desktop resolution?

---

### Post by colobix on 2011-10-26
Okay, it works when I choose not to let the window manager control the windows, but the keyboard isn't working then. Only mouse.
Any idea how I can fix it.

---

### Post by ergo-proxy on 2011-10-28
Undo the changes you made and just check "emulate a virtual desktop" and set for example 800x600 or higher resolution.

---

### Post by colobix on 2011-10-28
> **ergo-proxy said:**
> Undo the changes you made and just check "emulate a virtual desktop" and set for example 800x600 or higher resolution.
Then I get a light blue screen that goes away after a second.
Nothing more happens.

---

