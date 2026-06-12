---
title: "WOW sound gone after alt+tab"
date: 2008-07-14
forum: Wine
---

### Post by waggingwabbit on 2008-07-14
i cant alt+tab out of wow on ubuntu. but when i have firefox on while i have WOW on, or someother program maybe while i have wow on, I can alt+tab to that program and back to wow. but when i do this the sound goes away. is there a way to fix this? not really a big deal if i can't but itd be nice =]

---

### Post by darkaudit on 2008-07-14
Not really, no.

I've found that in Fluxbox at least I can tab out to Vent if it's in the same desktop and come back and still have sound, but not in GNOME or XFCE. If I tab out in those at all, I lose sound until I restart the game.

---

### Post by thisismalhotra on 2008-07-15
I think that was known bug in earlier version of wine, I am almost sure it does not exist anymore.  

This is an excerpt from following page;

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

```
Sound stops working after alt-tabbing out

Since Wine version 0.9.42, if WoW loses focus (that is, if you alt-tab to another window) the sound will stop working. Also, some users have reported that WoW crashes or black-screens completely when WoW loses focus.

The simplest way to make sound play while WoW doesn't have focus is to enabling the option Enable Sound in Background in the Sound Options menu.

Setting the game to run in Windowed Mode (and then simply making it fullscreen) also appears to fix this problem and there is little noticeable difference between this and actually being fullscreen.

There is also a post in the WoW appdb page, that gives a backwards diff patch that can be applied to the Wine source before compiling, that can fix the problem, but just commenting out the line in question - so that WoW never is even told that it has lost focus - works well too; you can then alt-tab between windows and back to WoW with zero delay, with WoW always running underneath, but this may break compatibility with other Wine apps and might not work with all windowmanagers, your mileage may vary.

To comment out the line:

    * download, extract the latest Wine tarball
    * open up the file dlls/winex11.drv/event.c
    * look for a bit of code that looks like the following: 

{{{/* Abey : 6-Oct-99. Check again if the focus out window is the Foreground window, because in most cases the messages sent above must have already changed the foreground window, in which case we don't have to change the foreground window to 0 */ if (hwnd == GetForegroundWindow()) {

    * TRACE( "lost focus, setting fg to 0\n" );

      SetForegroundWindow( GetDesktopWindow() ); 

}

    *

      comment out the SetForegroundWindow() line like this: 

if (hwnd == GetForegroundWindow()) {

    * TRACE( "lost focus, setting fg to 0\n" ); 

SetForegroundWindow( GetDesktopWindow() ); } }}}

    * build Wine as usual
    * ???
    * PROFIT 
```

---

### Post by Milos_SD on 2008-07-15
In WoW, go to Sounds & Voice settings and check "Sound in Background" option. Now sound will work even you are listening to music, and alt+tabing or changing workspaces. :)

---

