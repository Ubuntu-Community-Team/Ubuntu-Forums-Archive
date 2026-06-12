---
title: "Where do I put WoW?"
date: 2008-05-12
forum: Wine
---

### Post by TrezenChath on 2008-05-12
If I were to bring WoW over onto my Ubuntu box via an external harddrive from a Windows box, in what directory should I place the folders and files? Does it make a difference, or will Wine automatically startup when I run WoW?

---

### Post by Kinst on 2008-05-12
In your home folder there's a hidden folder called .wine.

/home/you/.wine/drive_c/ is your fake windows computer. From there you put the files wherever they would go in windows. 

Generally when you work with wine you want to reinstall though, by just running the installation .exe file like you would in windows.

---

### Post by DoktorSeven on 2008-05-12
Well, fortunately with World of Warcraft, you can just migrate over your installed directory anywhere and it will run in place, no reinstall necessary.  Just put it anywhere and run **wine Wow.exe**.

---

### Post by Kinst on 2008-05-12
Really? Wow, that's pretty impressive.

---

### Post by ajackson on 2008-05-13
> **Kinst said:**
> Really? Wow, that's pretty impressive.
Yeah WoW sticks nothing in the registry so copying it is a valid installation method. Might have something to do with WoW having a Mac version since most of the code is shared and Macs don't have registries either.

---

