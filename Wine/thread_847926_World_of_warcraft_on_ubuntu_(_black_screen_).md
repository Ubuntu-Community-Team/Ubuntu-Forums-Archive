---
title: "World of warcraft on ubuntu ( black screen )"
date: 2008-07-03
forum: Wine
---

### Post by FrankBro on 2008-07-03
So i've been following everything on this guide : [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I had wow installed on my windows partition, so i took the whole folder and put it in wine/c/program files/world of warcraft. I added SET gxApi "opengl" and SET M2UseShaders "0" to the config.wtf   and i'm still stuck with the black screen when i start the game, dont see anything. I did a lot of search and couldn't find anything. My graphic card is a ATI mobility Radeon HD 2600 ( with the restricted driver thing). I'm pretty knew to ubuntu, i've been looking for a fix for about a week and couldnt find anything so i hope the community can help me.

Thank :)

---

### Post by thisismalhotra on 2008-07-03
[http://ubuntuforums.org/showthread.php?t=770939](http://ubuntuforums.org/showthread.php?t=770939)

Try

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"

---

