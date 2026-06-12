---
title: "PlayOnLinux League Of Legends Issue"
date: 2014-06-27
forum: Wine
---

### Post by Tristan_Williams on 2014-06-27
I am running League Of Legends 1.7
PlayOnLinux version 4.2.2
Wine Version 1.7.1

I can open League of Legends, play the game normally, and most features work the way they should, except the store.

When I go to access the store (not the shop during matches, but the one that you click on when LoL first loads) it either:
[LIST=1]
[*]Crashes, giving an error saying something about wine crashing
[*]Stays on this black screen, which nothing shows on
[/LIST]

I have followed the tutorials on the following sites with no success:
[LIST]
[*][http://www.playonlinux.com/en/topic-10986.html](http://www.playonlinux.com/en/topic-10986.html)
[*][http://askubuntu.com/questions/459888/shop-and-in-game-item-shop-not-working-in-league-of-legend-lol](http://askubuntu.com/questions/459888/shop-and-in-game-item-shop-not-working-in-league-of-legend-lol)
[/LIST]

What kind of things can I try from here to get the store working?

---

### Post by Vladlenin5000 on 2014-06-27
> Crashes, giving an error saying something about wine crashing

Well... That "something" might be of the utmost importance...

---

### Post by Tristan_Williams on 2014-06-27
I followed another tutorial and fixed the issue

---

### Post by Vladlenin5000 on 2014-06-27
Great :p.

Now, how about posting that tutorial and/or what steps you took to solve the issue? It might be helpful for other user.

PS - Also please mark this one as solved by using the thread tools in your first post. Thank you.

---

### Post by Tristan_Williams on 2014-06-28
> **Vladlenin5000 said:**
> Great :p.

Now, how about posting that tutorial and/or what steps you took to solve the issue? It might be helpful for other user.

PS - Also please mark this one as solved by using the thread tools in your first post. Thank you.

Haha well I did, but I'm unmarking it, because the problem is back.

First of all, I followed PART of [this]("https://bitbucket.org/Xargoth/tuxlol/wiki/Home") tutorial. When I got to the part where the command:
```

mono tuxlol.exe patch --dir "/home/$USER/.wine/dosdevices/c:/Program Files/Riot Games/League of Legends"

```

It spit back the following error:
```

The specified directory is invalid.

```

So what directory do I need to put in place of "/home/USER/.wine//dosdevices/c:/Program Files/Riot Games/League of Legends"?

---

### Post by sandyd on 2014-06-28
Moved to WINE

---

### Post by shanu_novic on 2014-09-10
> **Tristan_Williams said:**
> I am running League Of Legends 1.7
PlayOnLinux version 4.2.2
Wine Version 1.7.1

I can open League of Legends, play the game normally, and most features work the way they should, except the store.

When I go to access the store (not the shop during matches, but the one that you click on when LoL first loads) it either:
[LIST=1]
[*]Crashes, giving an error saying something about wine crashing
[*]Stays on this black screen, which nothing shows on
[/LIST]

I have followed the tutorials on the following sites with no success:
[LIST]
[*][http://www.playonlinux.com/en/topic-10986.html](http://www.playonlinux.com/en/topic-10986.html)
[*][http://askubuntu.com/questions/459888/shop-and-in-game-item-shop-not-working-in-league-of-legend-lol](http://askubuntu.com/questions/459888/shop-and-in-game-item-shop-not-working-in-league-of-legend-lol)
[/LIST]

What kind of things can I try from here to get the store working?

on the second link, i think someone said you have to install internet explorer 8 component for the shop to work.

---

### Post by shanu_novic on 2014-09-10
[COLOR=#000000]one of these should work for tuxlol patching.

```
"/home/USER/.PlayOnLinux/wineprefix/LeagueOfLegends/drive_c/Riot Games/League of Legends/"
```
```
"/home/USER/.PlayOnLinux/wineprefix/LeagueOfLegends/dosdevices/c:/Riot Games/League of Legends/"
```
```
"/home/USER/.wine/dosdevices/c:/Program Files/Riot Games/League of Legends"
```[/COLOR]

---

