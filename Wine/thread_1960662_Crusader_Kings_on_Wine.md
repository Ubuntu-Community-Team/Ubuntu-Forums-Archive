---
title: "Crusader Kings on Wine"
date: 2012-04-17
forum: Wine
---

### Post by galoisring on 2012-04-17
I'm running Xubuntu 11.10 and Wine 1.3.28.

I installed Crusader Kings and everything goes fine until the menu screen.

I can see the top left corner of the menu and that's all. Most of the screen is off of my monitor, as if the resolution was extremely low.

Does anyone know a way to fix this?

Thanks

---

### Post by cogadh on 2012-04-18
In winecfg, go to the Graphics tab and check the box for "Emulate virtual desktop", then set the resolution to whatever you want to run the game at (I recommend sticking to standard 4:3 resolutions that fit within your screen's default resolution). This will force the game to run in a Wine window and keep it from going off the screen, which should allow you to run the game and alter whatever settings you need to get the resolution set right.

---

### Post by galoisring on 2012-04-24
Thanks for responding.

I checked the Emulate Virtual Desktop box and ran Crusader Kings.

However the game still doesn't work. Before the game starts, I get the following error message:

Fatal Error!
***Unhandled Exception Detected
Address: 0x0060202540

Any suggestions on how to solve this problem?

---

### Post by galoisring on 2012-04-24
Forgot to post the log file for the error. Here it is:



######## EXCEPTION: 0xC0000005 at address: 0x00602540: ACCESS VIOLATION  read attempt to address 0x0000000C 
04/24/12 16:32:32
SymGetLineFromAddr(): GetLastError = 123
SymGetLineFromAddr(): GetLastError = 123
SymGetLineFromAddr(): GetLastError = 123
SymGetLineFromAddr(): GetLastError = 123
SymGetLineFromAddr(): GetLastError = 123
SymGetLineFromAddr(): GetLastError = 123

StackWalk(): GetLastError = 998

---

### Post by cogadh on 2012-04-24
That could be the copy protection on the game not working with Wine. Have you tried using a cracked executable? Don't ask where to get or how to use one here, it's against the forum rules.

---

