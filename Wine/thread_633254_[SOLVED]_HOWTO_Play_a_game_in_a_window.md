---
title: "[SOLVED] HOWTO: Play a game in a window"
date: 2007-12-06
forum: Wine
---

### Post by b0rka7a on 2007-12-06
How can I run a game with Wine in a window from the terminal? I know I can set Wine to emulate a virtual desktop, but I want to run one game in a window, and others in fullscreen and I don't want to change my settings in winecfg every time I want to play game

I've tried these two commands ( which of course didn't worked :( ):
```
-windowed -width 800 -height 600
```
and:
```
-desktop 800x600
```

Please tell me what am I missing ?

---

### Post by i386DX on 2007-12-06
It depends from game to game...
Which game are you trying to play?

---

### Post by b0rka7a on 2007-12-07
I'm trying to play FlatOut 2. I've created a script to play it because it needs to be started from the game directory. Here's my script:

```
#!/bin/sh
cd "/media/sda1/Downloads/dcpp/FlatOut 2/";
wine flatout2.exe -windowed -width 800 -height 600
```

"-windowed -width 800 -height 600" works with Counter-Strike 1.6
"-desktop 800x600" doesn't work with any game

---

### Post by karth on 2007-12-07
the syntax is
wine **explorer /desktop=name,widthxheight** program.exe -flags

the desktop's name is optionnal, it's just tu identify it if you run several wine desktops along with this one.

For example for Warcraft 3 windowed in 1024*768 you can have
```
wine explorer /desktop=war3,1024x768 "C:\Program Files\Warcraft3\war3.exe" -dxlevel 81
```

FYI, "-windowed -width 800 -height 600" are native CS flags that interact with the source .exe's (and therefore won't do anything with other programs), and "explorer /desktop" are for Wine.

---

### Post by dethredic on 2007-12-07
Not sure, if this will work, but it works in windows.

Rightclick->Properties->Launcher Tab-> command, and add a *space*-windowed

---

