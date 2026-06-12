---
title: "How to execute a window wine program in Terminal"
date: 2022-11-29
forum: Wine
---

### Post by Ralph L on 2022-11-29
I have been trying to run iTunes in Wine. I am running Xubuntu 22.04. When I couldn't get iTunes to run right I tried a bunch of things and ended up trashing my Wine installation. So I tried to purge Wine and start over. Apparently I didn't get the purge done correctly, because when I reloaded Wine (no errors in the reload) and ran winecfg, I couldn't even run iexplore.exe that winecfg installed to demonstrate that Wine worked. When I started iexplore.exe (by double clicking it), it grinds for a while and then just quits. 
1. Is there a way to run "wine windows program loader" in a Terminal, so I can see error messages. I don't know what the real program name for "wine windows program loader" is, so I can't execute it in a Terminal and see errors from iexplore.exe.
2. Any other ideas on how to completely purge Wine, so I can reload it from scratch. I used these sites for guidance: [https://ubuntuhandbook.org/index.php/2022/04/wine-ubuntu-2204-windows-apps/](https://ubuntuhandbook.org/index.php/2022/04/wine-ubuntu-2204-windows-apps/) and [https://vitux.com/how-to-install-wine-on-ubuntu/](https://vitux.com/how-to-install-wine-on-ubuntu/).

Any help is appreciated.........

---

### Post by QIII on 2022-11-29
Moved to Wine as a more appropriate location.

---

### Post by kc1di on 2023-02-08
Wine folders are usually hidden files in your home directory so if the program you want to run is already installed in wine you will have to navigate to the .wine directory and go from there.

---

### Post by DuckHook on 2023-02-08
This thread is months old and it is unlikely that the OP is still subscribed to it, but for the sake of any lurkers out there&#8212;or just for posterity's sake&#8212;this is how WINE works:

[LIST=1]
[*]When you install the WINE app you are creating two "branches" of code.
[*]The first branch is the WINE system itself. This usually installs into the same place that all Linux executable code installs into: /usr/bin
[*]You can see where your WINE executable is by querying with:```
which wine
```
[*]But WINE cannot run with just its own executables. After all, its whole point is to mimic Windows. Therefore, it creates a second branch containing pseudo&#8209;Windows code that resides in your /home directory. This branch is "hidden" through the usual Linux expedient of prefacing the directory with a . (a dot) which you can reveal in Nautilus by toggling display of hidden files.
[*]When you purge WINE, you purge all of the first branch (in /usr/bin) but you do not purge the second branch (in /home) because the apt purge function considers all data under /home to be user owned and untouchable.
[*]When you reinstall WINE, it puts a new version of WINE into /usr/bin but when you run it the first time, it will detect the old second branch and will automatically assume that you want to inherit it.
[*]The upshot is: you cannot completely clean out your old WINE install without manually purging the second branch. An apt purge will not do this. You must do this manually.
[/LIST]

---

