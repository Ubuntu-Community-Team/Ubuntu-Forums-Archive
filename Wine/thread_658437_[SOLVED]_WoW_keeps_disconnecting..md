---
title: "[SOLVED] WoW keeps disconnecting."
date: 2008-01-04
forum: Wine
---

### Post by SpiXe on 2008-01-04
Hey. Im running with Ubuntu 7.10 and playing WoW using Wine. But I have a problem.. Whenever I play WoW it kinda disconnects after 10-30 minutes. When it happens I can still move around and see ppl talking and I can read what they say but I can't speak or do emotes or attack or anything. I can only run around and see other ppl play. This goes on for 5 minutes approx before I get disconnected.
I dunno what's wrong, but it may seem like something is wrong with the upload connection?
If anybody knows about this please help :)

Spixe (And sorry for my english ^^)

---

### Post by cryptonicpyro on 2008-03-29
I've been experiencing this same problem. I am running wow with a wireless network connection but its not dropping the connection. I would try to attempt to run wow off a hard line rather than wireless but I am not able to do to my circumstances. Does anyone have any ideas?

I'm going to try with other game to see if its just world of warcraft or all online games.

---

### Post by SpiXe on 2008-08-04
> **cryptonicpyro said:**
> I've been experiencing this same problem. I am running wow with a wireless network connection but its not dropping the connection. I would try to attempt to run wow off a hard line rather than wireless but I am not able to do to my circumstances. Does anyone have any ideas?

I'm going to try with other game to see if its just world of warcraft or all online games.

That could be a possiblity.. When i use the internet (browser) i disconnects sometimes, not often though. But nor i can use a cable .. :S

---

### Post by SpiXe on 2008-08-21
> **cryptonicpyro said:**
> I've been experiencing this same problem. I am running wow with a wireless network connection but its not dropping the connection. I would try to attempt to run wow off a hard line rather than wireless but I am not able to do to my circumstances. Does anyone have any ideas?

I'm going to try with other game to see if its just world of warcraft or all online games.

Now I've tried to run with cable. That works great, with no dc's at all :) But I still can't see why WLAN won't work... If anybody knows how to solve this, please help ;)

---

### Post by pedro_orange on 2008-08-21
Sounds like a networking issue.

You'll probably have more luck within that section of the forums, rather than in the wine section.

I'd start your posts with what hardware your wireless cards are, using a command such as:

```
sudo lshw | less
```

Or you can use:

```
sudo ethtool eth0
```

Replace eth0 with the identifier for your network interface card.
Do you use Linux drivers for your network cards? Or NDISWRAPPER?

Google for it and you might find someone else has had the same problem.

Good luck

---

### Post by SpiXe on 2008-08-27
I think i've made it work now.. I installed Wcie instead of the network manager in gnome. It seems to work fine now.

---

