---
title: "how to enable default desktop effects in suse 10.3?"
date: 2008-04-19
forum: openSUSE and SUSE Linux Enterprise
---

### Post by haha123 on 2008-04-19
hi every one.I just installed opensuse 10.3 on one of my desktops.I use KDE.how (where is the option?) to enable default compiz in KDE? thanks in advance...

---

### Post by Growbag on 2008-04-20
a good question, and not one I know the answer to!

I use the default KDE effects for drop shadows only, you can enable them from the (old style KDE menu) under Settings - Desktop - Window Behaviour, Or the Control Center.

If you have a "Translucency" option as the far right hand side tab, you can enable it from there.

It also does translucency of course.

I think Compiz is installed by default though, have you tried typing *compiz* at a command prompt?

You will also have to make sure you have Direct renfering enabled first of course, open a terminal and type:

```
glxinfo | grep direct
```

If it responds with "Yes", then you are in luck, otherwise you will have to install the correct driver for your video card (through Yast), then enable direct rendering, which can be a pain with an Nvidia card!

---

### Post by joshrobinson on 2008-04-20
```
compiz --replace
```

after you have your drivers correct of course
you could also compile fusion-icon from source and use that to start it

sorry i cant be more helpfull, been awhile since i ran openSuse
its a great OS, but the only problem is its not as fast for me as ubuntu

---

### Post by Erunno on 2008-04-21
There's no Yast module in the Qt frontend for easily switching from KWin to Compiz. The GTK+ version does feature such a module, but it also forces XGL down your throat so this solution is also suboptimal. I'm not really into Compiz as it doesn't have KWin's amount of features but I'm a bit puzzled that the KDE maintainers didn't even try to integrate Compiz into KDE given the amount of hype it generates.

---

