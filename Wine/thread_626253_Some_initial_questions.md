---
title: "Some initial questions"
date: 2007-11-28
forum: Wine
---

### Post by thevictor390 on 2007-11-28
I can't install wine right now due to an excruciatingly slow connection to the site, so in the meantime I have a few questions:

1) Is anyone else having problems connecting to download the package? Mt internet connection is otherwise fine.
2) From what I understand, wine is more or less a free version of the built-in windows libraries, and I can override them with the official ones if I want.  Am I expected to do this, or should the initial setup work for most programs? Basically, I do not have windows installed, so I can replace errant dlls individually but do not have access to the whole thing.

I am new to wine completely, and now that I seem to have gotten the hang of linux (I actually do not have any problems with my system right now, a first), I would like to get this working for those few irreplaceable apps (and some decent games, even if they would have to be classics).  Thanks for your help, I would be nowhere without this forum!

---

### Post by jken146 on 2007-11-28
In my (somewhat limited) experience with wine, there is no need to add Windows dlls yourself.  Whether wine will work for most programs depends on the program in question.  For some, no problems at all, for others, no results at all.  See winehq.com

---

### Post by cogadh on 2007-11-29
Most of the core Windows DLLs required by most Windows applications already exist in Wine, but they may not have fully complete functionality (yet). You should really only need to add a Windows DLL when one is completely missing from Wine, though there are a few instances where a native DLL may work better than the Wine built-in ones. As jken146 said, it really depends on the application. Before trying to run anything in Wine, you should look for the application in Wine's [Application Database](http://appdb.winehq.org/) for information on whether or not the app will run and what you may need to do to get it to run.

One group of DLLs I always add to Wine are the d3dx9_##.dll and d3dx10_##.dll files, which are DirectX support DLLs that are not present in Wine. Most games don't really need them, but they don't hurt anything by adding them and if a game does need them, they are already there, waiting to be used. 

If you don't have an available Windows installation to get DLLs from, you can Google for them, there are many places to download them. However, it should be noted that most of the Windows core DLLs do require you to legally own and agree to the MS Windows license before you can use them.

---

### Post by thevictor390 on 2007-11-29
Thanks for the response! I do own windows XP and Vista (just not on this comp) so there should be no legal problem, and I finally got a connection to the server and am installing wine now.

---

