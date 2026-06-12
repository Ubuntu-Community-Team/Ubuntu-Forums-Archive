---
title: "Wine in-game cursor problems"
date: 2013-06-28
forum: Wine
---

### Post by Dinosawer on 2013-06-28
So I am experiencing a bit of cursor problems in Warcraft 3 and Morrowind (Steam version). In both games's menu's the cursor lags slightly but noticeably behind, and in Morrowind in-game it jumps around - it moves fast and randomly in a small area around where it actually should be, which makes the screen stutter when playing and makes it hard to click things in the in-game menu's. 
I have tried googling but couldn't find anything. The mouse acts completely normal when just using the computer. Wine version is 1.5.25 for Morrowind and 1.2.3 for Warcraft 3, and I installed them with PlayOnLinux.
Anyone knows what could solve this? Thanks in advance.
PS: I'm new to Ubuntu and Wine but can handle a computer.

---

### Post by Dinosawer on 2013-07-04
PS: I tried with a different mouse and the touchpad and the problem persists, so it's not hardware-related.

---

### Post by Dinosawer on 2013-08-03
The lagginess came from a bad video card driver, and I solved the shaking cursor in Morrowind (and set it fullscreen and greatly improved performance) by doing this (I use PlayOnLinux):
*Using the register editor, I went to HKEY_LOCAL_MACHINE\Software\Bethesda Softworks\Morrowind and set Screen Height and Screen Depth to the resolution of my screen (don't forget to put it in decimal).
*In the Graphics tab in POL (the fourth tab) I changed:
GLSL to enabled
Direct Draw to opengl
Video size to what my video size is
Modus offscreen rendering to fbo
and the rest stays default.

---

