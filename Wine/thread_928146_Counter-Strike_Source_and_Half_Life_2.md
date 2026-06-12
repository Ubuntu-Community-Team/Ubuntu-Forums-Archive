---
title: "Counter-Strike Source and Half Life 2"
date: 2008-09-23
forum: Wine
---

### Post by thedudething on 2008-09-23
How do you get Counter-Strike Source and Half Life games to work on Ubuntu when you've installed them on steam?

---

### Post by GSZX1337 on 2008-09-23
Try out [Wine Doors]("http://www.wine-doors.org/wordpress/").

---

### Post by thedudething on 2008-09-23
I installed steam on it and it said "Steam.exe (main exception): Cannot open blob archive file: CMultiFieldBlob(mem-mapped file): Failed to MapViewOfFile"

What do I do?

---

### Post by Dark9204 on 2008-09-24
Update wine to 1.1.5 and download steam, then run the steam installer with this command: wine start SteamInstall.msi.

HL2 and CSS works fine in wine. but you must run it in dxlevel 81

---

### Post by thedudething on 2008-09-25
still duz the same thing

---

### Post by ooobuntooo on 2008-09-26
I just launch the game from steam and it works.
I use playonlinux because it installs directx properly.

---

### Post by aoanla on 2008-09-26
You are using an installation of Steam on a Windows partition, probably NTFS formatted?

This doesn't work - it clearly says it doesn't work on the Steam AppDB page (nothing to do with Wine - it's the way in which Linux mounts NTFS partitions that causes the problems).

If not, then it's still a filesystem level problem you're having.

(See: [http://developer.valvesoftware.com/wiki/Steam_under_Linux](http://developer.valvesoftware.com/wiki/Steam_under_Linux) for example, which was one of the first hits googling for your precise error message, even if you didn't read the AppDB.)

---

