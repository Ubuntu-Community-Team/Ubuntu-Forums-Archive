---
title: "[SOLVED] Quake 3 (Windows Version) on Ubuntu 8.04 Beta"
date: 2008-04-18
forum: Wine
---

### Post by sixstorm on 2008-04-18
Well, there isn't much n00b info around the net to install Quake 3 Arena on Ubuntu via Wine OR ioquake.  Can anyone direct me some instructions on installing this?  I've installed ioquake and copied the PAK03.PAK from the Q3 CD to the ioquake install folder, but the ioquake program won't even run.

Also, I tried to install in wine via terminal but where there are spaces in the folder name, I can't CD into it.  Any help for a poor n00b?

---

### Post by pseudo-random on 2008-04-18
```
cd "folder with spaces"
```

Try cedega for Quake 3. See this link:
[http://games.cedega.com/gamesdb/games/view.mhtml?game_id=2643](http://games.cedega.com/gamesdb/games/view.mhtml?game_id=2643)

---

### Post by sixstorm on 2008-04-18
> **pseudo-random said:**
> ```
cd "folder with spaces"
```

Try cedega for Quake 3. See this link:
[http://games.cedega.com/gamesdb/games/view.mhtml?game_id=2643](http://games.cedega.com/gamesdb/games/view.mhtml?game_id=2643)

Eh, no thanks.  I'm trying to play this for free.  ;)

---

### Post by compiledkernel on 2008-04-18
Theres no need to bother with wine or other such implementation for quake 3. Q3A will play natively. Look here. 

[http://zerowing.idsoftware.com/linux/q3a/](http://zerowing.idsoftware.com/linux/q3a/)

---

### Post by sixstorm on 2008-04-18
> **compiledkernel said:**
> Theres no need to bother with wine or other such implementation for quake 3. Q3A will play natively. Look here. 

[http://zerowing.idsoftware.com/linux/q3a/](http://zerowing.idsoftware.com/linux/q3a/)

I've done all this but Quake 3 can't find the default.cfg file.  WTF?   That PK0.PK3 is in the /usr/local/games/quake3/baseq3 folder . . . what else do I need to do?

---

### Post by sixstorm on 2008-04-18
NM.  I just started all over again from stratch and it works.  Awesome!  Thanks guys!

---

### Post by disturbedite on 2008-04-18
> **sixstorm said:**
> Well, there isn't much n00b info around the net to install Quake 3 Arena on Ubuntu via Wine OR ioquake.  Can anyone direct me some instructions on installing this?  I've installed ioquake and copied the PAK03.PAK from the Q3 CD to the ioquake install folder, but the ioquake program won't even run.

Also, I tried to install in wine via terminal but where there are spaces in the folder name, I can't CD into it.  Any help for a poor n00b?
there is clear documentation on how to compile & "install" ioquake3 on the ioquake3 site.  it is extremely simple.  i actually discourage ppl from using the official native q3 for linux.  ioquake3 is the continuation of development, so there is no reason to use the official client any more!

please see my post here for more info:
[http://ubuntuforums.org/showthread.php?p=4637809#post4637809](http://ubuntuforums.org/showthread.php?p=4637809#post4637809)

---

### Post by LucidLoon on 2008-05-11
These are the instructions I used to install quake3 arena

[https://help.ubuntu.com/community/Games/Native/QuakeIIIArena?highlight=(quake](https://help.ubuntu.com/community/Games/Native/QuakeIIIArena?highlight=(quake))

I've got an older video card so I had to change my nvidia driver to get the OpenGL working but after that it the game worked great with the exception of no sound, which seems to be a common problem.

---

### Post by disturbedite on 2008-05-11
i'd just like to state again that i recommend that ppl don't use the official q3 client.  use ioquake, it has continued development of the official q3 client which died with v1.32 or whatever.

---

### Post by DeezNuts on 2008-05-13
I know this was solved but why not check out OpenArena? It is a popular FPS game that is created with the Quake III engine. It is also good fun, because it runs natively in Linux.

[www.openarena.ws](www.openarena.ws)

It is in the depos too.

```
sudo apt-get openarena
```

---

### Post by disturbedite on 2008-05-14
oh yes.  i definitely also recommend openarena.  i really like it.  the new version is great.  (openarena is based off of ioquake3, not the official q3 client/source, per se).

i also recommend nexuiz, it is even better than openarena in different ways, imo.

---

