---
title: "Repopulating the Wine Start Menu entry"
date: 2017-08-02
forum: Wine
---

### Post by mr-good555 on 2017-08-02
Long story short, there were programs in Wine that were uninstalled, but their Start menu entries were still there. I deleted quite a few, then accidentally deleted a few entries that were still installed, namely the ones for Notepad and other Windows Accesories. I, soon after, deleted the entire folder, hoping that reinstalling Wine would replace or return those entries, but it didn't happen.

Do you have any ideas how to get back Wine's Start Menu entry?

It doesn't matter if all the manuallyinstalled items are back (I can manually do that). I just need notepad, iexplore, winetricks, etc to be in the Start Menu. Feels odd without them there.

---

### Post by noxarcz on 2017-08-04
If you are talking about Start Menu Wine shortcuts, i can tell you the path to the folder where they are supposed to be, but i dont know how to create new ones, i would like to know as well.

The .desktop files (contains path to exe, icon,...) can be found in
[B]home/username/.local/share/application/wine/Programs/foldername/file.desktop
[/B]Tip: If you need to add an argument (parameter) to the exe launch, just add it at the end of the line with EXEC command, for example **-no-cef-sandbox** to fix the non functional Steam store page

However, you also need a Desktop Entry file, those are located in
[B].local/share/desktop-directories
[/B]The files have the extension **.directory **and their content looks like this for example

[Desktop Entry]
Type=Directory
Name=Steam
Icon=folder


I suppose one could manually replicate those files for certain exes, with proper paths etc.

---

### Post by mr-good555 on 2017-08-13
That certainly helps. All I need now is a listing of the default set of shortcuts, then I can mimic it. Even a screenshot of it would probably work. XD

Many thanks. ^u^

=========

I noticed so many more shortcuts here of programs I don't use or have uninstalled. Makes me sad to say that Ubuntu has a lot of cataloging and cleaning up to do when using apt and stuff. This is how I got this problem in the first place. All the extra unused debris from uninstalled programs.

---

### Post by dacha on 2017-09-18
As the original developer of Wine's menus, I can tell you how it's done.

Find the .lnk file of the menu or desktop entry. Convert it to a Windows path, ie. C:\\path\\to\\file.lnk, which you can do easily with:
```
winepath -w /unix/path/to/file.lnk
```

Once you have that, run:
```
winemenubuilder C:\\path\\to\\file.lnk
```
(You may need to quote the Windows path and/or use double-backslashes; please experiment.)

Please let me know if you have any problems or suggestions ;-).

---

