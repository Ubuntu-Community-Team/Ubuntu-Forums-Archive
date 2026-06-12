---
title: "Wine does not appear on menus"
date: 2019-12-17
forum: Wine
---

### Post by lou6 on 2019-12-17
Running Xubuntu 18.04 64 bit - I installed wine64 and wine-stable via synaptic but wine does not appear in any menu.  I tried running winecfg from terminal - that works but no joy on menus.  I installed a windows program (Lucas Chess) which created a desktop icon (so I can run the program) but still no menus.  Tried a restart - still nothing.  Is there a way to get the Wine menus working (both desktop and Whisker)?  Sorry if this should be in Xubuntu section - I'm never sure where to post.

Thanks in advance for any and all help...

---

### Post by Autodave on 2019-12-17
On my Xubuntu 18.04, it appears at the very bottom of the first menu: the one that you see after clicking on the mouse in the top left corner.

---

### Post by CatKiller on 2019-12-17
It's not clear from your post what you mean.

You don't run Wine itself, you use Wine to run other things, so there aren't menu entries for launching Wine. If that's what you were expecting, then there aren't any. 

There are menu entries for things like "run with Wine" on right-click, but the Wine packagers decided to disable them for some reason. Correcting that behaviour is done by copying .desktop files from an examples directory to an applications directory as I recall, but I only use Wine as part of Proton these days so I can't remember the specifics.

---

### Post by lou6 on 2019-12-17
I understand that wine is not run by itself but in past Xubuntu installs wine has appeared as a menu entry with installed windows programs listed under the wine category.

Unfortunately, I don't have an examples directory from which to copy the missing .desktop files.

---

### Post by Holger_Gehrke on 2019-12-17
The examples directory CatKiller is talking about is '/usr/share/doc/wine-stable/examples' which has a file 'wine.desktop' that should give you a context menu entry for Windows executables, MSI packages and Windows shortcuts (.lnk-files) in the file manager if you copy it to one of the places that desktop files are expected to be ('usr/share/applications/' or '~/.local/share/applications/').
And on my XUbuntu 18.04 I do have a category Wine in the whisker-menu into which Windows-programs that are installed through wine go automatically (wine seems to produce .desktop files that go into ~/.local/share/applications/wine/Programs/ ... if a Windows installer does whatever is needed to produce a menu entry in windows). It's at the very bottom of the list of categories and I either have to scroll down in the categories list or enlarge the menu to see it.

Holger

---

### Post by Dennis N on 2019-12-17
In my XFCE, this desktop file in the indicated directory:
```
[dmn@Roxanne ~/.local/share/desktop-directories]$ cat wine-wine.directory 
[Desktop Entry]
Type=Directory
Name=Wine
Icon=wine
```
gives me the Wine category in the attached image.

Maybe it will work for you?

---

### Post by lou6 on 2019-12-17
Unfortunately, my/usr/share/doc/wine-stable/examples directory does not contain the wine.desktop file - only file there is a Wine Windows Program Loader

Dennis - thanks for the reply.  I already have the file you posted in the same location but it isn't giving me a menu entry for wine...

---

### Post by deadflowr on 2019-12-17
> Sorry if this should be in Xubuntu section 
There is no such place.
But there is a wine section, which is where I've moved this thread.

[s]FWIW, desktop file names, like the wine.desktop name, can differ from the name the desktop file is for.
the wine.desktop's Program name should be Wine Program Loader, if you look at the contents of the file.[/s]

scratch that, I think I misread the post.

Actually,
> my/usr/share/doc/wine-stable/examples directory does not contain the wine.desktop file - only file there is a Wine Windows Program Loader
that's what the wine.desktop file is, they are the same thing.

---

### Post by lou6 on 2019-12-17
Okay, but I still already have it in .local/share/desktop-directories on my system and I don't have a wine entry on whisker menu or on the system menu (the one that appears when I right-click on the xubuntu desktop).

Never mind - I've located the bug reports on this subject and can see that there is some debate going on between the Debian gang and the ubuntu developers over whether this is a self-inflicted wound or a necessary protection so that feeble-minded users (like me) will not try to install virus-ridden windows apps.  It's been going back and forth for a year or more and the only losers are those who are simply trying to get a windows app to run.

I'll mark this as closed and try very hard not so post in the wrong place anymore.

---

### Post by CatKiller on 2019-12-17
> **lou6 said:**
> I'll mark this as closed and try very hard not so post in the wrong place anymore.
If we didn't give the mods threads to move, how would they fill their time?

---

### Post by deadflowr on 2019-12-17
> **CatKiller said:**
> If we didn't give the mods threads to move, how would they fill their time?

The tug of war games, I guess.

---

