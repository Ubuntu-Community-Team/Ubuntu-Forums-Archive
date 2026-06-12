---
title: "[SOLVED] Cedega and Gutsy (ubuntu 7.10)"
date: 2007-10-21
forum: Wine
---

### Post by Subban on 2007-10-21
Formatted and installed newest Ubuntu after backing up all data.

Installed Cedega 6.0.2 and updated to 6.0.3, put all my games back in place and now can't play a single one (Guild Wars, Eve Online, WoW).
Starting cedega normally from menu/launcher just silently doesn't start the games, running cedega from a terminal gives this :

```
subbass@subbass-desktop:~$ cedega
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
```


For each game I try and start I get one output of :

```
cat: /home/subbass/.transgaming_global/Fonts/tg_font_version: No such file or directory
[: 337: 81: unexpected operator
```


Any way to fix this or suggestions on things to try?

---

### Post by Subban on 2007-10-23
Removed the .cedega folder in ~/ and ran Cedega to rebuild the .cedega folder in ~/

In Cedega I then added a "World of Warcraft" game folder, Cedega then built that folder structure ok. I then closed Cedega and copied over ONLY the backup World Of Warcraft folder into ~/.cedega/World Of Warcraft/c_drive/Program Files

In Cedega I then added a game shortcut inside the World of Warcraft folder pointing to WoW.exe, changed the settings as normal to improve play and it all worked.

My best guess is something in copying the entire the whole .cedega folder from backup broke something though the folder structure was identical to last install so I'm not sure what/how.

---

### Post by DeMoN3 on 2007-10-28
Excuse me,can you help me to install cedega on ubuntu 7.10 ?

---

