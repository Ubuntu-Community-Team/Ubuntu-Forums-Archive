---
title: "StarCraft UDP..."
date: 2008-01-13
forum: Wine
---

### Post by puppyfarts on 2008-01-13
My friends and I are trying to LAN StarCraft.
One uses Vista, one XP, and I'm using Ubuntu, of course.

They both tried to register with Battle.net, and then they got a new choice that appeared -- LAN with UDP instead of IPX.

I cannot get this choice to appear. When I try to register with Battle.net, I get a popup saying Battle.net is searching for the fastest servers, and then it freezes.

What can I do?

I am running it under WINE.

---

### Post by kostkon on 2008-01-13
> **puppyfarts said:**
> My friends and I are trying to LAN StarCraft.
One uses Vista, one XP, and I'm using Ubuntu, of course.

They both tried to register with Battle.net, and then they got a new choice that appeared -- LAN with UDP instead of IPX.

I cannot get this choice to appear. When I try to register with Battle.net, I get a popup saying Battle.net is searching for the fastest servers, and then it freezes.

What can I do?

I am running it under WINE.

According to the [W*ine Application DB* page for *Starcraft*]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=51") or the [*Brood War* expansion]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=149"):
> The only networking method in the release version is IPX. However, if you [update]("http://www.battle.net/files.shtml#starcraft") the game, a new UDP networking option is available, which should work for all users. In order to use IPX networking, IPX will have to be enabled in the kernel, and you need some userspace utilities, usually called ipx-utils; and IPX must be started (there should be an initscript). Also note that StarCraft's network support is only available when it is run as root.

Please update the game and check if you will get the UDP option.

---

### Post by puppyfarts on 2008-01-13
Where can I go to update the game?

I have never played SC before (a sin, I know...)

---

### Post by puppyfarts on 2008-01-13
Okay, I'm sorry... I am unobservant...
Thanks for the fix.   :popcorn:

---

