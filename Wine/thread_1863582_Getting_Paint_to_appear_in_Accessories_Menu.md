---
title: "Getting Paint to appear in Accessories Menu"
date: 2011-10-18
forum: Wine
---

### Post by krakket on 2011-10-18
Hopefully this is a simple question, does anybody know how to get Paint to show up under the accesories menu in Wine? I tried pasting it in the same area as notepad (c:\windows) but this didn't do the trick. I'd like to be able to access it from the menu bar instead of having to go into a folder and click on the .exe every time.

If so could the same method be used to make Wine Wordpad show up in the accessories directory? I know I have it installed because I can open .rtf files with it but it isn;t under the wine menu in applications.

---

### Post by Tweak42 on 2011-10-19
> **krakket said:**
> Hopefully this is a simple question, does anybody know how to get Paint to show up under the accesories menu in Wine? I tried pasting it in the same area as notepad (c:\windows) but this didn't do the trick. I'd like to be able to access it from the menu bar instead of having to go into a folder and click on the .exe every time.

If so could the same method be used to make Wine Wordpad show up in the accessories directory? I know I have it installed because I can open .rtf files with it but it isn;t under the wine menu in applications.

You didn't mention what desktop environment you are using (gnome 2.0 or unity), but the method is pretty similar: create a new menu launcher entry using the command line syntax "wine <windows path>".

So for example in gnome.
[LIST=1]
[*]Right click 'Applications' menu - select 'Edit Menus'
[*]Select 'Accessories' on the left pane - click 'New Item' button on the upper right
[*]Name: 'Paint'
[*]Command: 'wine c:\windows\system32\mspaint.exe'
[*]*Comment and Icon optional
[*]Click OK and enjoy.
[/LIST]

---

### Post by krakket on 2011-10-20
Thanks a bunch! I'm using gnome 2 so those instrustions were what i needed.

---

