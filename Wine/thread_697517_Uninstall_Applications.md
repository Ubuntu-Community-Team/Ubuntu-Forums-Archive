---
title: "Uninstall Applications"
date: 2008-02-15
forum: Wine
---

### Post by nebu on 2008-02-15
i installed some applications through wine..... later i uninstalled these apps using wines uninstal wine software wizard.... but however the entries of these programs in the  Applications > Wine > Programs menu is not going away!!! how do i remove these from this list???

---

### Post by dannyboy79 on 2008-02-15
there should be a file located in /usr/share/app-install/desktop/ that is something like WINEAPP.desktop

or maybe in /home/daniel/.local/share/applications/

BE CAREFUL though, you can just move it or rename it by adding a .test on the end of the filename. then hit ctrl-alt-backspace, that will restart X and you can then check your Applications menu.


Otherwise, there's a menu editor within System, Preferences, Main Menu

good luck

---

### Post by nebu on 2008-02-16
thnx.... that seems to have done the trick!!

---

