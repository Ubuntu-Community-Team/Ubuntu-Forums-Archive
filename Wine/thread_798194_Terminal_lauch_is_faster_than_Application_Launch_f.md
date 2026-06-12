---
title: "Terminal lauch is faster than Application Launch for running Counter-Strike via WINE"
date: 2008-05-18
forum: Wine
---

### Post by darinmiller@cableone.net on 2008-05-18
After due Google and other forum searching diligence, I could not find mention of the topic below.

In Hardy Heron, (64 bit), has anybody noticed a performance difference between launching CounterStrike source via CLI vs a link in the Application Launcher or Nautilus?

For instance, if I run the following command via CLI, a script launch from Nautilus and Application Launcher shortcut:

```
WINEDEBUG=-all "/home/darin/.wine/drive_c/Games/Steam/steam.exe" -applaunch 240 -novid -dxlevel 81 -width 1920 -height 1200
```

Then run CounterStrike's Video stress test, I observe the following frame rates:

CLI:                    ~62 fps
Nautilus script launch: ~40 fps
Application Launch:     ~40 fps

Given my limited but expanding Linux knowledge, the CLI method seems to run CounterStrike at a much higher priority "nice" level.

Any idea how to achieve the CLI performance via an Application Launcher short cut?

FWIW, Compiz also "seems" to run smoother (less random choppiness when killed and restarted via CLI).  Unfortunately, I am not aware of a way to measure random choppiness.

---

