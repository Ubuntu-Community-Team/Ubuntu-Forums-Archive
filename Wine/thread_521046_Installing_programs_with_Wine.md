---
title: "Installing programs with Wine?"
date: 2007-08-08
forum: Wine
---

### Post by cmillican on 2007-08-08
I'm trying to install a game called 18 Wheels of Steel just as a first windows install through Wine that I downloaded off of WineHQ.

I installed wine with aptitude, put the .exe installer in c:/games/, then ran winefile and clicked on the installer. It shows this:
```
fixme:actctx:QueryActCtxW 80000010 0x41c068 (nil) 1 0x34fdb4 8 (nil)
Usage: winebrowser URL
```
then seems to not respond until I kill it with Ctrl-C.

I also tried just typing "wine [full file path]", but it produced the same results.

I would think this program would work seamlessly under Wine due to it being on the page without any warnings, but I could be wrong.

Any help is greatly appreciated.

Thanks,
Chris

---

### Post by lixy on 2007-08-09
> **cmillican said:**
> 
I would think this program would work seamlessly under Wine due to it being on the page without any warnings, but I could be wrong. 

What page are you talking about?

---

### Post by hikaricore on 2007-08-09
Aka which version here: [http://appdb.winehq.org/search.php?sSearchQuery=18+wheels](http://appdb.winehq.org/search.php?sSearchQuery=18+wheels)

Are you talking about?

---

### Post by cmillican on 2007-08-09
It was Convoy.

---

### Post by hikaricore on 2007-08-09
Whoops, moving this over to Gaming & Leisure.

Better chance at getting help there.  ^_^

I'm not 100% familiar with the game, but are you running it from it's actual directory?

This is what you should be doing.

---

### Post by cmillican on 2007-08-09
All I'm trying to do now is install it. I put it in the virtual c drive in a folder called "games"...I ran winefile, clicked it, and got the errors at the ^^top^^.

---

### Post by cogadh on 2007-08-09
What did you download from WineHQ? The game is only available on CD and is not available for download at WineHQ, so I don't think that is the executable you are actually trying to run.

Unless you are trying to install/run the demo version of the game. If that is the case, you don't need to put the installer into your Wine directory, you just need it in your home folder. Then you just need to open a terminal and run this:
```
wine 18WheelsofSteelConvoy-dm.exe
```
However, the demo currently has a "garbage" rating on AppDB, so it may not run at all if it installs.

---

### Post by cmillican on 2007-08-09
Ooh...yea it was the demo I was trying to run, but I thought it would work...thanks guys.

---

