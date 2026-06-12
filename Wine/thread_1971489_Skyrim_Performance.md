---
title: "Skyrim Performance"
date: 2012-05-02
forum: Wine
---

### Post by BarfBag on 2012-05-02
Hello, all!  I installed the Steam version of Skyrim via PlayOnLinux.  I have a Quad Core, 4 GB Ram, and a GeForce 9600 GT (1 GB VRam).  My performance isn't the best.  The main issue is the frame rate, which is so irregular the game is annoying to play.  I know I'll never get this game running perfectly under Wine, but is there anything I can do to improve performance?  I've tried adjusting the texture quality and the resolution, which oddly, didn't make it any better or worse.

---

### Post by thatguruguy on 2012-05-02
You may want to read the discussion [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=24749").

---

### Post by Dlambert on 2012-05-04
Here are the tweaks I used, for wine, and the the Skyrim Preferences. Also I noticed that if you override the application settings in Nvidia Control panel (Antialiasing, etc), the performance increases.
 
[WINE]
glsl=disabled
OffscreenRenderer=fbo
 
[DISPLAY]
iPresentIntervals=0
 
[Not sure look for other "b's"]
bMouseAcceleration=0
 
 
Nvidia GTX 560 Ti

---

