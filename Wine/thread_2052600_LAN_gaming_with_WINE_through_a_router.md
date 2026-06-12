---
title: "LAN gaming with WINE through a router"
date: 2012-09-03
forum: Wine
---

### Post by jared both on 2012-09-03
How do I setup and play a LAN game (specifically Age of Wonders 2) using Wine? Can I do this with my wireless internet router?

I tried searching for the specific IP address regularily and Haguichi but both do not connect. I know there is something to do with port-forwarding for Huguichi, but I can't seem to find a tutorial for that.

Much appreciated! and happy labour day weekend fellow Canadians

---

### Post by stevenroose on 2012-11-04
Bump.

I'm trying to setup a LAN connection to other gamers in my network as well.
(It's for Battle for Middle Earth in this case, but that shouldn't matter; before with Anno 1602 I couldn't get a LAN connection either.)

Is there a general way of achieving LAN access for games in Wine/Crossover for Linux?

---

### Post by gordintoronto on 2012-11-04
Is this gaming within your own LAN, or going out to the Internet? If the issue is port forwarding, then you should figure out how port forwarding works on your specific router. It begins with getting admin access to the router, and most modern routers have menus to go from there.

I only have one program which I run under Wine, Irfanview. I don't think it accesses the Internet directly, it just sends a URL to Firefox.

---

### Post by Tweak42 on 2012-11-06
> **stevenroose said:**
> Bump.

I'm trying to setup a LAN connection to other gamers in my network as well.
(It's for Battle for Middle Earth in this case, but that shouldn't matter; before with Anno 1602 I couldn't get a LAN connection either.)

Is there a general way of achieving LAN access for games in Wine/Crossover for Linux?

Pretty much all network connections with regards to programs run using wine should just work transparently. However for Battle for Middle Earth according to a [wine appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2713") user post back in Janurary, LAN gaming was not working.  I doesn't appear that anyone followed up on it, so either it was fixed in later versions or you should file a bug report so a dev can look into it.

---

