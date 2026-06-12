---
title: "How to install games for windows live in the same wine prefix as steam?"
date: 2012-08-06
forum: Wine
---

### Post by Builder979 on 2012-08-06
I'm looking for help on how to install games for windows live in the same wine prefix as I installed steam in. I am looking to play Fallout 3 through steam and I am following this guide: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322) ( Scroll down to get to the how-to ). I have been able to follow all the steps except for installing games for windows live. I installed steam with winetricks so it's in it's own wineprefix. So how can I install games for windows live in that same wineprefix? Thank you.

---

### Post by Toz on 2012-08-06
Hello and welcome to the forums.

To install into a specific wine prefix, try something like this:
```
WINEPREFIX=/path/to/prefix wine game.exe
```

Later down in that HOWTO it talks about installing the game using PlayOnLinux. You might want to give that a try - PlayOnLinux is a front-end to wine.

---

### Post by Builder979 on 2012-08-06
Toz, I tried your solution and got this bug:

(My Username)@(My Hostname):~/Downloads$ WINEPREFIX=/.local/share/wineprefixes/steam wine gfwlivesetupmin.exe /nodotnet

wine: chdir to /.local/share/wineprefixes/steam
 : No such file or directory

/.local/share/wineprefixes/steam exists because I have seen it in Nautilus File Manager.

Does anyone have an idea of whats going on?

---

### Post by DarkAmbient on 2012-08-06
Just wanna point out that you could try PlayOnLinux for that. It pretty much handle things like dealing with multiple Wine-environments (WinePrefixes).

---

### Post by Toz on 2012-08-06
The path is actually **$HOME**/.local/share/wineprefixes/steam. The way you have it entered shows it existing off the root (/) directory.

---

