---
title: "League of Legends on Ubuntu"
date: 2011-10-04
forum: Wine
---

### Post by sm3 on 2011-10-04
I followed the outdated, yet relatively functional instructions here:
[http://na.leagueoflegends.com/board/showthread.php?p=15100375#post15100375](http://na.leagueoflegends.com/board/showthread.php?p=15100375#post15100375)

I ended up to the point where my launcher loads and works (For the most part)... but whenever I try to get into a game, it says "Something has caused this program to crash." in a Wine Error message... and then the game loads the "Game has crashed, please Reconnect" Screen.

Could I please get some help here? or at least a lot of thumbs up voting for LoL to learn from the GOOD things of HoN and make a native UBUNTU Client? (You can thumbs up in this forum: [http://na.leagueoflegends.com/board/showthread.php?p=15341417#post15341417](http://na.leagueoflegends.com/board/showthread.php?p=15341417#post15341417))

Just a note: Even though Ubuntu is all about open source and such, I'd be willing (and I'm sure some others would be too) to pay 35 USD or so to support and ensure the development of a Native Ubuntu client in the near future.

---

### Post by Perfect Storm on 2011-10-04
Moved to Wine Section.

---

### Post by ubupirate on 2011-10-04
Might be helpful for someone if you ran LoL via terminal with wine and post any debug errors that may come up.

Could certainly tell us what might possibly be causing it to crash. :)

---

### Post by Soulcage on 2011-10-04
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141")

Says that adobe air is the problem.

---

### Post by pjd99 on 2011-10-04
Some say the ACE client can work. I've never had any success with it.

I've tried (Riot's client and ACE) with wine, the winelol ppa and PlayonLinux with only partial success. I could get as far as champion select IF I could get the Air client running. This required manually starting the rads_user_kernel, waiting a short time, then running the lol.launcher.exe. 3/4 of the time it would fail to start, with an inter-process communication error.

I think the game started to launch, but wine could never grab the window, so it always had to be manually killed.

I gave up, the LoL client is based on Adobe Air, a port may have been possible but Adobe dropped support for it on Linux. And given how unstable the LoL client is on Windows I think it will be a long time before it runs smoothly under Wine.

Save yourself the headache and play it on Windows. It's the main reason I still have a Windows partition.

---

### Post by pjd99 on 2011-10-04
> **sm3 said:**
> I followed the outdated, yet relatively functional instructions here:
[http://na.leagueoflegends.com/board/showthread.php?p=15100375#post15100375](http://na.leagueoflegends.com/board/showthread.php?p=15100375#post15100375)

I'm pretty sure that guide was written before Riot completely changed the out-of-game client. I don't know why, but the directory structure changed significantly about 6 months ago, it may have been an Air upgrade.


> **sm3 said:**
> 
Just a note: Even though Ubuntu is all about open source and such, I'd  be willing (and I'm sure some others would be too) to pay 35 USD or so  to support and ensure the development of a Native Ubuntu client in the  near future.

100% agree, I'd be willing to drop 30-50 bucks on a native client, though it doesn't really fit their microtransaction model.

And as much as I prefer LoL to HoN, the code base it's built on seems much more stable than LoL's (it actually has a native Linux client, too bad the HoN community are a bunch of ****s.)

---

### Post by sm3 on 2011-10-04
I would partition with windows... but I don't exactly OWN windows.

The ACE launcher seems to work fine... I can get through champion select and everything.

It's just when launching the actual game that it crashes.

---

### Post by pjd99 on 2011-10-04
Given how buggy the Windows client actually is and the state of the Mac beta client (apparently Transgaming were doing it, but Riot shut it down last month) my guess is that you're out of luck.

If they actually fix the Windows client, it might start working in Wine (but don't hold your breath)...

---

### Post by b2zeldafreak on 2011-10-04
> **pjd99 said:**
> Given how buggy the Windows client actually is and the state of the Mac beta client (apparently Transgaming were doing it, but Riot shut it down last month) my guess is that you're out of luck.

If they actually fix the Windows client, it might start working in Wine (but don't hold your breath)...

This is basically what I've seen as well. The Window's client seems to be very volatile.

I'd love a native Ubuntu/Wine compatible client (although 35$ might be a bit steep to just be able to play the game xP), but until Riot gets serious about coding it's gonna be hard to make it happen.

Imo they need to not hire someone for the port, but rather do it themselves (and ditch Adobe Air) or let the community develop the Linux version.

---

### Post by madjr on 2012-02-06
> **b2zeldafreak said:**
> This is basically what I've seen as well. The Window's client seems to be very volatile.

I'd love a native Ubuntu/Wine compatible client (although 35$ might be a bit steep to just be able to play the game xP), but until Riot gets serious about coding it's gonna be hard to make it happen.

Imo they need to not hire someone for the port, but rather do it themselves (and ditch Adobe Air) or let the community develop the Linux version.

or maybe using googles NaCl.

[http://na.leagueoflegends.com/board/showthread.php?t=1792062](http://na.leagueoflegends.com/board/showthread.php?t=1792062)

---

