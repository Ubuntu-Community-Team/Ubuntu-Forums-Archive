---
title: "How do you uninstill &quot;Knight Online&quot; from Wine?"
date: 2007-10-26
forum: Wine
---

### Post by UK-Wobbie on 2007-10-26
Hey do any one know how to uninstall "Knight Online" from Wine?
I have instilled it and it did not work so i like to uninstall it! 

It as not got a uninstill link :( Any one?

Thanks :)

---

### Post by cogadh on 2007-10-26
Open a terminal and type "uninstaller" without the quotes. That will launch the Wine uninstall application and should allow you to uninstall the game correctly.

---

### Post by UK-Wobbie on 2007-10-26
> **cogadh said:**
> Open a terminal and type "uninstaller" without the quotes. That will launch the Wine uninstall application and should allow you to uninstall the game correctly.

Hey thanks for the reply,
I have had a go going to Wine and Uninstall.. But when i click on the game and click uninstall it do not do anything! 

No box or anything :confused:

---

### Post by UK-Wobbie on 2007-10-26
Do any one know how to delete the name from the uninstall list?
And how can i delete Wines registrty to deleted this game and from the uninstall list. :)

---

### Post by cogadh on 2007-10-26
If that was the only thing you had installed in Wine, then you can just delete the .wine directory from your home directory then run "winecfg" again to re-create it. If not, then there are a couple of things you can try. First you can try deleting the game's program folder from ~/.wine/drive_c/Program Files/ then re-run uninstaller and it should detect that the game is no longer present and remove it from the list. If that doesn't work, then run "regedit" in the terminal, navigate to HKEY_LOCAL_MACHINE/Software/Microsoft/Windows/CurrentVersion/Uninstall and delete the key that belongs to the game.

---

