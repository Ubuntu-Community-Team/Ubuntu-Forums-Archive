---
title: "Running Games Full-screen in Wine+Gnome - causes scrolling"
date: 2007-06-11
forum: Wine
---

### Post by almkglor on 2007-06-11
Whenever I run a game that switches to fullscreen, the correct resolution is applied, but when I move my mouse to a screen edge the game's fullscreen scrolls, Gnome scrolls the screen to show other parts of the desktop.  Clicking outside the game's screen causes the game to lose keyboard focus; when this happens there is no way (that I have found) to return keyboard focus to the game.

This happens with Diablo II and StarCraft.

From what little I could glean from Google, it seems to be a problem with interacting with the desktop/window manager.

In my default settings I have:
Yes: Allow DirectX apps to stop the mouse leaving their window
No: Allow the window manager to control the windows
No: Emulate a virtual desktop
Vertex Shader Support: Hardware
Yes: Allow Pixel Shader (if supported by hardware)

I've tried playing a bit with the first three settings.  I didn't really like using a virtual desktop since it gets into a window.  The first setting doesn't seem to have any effect on my system.  The second allows me to see Wine windows on my taskbar but still doesn't stop the scroll.

I've added a "fullscreen" shortcut key to my Gnome but it doesn't seem to work, even when I allow the window manager to control the windows.


So aside from just playing in virtual desktop mode, is there some setting in Gnome to help me?

---

### Post by lordhebe on 2007-06-11
well i do have this problem, for me the solution is to always run the game in the same resolution as my desktop.

---

### Post by almkglor on 2007-06-13
Unfortunately my 2d game is limited only to 640x480 or 800x600.  However I find those resolutions a little too low (fonts are too big).

---

### Post by Wintershade on 2009-08-20
Hi, and sorry for resurrecting an old thread, but I've found this via google and have exactly the same problem. Did anyone find any way to fix this?

apart from manually changing the resolution all the time...

---

### Post by disparil on 2011-02-03
Hello,

I have achieved with the following configuration in the Graphics tab of winecfg. Try it ..

check:
[LIST]
[*]Allow DirectX apps to stop ....
[/LIST]

uncheck:
[LIST]
[*]Allow the window manager to decorate ....
[*]    Allow the windows manager to control ....
[*]    Emulate a virtual desktop ...
[/LIST]

Greetings!

---

