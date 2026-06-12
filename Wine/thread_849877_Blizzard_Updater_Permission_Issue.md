---
title: "Blizzard Updater Permission Issue"
date: 2008-07-04
forum: Wine
---

### Post by sil3nt on 2008-07-04
Hi Guys I just installed wow on Hardy the game launches ok no issues there but I need to apply the new patches.

I run the launcher.exe works ok downloads the patch but then I get a permission error :

```
 Blizzard Updater is unable to write to this location because it is a system directory.
```

What directory is this trying to write to? I have the correct RW-X permissions on my home folder where wine is installed.

The program itself is located in the root of C: in wine not program files but I am assuming this should make no difference.

Im stuck any advice?

---

### Post by sil3nt on 2008-07-05
Solved I copied the WOW folder to Program Files inside of .Wine works fine now :)

---

