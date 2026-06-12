---
title: "Can't uninstall?"
date: 2008-07-24
forum: Wine
---

### Post by TrikeKid on 2008-07-24
I just installed wine and to test it I just grabbed the first game I found, Trophy Bass 3D, fun game but I haven't played it since my W98 days, it did install, and it tries really hard to work but the graphics are so far out of whack you can't really do much of anything. Game wasn't the reason I installed wine in the first place so I'd like to get rid of it, but I can't uninstall it using the uninstall tool from the game itself. I get an error message saying that it can't find an installation log file that is the uninstaller. How do I get rid of it? I removed the graphic software it uses no problem.

---

### Post by lanmancz on 2008-07-24
go to /home/<username>/.wine/drive_c/, find the instalation folder of that game and just delete it manually :)

---

### Post by prabath_fun on 2008-07-30
Hi,
  After deleting the application folder, Is it, required to delete the registry entry as well? If, so, How?
   That is, I want to remove the application under wine completely. :)

Prabath

---

### Post by EnGorDiaz on 2008-07-31
look for regedit.exe in the windows folder then look at the hkeys and delete the registry

---

### Post by DoktorSeven on 2008-07-31
How about Wine's uninstaller?

From terminal:
```
uninstaller
```

---

### Post by prabath_fun on 2008-08-01
But, Still menu under applications -> wine -> programs, It is available. 
Prabath

---

### Post by Quelthuzar on 2008-08-01
> **prabath_fun said:**
> But, Still menu under applications -> wine -> programs, It is available. 
Prabath

I had same prob and cleared it once I had hit right click on "Applications" on panel, "edit menu" and delete the wine folder.

However that was after I uninstalled wine.

Greetings,
Quelthuzar

---

### Post by prabath_fun on 2008-08-03
Thanks.
  I got it deleted. 
Prabath

---

