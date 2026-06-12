---
title: "Diablo 3 firewall configuration"
date: 2017-12-23
forum: Wine
---

### Post by deadwheel on 2017-12-23
I'm running Linux, more to the precise point: Ubuntu 17.10 (with my firewall set to block everything). I've tried to connect to the Diablo 3 game servers for the past week or so without success.
Note: I have been following Blizzard's guide for port forwarding located here [https://us.battle.net/support/en/article/7842,](https://us.battle.net/support/en/article/7842,) however, those rules seems to be incomplete. I can do the following: Connect to battle.net via the app, authenticate, chat with friends, start the game, see what games are available on Torment levels but not connect to a game with the firewall enabled. If I shut it off it connects nicely. Thus it's a firewall problem.

Has anyone else run into a similar problem with UFW enabled? As I said, it's rather clear that it's the firewall. When I am viewing the logs it says "Connection UFW blocked" and some random Blizzard server IP, but the log doesn't specify a port from what I can see. Is there any way to debug this efficiently?

---

### Post by deadwheel on 2017-12-23
Solved it! The Diablo client has a dependency on the Blizzard Downloader, so in order to play Diablo on Linux with firewall enabled you need to first allow the Downloader for some background connections. Probably to download server data or something and then allow the Diablo3 ports listed.

---

### Post by deadflowr on 2017-12-24
*Thread moved to **Wine***

---

