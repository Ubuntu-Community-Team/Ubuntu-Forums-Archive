---
title: "Playing &quot;Tag: The Power of Paint&quot; in ubuntu."
date: 2011-10-18
forum: Wine
---

### Post by Squidgeididdly on 2011-10-18
Hi there.
I've downloaded the normal install.exe file from the website of this game which is only designed for windows so I tried just running it under Wine and it installs fine to my knowledge.

When I run the game I get a message saying that my graphics card does not meet system requirements and then another saying it could not initialize Direct3D.

I'm sure 3D games, like Minecraft, work fine normally so I'm wondering whether this is a problem with Wine or not, and how to fix it. 

The website for the game is [https://www.digipen.edu/studentprojects/tag](https://www.digipen.edu/studentprojects/tag)

---

### Post by Tweak42 on 2011-10-19
Simplified summary:
Linux uses opengl language for 3d rendering.
Windows uses Direct3D language for 3d rendering.
Wine can translate windows api calls to linux and Direct3D to opengl allowing 3d windows programs to run on linux.  (some caveats apply) 

Minecraft can run because uses java (runs on everything) and supports both opengl and Direct3d for 3d rendering.

A ancient entry in [Wine appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16215") is evidence that TAG worked at one time. You might have luck using a older version of wine and possibly graphics drivers.  Failing that, file a detailed bug report to the wine bugzilla and hopefully the devs can look into it.

---

### Post by Amaroq Dricaldari on 2012-12-10
Speaking of Tag, it turns out that it has horrible texture optimization. More than half of the textures are larger in file size than they need to be, since every single one is 32-bit when most them look just fine in 24-bit or 8-bit.
 
Also, the version up on CNET is slightly more up-to-date than the version on the digipen website, so the next time you install the game I recommend the CNET version (that CNET installer is annoying though).

---

