---
title: "wine + wow keyboard/mouse lockup"
date: 2008-06-08
forum: Wine
---

### Post by davedaver on 2008-06-08
I have gotten wow installed (wine-1.0-rc4) and am running into a rather severe problem starting it up. I can get the launcher up no problem, and after clicking on "Play" the game switches to full-screen and the opening cinematic starts. If I hit escape there to skip it, I am taken to the initial license agreement window, and this is where I run into trouble. There is a cursor, I can move it about, but none of the mouse buttons work, and my keyboard no longer responds (numlock key doesn't toggle numlock, etc). 

Both keyboard and mouse are perfectly normal USB. They work fine in every other application, no issues there. Anyone have any helpful hints or ideas where I can look here? Bear in mind I can't get terminal output here because the game essentially locks me out of everything but that screen.

Edit: Nvidia 6800 video card, if that helps

---

### Post by thisismalhotra on 2008-06-09
Tell Wine to use windows XP settings rather than Vista and see what happens

---

### Post by davedaver on 2008-06-10
Alrighty, here we go. Ran winecfg again, set wow to run in windows XP mode (or however you want to call it) explicitly. Start it up, get the launcher, click play the cinematic starts, I hit esc to skip it, and get to the EULA. And once again, I have no keyboard, and if I click any of the mouse buttons, it freezes, and locks me out of the comp entirely.

---

### Post by thisismalhotra on 2008-06-10
Did you install it from scratch?? Try copying whole folder from windows partition(if you have one).. Also there is some setting that you can do in config.wtf file so that ur EULA is automatically accepted and the trailers will turn off. Google it!! LOL

---

### Post by wtiz on 2009-02-18
Have you found a fix for this yet? I've struggling with this same issue for a week now and found nothing. Coincidently I also have an NV6800 card

---

