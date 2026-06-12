---
title: "COD2 Wine Error"
date: 2007-07-08
forum: Wine
---

### Post by Vendetta_NZ on 2007-07-08
I have managed to install Call of Duty 2 in Wine with no hitches, but when I try to play it (cod2_mp.exe) in wine, it brings up this error in the COD2 Console. Does anyone know how to fix this?

```
CoD2 MP 1.0 build win-x86 Oct  6 2005
----- FS_Startup -----
Current language: english
Current search path:
Z:\home\sjcurran/main
Z:\home\sjcurran/raw
Z:\home\sjcurran/raw_shared
Z:\home\sjcurran/devraw
Z:\home\sjcurran/devraw_shared

File Handles:
----------------------
0 files in iwd files
ERROR: No languages available because no localized assets were found
Error during initialization:
Couldn't load default_mp.cfg.  Make sure Call of Duty is run from the correct folder.
```

---

### Post by Vendetta_NZ on 2007-07-08
Ah nevermind, managed to fix it. For future reference. To run COD2 in Wine, you must install it in Linux. And install it in Windows. Enter a multiplayer match in Windows, as to make the Multiplayer configuration files. Copy the missing folders from Windows to Linux COD2 directory, then run the game in Linux. It should work. I get around 30fps ingame, so not great playablilty, but it works. You **must** run COD2 in root account.

---

### Post by cogadh on 2007-07-08
You shouldn't ever need to run a Wine game as root. In fact, it is strongly recommended that you do not run Wine as root ever. Why do you need to run it as root?

---

### Post by Vendetta_NZ on 2007-07-09
Because I tried it in both, and only root worked?

---

### Post by cogadh on 2007-07-09
Did you install the game as root or using the sudo command? How about winecfg, was that run as root or with sudo?

---

### Post by Vendetta_NZ on 2007-07-09
Winecfg runs without sudo. I installed the game outside of root, but had no installation errors or anything?

---

### Post by cogadh on 2007-07-09
I realize winecfg runs without sudo, however if you do use sudo to run it, it will then require sudo or root access to run anything installed in the profile that was created by winecfg. It still doesn't make any sense that you would need to run the game as root. If you had used sudo or root access to run winecfg or install the game, then it would make a lot more sense.

From the WineHQ FAQ:
> NEVER run Wine as root. Doing so gives Windows programs (and viruses) full access to your computer and thus every piece of media attached to it. Running with sudo also has these same risks but with the added bonus of breaking the permission on the users ~/.wine folder in the process. If you have run Wine with sudo you need to sudo rm -rf ~/.wine and then run winecfg to set wine back up. You should run Wine as the normal user you use to login.

---

### Post by fj401971 on 2007-11-28
I believe the reason why root worked and the regular user mode didn't because you were not in the proper directory.  This worked for me at least.

```

cd /this/is/the/directory/where/COD2/is/installed
wine CoD2SP_s.exe &
```

---

