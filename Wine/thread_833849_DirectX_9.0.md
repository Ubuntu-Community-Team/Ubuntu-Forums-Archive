---
title: "DirectX 9.0"
date: 2008-06-19
forum: Wine
---

### Post by MechWarrior001 on 2008-06-19
I installed *Star Wars: Empire at War* under *Wine 1.0 *and it asked me to install DirectX.
So I said yes and it begun the install then it generated a exception and it said install failed.

I uploaded the DirectX.log it generated so you can see the Technical Specs of the Error.

---

### Post by Fred_E _krugar on 2008-06-19
Just for future reference do not install any directX, wine uses their own implementation of DirectX.

---

### Post by MechWarrior001 on 2008-06-19
Ok but I thought that was the Reason EaW wasn't working. I installed 1.05 patch but it still doesnt run.

---

### Post by cogadh on 2008-06-19
There is a very lengthy and informative how-to for the game here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7955](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7955)
Skip all the stuff about getting and compiling Wine, just move down to the section about installing the game.

However, if any of that DX install was successful, you probably just broke DX on Wine. If you have any other previously working DX games already installed in Wine, try them out again. If they don't work now, then you are probably going to have to delete your .wine directory and start over again. If they do still work, then you are probably OK and can keep using your current .wine drive.

---

