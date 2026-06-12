---
title: "Wine, Steam, and Portal. Oh my. Plzhalp"
date: 2011-08-16
forum: Wine
---

### Post by jfed on 2011-08-16
Hello. I am running Ubuntu 10.10. I recently installed Wine, and installed the Steam client. Everything works like a dream, as far as the client works. I can voice chat with friends, IM, use the community to the fullest. So I decided it was time to download Portal 1. I downloaded it, and installed it, no problems. I can launch it just fine, smooth and everything. Goes into the valve splash, and the source splash, running smooth as can be. Then we get to the first loading menu and the crap hits the fan. I just see the background image, blurred out, as its supposed to be, but here and there a few pixels are...green. Then all of a sudden, I get the little box in the bottum right corner that says "loading", then the entire screen goes green, not just completely green, you can still see a bit of the original image, but its not at all ideal. I thought of just leaving it there, and seeing if it would fix itself, but no, sure enough, after a few minutes, it crashes. I am completely clueless as to what to do. Has anyone else had this problem? Anyone know of a fix? It might JUST be portal one, I haven't downloaded any of my other games, such as Half-Life 2 or Team Fortress 2 yet. I figured it'd be a waste of 2 hours just for them not to load up properly. Any guidance as to how I can fix this is appreciated, thanks in advance.

P.S. I managed to grab a screenshot of the horrible frenzy of green. Here it is. [IMG]http://img41.imageshack.us/img41/5318/thisdidntwork.png[/IMG]

---

### Post by Soulcage on 2011-08-16
Looks like it's because you're using an intel card instead of a nvidia card. [http://ubuntuforums.org/showthread.php?t=885111]("http://ubuntuforums.org/showthread.php?t=885111")

---

### Post by jfed on 2011-08-17
Could be right, however I already found a fix for this. Just have to run the game with launch options set as:

```
-novid -dxlevel81
```

That did the trick, along with my other source games, gmod, tf2, etc.

---

