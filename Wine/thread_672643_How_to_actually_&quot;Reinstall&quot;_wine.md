---
title: "How to actually &quot;Reinstall&quot; wine?"
date: 2008-01-19
forum: Wine
---

### Post by stevothewise on 2008-01-19
Okay, as my experience thus far has dictated, linux, wine and everything else software wise hates me with a burning evil passion. Therefore: I have endless amounts of problems that are ridiculous and annoying. For today, I have a question about wine.

You see, I was trying to get Magic Workstation to work correctly under wine, as it does for everyone else who installs the microsoft core fonts. So I install them, it doesn't work. Okay, I uninstall Magic Workstation and try again, still doesn't work. So I figure "maybe I'll just start with a fresh thing of Wine, since that seems to work for everyone". So I do that, and now the program is running 500x worse than originally, and the nice wine configuration (you know how it puts the folder and subfolders and nice quick links under "Applications") does not show up, and being the epic noob I am, have no idea how to get it back there. Therefore I try a couple more times, this time making sure to check "Complete Removal", which in theory should wipe the knowledge to the computer is was on there in the past, which should make it so that it installs as if it were the first time. No no no, certainly not. So now, I am wine-less and have no idea how to fix anything. And all this annoying frustration has kept me freaking out at the terminal since I have next to zero knowledge of how to deal with anything.

So my question: is there anyway to COMPLETELY and WHOLLY destroy ALL information of a certain program (wine) on a computer so that it actually will set up the way it is supposed to?

---

### Post by Cappy on 2008-01-20
When you run a program as a user it stores your information in hidden folders in your home folder. These folders have a "." (dot) appended on the front. You can see them in the file browser if you click View-->"Show Hidden Files". You will want to delete (or move/rename!) the .wine folder.

You can delete the .wine folder from the terminal using ```
rm -rf .wine
```

On Windows you reinstall a program if it stops working. On Linux you remove (or edit!) your hidden folder with that program's preferences.

---

### Post by hikaricore on 2008-01-20
I still wouldn't actually recommend that method Cappy.
Although it will work just fine you're better off doing it this way:

```
sudo apt-get remove --purge wine
```

As for the problem with WINE not adding menu entries, many people have had this problem and it seems to be just an issue /w WINE in general.
Most of its menu entries are a pretty new thing, give it time and eventually the WINE dev team will get it right.

---

### Post by Cappy on 2008-01-20
The apt-get --purge would be better for getting rid of corrupt settings or if root was used to install something in wine (which happens more often than it should!). I can see the reasoning here.

That should be
```
sudo apt-get remove --purge wine
```

---

### Post by hikaricore on 2008-01-20
fixed the typo :P

---

