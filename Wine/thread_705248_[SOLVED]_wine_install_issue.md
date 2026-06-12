---
title: "[SOLVED] wine install issue"
date: 2008-02-23
forum: Wine
---

### Post by noremacyug on 2008-02-23
earlier today i had wine installed and working fine.  i installed it to use utorrent, however i ended up decided on azureus.  so i uninstalled wine.  now i'm wanting it to once again try another windoz program.  for whatever reason after going to the application/add-remove and installing wine it doesn't show up in the applications list like it did on after my first time installing it.

anyone have any clues/solutions?

thanks in advance.

---

### Post by noremacyug on 2008-02-23
anyone????

---

### Post by FrozenFox on 2008-02-23
Open up the terminal, then..

sudo apt-get update
sudo apt-get install wine
whereis wine
If it indeed installed from the output above, sudo apt-get purge wine
sudo apt-get install wine

Essentially, update your repos, reinstall wine, totally purge it to make sure something weird didn't happen to keep it from adding an entry, then install it again from the repos.
Then report back.

---

### Post by noremacyug on 2008-02-23
ok, did all of that.  wine was installed, i purged it and then reinstalled it.  still no shortcuts on the apps menu.  perhaps i just need to create and add shortcuts to the apps menu.  what's you're thoughts?

and thanks by the way.

---

### Post by FrozenFox on 2008-02-23
Very strange indeed..

I assume you're in gnome, so can you please run alacarte and check to see if the wine folder stuff in question is there but perhaps just not checked or something?

For your use, in case you can't figure out the problem, my shortcuts in the start menu and their commands are:

"Browse c drive"  xdg-open ~/.wine/drive_c
"Uninstall wine software" uninstaller
"Configure wine" winecfg
And I have playonlinux and wine-doors installed as well. The links to windows wordpad and regedit would be wine wordpad and wine regedit respectively, i imagine, if you use those links.

---

### Post by noremacyug on 2008-02-24
heres a screenie showing what i have.  no sign of wine in alacarte.  yet the files are installed.

also, how do i check the wine.cfg file.  i don't see it anywhere.

---

### Post by noremacyug on 2008-02-24
anyone have any ideas, this is driving me nuts.  i think i'm running into the same situation with cedega as well.  i've installed it once, unistalled and now when i reinstall none of the shortcuts are in the menu.

---

### Post by noremacyug on 2008-02-24
WOOT!!! i got it fixed.  i'm pretty sure that it was merely a case of my editing the menu to remove some shortcuts in wine.  it saved the menu config in a file and it didn't matter how many times i unistalled/reinstalled wine because that menu config file was still in existence and keeping wine from showing up.

i hope some of that made sense.  anyhow, for documentation purposes, here's what i did.

via the wonders of google i found a command to completely remove a program

```
aptitude purge <program>
```

in my case,....
```
sudo aptitude purge wine
```

after that i went to /home/"login name", enabled "show hidden folders" and wiped out anything i found wine related, like.....oh.... say..... the wine folder that was still there.

next i just so happened to see the folder /home/guy/.config and thought i'd take a peak in it.  lo and behold in there is the menus folder.  i opened that up and gave it a looksy.  i noticed a bunch of files that said something like "modified" (i can't remember the exact term) or something in the file name.  so i backed out and completely deleted the menus folder.  soon as i did i checked alacarte and stuff that i had removed had come back.  i then reinstalled wine and everything was back to normal.

i appreciate the help guys.

---

