---
title: "Can't Browse C:\ Drive"
date: 2008-01-19
forum: Wine
---

### Post by Cardamar on 2008-01-19
The problem here is simple: I just can't browse my C:\ Drive. Upon navigation to the Browse C:\ Drive command via Applications > Wine > Browse C:\ Drive, nothing happens. Literally, nothing. No error message or anything, no windows appear. Any help?

---

### Post by hikaricore on 2008-01-19
That must be a new menu item for WINE cos I've never heard of it.

The location is *~/.wine/drive_c* you may want to run the menu editor to see what it's actually linking to.

---

### Post by EXCiD3 on 2008-01-19
> **hikaricore said:**
> That must be a new menu item for WINE cos I've never heard of it.

The location is *~/.wine/drive_c* you may want to run the menu editor to see what it's actually linking to.

Yes i think it is. In Gnome, Places->Home, then press Ctrl-H or check the "Show Hidden Files/Folders" option in the menu. and browse to /.wine/drive_c

---

