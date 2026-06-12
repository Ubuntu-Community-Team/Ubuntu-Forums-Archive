---
title: "Wine 1.3.34 won't exit the game"
date: 2011-12-09
forum: Wine
---

### Post by sunfromhere on 2011-12-09
Hello, I am currently running Ubuntu 11.10 and just yesterday I upgraded Wine to 1.3.34. The game in question is Sims 3, and before the update it ran perfectly (no crashes, no glitches, fast save & exit, only the create-a-pattern tool was a bit laggish).

However, today, after the upgrade:

1. The game starts with the pannel on top (the one showing date, battery, shut down etc) and the only way to remove it is to change display settings.

2. Exit game doesn't work - the game just hangs on black screen, mouse reacts, I can alt-tab to desktop, but any other click returns me to black screen. Forced log-out doesn't let me log back in, so the only way to "exit" the game seems to be hard restart.

Has anyone had similar problems? Any ideas how to resolve it or should I just revert to previous version of Wine?

---

### Post by ergo-proxy on 2011-12-09
Check emulate desktop in winecfg and set your resolution.

---

### Post by Tweak42 on 2011-12-13
A workaround to avoid hard restart from hanging wine apps, is killing the wineserver at command line.

Either ctrl-alt-f1, login at command prompt or ctrl-alt-t to open a command terminal.  Then enter:```

wineserver -k
```

This should kill the wine server which should drop any wine apps hogging control of your desktop.

ctrl-alt-f7 should return you to your X windows desktop.

---

