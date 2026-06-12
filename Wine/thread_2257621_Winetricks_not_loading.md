---
title: "Winetricks not loading"
date: 2014-12-21
forum: Wine
---

### Post by UncleMonty on 2014-12-21
Winetricks is not loading at all. I am using Ubuntu 14.04 lts, 64 bit. Advice please.

---

### Post by howefield on 2014-12-21
Thread moved, you'll probably get quicker help here in the "*Wine*" forum.

---

### Post by andrew.46 on 2014-12-24
Winetricks uses zenity to create a gui so perhaps this is broken on your system? Test the actual functioning of the commandline winetricks by trying a simple command such as:

```

andrew@ilium~$ **[COLOR="#FF0000"]winetricks list[/COLOR]**
apps
benchmarks
dlls
fonts
games
settings
andrew@ilium~$ 

```

and possible more useful:

```

andrew@ilium~$ **[COLOR="#FF0000"]winetricks --version[/COLOR]**
20140302

```

---

### Post by UncleMonty on 2015-01-20
winetricks list
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned a string containing the word 'unknown', as if a voice had cried out in terror, and was suddenly silenced.

winetricks --version
20140302

---

### Post by andrew.46 on 2015-01-20
Wonder who thought up that error message :). Try:

```

winetricks --gui

```

---

