---
title: "Morrowind freezes on PlayOnLinux."
date: 2013-03-14
forum: Wine
---

### Post by TheoJava on 2013-03-14
After trying a bunch of things to get Morrowind working reliably on WINE (all to failure), I reinstalled it using PlayOnLinux. Everything seemed to be working fine, but then I exited a building and noticed there was no sound. So I quicksaved and reloaded, which immediately froze the game. Every time I try to load that same file now, the game instantly freezes.

I'm running 32bit Ubuntu 12.10, and I startup POL with the ```
optirun -b primus
``` command, if that matters. Any ideas on what's wrong?

---

### Post by Lightning Dragon on 2013-03-14
Hello,

[SIZE=1] *Sounds like the problem for wine 0.9.59+...*[/SIZE]

I have an idea as to why, but it may not be what you want to hear. Sounds like the quicksave is broken. Have you considered saving the quicksave file/saves someplace, delete the old ones, restart the computer and then put the saves back into the folder? Sometimes I find that that helps. Otherwise I suggest reinstalling Morrowind via PoL again.

Have you tried configuring PoL differently?

---

