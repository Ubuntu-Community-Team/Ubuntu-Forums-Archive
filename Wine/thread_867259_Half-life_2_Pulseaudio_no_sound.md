---
title: "Half-life 2 Pulseaudio no sound"
date: 2008-07-22
forum: Wine
---

### Post by el mariachi on 2008-07-22
I think pulseaudio is preventing my Half-life 2 from giving me sound (any source game in fact) the valve logo has sound (the game 'intro') but the game itself hasn't.
How can this be??

---

### Post by Nexusx6 on 2008-07-23
I'm just about to head to work so I apologize for the really fast solution.

In terminal, run this:
```
padsp winecfg
```

Then, go to your ~/.wine/drive_c/Program Files/Steam/ folder, and type this in
```
WINEDEBUG=-all padsp wine steam.exe
```

you should have sound in any game you launch from steam now.

---

### Post by YaroMan86 on 2008-08-21
> **Nexusx6 said:**
> I'm just about to head to work so I apologize for the really fast solution.

In terminal, run this:
```
padsp winecfg
```

Then, go to your ~/.wine/drive_c/Program Files/Steam/ folder, and type this in
```
WINEDEBUG=-all padsp wine steam.exe
```

you should have sound in any game you launch from steam now.

This didn't work. I still got the same ol' same ol' only sound from the logo. Here's my terminal output:

```

yaro@irma:~/.wine/drive_c/Program Files/Steam$ WINEDEBUG=-all padsp wine steam.exe
CellID: Fetching server list from CSDS. . .
CellID: CSDS returned 169 servers.
CellID: Connecting to 210.208.88.56:27031. . .
CellID: Connect to 210.208.88.56:27031 took 240 MS
CellID: Nothing beat our old best time of 32 MS
wine: Call from 0xf252321 to unimplemented function vstdlib_s.dll.Q_CopyAndFixSlashes, aborting
Reference Count for Material __lookupviewpanel (1) != 0
Reference Count for Material vgui/zoom (1) != 0
Shutting down. . .
1yaro@irma:~/.wine/drive_c/Program Files/Steam$ 

```

I might have to reinstall Windows just so I can play it on there without any problems. I never USED to have problems on WINE, but without sound, HL2 isn't worth playing.

---

### Post by Ferrat on 2008-08-21
What you can do is change so that Ubuntu doesn't use pluseaudio, just fix it in 
System >> Preferences >> Sound

There you can choose from all the audio mixers ect :)

---

### Post by Gartral on 2010-05-31
there is no option in System>Preferences>Sound for changing the soundcore anymore!

---

### Post by frogotronic on 2012-01-28
I also do not have any sound (not the valve logo, or anysound).  Everything else works well.

Will investigate and fix.

- CH

---

### Post by edmonds on 2012-03-10
i have no sund with HL or HL2.
UI used to a few years ago, (probably befor pulseaudio).
and strangley the very first time HL2 booted this time round (with Steam) there was sound. but never again.

---

### Post by Elfy on 2012-03-10
I'd try a new thread with relevant information - this thread is almost 4 years old.

Closed

---

