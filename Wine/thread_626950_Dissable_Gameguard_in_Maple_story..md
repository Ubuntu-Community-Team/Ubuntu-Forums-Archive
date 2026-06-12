---
title: "Dissable Gameguard in Maple story."
date: 2007-11-29
forum: Wine
---

### Post by Dwiman89 on 2007-11-29
Hi, I was just wondering. A friend of mine told me there are hacks that disable gameguard. I have done a lot of resherch on it, but its my understanding that gameguard is the reason Maple story wont run in wine. I would like to play the game but its not worth installing a virtual windows for maple story.. Just wondering if that would make it possible to play the game.

---

### Post by cogadh on 2007-11-29
Yes, GameGuard is the main reason MapleStory won't work. Basically it is a very intrusive rootkit-like hack and cheat prevention utility that installs its own driver in Windows that cannot run in Wine. However, I don't believe disabling GameGuard will fix the problem, since the MapleStory client performs a check at launch to ensure that GameGuard is running. If it isn't, then the client closes itself (on Windows, in Wine it either locks up or crashes).

---

### Post by nikoPSK on 2007-12-19
> **cogadh said:**
> Yes, GameGuard is the main reason MapleStory won't work. Basically it is a very intrusive rootkit-like hack and cheat prevention utility that installs its own driver in Windows that cannot run in Wine. However, I don't believe disabling GameGuard will fix the problem, since the MapleStory client performs a check at launch to ensure that GameGuard is running. If it isn't, then the client closes itself (on Windows, in Wine it either locks up or crashes).

that sucks, I asked nexon if there will be possible updates for linux or gameguard for linux but they basically told me to screw off... :(

---

