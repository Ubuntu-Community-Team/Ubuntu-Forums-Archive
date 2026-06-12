---
title: "Can't edit applications menu / menu will not display"
date: 2008-12-18
forum: x86 64-bit Users
---

### Post by BightningLug on 2008-12-18
I had just installed a cd/dvd burning program, but it didn't appear in the multimedia menu so I used the Edit Menu option. I found the burning program listed in the multimedia folder but was not checked. I checked it and saved the changes and closed the window. Now the Applications menu will not display. When I click Applications, I see a small box, maybe 4px by 4px appear at the top left corner above the Ubuntu logo where the menu should pop-up from. I have the menu on the bottom of the screen instead of the top. When I click System->Preferences->Main Menu, nothing opens. I cannot access any of the programs that are listed in the Applications menu.

Is there a way to repair the applications menu? The Places and System menus still function and display everything as usual, but the Main Menu application isn't working or is just refusing to run.

---

### Post by BightningLug on 2008-12-18
Seems I found a fix. I found that there were undo versions of the menu under ~/.config/menus so I opened up the last undo file there and saved it over the applications.menu file. I would still like to know how to avoid this happening again and/or what caused it.

---

