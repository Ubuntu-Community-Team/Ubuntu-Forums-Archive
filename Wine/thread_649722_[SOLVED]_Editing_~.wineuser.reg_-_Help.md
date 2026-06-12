---
title: "[SOLVED] Editing ~/.wine/user.reg - Help"
date: 2007-12-25
forum: Wine
---

### Post by dethredic on 2007-12-25
So I want to run warcraft 3 in wide screen, and these are the instructions.
> 
Change the following values in user.reg. These are hexadecimal for 1680x1050. This is only necassary for older versions of World Of Warcraft. Since Blizzard has released a patch, widescreen is supported.

File: ~/.wine/user.reg

[Software\\Blizzard Entertainment\\Warcraft III\\Video] ...
...
"resheight"=dword:0000041a
"reswidth"=dword:00000690

[Source]("http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_(WSXGA)#Warcraft_III_and_World_of_Warcraft")

So, I can't find this file. I tried searching for it: nothing came up.

I went into the registry, and changed those values, but that does not work.

Thanks.

---

### Post by dethredic on 2007-12-25
Ok, nvm I found it. Darn hidden files.

---

### Post by nipponzen on 2008-03-30
where did you find the file?
I'm trying to edit the registry in Wine...

---

### Post by happyhamster on 2008-03-30
- Editing the registry can be done by running:

regedit

- Or by importing a text file that contains the registry keys:

regedit filename.reg

- Editing the registry files manually is possible also (but using regedit is better). The text files can be found in the hidden .wine folder in your home dir.

---

### Post by dethredic on 2008-03-31
I just searched, and included hiden files in the search.

---

