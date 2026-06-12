---
title: "Ubuntu and Win games on Wine"
date: 2013-04-26
forum: Wine
---

### Post by Dallas2coolio on 2013-04-26
Is this true about someone saying that Wine will never play games and perform the same was as playing the same games on Windows systems? Basicly if you had two the same systems and one had Ubuntu with latest Wine and one had Win 7 will Win 7 allways perform better on Windows games no matter how updated Wine is?


Also with the new Ubuntu 13.04 will that still not perform as good as Windows even if you have the latest drivers and Wine version on Ubuntu?

---

### Post by Mark Phelps on 2013-04-26
It's not so much the Wine version as it is the fact that the video drivers are different.  The latest Windows drivers will provide the latest DirectX support and other new features; the latest Linux drivers might not.  

Plus, each game tends to have its own problems and performance characteristics.  Some run fine without problems, others requires lots of tweaking, others don't run at all.

You should investigate each game you want to run at the WineHQ website, the application compatibility page, to see what the problems are.

---

### Post by gamblor01 on 2013-04-26
Mark is right, and typically the drivers are reverse engineered and rebuilt so they aren't exactly the same.  Last time I really tried the best that wine could do was Direct X 8.  You can copy over native DLL files and instruct wine to use them but things don't always play nicely and the results may actually slow down performance and/or break things in the game.  I always had problems trying to play source based games (HL2, TF2, Portal, etc.) using native DX9 files for example.

There is a modest but growing list of games now supported natively in steam.  The most popular are ones like TF2 and CS Source.  A bit older for sure, but the list is growing and the more people that purchase games with Linux support/request Linux support -- the better the chances that more and more games in the future will be released for Linux.

The wine HQ compatibility pages are great and often contain various workarounds and instructions for common problems.


As for comparing 13.04 to Windows -- it depends more on the game and the video drivers than the OS itself.  I would like to point out that my system actually runs TF2 and CS Source slightly better in Steam for Linux than it does in my old XP partition.  About 20FPS better on average.

Just FYI, Valve seemed to suggest that OpenGL appears to be much more efficient than DX.  Here is an old post when they were working on L4D2, prior to Steam even going beta on Linux.  Again, the more people begin to develop games for Linux, the better and better things will get.

[http://blogs.valvesoftware.com/linux/faster-zombies/](http://blogs.valvesoftware.com/linux/faster-zombies/)

---

### Post by RefinedCode on 2013-04-28
I can play Portal 2 (or any source game for that matter) and Company of Heroes better than I could in Windows 7, but I think that might be due to the fact that windows can get clogged up with crap alot easier than Ubuntu.

---

