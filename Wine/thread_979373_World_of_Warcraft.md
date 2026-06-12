---
title: "World of Warcraft"
date: 2008-11-11
forum: Wine
---

### Post by Dot Cong on 2008-11-11
So with the release of WoW:WotLK on the 13th I'm going to need to be able to run it on my desktop. The problem is my Desktop is Ubuntu and I don't know how to run WoW on Ubuntu. What can I do?

---

### Post by Shwefty on 2008-11-11
Well, there's always Wine.  Add/Remove Programs -> Wine.

[The Wine App db seems to think it runs fine.]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329")

[Here's an outdated thread on how to get it to work step by step.]("http://ubuntuforums.org/showthread.php?t=120615")

---

### Post by Dot Cong on 2008-11-12
Cool thanks!

---

### Post by Neurasthenic on 2008-11-12
Dot Cong, I just got WoW set up on my laptop this morning. One tip that I only found in a single thread after searching for quite a while:

Adding 
SET gxApi "opengl"
to your Config.wtf file is probably the most important step. Without that line, WoW would instantly crash on my computer. None of these guides mention though, that you won't have a Config.wtf file if the game hasn't been run yet - so make one yourself and put it into Program Files\World of Warcraft\WTF. Just open up a text editor, add that one line, and save.

---

### Post by Dot Cong on 2008-11-12
I'm so glad you posted you probably just saved me some frustration and hair pulling.

---

### Post by Tea4all on 2008-11-12
Sometimes Direct 3D works better, depending on your hardware.

---

