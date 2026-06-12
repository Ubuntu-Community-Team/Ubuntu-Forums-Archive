---
title: "Ghraphic Problem With Wine"
date: 2015-05-22
forum: Wine
---

### Post by mohammad14 on 2015-05-22
hello 
i want play Pro Evolution Soccer 2015 and everythings will be ok and i can run and play the game
but wine can't detect my video memory size and the game forced run with low quality and box window mode
i need a way for detect my reall video size in wine

this pic warning message from game:
[img]http://s2.img7.ir/KtyQG.jpg[/img]

this test my hardware from the game setting:
[img]http://s2.img7.ir/1DY1y.jpg[/img]

---

### Post by sandyd on 2015-05-22
To increase video ram on wine
```

wine regedit
```
Go to HKEY_CURRENT_USER -> Software -> Wine -> Direct3D -> VideoMemorySize
Increase the value to the required one. If it does not exist, right click create new string value and name it VideoMemorySize.

---

### Post by mohammad14 on 2015-05-23
i set this before in wine configuration. and now are 2048
but still have problem :(

---

### Post by mohammad14 on 2015-05-23
please help..

---

