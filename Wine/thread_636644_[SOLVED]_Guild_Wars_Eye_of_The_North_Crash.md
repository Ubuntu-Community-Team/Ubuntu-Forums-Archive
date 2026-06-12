---
title: "[SOLVED] Guild Wars: Eye of The North Crash"
date: 2007-12-10
forum: Wine
---

### Post by MonkeyBoy on 2007-12-10
I just started playing GW:EN and it works nicely like the other campaigns until I get to The Hall of Monuments.  When I try to enter the hall the loading screen freezes and the game stops responding.

This is something that happens intermittently when entering other areas but rarely more than once whereas I have tried a load of times to enter this Hall.

Anyone else have this problem or any suggestions re a fix?

I am using the following:
```
 -dsound -noshaders -dx8 flags -repair -image WINEDEBUG=-all >/dev/null 2>&1
```

---

### Post by MonkeyBoy on 2007-12-10
Got it fixed by patching with the concurrent lights patch.

---

