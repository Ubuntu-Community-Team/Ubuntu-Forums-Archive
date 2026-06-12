---
title: "[SOLVED] Something weird"
date: 2008-05-05
forum: Wine
---

### Post by Tryfon on 2008-05-05
Something weird is going on in my system. Every time I start up firefox, the Wine desktop flashes for a second before firefox actually starts! And I think that firefox takes a little longer than before to startup. How can this happen? Unfortunately I can't recall the exact time that this phenomenon first appeared.
I have Wine 0.9.59-0ubuntu4 installed, from the Synaptics package manager.

---

### Post by Saint Angeles on 2008-05-05
are you running firefox through wine? i don't see how else they are related at all.

---

### Post by Tryfon on 2008-05-05
Of course not! I'm running firefox 3 beta 5 normally. I'm thinking that perhaps a plugin could be the cause, but I don't suspect anyone specifically. Here is a list of my plug ins and addons in case it is of any help:
Add-ons
[LIST]
[*]Adblock Plus
[*]Adblock Filterset.G Updater
[*]All-in-One Sidebar
[*]British English Dictionary
[*]CustomizeGoogle
[*]Download Statusbar
[*]DownloadHelper
[*]FlashGot
[*]Forecastfox Enhanced
[*]Greek spelling dictionary
[/LIST]

Plugins:
[LIST]
[*]DivX Web player
[*]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
[*]iTunes Application Detector
[*]Java(TM) Plug-in
[*]QuickTime Plug-in 7.2.0
[*]Shockwave Flash
[*]Totem Web Browawe Plugin 2.22.1
[*]VLC Multimedia Plugin
[*]Windows Media Player Plug-in 10
[/LIST]

---

### Post by Tryfon on 2008-05-06
Anyone?

---

### Post by Kinst on 2008-05-06
Remove wine and rename your .wine folder and see what happens.

---

### Post by Tryfon on 2008-05-06
well, I tried that and it worked. But when I reinstalled wine, same think happens again. I even completely uninstalled wine (by deleting the .wine folder too), but still the same after reinstalling. It pisses me off! It's very odd...

---

### Post by Hybrid Son Of Oxayotl on 2008-05-07
Did you tried to desactivate "iTunes Application Detector" ?

---

### Post by Tryfon on 2008-05-08
Did that. Still the same.

---

### Post by Tryfon on 2008-05-08
Well, I completely uninstalled and reinstalled firefox and everything is back to normal. Shame we didn't find out the reason for this anomaly. Anyway, thanks all for your help!

---

### Post by radtek on 2008-05-08
Adblock  does something weird and I don't like it. It has caused FF to lock up and subsequently the the whole desktop. I've experienced this repeatedly in 7.10 and now in 8.04. Also, why should it be necessary to enter your "root" pwd to install Adblock? Why does FF need a root access?

I've disabled it and will do a clean install in teh AM. As it is I consider my machine infected or compromised somehow.

---

### Post by Urbanmoth on 2008-05-08
> **Tryfon said:**
> Something weird is going on in my system. Every time I start up firefox, the Wine desktop flashes for a second before firefox actually starts! And I think that firefox takes a little longer than before to startup. How can this happen? Unfortunately I can't recall the exact time that this phenomenon first appeared.
I have Wine 0.9.59-0ubuntu4 installed, from the Synaptics package manager.

I have an identical symptom - 8.04 with Firefox 3 beta 5
before I go do what Tryfon did - does anyone have any ideas?

Firefox Extensions:
Adblock Plus 0.7.5.4
BugMeNot 1.8
FlashGot 0.9.9
Java Console 6.0.02
NoScript 1.6.4
StumbleUpon 3.18
Ubuntu FireFox Modifications 0.5

UM

---

### Post by zimiq on 2008-05-08
Newest FlashGot supports download managers true wine.
Uncheck "Automatic download manager detection" on FlashGot Advanced prefences tab.

---

### Post by Urbanmoth on 2008-05-08
That was it - Thanks zimiq :)

---

### Post by Tryfon on 2008-05-21
Yeap, that was it. Thanks!

---

