---
title: "TweetDeck"
date: 2014-09-28
forum: Wine
---

### Post by skppy1225 on 2014-09-28
Hi, guys and girls!

I'm trying to run the desktop version of TweetDeck via Wine and I can't seem to get it working. I've tried everything I could think of and was suggested to do, from running a virtual desktop to changing the screen resolution, but nothing is working. I just get a white box every time the program starts. Does anyone have any other suggestions?

The web version is fine, however, I like having it run as a separate application so I can quickly access my timeline and mentions.

---

### Post by Toz on 2014-09-28
Welcome.

Not sure which version of *buntu or wine you are running, but I got Tweetdeck to work on my Xubuntu 14.04 64-bit with [wine version 1.7]("https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa"). It seems to work better in 32-bit mode, so I created a 32-bit prefix and installed it via:
```
WINEARCH=win32 WINEPREFIX=~/.wineTD wine msiexec /i /path/to/TweetDeck.msi
```
Note: I also created a separate prefix for it ("WINEPREFIX=" above).

---

### Post by skppy1225 on 2014-09-28
Hi, Toz!

I'm sorry. I should have specified that I'm using Wine 1.6.2 and the latest version of Ubuntu 14.04.

I tried creating the wine prefix and launching the program from the prefix but I am still having the same problem. Nothing but a white box appears and nothing happens if I leave the program running.

---

### Post by Toz on 2014-09-29
Yes, I had the same problem with version 1.6.2. Upgrading to [wine version 1.7]("https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa") solves that problem. But it means you'll have to install a PPA and a version that is not shipped with 14.04.

---

### Post by skppy1225 on 2014-10-06
I'll give that a shot as soon as possible. Thank you so much for your help. I'll let you know if I'm still having the same issue after I upgrade.

---

