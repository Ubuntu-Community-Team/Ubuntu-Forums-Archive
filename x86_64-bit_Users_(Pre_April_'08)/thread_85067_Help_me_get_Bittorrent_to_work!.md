---
title: "Help me get Bittorrent to work!"
date: 2005-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by pusman83 on 2005-11-01
I'm on an iMac 333 and the big trouble seems to be that I'm on a proxy server (in res). 

The default BT client for Breezy won't let me input proxy settings so I downloaded Azureus, for which no port gets detected in the wizard.

Any tips?

---

### Post by craks on 2005-11-02
Use Azureus:rolleyes:

---

### Post by pusman83 on 2005-11-02
Have you read my initial post? No port gets detected with Azureus.

I have to give a proxy URL, server, username and password to get online.

---

### Post by tiagobt on 2005-11-02
Do you hava Java installed? Are you behind a firewall? If you are, you need to disable it at least in one port so that Azureus can connect.

---

### Post by monway on 2005-11-03
Bittorrent should work out of the box on Breezy 5.10.
If you want to make sure you can use it, I suggest to install the following clients.

```
sudo apt-get install gnome-btdownload bittorrent bittorrent-gui bittornado bittornado-gui
```

Those clients and gui are both equally good. One of them has more features than the other. If you want to use one as default you can just simply right-click on the bittorrent file and select to open with whichever client you choose, whichever is best for you.

I hope this helps.

---

### Post by pusman83 on 2005-11-03
Problem with BTornado is that I can't seem to input the Proxy server info anywhere so it just times out if I try to download something.

---

### Post by pusman83 on 2005-11-04
[http://forums.degreez.net/viewtopic.php?t=5361&highlight=proxy](http://forums.degreez.net/viewtopic.php?t=5361&highlight=proxy)

No proxy support for Bittornado. D'oh!

---

### Post by pusman83 on 2005-11-04
[QUOTE=tiagobt]Do you hava Java installed? Are you behind a firewall? If you are, you need to disable it at least in one port so that Azureus can connect.[/QUOTE]

How do I do that?

---

### Post by monway on 2005-11-06
I'll be honest here. Adding proxies to bittorrent will visibly slow down your downloads and it doesn't hide you from the internet from whatever you may be downloading. The speed is in the numbers and ports. as a general rule I would personally have a router that has a built in firewall and open ports by triggers 6881~6889. Visit the website. Here's a link which may be your anwer. ```
http://userpages.umbc.edu/%7Ehamilton/btclientconfig.html
```

---

