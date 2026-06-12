---
title: "I need help running a .msi under Wine"
date: 2012-01-14
forum: Wine
---

### Post by Thelinuxgeek on 2012-01-14
I'm installing some games on Wine, and I need to install a patch for a game so I can install mods and expansion packs for it. (The game is Impossible Creatures, great game :) ) Anyway, The patch I need to run is a .msi, and right-clicking and running it with Wine Windows Program Loader does nothing. It acts like Wine is loading, but nothing happens. Is there a trick to getting a .msi to work on Wine? Thanks in advance :)

PS, the name of the file is IC_Patch_101_English.msi, and it's on my desktop, should I move it somewhere else?

---

### Post by Paddy Landau on 2012-01-15
As no one has answered, I'll give you my view.

I don't know how to use Wine, and that's because I use PlayOnLinux (it's in the repositories). PlayOnLinux is a front-end to Wine and hides its complexity for you.

In your place, I would install your game using PlayOnLinux -- it allows you to load it into a separate "virtual drive", so it is separate from any other Windows applications (unless you choose otherwise).

Then use PlayOnLinux to install your .msi, but do so into the same virtual drive.

Unfortunately, Wine is a bit of a kludge and therefore not all applications will work; you may find that the .msi won't work.

Good luck.

---

### Post by oldos2er on 2012-01-15
Moved to Wine.

---

### Post by Soulcage on 2012-01-15
[http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f]("http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f")

---

### Post by Mark Phelps on 2012-01-16
The link below is to the WineHQ site entry for that game:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4845]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=4845")

Looks like there's a fair amount of work to even get it to install and work at all -- and when you're done, it only rates a Silver.  Pretty much a waste of your time unless you willing to live with little of the game actually working.

---

### Post by JustinR on 2012-01-16
.MSI files are for the Windows Installer Service, do you have that installed through WineTricks? It's called MSI2.

---

