---
title: "How to install package from launchpad.net?"
date: 2014-07-17
forum: Wine
---

### Post by Yamato_Hotsuin on 2014-07-17
I'm still newbie.
I want install wine from package launchpad.net, because my ubuntu can't connect to my modem.
This file i got from download, but i don't know to install it.
    wine-gecko2.21_2.21-0ubuntu1~ppa1~precise1.debian.tar.gz (40.4 MiB)
    wine-gecko2.21_2.21-0ubuntu1~ppa1~precise1.dsc (1.2 KiB)
    wine-gecko2.21_2.21-0ubuntu1~ppa1~precise1_amd64.deb (20.6 MiB)
    wine-gecko2.21_2.21-0ubuntu1~ppa1~precise1_i386.deb (19.8 MiB)
    wine-gecko2.21_2.21.orig.tar.bz2 (98.9 MiB)
Can you give me tutor?

---

### Post by Mark Phelps on 2014-07-17
The word "precise" indicates these are for Ubuntu 12.04 -- which is not supported anymore, as the current version is 14.04.

If you're still running 12.04, you need to consider using 14.04 instead -- before you mess around with installing Wine.

---

### Post by Yamato_Hotsuin on 2014-07-17
No, problem. This time, i'm using ubuntu 14.04 lts.

---

### Post by coffeecat on 2014-07-17
> **Mark Phelps said:**
> The word "precise" indicates these are for Ubuntu 12.04 -- which is not supported anymore, as the current version is 14.04.

Why would you think that? 12.04, desktop version included, is supported until April 2017. Although I agree that the OP may be better off with 14.04.

> **Yamato_Hotsuin said:**
> I want install wine from package launchpad.net, because my ubuntu can't connect to my modem.

You are severely limited in what you can do if you cannot connect to your modem. A better solution would be to fix the modem connection problem, after which you can install wine and anything else you want to from the repositories with the software centre. Perhaps if you give more details of your modem connection problem, people could help with that.

---

### Post by Yamato_Hotsuin on 2014-07-17
Thank's for sugestion, but i want can install it again if my ubuntu got problem.

---

### Post by Rob Sayer on 2014-07-17
> **Yamato_Hotsuin said:**
> Thank's for sugestion, but i want can install it again if my ubuntu got problem.

No, you want to try to fix the connection problem.  If it's just not configured properly, which is certainly possible, you'll just have to do it after re installing.

Start by copying and pasting this into the terminal:

```
sudo lshw -C network
```

then enter your password.  Copy the result and paste it here, wrapping it in code tags.

Actually, since that's a different issue, you should probably start a new thread in the wireless section with the network info posted there.

---

