---
title: "New *almost* Xubuntu user"
date: 2006-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by arulzz on 2006-11-12
I installed 64-bit Ubuntu today, (actually Xubuntu) and replaced my Gentoo 64-bit.

I was using Gentoo 64-bit for the last one year and got bored with it, decided to try Ubuntu. Its quite good, I should say.

It got installed without my typing anything. :-? A big change from Gentoo, but I guess it was worth it - I have the rest of the evening to do something else.

I really missed the old apt-get commands - I used to use Debian 64-bit before moving to Gentoo 64-bit.

Anyway, just wanted to say hello to all of you guys. :)

---

### Post by loell on 2006-11-12
welcome to the forum, and welcome again to the deb world :mrgreen:

---

### Post by jamesr on 2006-11-12
Welcome to the forum. You can still use the apt-get commands infact I do quite frequently. Just go to a terminal window.

---

### Post by arulzz on 2006-11-12
> **loell said:**
> welcome to the forum, and welcome again to the deb world :mrgreen:Salamat po :D

---

### Post by arulzz on 2006-11-12
> **jamesr said:**
> Welcome to the forum. You can still use the apt-get commands infact I do quite frequently. Just go to a terminal window.

Thanks for the welcome James :D. Yes I did install all my servers (lighttpd, mysql, ssh) on the terminal with apt-get.

Is the latest Ubuntu kernel 2.6.17? Thats what I see with apt-cache search. Gentoo has 2.6.18 in the official release and 2.6.19 in the vanilla-sources. Is there something I should add/modify in /etc/apt/sources.list?

---

### Post by RAOF on 2006-11-13
> **arulzz said:**
> Thanks for the welcome James :D. Yes I did install all my servers (lighttpd, mysql, ssh) on the terminal with apt-get.

Is the latest Ubuntu kernel 2.6.17? Thats what I see with apt-cache search. Gentoo has 2.6.18 in the official release and 2.6.19 in the vanilla-sources. Is there something I should add/modify in /etc/apt/sources.list?

No.  Once an ubuntu version is **released** no new versions of packages get added (although bugfixes and security patches will get backported and applied).  Also, there's a "backports" repository which gets selected packages taken from the new development version built for previous releases, but only a few apps end up in there.

It was recently discussed, and decided against, to include newer kernels in the backports.  They just have the potential to break too many things.

If you **really** want to be cutting-edge, the Fiesty (the current development version) repos contain 2.6.19 git kernels at the moment :).

---

### Post by dermotti on 2006-11-17
Xubuntu + Lighttpd = the hotness :-) 


Welcome aboard.

---

