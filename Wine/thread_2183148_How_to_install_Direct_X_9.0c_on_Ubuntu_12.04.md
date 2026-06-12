---
title: "How to install Direct X 9.0c on Ubuntu 12.04"
date: 2013-10-23
forum: Wine
---

### Post by Scottty on 2013-10-23
Hi

I am installing a game called Command. I used PlayonLinux and the install went smoothly. The problem is running the game. It needs Direct X 9.0c and I have Direct X Redistributable.

I really want to get this game running on Ubuntu; Reason, because with Ubuntu I can get 3 monitors running with Windows 7 I can only get 2 to work.

 The .net framework seemed to install properly However I'm unsure how to check.

Does anyone know how I can get this going?

S

---

### Post by MikeCyber on 2013-10-24
get the wine 1.6 ppa and start with a new ~.wine

I used the directx 9c from the wolfenstein cd but probably the Ms download will do.
Than install your game. My Wolfenstein uses direct9c and works perfectly. Also have a look 
at: 
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by mastablasta on 2013-10-24
can't "play on linux" install direct3D as well?

[http://www.dedoimedo.com/games/wine-directx.html](http://www.dedoimedo.com/games/wine-directx.html)

[http://wiki.winehq.org/Native_D3DX9](http://wiki.winehq.org/Native_D3DX9)

---

### Post by oldos2er on 2013-10-24
Thread moved to Wine.

---

### Post by fehermate76 on 2013-11-04
Run this command:
winetricks

then confirm, confirm again and choose "Install windows dll or program files".
You should be able to choose directx 9.

---

