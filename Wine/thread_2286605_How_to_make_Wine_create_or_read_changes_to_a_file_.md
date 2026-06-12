---
title: "How to make Wine create or read changes to a file installed outside of it"
date: 2015-07-13
forum: Wine
---

### Post by britsin on 2015-07-13
Ok, I have a game folder which has the file "xyzsp.exe". (The game was not installed through or in Wine, and is just a "click and play" one without cd or a setup file needed. It plays right on Windows.)

When I open it (the above file) with Wine on Ubuntu, immediately after initializing files etc. it takes me back to the desktop screen. The solution for this is to simply use the relevant Wine version (1.3 in my case) and then either give the command "[COLOR=#000000][FONT=bitstream vera sans]MESA_EXTENSION_MAX_YEAR=2003 wine XYZSP.exe" or "[/FONT][/COLOR][COLOR=#000000][FONT=bitstream vera sans] __GL_ExtensionStringVersion=17700 XYZSP.exe". 

But this isn't working for my file (as it wasn't installed through Wine to begin with) and the terminal returns "[/FONT][/COLOR]cannot find...XYZSP.exe". So, how can I make Wine to create/ read the change to this file. I do Not have Windows OS on this computer.

---

