---
title: "portal"
date: 2007-12-28
forum: Wine
---

### Post by trynet on 2007-12-28
I'm trying to play portal, I've tried opening it with-
```
env WINEPREFIX="/home/tyler/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 400

```
and
```
env WINEPREFIX="/home/tyler/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 400 -dxlevel 80

```
but every time it opens, it gets to the "loading..." screen and closes with the message "This game has a minimum requirement of DirectX 8.0 to run properly"
I'll admit that I have no clue what I'm doing, never had the need to use wine before.

---

### Post by Ertai87 on 2007-12-28
My guess would be that Wine doesn't emulate DirectX above 8.0.  Try running portal with the -opengl flag.  Since Wine emulates DirectX and doesn't actually use real DirectX, it'll probably run better that way anyway.

---

### Post by trynet on 2007-12-30
nope, still same error -_-

---

