---
title: "Different versions of wine in software center and disk"
date: 2014-04-17
forum: Wine
---

### Post by vortexmak on 2014-04-17
Hi,

I had installed wine and is currently at version 1.6.1 on my system.

I received an autoupdate today which showed a wine version of 1.7.x

However running ```
wine --version
``` still shows 1.6.1

Ubuntu software center shows that the new version of wine is intalled (1.7.16)

[IMG]http://i1216.photobucket.com/albums/dd366/vortexmak/Screenshotfrom2014-04-17012335.png[/IMG]

I can't figure out why two different versions of wine are being shown

---

### Post by jbaerboc on 2014-04-17
I would run "Synaptic Package Manager" and check to see what it says. In my experience it is much more reliable than the Software Center. Worse comes to worse add the official WineHQ PPA and then use synaptic to update it and see if that gets you there. 

Another option is to use PlayOnLinux to manage your Wine needs. For example I have it install different games in different version of Wine based on what has worked best for me in the past. It is also a decent way to install older or newer versions of Wine on your system.

---

### Post by Sandgoose on 2014-04-23
I "think" it's possible to have multiple versions installed side by side if you open a terminal and type wine followed by pressing tab it may display multiple executable versions?

---

