---
title: "dungeon defenders, pixel shader 3.0 not detected while present"
date: 2012-02-10
forum: Wine
---

### Post by uh20 on 2012-02-10
i have a nvidia quadro fx1400
in the description from 3 sites it has benchmarks of
directx:9c
shader model:3.0

while downloading dungeon defenders from steam and following the directions from winehq on its dependencies, i start the game only to come up with a message saying my pixel shader is not 3.0
(yes i have turned shaders on in winecfg)
i recall once getting it to maraculously work after changing nvidia drivers at least 2 weeks ago, but joining again after a game crash brought back the bad shader message and when i tried to recreate what i did last 2 weeks, it did not work
so... what now

---

### Post by brpylko on 2012-02-10
Some windows applications will not run correctly because the graphics card is reported as the x window system. In winetricks I would try installing physx, direct3d 9, 10, and 11 dlls, and any other directx related components.

---

### Post by Dlambert on 2012-02-10
Latest Nvidia drivers?

---

### Post by uh20 on 2012-02-10
sorry, installed physx and the 2 other direct3d's i did not have and nothing happened after a wine restart, i feel it is related to the game failing to detect 3.0 other than me not having the right components, course no-one has reported this yet in the hq

---

### Post by uh20 on 2012-02-10
cant find my additional drivers hold on, i do think i have the current driver though
edit: additional drivers: i have version current recommended nvidia accelerated graphics driver

---

### Post by Dlambert on 2012-02-11
Try the update version

---

### Post by uh20 on 2012-02-12
try the update what?
like i said before, this probably has to do with game software detection

---

### Post by Dlambert on 2012-02-15
Interesting, well to me ubuntu has two drivers avaliable.

---

