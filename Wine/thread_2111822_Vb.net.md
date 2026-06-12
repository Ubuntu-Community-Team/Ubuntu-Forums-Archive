---
title: "Vb.net"
date: 2013-02-03
forum: Wine
---

### Post by ultimatetechie on 2013-02-03
Is there a way for me to run a Windows™ Visual Basic (VB.NET) program on Linux? Wineskin (for mac) and WINE (for Linux) both don't do this out of the box - is there some sort of hack or patch I can use?

---

### Post by RealmEleven on 2013-02-07
I recall that the *.NET Framework* does not ship with *VB.NET* application packages. So, *VB.NET* applications are not likely to work on *Wine* (e.g. without the *.NET interpreter* or "*JIT compiler*") unless you install the applicable *.NET framework* in *Wine *- which you can download from *Microsoft*'s website.
.
This is not saying that this approach will work but that without the *.NET Framework* installed, I don't see how uncompiled, interpreted applications made in *VB7 *and above will work with *Wine*.
.
But I think that it's always worth rolling the dice to see if something like this might work...

---

### Post by Mark Phelps on 2013-02-07
According the the WineHQ page below, all the recent versions of .NET have really poor ratings -- indicating that trying to run anything that depends on .NET is likely to fail:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586")

---

### Post by Zteam on 2013-02-08
The Best way to deal with this is to install winetricks and then run winetricks from a terminal and install dot.net from there (this would require you have to a Windows license)

---

### Post by RealmEleven on 2013-02-09
I also noticed that there is also an extra package, called Mono, which takes care of some of the .NET functionality on Wine...

---

