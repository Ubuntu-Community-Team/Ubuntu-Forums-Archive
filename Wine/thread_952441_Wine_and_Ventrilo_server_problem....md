---
title: "Wine and Ventrilo server problem..."
date: 2008-10-19
forum: Wine
---

### Post by pzhukke on 2008-10-19
Heya!

I'm running a windows-version of a ventrilo server under wine on my ubuntu machine, but I've got some problems.

You see, when I start it, this is the end of my output:
> 20081019 00:03:05 Accepting connections on these interface(s).
20081019 00:03:05   1: 127.0.0.1
20081019 00:03:05
20081019 00:03:05 Accepting UDP Status/Control messages on these interface(s).
20081019 00:03:05   1: 127.0.0.1
20081019 00:03:05
20081019 00:03:05 READY:


And this is what it says in Windows:
> 20081019 00:03:05 Accepting connections on these interface(s).
20081019 00:03:05 1: 192.168.0.195
20081019 00:03:05 2: 127.0.0.1
20081019 00:03:05
20081019 00:03:05 Accepting UDP Status/Control messages on these interface(s).
20081019 00:03:05 1: 192.168.0.195
20081019 00:03:05 2: 127.0.0.1
20081019 00:03:05
20081019 00:03:05 READY: 

And when I run it under Windows, there's no problem to connect to the server, but I can't connect to it in Ubuntu.

The problem has something to do with my network, since I only get 127.0.0.1 as an interface in Ubuntu, while I get 127.0.0.1 and my local adress (192.168.0.195) given by the router - in Windows.


I am really in need of help, so please, share a bit of your time! :)


Thank you for being polite and helpful! :)
Eric.

---

