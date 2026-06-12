---
title: "mouse pointer is limited to moving in game window."
date: 2007-11-29
forum: Wine
---

### Post by elvin11 on 2007-11-29
ON obilivion when I open the window to see quest and info on charater my mouse is not moving far enough.any direction is now half of the area it was when i get out and go back to game.

it's just a usb mouse trackball is there something I need to do.New to linux as well.

---

### Post by cogadh on 2007-11-29
That is a known limitation of Wine's implementation of DirectInput. It doesn't happen to every game, but many are affected by it. If the game has the ability to disable the use of DirectInput for mouse events, it may correct the problem. You'll have to look through the in-game configuration options and any manually editable configuration files for the game to see if that can be done.

---

### Post by elvin11 on 2007-11-29
Thx for the info on that.I'll look and see if it does have,I did disable the joystick was on for some reason on the ini file.

---

