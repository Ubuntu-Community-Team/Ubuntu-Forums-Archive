---
title: "Torrent problem"
date: 2005-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by pof on 2005-03-12
Hi
After dist-upgrade to Hoary, I have not been able to download using torrent. It looks like the ports 6881-6999 are blocked. No connection to tracker.
Router config is not altered. I refuse to reverse - Hoary is great.

Per Otto

---

### Post by kubla on 2005-03-12
Sounds more like an issue with either your firewall or your ISP then... or perhaps you've got a dud tracker? I'm torrenting a couple of iso's at the moment with no problems at all.

Do you have another OS there that you can try torrenting with just to exclude a problem specific to your ubuntu installation? I'm pretty sure you'll find the issue is downstream.

Ian

---

### Post by bored2k on 2005-03-12
[QUOTE=kubla]Sounds more like an issue with either your firewall or your ISP then... or perhaps you've got a dud tracker? I'm torrenting a couple of iso's at the moment with no problems at all.

Do you have another OS there that you can try torrenting with just to exclude a problem specific to your ubuntu installation? I'm pretty sure you'll find the issue is downstream.

Ian[/QUOTE]
 Make sure ports are forwarded.
No firewalls [firestarter] are on, if so, make them allow bt.

Bittorrent.com, download latest source package, it rocks ! ^_^

---

### Post by bored2k on 2005-03-12
[QUOTE=bored2k]Make sure ports are forwarded.
No firewalls [firestarter] are on, if so, make them allow bt.

Bittorrent.com, download latest source package, it rocks ! ^_^[/QUOTE]
 Hoary and bt have no connection at all.

---

### Post by pof on 2005-03-13
Hi again

The ports are forwarded OK. I could connect to the same tracker with another pc without any problems. My Cisco router did not reconfigure  :smile: during dist_upgrade to Hoary. Still the same problem.  

Per Otto

---

### Post by pof on 2005-03-13
Hi !  Problem solved

Iptables where established on my box.(dont know why) I uninstalled them since 
I am not using firewall (perhaps I ought to), and everything got back to normal.
Thanks for all replies - they lead me in the right direction.

Per Otto

---

