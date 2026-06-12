---
title: "Diablo II in windowed mode - problem"
date: 2008-04-04
forum: Wine
---

### Post by hawky on 2008-04-04
Hello everyone,

I have a quite interesting problem with wine. I am running Diablo II LOD in windowed mode, if I change window and attempt to come back to the Diablo II game, the game will resize to a very small size, and it is impossible to bring it back to the original size. If I attempt to right click and change resize, the only option is move. If I attempt to double click the new resized window, the game will close, but I can still hear the background music in the back.

I haven't been able to find a solution to this problem online so I'm hoping someone can help me here!

Thanks,
Marc

---

### Post by hawky on 2008-04-05
ok, so I kind of fixed the problem. i went into the winecfg, and uncheck the option to allow the window manager to control the wine applications. so now i can switch windows and come back, but now I have another problem. if i change windows and come back too often, i won't be able to type in Diablo 2 anymore, if i type something, it'll type for another application in the back.

any ideas?

---

### Post by ekravche on 2008-04-05
Try this. Change your shortcut to run diablo 2 lod to this

> env WINEPREFIX="/home/evgenyserver/.wine" **wine explorer /desktop=MyDesktopName,805x625 **"C:\Program Files\Diablo II\Diablo II.exe"

The key is to make sure that you have this part of the line **wine explorer /desktop=MyDesktopName,805x625 **
Also uncheck the checkbox that says allow the window manager to control the windows.

It works for me :) Happy ubuntuing :)

---

### Post by hawky on 2008-04-06
Solved! Thanks.

---

### Post by hawky on 2008-04-09
I am having another problem, I have attempted to get the game to play in fullscreen, but I believe that it may of caused some problems to the game. Whenever I attempt to pick up an item while holding alt, it won't let me, any ideas? Also, I noticed that the environment window now has a maximize button, something that was lacking before I starting using fullscreen.

Thanks

---

### Post by hawky on 2008-04-09
i changed alt to space for diablo, that way when i press space, i'll see the items instead of the regular alt, seems to work for me.

thanks

---

### Post by ekravche on 2008-04-09
You can also uncheck the checkbox in wine configuration that says "Allow window manager to control the windows"

---

### Post by HuoMaKe on 2008-04-12
Hawky-the reason for your alt-click problem is that it is the universal shortcut for moving windows (try it on the browser window now). Anywhere you alt-click, it will move the window.

Incidentally, I am having similar problems as described above. I tried the wine explorer... command, but it has negative effects on my graphics, which work fine in fullscreen.

Also, it won't let me use alt for my held-down shortcut for toggling the display of items. I am using ctrl at the moment, but it's annoying.

Specs: Macbook, it says I don't need any drivers for my graphics, Gutsy, and fully updated Diablo 2 LOD.

---

