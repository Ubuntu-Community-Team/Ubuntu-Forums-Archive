---
title: "Wine registry"
date: 2012-03-18
forum: Wine
---

### Post by srharri9 on 2012-03-18
I can open regedit in Wine, but I'm looking to import some changes to a key within.  When I use the import feature of regedit, nothing happens.  I see the .reg file to add, but when I click import, it doesn't do anything. No data is imported.  What am I doing wrong?

---

### Post by Mark Phelps on 2012-03-18
You need to understand that Wine is NOT an emulation of MS Windows but instead, a hack that replaces Windows DLLs with custom DLLs that make Linux kernel OS calls.

While I would have expected regedit to work, I am not surprised that it doesn't.  Registry add-on programs are known not to work in Wine.

If you're using MS Windows enough that you need to hack away at the registry, then Wine is not the solution you need; instead, you need to dual-boot or use Virtualbox.

---

### Post by zombifier25 on 2012-03-18
You can manually add the registry key if you want. Open the .reg file, see what will be added and do the dirty work in regedit yourself instead.

---

### Post by Perfect Storm on 2012-03-18
Moved to wine forum.

---

### Post by srharri9 on 2012-03-18
It's not that I need to hack away, its that I need to add some values to it so that a game will work.  I'm not familiar enough with the regristry to manually add values (though I'm sure it's not too hard) and I was hoping to just be able to add them all at once. I'll figure out how to add them manually.  

Thanks for the info.

---

