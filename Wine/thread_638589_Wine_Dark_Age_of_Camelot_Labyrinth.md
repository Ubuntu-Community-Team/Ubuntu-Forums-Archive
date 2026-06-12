---
title: "Wine Dark Age of Camelot Labyrinth"
date: 2007-12-12
forum: Wine
---

### Post by provenzano on 2007-12-12
HELLO  i got a problem with wine, while i try  to play dark age of camelot i can not go over the character login it block almost like a freeze , a crash .


help plz

my videocard is ati 9550 radeon sapphyre

---

### Post by cogadh on 2007-12-12
Please see this post for the kind of information we need for you to help us help you:
[http://ubuntuforums.org/showthread.php?t=624424](http://ubuntuforums.org/showthread.php?t=624424)

---

### Post by provenzano on 2007-12-12
ok 

1- using wine 0.9.46

this is the error i get 

err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet

my wine conf is winxp disabled pixel shader , 

using accelerater ati drivers from ubuntu fglrx

no other app installed in wine

---

### Post by provenzano on 2007-12-13
up

---

### Post by cogadh on 2007-12-13
First you should update to the latest Wine, 0.9.50. Go here for instructions:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
After updating, try the game again and post any results.

---

### Post by provenzano on 2007-12-14
i did it does the same

---

### Post by cogadh on 2007-12-14
Check the AppDB page for the game, there may be some specific settings that we are missing:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=443](http://appdb.winehq.org/objectManager.php?sClass=application&iId=443)

---

### Post by provenzano on 2007-12-15
from what i've read it should work but , when i try to log after character selection i keep getting this 

err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet

and all game freeze and dont' load

i 've read that it worked with wine 0.27 maybe i should downgrade

---

### Post by provenzano on 2007-12-15
update

i did an update to .51 and now got same prob but the error message is different 

fixme:d3d:transform_projection >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glOrtho @ state.c / 2796

---

