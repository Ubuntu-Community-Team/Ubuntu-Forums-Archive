---
title: "World of Warcraft: Video freezing, audio is fine"
date: 2007-10-14
forum: Wine
---

### Post by morweni on 2007-10-14
Afternoon! I have been able to fix loads of different issues with my first real good install of Ubuntu.. but I am having issues with WoW... not that I intend to play it.. but rather to get it to work! Any game to work :)

I am able to login to WoW, however once loading in-game, video completely freezes (gives me perhaps 1 second to move around then freezes). Audio on the other hand, does work, and continues to work after video freezes.....

End up having to force the laptop to reboot, any thoughts?

```

adria@minime:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)

adria@minime:~$ 

```

WoW command line : wine "/home/adria/.wine/drive_c/Program Files/World of Warcraft/Launcher.exe" -opengl

thank you!

---

### Post by morweni on 2007-10-15
bump

---

### Post by vacolten on 2007-10-15
I had that same problem when I was running it in d3d but (among other things) running in opengl helped.  Also in config.WTF make sure you have:

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"

It may be an ATI driver issue?  I use NVidia so I cant speak from experience but I know some folks have experienced weirdness with the driver.  Actually, until I updated my NVidia driver I had similar issues.

---

### Post by vacolten on 2007-10-15
OK this worked for me:

make sure you chmod 777 Config.wtf

---

### Post by morweni on 2007-10-16
Thank you for the input, the other night before receiving these posts I went and upgraded to Feisty.. and now when i try launching WoW it brings me to the html like page where you have to first click play before it launches.... 

I click play and nothing happens at all?
:confused:

---

