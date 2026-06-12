---
title: "[SOLVED] Opening the WoW direcory in Wine"
date: 2007-12-09
forum: Wine
---

### Post by jordanae on 2007-12-09
I downloaded WoW in Linux and it works. But I want to access the directory in wine. How do I do that?

---

### Post by jordanae on 2007-12-09
How do I open the WoW directory?

---

### Post by hikaricore on 2007-12-09
If you're using Gnome you'd open Nautilus and browse to your WoW folder:

"~/.wine/drive_c/Program\ Files/World of Warcraft"

Likewise if you're using KDE you'd open Konqueror and do the same.  ^_^

The WINE configuration and data storage folder is a hidden folder like most proper software titles use to keep your home folder looking clean and tidy in normal view.
Enabling "show hidden files" will also allow you to browse there directly.

---

### Post by jordanae on 2007-12-09
> **hikaricore said:**
> If you're using Gnome you'd open Nautilus and browse to your WoW folder:

"~/.wine/drive_c/Program\ Files/World of Warcraft"

Likewise if you're using KDE you'd open Konqueror and do the same.  ^_^

what is Nautilus?

---

### Post by hikaricore on 2007-12-09
Your default file browser that you use to view your files in Ubuntu.

---

### Post by jordanae on 2007-12-09
Well I put that in and I guess I don't have a wine folder

---

### Post by jordanae on 2007-12-09
Well I think I found the directory but it won't open. It's called "World of Warcraft.Ink"

---

### Post by hikaricore on 2007-12-09
Yes you do, just enable "show hidden files" from the view menu, or hit ctrl+H in Nautilus.

You should then see all the hidden files in your home directory, Including the .wine folder.

This all assumes you have installed both WINE and WoW which I'd imagine would have to happen for this thread to exist. :)

> **jordanae said:**
> Well I think I found the directory but it won't open. It's called "World of Warcraft.Ink"

That's a ***dows desktop link file, this would not be what you're looking for.

---

### Post by jordanae on 2007-12-09
I found it. Well thanks for your help!

---

### Post by Kosimo on 2007-12-09
Go to home directory

Then press control + H   in order to show hidden files

Then search this foler .wine

---

### Post by LookTJ on 2007-12-09
or /home/.wine/   :)

---

