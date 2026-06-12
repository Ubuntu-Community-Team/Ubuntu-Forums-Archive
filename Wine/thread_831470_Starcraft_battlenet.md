---
title: "Starcraft battlenet"
date: 2008-06-16
forum: Wine
---

### Post by MegaUA on 2008-06-16
When ever i try to run battlenet, it displays a black screen with a user name field where you can time (though the rest of the screen is black) but i am unable to do anything, since wine ends up freezing what can i do?

---

### Post by cogadh on 2008-06-16
I posted this over in your original thread in the Gaming & Leisure forum, didn't notice you had posted again here.

Known issues with Battle.NET:
Warcraft3 Battle.net Doesn't work (Needs AcceptEx) - [http://bugs.winehq.org/show_bug.cgi?id=9787](http://bugs.winehq.org/show_bug.cgi?id=9787)
starcraft doesn't display battle.net menus correctly - [http://bugs.winehq.org/show_bug.cgi?id=2467](http://bugs.winehq.org/show_bug.cgi?id=2467)
Starcraft/Diablo/Battle.net crashes from font metrics problem - [http://bugs.winehq.org/show_bug.cgi?id=5253](http://bugs.winehq.org/show_bug.cgi?id=5253)
StarCraft Battle.net-Hitting the Browse button hangs the game - [http://bugs.winehq.org/show_bug.cgi?id=9500](http://bugs.winehq.org/show_bug.cgi?id=9500)

That last one sounds remotely similar to the problem you are having and it is reported it can be fixed by just unchecking "Allow the window manager to control the windows" in winecfg. It could also be related to the menu display problem, which I don't believe has a real fix.

---

