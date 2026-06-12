---
title: "Getting Ruckus to Work (And Internet for that matter)"
date: 2008-09-18
forum: Wine
---

### Post by raiderleaf on 2008-09-18
Hi, I tried installing Ruckus on my Ubuntu (newest version). For those of you not familiar with ruckus, it is like an iTunes thing for College Students which allows us to download music legally. Anyways, once installed, I tried to sign in on it and it said the following:

Cannot connect to the Ruckus server:
Error: A security error occurred (12175).

Please check your firewall settings to verify that Ruckus is allowed to make outgoing connections.


After this error, I also tried to make some sort of a connection with Wine to my other hard drive which has Windows XP installed on it. I want to be able to use my library on the windows partition but I don't know how to make the relation between that petition and the "virtual" petition that Wine made.

Any help would be appreciated Very Happy

-Raiderleaf

---

### Post by hikaricore on 2008-09-18
Sorry friend, Ruckus does not run under WINE.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3601](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3601)

You may want to look into one of the various VMs such as qEMU or VmWare.
I don't know for sure if this would work but you could give it a shot.

Also be warned trying to use WINE with an existing windows installations files or configurations could cause other problems on the windows side of things.
This is generally not advised.

---

