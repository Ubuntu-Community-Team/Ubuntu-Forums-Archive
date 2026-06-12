---
title: "Wine Cursor"
date: 2008-11-12
forum: Wine
---

### Post by sudomania4 on 2008-11-12
Is it possible to change the wine cursor? I tried using stardock's cursorxp to change the wine cursor, but it didn't work.

---

### Post by cogadh on 2008-11-12
AFAIK, Wine uses the system cursor, so if you (can) change it in your window manager, it should change it in Wine. 

BTW - I don't believe any of StarDock's Windows customization apps work in Wine.

---

### Post by AndrewRiedi on 2008-11-14
No, Wine doesn't use the system cursor.  Currently, Wine has its own set of black and white cursors that it uses.  The cursors need to be moved into wineserver before cursor theming can be properly implemented.  Unfortunately, that is not so easy of a task.

---

