---
title: "Trying to play Morrowind using Steam through WINE - help requested"
date: 2011-09-13
forum: Wine
---

### Post by chris282 on 2011-09-13
I'm using Ubuntu Lucid 10.04 and WINE 1.3.26, and trying to run Morrowind using Steam.

Steam is running fine and I've downloaded the game, but when I try to play I get the error message: "The program Morrowind.exe has encountered a serious problem and needs to close.  We are sorry for the inconvenience."

Can anyone suggest where I'm going wrong?

Thanks in advance,

- Chris.

---

### Post by Elfy on 2011-09-13
Thread moved to Wine.

---

### Post by MyR on 2011-09-13
the author of [http://www.steamgamesonlinux.com/the-elder-scrolls-iii-morrowind/](http://www.steamgamesonlinux.com/the-elder-scrolls-iii-morrowind/) used wine 1.3.2 to play it.
All the platium-rated wine tests use the morrowind CDs, so they may not be indicative that the same version of wine would support the steam version of the game.

If you manage to get it working, please consider reviewing the game here: [http://linuxdeal.com/Game-The-Elder-Scrolls-III:-Morrowind](http://linuxdeal.com/Game-The-Elder-Scrolls-III:-Morrowind)
If all else fails, you could purchase the boxed version.

---

### Post by chris282 on 2011-09-14
Thanks MyR.  I've read through the [WineHQ instructions]("http://wiki.winehq.org/FAQ#head-cfe3d786caf003a7019554ec9a943ba1289972cf") for installing an older version of Wine, but I'm a little confused about which of [these files]("http://wine.budgetdedicated.com/archive/binary/") I should be downloading (and tbh generally a little confused overall).

My intention is to run a second version so as not to avoid screwing up the applications I do have working on the current version.  Is this wise/unnecessary?

Any advice?

PS. In case it's relevant, my graphics card is a GeForce GTX 260.

---

### Post by MyR on 2011-09-14
> **chris282 said:**
> Thanks MyR.  I've read through the [WineHQ instructions]("http://wiki.winehq.org/FAQ#head-cfe3d786caf003a7019554ec9a943ba1289972cf") for installing an older version of Wine, but I'm a little confused about which of [these files]("http://wine.budgetdedicated.com/archive/binary/") I should be downloading (and tbh generally a little confused overall).

My intention is to run a second version so as not to avoid screwing up the applications I do have working on the current version.  Is this wise/unnecessary?

Any advice?

Well, bad news. 1.3.2 in no longer in the wine archive. If you're ready for an adventure to can try to compile it from [source]("http://iweb.dl.sourceforge.net/project/wine/Source/wine-1.3.2.tar.bz2"). Or perhaps you can find a download somewhere; I only looked for a few minutes.

You can only have one version of wine installed at a time.  All the programs you install go into the folder ~/.wine so you can save all the settings for multiple versions of wine or multiple apps, which is what I would do.

So what I suggest is to rename your ~/.wine folder to something else, install the older 1.3.2 version of wine, and then try to install steam/morrowind.

---

### Post by MyR on 2011-09-14
or you could give 1.3.3 a try, since it is in the archive still.

---

