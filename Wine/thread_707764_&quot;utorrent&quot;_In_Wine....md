---
title: "&quot;utorrent&quot; In Wine..."
date: 2008-02-25
forum: Wine
---

### Post by Dissident85 on 2008-02-25
Hi all, I am having a few little issues with running utorrent in wine. Firstly i cant get my little network config icon to turn green from red... even tho my router is configured correctly, and i am downloading at the maximum possible speed for my connection. That isn’t really a big issue, just wanted to know if that is a sort of side effect of running utorrent in wine. Secondly I cant view the files, pears, peaces??? Anyone know why? And finally the colours are shocking all grey and black. I herd there is a way to change that? anyone know how?

---

### Post by mikedep333 on 2008-02-25
In case this is of any help, transmission's (a new lightweight linux-native BT client) latest version is available on 7.10 through the backports (enable them under synaptic) and it will be the default BT client on 8.04. You might want to try that.
[http://www.transmissionbt.com/](http://www.transmissionbt.com/)

---

### Post by papafreebird on 2008-02-26
Why not use native linux torrent app?  I use and love utorrent in windows but when running linux I use ktorrent.  It is basically a linux clone to utorrent.  You can find it in synaptic.

---

### Post by varangian on 2008-02-28
utorrent and Wine do seem to have some quirks - I've posted a couple of threads on other such which you can search for if interested. Re the oddities you report:

The icon thing is probably a router issue so I'd recheck port forwarding. ISTR utorrent has a built-in port check option so see what it thinks. It's perfectly possible to get torrents merrily chugging along without the port being set up correctly - I've had this on XP. My own utorrent/Wine combo doesn't manifest this problem so it's unlikely to be a Wine related issue.

The peers/pieces etc. tab thing might just be something simple like the window size - when I first started it up the top of the tab had gone right to the bottom of the window and I had to fish around with the cursor and drag it back into view. Try maximising the window. Also (I don't have utorrent in front of me and don't really remember) isn't the details pane something you have to turn on in settings?

I also get the colours thing but don't be surprised if it changes. Currently in my torrents pane what should be whitespace is blackspace and looks pretty ugly. However, a while back I had enough torrents on the go to fill the pane and, coincidentally or not, the window colours suddenly toggled over to looking more or less identical to the XP version. Then I had to nuke my settings and it toggled back again. But Wine is a beta so we just have to live with these little quirks :)

---

### Post by Nameless_one on 2008-02-28
[Deluge](http://deluge-torrent.org/) seems to have matured enough, too. It's a native gtk application written in Python, and it works very well. Fast and snappy, and achieves good speeds, in my (brief) experience. 

If you want something full-featured, you can also try Azureus (although it's heavy).

---

### Post by Sammi on 2008-02-28
uTorrent as a whole works great in Wine, but it doesn't do automatic port forwarding very well.

So you'll have to do that part manually.

Howto guides here: [http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm) (just choose your router on the first page, and uTorrent on the second, and you'll get a nice howto)

---

