---
title: "Wine crashes when OpenGL enabled in WoW"
date: 2012-06-28
forum: Wine
---

### Post by blennox on 2012-06-28
Hi guys, I have World of Warcraft installed on my ubuntu 12.04 64 bit system and it runs just fine, except for slow fps, which I tried to solve by editing the config.wtf to add 
"SET gxApi = "openGl"
Unfortunately this causes a Wine program crash as soon as the game boots up (on one occasion it lasted around 30 secs during which the fps seemed to be improved) stating
"Internal Errors - Invalid Parameters Received"
I had read on the forums that launching wow from the terminal would workaround this but no luck. The game runs just fine again when I remove this line from the config.wtf (apart from slow fps) so does anyone know what I've did wrong, is there another way of directly enabling OpenGL, or another way to improve the fps? BTW my graphics card is ATI Mobility radeon 5470 and 4GB RAM, on Windows I can have high graphical settings and fine fps, I've even tried turning the graphics down to low, but still too slow.
Many thanks.

---

### Post by uRock on 2012-06-28
Moved to *Wine* sub-forum.

---

### Post by Dlambert on 2012-06-28
SET gxApi "OpenGL" It's that (case sensitive) Did you maybe misspell it like in your post?

---

### Post by Dlambert on 2012-06-28
Also do you have your graphics drivers installed?

---

### Post by cwwilson721 on 2012-06-28
I'll bet you have Intel Graphics.

Search this forum for "wow+intel" for the workaround.

(The only time wine "crashes" with WoW because of opengl is when you use Intel. Good Luck)

---

