---
title: "Cannot add to panel"
date: 2007-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Trymic on 2007-12-23
I am looking to add rhythmbox to panel but unfortunately i can
When i right click on the panel i only get Help and About Panels nothing else.
Also when i right click the firefox icon i only get launch, the properties option is not there anymore
Any suggestions?

Thank you in advance

---

### Post by saru411 on 2007-12-23
are you right clicking on the center of the panel?

---

### Post by Trymic on 2007-12-23
I tried everywhere on the panel with no luck.

---

### Post by purplenite on 2007-12-23
I'm having the same issue right now. For me the problem started a few minutes ago after I changed some panel settings in gconf-editor. Reverting those settings isn't helping, I still have only Help and About when I right-click on a panel.

---

### Post by Ehtetur on 2007-12-23
I had some gnome-panel issues when I was mucking about with compiz...

Have you tried restarting the gnome panel?
> killall gnome-panel

If that doesn't work, try restarting dbus:
> sudo /etc/init.d/dbus restart

---

### Post by purplenite on 2007-12-23
neither one of those solved my problem. thanks for the help tho.

---

### Post by Ehtetur on 2007-12-23
purplenite - you made some mods with gconf-editor right?
So maybe if you rename the folder .gconf to _gconf and then logout/login.
It's important to **rename .gconf; do not delete .gconf**  :twisted:

When you log back in, a new.gconf folder will be created with default entries %gconf.xml

---

### Post by purplenite on 2007-12-23
i solved it. gconf-editor>apps>panel>global>locked_down was checked, i must have accidentally clicked it. unchecking the box returns the normal options to the right-click menu.

---

### Post by Trymic on 2007-12-24
Thank you purplenite

it solved my problem too. excellent

---

