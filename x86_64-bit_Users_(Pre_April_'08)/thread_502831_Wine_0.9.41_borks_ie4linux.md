---
title: "Wine 0.9.41 borks ie4linux"
date: 2007-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by f1uxam on 2007-07-17
I got the update from 0.9.41 installed via Update Manager and then discovered that the URL line in ie4linux won't accept any typed input but simply puts in an "h" and then says page cannot be found.
I reinstalled ie4linux several times and did complete uninstall/reinstalls of Wine 0.9.41.  When I again installed version 0.9.40 from a Debian repository
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
all was back to as before in ie4linux. (I'm still amazed how well an HE-AAC ActiveX music player works!)
I've no doubt that there's a bug in the latest Wine.

---

### Post by thesoothsayer on 2007-07-21
Ah okay. That explains it. I was experiencing the same thing and I could have sworn that ie6 was working just a few days ago.

---

### Post by Kilz on 2007-07-21
> **f1uxam said:**
> I got the update from 0.9.41 installed via Update Manager and then discovered that the URL line in ie4linux won't accept any typed input but simply puts in an "h" and then says page cannot be found.
I reinstalled ie4linux several times and did complete uninstall/reinstalls of Wine 0.9.41.  When I again installed version 0.9.40 from a Debian repository
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
all was back to as before in ie4linux. (I'm still amazed how well an HE-AAC ActiveX music player works!)
I've no doubt that there's a bug in the latest Wine.

You do understand that IE running under wine is not safe to surf with, right? Wine is a bug for bug copy of windows. IE and active x are security problems waiting to happen. IE under wine is good for checking to see if a page you made looks right on IE, but please dont surf with it. Not even to just a few sites.

---

### Post by franganghi on 2007-07-21
> **f1uxam said:**
> 
I've no doubt that there's a bug in the latest Wine.

Abosolutely confirmed on my ubuntu desktop with 0.9.41!

---

### Post by revolution_mac_usr on 2007-07-22
Using IE on Linux is more of a novelty than anything. For everyday browsing could be harmful. Besides, that kinda defeats the purpose of having a non-Windows os, like using m$ word on a Mac.

---

### Post by Flactivist on 2007-08-01
IE4Linux is a handy utility that can check how pages render on a really popular and buggy web browser. It makes web designing on Linux a lot easier. Thanks to everyone who posted about this bug and the fix, try not to mind the paternalistic browbeaters.

---

### Post by kuja on 2007-08-01
Could be worth a try for you guys to upgrade to Wine 0.9.42 then.

---

### Post by Kilz on 2007-08-01
> **Flactivist said:**
> IE4Linux is a handy utility that can check how pages render on a really popular and buggy web browser. It makes web designing on Linux a lot easier. Thanks to everyone who posted about this bug and the fix,** try not to mind the paternalistic browbeaters.**

Just as we should ignore the foolish children who advocate the use wine and IE to surf with. Dont think it doesnt happen, there are probably a few that even do it as root.

Things posted such as 
> (I'm still amazed how well an HE-AAC ActiveX music player works!)
Would lead a lot of people to think that someone isnt just taking a look at the pages they made to make sure they look ok.

---

### Post by Cappy on 2007-08-01
This bug is NOT fixed in .42 .. I really really hate wine for breaking stuff each release. I'm gonna downgrade and take it out of my repos =-/
IE4Linux seems to work for the most part but my pngfix javascript which allows IE5.5-6 to see transparent PNGs doesn't work on IE4Linux even though it works on a real machine.
**Note that it is only IE6 that is broken in the last two releases - 5.5 and 5.0 still work for me**


And Flactivist there is absolutely no need to be rude when all Kilz (and mac) did was warn everyone of the danger. No one was rude to you or anyone about it. An IE exploit and/or virus and/or trojan can effect your machine - not just your wine environment.

---

