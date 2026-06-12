---
title: "Dota 2 Ubuntu 12.04 how?"
date: 2012-09-06
forum: Wine
---

### Post by fixles on 2012-09-06
Hi,

I've seen loads of people online say they can get Dota 2 working no problem with wine but I've spent about 5 hours trying and I can only get it to run with horrible screen tearing and horrible lighting effects.

I've followed the wine hq quide which helpfully starts with "Wine should be compiled with all the required features to run 32-bit  Windows applications and games, and all of Wine's dependencies should be  satisfied" but no link to a guide or where to find.

I can get steam running no problem. Can anyone tell me how to get Dota 2 working or how to get "all the required features to run 32-bit  Windows applications and games" or a link to a good guide please?

I'm running wine 1.5 .12 Ubuntu 12.4.1 64Bit

Thanks.

---

### Post by Lila7714 on 2013-01-02
I think they mean to get all of the 32 bit libraries. Try getting ia32-libs package.

---

### Post by kreggz on 2013-01-03
Try installing Steam through Playonlinux. Its working for me but I am using Precise 32 bit.

---

### Post by mentorious on 2013-01-04
I installed with Crossover Games a few days ago, but you can do it also with Playonlinux or clear wine etc.

In Playonlinux choose Install > Games > Steam, after this install Dota 2 in Steam. When game doesn't start up, click RMB on title, then Properties > Set launch options and paste following command:

> -novid -sw -nod3d9ex -noborder Instructions for "clear" wine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444)

---

