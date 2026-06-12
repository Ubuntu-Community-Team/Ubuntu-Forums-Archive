---
title: "Galactic Civilisations II: Fine in AppDB, But Not for Me"
date: 2008-01-27
forum: Wine
---

### Post by H4rm0ny on 2008-01-27
I have a game called Galactic Civilisations II which has a reproducible crash but which is Bronze in the AppDB. Furthermore, I was able to play it on my old computer, although it was a little too slow to be satisfying. I now have a much upgraded system and the game dies on start-up everytime.

If it were a general problem, I'd leave it be, but as it appears to be just my system, I thought I'd see if it could be anything obvious.

I have a PCI Radeon 2600HD 512MB graphics card and am using the latest binary drivers from the AMD site (8.45.4 at time of posting). fgl_glxgears seems to go like lightening. Reason for specifying all this is that it seems to be a problem with the graphics from the following:

```
Backtrace:
=>1 0x7c03c4b0 (0x0034f820)
  2 0x7ed6fe4e ActivateContext+0x5fe() in wined3d (0x0034f8b0)
  3 0x7ed9f35e drawPrimitive+0xce() in wined3d (0x0034fc40)
  4 0x7ed8400e in wined3d (+0x2400e) (0x0034fc80)
  5 0x7ee516e1 in d3d9 (+0x116e1) (0x0034fcb0)
  6 0x0069c40c in galciv2 (+0x29c40c) (0x7bc33000)
  7 0x758918ec (0x83e58955)
  8 0x00000000 (0x00000000)
```

Obviously that's not the complete log, but I thought it might be something to do with my system rather than Wine, exactly. The game did run on this system with the open source drivers, but it went at an incredibly slow place whenever 3D was used.

Thanks for any help, though I know it might not be possible,

-Harmony.

---

