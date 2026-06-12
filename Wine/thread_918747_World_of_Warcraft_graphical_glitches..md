---
title: "World of Warcraft graphical glitches."
date: 2008-09-13
forum: Wine
---

### Post by Anathallo on 2008-09-13
Ok, so I got WoW running under wine and the game loads everything up fine but on the log in screen whenever I click the mouse the screen will go black, like it is blinking (weird I know). And in game it is no different it still does the blinking thing and I get a framerate of 3fps. I followed the instructions here
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
 and I have put these lines into the wtf config file

```
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
```

Help is greatly appreciated :)

---

### Post by hikaricore on 2008-09-13
We'll need to know more about your hardware with this type of an issue to even start to make suggestions.

Video card info would be a start.

---

### Post by zeifertstc on 2008-12-01
I have recently gotten World of Warcraft 3.0.x installed (copied from Windows installation) on Ubuntu 8.04. My wine environment is 1.1.8 which has WoW listed as Platinum according to WineHQ. 

Using the same guide as the OP, I managed to get most of the game working. However, whenever I step inside a building just enough so that the map changes to an interior one the text seems to be ripped from it's location on the screen and projected across 3/4 of the screen from the lower left hand corner. If you'd like a screen-shot of this effect, I might be able to get you one.

Machine Specs:

Intel Core2Duo 3.33 GHz
ATi Radeon X1650 @ 256 Mb
1 Gb PC-3200 (x2 512Mb) RAM
Creative Sound Blaster Audigy 24-bit
160 Gb HD
250 Gb External HD
DVD writer x2

---

### Post by zeifertstc on 2008-12-02
Alright, I've fixed most of the problem I was having with my WoW installation. I finally saw something to do with the registry portion of Wine. After setting that registry key up, the text glitches disappeared. The only problem that remains is one where my mini-map refuses to show me the maps of interiors.

For instance, I'm standing at the bottom of a zep tower outside, I still see the exterior map in the mini-map. Now, when I step inside the zep tower and it's supposed to update the mini-map it just turns white and will occasionally flicker as I walk. Once I step back outside the structure (or in this case, get to the top of the zep tower) the exterior map takes over like it should. Are there any fixes/addons or other that I can try to get my interior maps back on the minimap?

---

### Post by dre_in_ham on 2008-12-03
that white mini map is an ati driver problem!

[http://bugs.winehq.org/show_bug.cgi?id=11826](http://bugs.winehq.org/show_bug.cgi?id=11826)

[http://ubuntuforums.org/showthread.php?t=828116&highlight=white+mini+map](http://ubuntuforums.org/showthread.php?t=828116&highlight=white+mini+map)

---

### Post by zeifertstc on 2008-12-04
Thank you for showing me these links, it wasn't the answer I was hoping for, but nonetheless helpful. At least I know I shouldn't go looking for answers to problems when the answers don't exist yet. I hope your linux gaming experience goes well aside from this issue as well.

---

