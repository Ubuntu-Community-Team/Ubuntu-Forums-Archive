---
title: "[SOLVED] Slow torrent downloads in Deluge"
date: 2008-06-29
forum: x86 64-bit Users
---

### Post by Nazty_Nayt on 2008-06-29
Hey all, for some reason my deluge just isn't working like it should or any other bit torrent client for that matter.  My ISP gives me 16Mbps down, and 2Mbps up.  I have the speed set up correctly in the preferences, but most downloads that should take about 20 minutes are taking about 5 hours, even with a lot of seeders.  Can someone help me out here?

Also in my speed settings for download speed Deluge caps me at 9000, even though it should be up at 15000

---

### Post by felker2 on 2008-06-29
First thing to check: have you taken care of port forwarding to your system? In other words: is your bittorrent client reachable from Internet?

[http://portforward.com/](http://portforward.com/) and/or UPnP are helpful.

---

### Post by Nazty_Nayt on 2008-06-29
Ok, that site doesn't really have anything for deluge, but they do for azureus, would it be the same since they're both bit torrent clients?

---

### Post by LO Matt on 2008-06-29
> **Nazty_Nayt said:**
> Hey all, for some reason my deluge just isn't working like it should or any other bit torrent client for that matter.  My ISP gives me 16Mbps down, and 2Mbps up.  I have the speed set up correctly in the preferences, but most downloads that should take about 20 minutes are taking about 5 hours, even with a lot of seeders.  Can someone help me out here?

Also in my speed settings for download speed Deluge caps me at 9000, even though it should be up at 15000

Well 16Mbps is more like 2MBps.  Deluge reports in KiB.  So you're probably allowing the max anyway.  

And yes, open ports and forwarding ports needs to be done for any bittorrent client behind a firewall, not just azureus.

---

### Post by Nazty_Nayt on 2008-06-29
I opened the ports on my router, but it's not going any faster at all.  Should I switch to a different torrent client or what?  I mean it takes me like a whole day to download a CD when it should take 20 minutes. :(

---

### Post by felker2 on 2008-06-30
You say you opened up the ports. Have you tested that deluge client is reachable from Internet? You can test that in deluge like this: Edit -> Preferences -> Network and then "Test Active Port". That will start a browser that will tell whether your bittorrent client is reachable from Internet.

If portforwarding is not done correctly, you might consider using UPnP: check it on the same page Edit -> Preferences -> Network. It could also be a good idead to select different ports than the well known 6881; your ISP might block it.

Furthermore: Have you limited your *upstream* bandwidth in deluge to a max of half of your available upstream bandwidth?

About Azureus: Azureus will show with green happy faces whether your port forwarding is done correctly, so that might be more informative then deluge's info.

---

### Post by felker2 on 2008-06-30
BTW: what makes you think your download should take only 20 minutes, not 5 hours?

---

### Post by Nazty_Nayt on 2008-07-01
Thanks Felker2, I think it's just the Deluge program.  Cause when I do everything with Azureus it works fine (Green smileys, lol).

And the only reason I knew my downloads should be going quicker was last month when I was back on Vista my torrents were working like a charm.  Probably the only thing on Vista that did work right.
:guitar:

---

### Post by TenPlus1 on 2008-07-01
I only have a 2mb line but can download movies within 45 minutes...  You just need to tweak Deluge (I use ports 65521 to 65529 because some isp's block torrent ports 6881-6889)... I enable uPnP, Nat-PmP and Peer Exchange... I limit bandwidth to 190 instead of setting to 0-unlimited, and also limit max connections per sec to 8, max connections to 200 and max upload slots to 8...  you can change these since your connection is faster...

---

### Post by philinux on 2008-07-01
> **LO Matt said:**
> Well 16Mbps is more like 2MBps.  Deluge reports in KiB.  So you're probably allowing the max anyway.  

And yes, open ports and forwarding ports needs to be done for any bittorrent client behind a firewall, not just azureus.


When I first installed Deluge on a clean system I chose random ports and didn't have to do any port forwarding for it to work correctly.
I'm behind a router with it's firewall on.

---

