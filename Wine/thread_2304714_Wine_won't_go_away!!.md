---
title: "Wine won't go away!!"
date: 2015-11-29
forum: Wine
---

### Post by dante3 on 2015-11-29
I followed the instructions at [http://askubuntu.com/questions/15551/how-to-remove-wine-completely](http://askubuntu.com/questions/15551/how-to-remove-wine-completely), as well as running sudo apt-get remove winetricks, but the other 3 Wine applications (Configure Wine, Uninstall Wine Applications, and Browse C: Drive) are still there. How do I get rid of them.

---

### Post by furtom on 2015-11-29
Did you try the supplimentry steps toward the bottom of the page:


[B]Run these to get rid of menu entries instead of (or in addition to) using "Edit Menus".
[/B]
```
rm $HOME/.config/menus/applications-merged/wine*
rm -r $HOME/.local/share/applications/wine
rm $HOME/.local/share/desktop-directories/wine*
```

---

### Post by dante3 on 2015-11-29
Actually, no. Thanks for bringing that to my attention. I'll try it.

EDIT: It didn't work. All three of the above commands returned a 'No such file or directory' error.

---

### Post by furtom on 2015-11-30
I'm surprised. 

Just a lark: Have you rebooted since you did the uninstall?

---

