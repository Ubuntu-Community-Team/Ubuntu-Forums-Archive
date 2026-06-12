---
title: "Wine and Counter Strike 1.6 problem"
date: 2008-06-30
forum: Wine
---

### Post by BlackSpot on 2008-06-30
Hi i install wine and install CS cs work perfect but the font in the game is very strange how i make it like in windows. I search for thread but dont understand how to do it. And 2nd things  when i start wine config is go on very large window and i cant move and use setings.

---

### Post by cogadh on 2008-06-30
You need to manually modify Wine's registry settings. Open the /home/<username>/.wine/system.reg file with a text editor (**not** OpenOffice) and scroll down to the section that looks something like this:
```
[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts]
"LogPixels"=dword:00000060
```
The "LogPixels" line in yours will say something different, modify to match what I have posted here, then save the file and re-run winecfg. The fonts should be back to normal.

NOTE - the ".wine" directory is a hidden directory, you will need to show hidden files in order to find it.

---

### Post by BlackSpot on 2008-06-30
thank a lot of with this wine manager work but ugly font in cs countinue

---

### Post by cogadh on 2008-06-30
I'm not really seeing what you mean. The fonts look normal to me (assuming you are referring to the chat and stats font).

---

### Post by BlackSpot on 2008-06-30
1 screenshot is with compiz font sux
2 screenshot is with metacity font sux :/
I need to play in metacity because in compiz my screen blinking

---

### Post by cogadh on 2008-06-30
Yeah, Compiz and Wine don't get along at all.

That second screen shot is a bit better, I think I see what you mean now, the fonts look "lumpy". You might try using [winetricks](http://wiki.winehq.org/winetricks) to install actual Microsoft fonts in Wine. I believe CS is using the Tahoma font, which does come with Wine, but doesn't look as nice as the "real" one from MS.

---

### Post by BlackSpot on 2008-06-30
i cant find how to choose other font in wine ?

---

### Post by cogadh on 2008-06-30
You don't choose a different font, you just install the actual MS font using winetricks and Wine uses that by default instead of the font it comes with.

---

### Post by BlackSpot on 2008-06-30
dude 10x you got 1 beer from me ;)
i fix font thanks to you

---

