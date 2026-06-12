---
title: "Steam Issues"
date: 2008-02-21
forum: Wine
---

### Post by srozzman on 2008-02-21
I have an issue in Steam, that when I try to start any game, it says "This game is currently unavailable.  Please try again at another time."  Also, it will not get past 0% when it tries to update the games, and if I try to download something from steam, it claims that the servers are busy.  Any help will be appreciated.

---

### Post by srozzman on 2008-02-22
Should I just install a windows partition?  I would rather go all ubuntu

---

### Post by xtek0 on 2008-02-22
Also my keyboard doesnt work =[

---

### Post by srozzman on 2008-02-22
Did you just jack my thread?

---

### Post by xtek0 on 2008-02-22
I beleive i  did =]]

---

### Post by aoanla on 2008-02-23
> **srozzman said:**
> I have an issue in Steam, that when I try to start any game, it says "This game is currently unavailable.  Please try again at another time."  Also, it will not get past 0% when it tries to update the games, and if I try to download something from steam, it claims that the servers are busy.  Any help will be appreciated.

Is your network connection okay? It sounds almost like Steam's having problems talking to the servers, specifically - I think that can cause all of those problems. 

(No, you shouldn't just install Windows - Steam works very well with Wine, and you probably just have some obscure configuration issue.)

Oh, and for the hijacker - if you mean that you don't get keyboard input in Source games, then try Alt-Tab ing out of the game - you should be automatically switched back to it after a couple of seconds, but this time with proper keyboard focus.

---

### Post by srozzman on 2008-02-23
My connection seems fine to me; I can play other games like Urban Terror just fine. Should I try the reinstall route, and install steam from an online source, then orangebox?

EDIT: I have now gotten Steam to install the source SDK by uninstalling wine and Steam etc., then following this guide here [http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/) and the 26% error fix on the wine website ([http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554))  I will now attempt installing orange box

EDIT 2: Everything works now.

---

### Post by boombox1387 on 2008-04-09
Which version of Wine were you using when you were having the problem?  My Steam was working fine with Wine 0.9.55, but I just got an update to 0.9.58 and Steam started giving me the "This game is currently unavailable" message.  I manually upgraded Wine to 0.9.59 but I still have the same problem.

I'd like to make this work without reinstalling Wine and Steam, etc, but I may end up giving that a shot when I get some free time.

---

### Post by Jemain on 2009-10-29
hi,

i had the same problem with the not-working update.
I justed switched around the download servers (settings->download)
don't ask why, but it worked.

for the second problem, add the following in the properties of the game in steam:
[B]
-dxlevel 90 -novid -windowed -width 1024 -height 768 -heapsize 512000[/B]

change as needed.

---

