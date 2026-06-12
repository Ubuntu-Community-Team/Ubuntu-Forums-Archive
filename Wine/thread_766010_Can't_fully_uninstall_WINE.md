---
title: "Can't fully uninstall WINE"
date: 2008-04-24
forum: Wine
---

### Post by Stabilityonitsown on 2008-04-24
Hi guys, I just uninstalled wine through
"$ Sudo apt-get remove wine" and it did it successfully then I noticed something, all the programs and menus and files in particular where still there from the wine install, so I went ahead and went on package manager and right-clicked and clicked "mark for complete removal" and applied. But then the menus and files where STILL there, so I went ahead and did 
"$ sudo aptitude purge wine"
and that didn't work too. So I decided to restart GUI with ALT+CTRL+BACKSPACE
and the menus where STILL there, so I went into the default menu editor(right-click edit menu) and didn't see wine anywhere at all, then I went into Alacarte and STILL didn't see wine anywhere, but yet it was in my menu! Someone please help me out.

---

### Post by reviver on 2008-10-28
I had this same problem.  Is there a better way to uninstall Wine than removing the packages?  I'm kind of confused on this one.

---

### Post by marshalium on 2008-10-28
When you remove wine with the package manager it removes the global application but it does not remove the files that wine installs for each user. You will have to remove them yourself.

Wine installs its .desktop menu entries in ~/.local/share/applications/wine
 and ~/.local/share/desktop-directories. To remove all of wine's menu entries remove the stuff from this directories.
```
rm -R ~/.local/share/applications/wine
```
```
rm ~/.local/share/desktop-directories/wine*
```

Also wine creates ~/.wine where it stores your fake c: drive and the wine registry. If you want to remove all of your installed wine applications and your wine settings then remove ~/.wine.
```
rm -R ~/.wine
```

---

### Post by reviver on 2008-10-28
Thank you for answering such an old, necro'd thread.  Resolved all my issues.

=]

---

### Post by PoopyTheJ on 2008-11-11
Thank you old thread I know but this was driving my bats__t crazy!

---

