---
title: "Playonlinux/Wine Leftovers in Dash"
date: 2011-10-25
forum: Wine
---

### Post by Untold on 2011-10-25
I have tried to search this and could not find it.  I hope this is not a double.  I am trying to get rid of icons that deleted Playonlinux prefixes leave behind.  I am running Ubuntu 11.10 amd64 with Playonlinux 4.0.13.  I just want to clean up my dash a bit without having to uninstall Playonlinux.  Any help would be sweet.  

Again, if this is a double, my humble apologies..

---

### Post by ergo-proxy on 2011-10-26
Check here:
[http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa](http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa)

---

### Post by Radical_Dreamer on 2011-10-28
```
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.{xpm,png}
rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png}

```

This seemed to work for me as it says on his link

---

### Post by ergo-proxy on 2011-10-28
Good, please mark the thread as solved.

---

