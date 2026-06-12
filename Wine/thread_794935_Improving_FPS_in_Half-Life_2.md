---
title: "Improving FPS in Half-Life 2"
date: 2008-05-15
forum: Wine
---

### Post by SolidStClair on 2008-05-15
Hi,
I recently put Ubuntu on my Inspiron 1520, and I now have Steam up and running through Wine. My only issue is that fps in Half-Life 2 and CSS are substantially lower than when I was running Vista (20 fps vs 80-100 fps with settings maxed out). I knew I could expect a drop, but I didn't know it would be this much. Are there any tweaks I can implement to improve my performance? I am fairly new at Linux, so step by step instruction would be greatly appreciated. Thanks.
Inspiron 1520
Intel T7500 2.20ghz
2gb PC667
160gb 7200rpm
nVidia 8600m GT 256mb

---

### Post by Sleaka J on 2008-05-15
DirectX 9 performance is sub-par in Wine. You'll probably need to add a -dxlevel 81 or 70 as a Launch Option within the Steam Games Menu to for those games to run in either DirectX 8.1 or 7.0 mode.

---

