---
title: "Running Baldur's Gate II"
date: 2013-03-11
forum: Wine
---

### Post by Nyakitty on 2013-03-11
I'm running wine 1.4.1 on ubuntu 12.10. I've managed to get the game successfully installed using instructions found online, but when I try to launch the game nothing happens. Clicking on BGMain.exe or baldur.exe doesn't do anything, though when I type "wine BGMain.exe" in a terminal I get the following errors:

"err:module:import_dll Library DPLAYX.dll (which is needed by L"C:\\Program Files\\Black Isle\\BGII - SoA\\BGMain.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Black Isle\\BGII - SoA\\BGMain.exe" failed, status c0000135"

I'm guessing the errors have something to do with this, but I haven't been using linux or wine for very long, so I have no clue what to do.

---

### Post by kostkon on 2013-03-11
Search for *winetricks* in your dash, launch it and install *DirectPlay*.

If you can't find it in the dash, the try to do the above using the terminal, i.e.:
```
winetricks directplay
```

Also, try installing the latest version of Wine; instructions are [here]("http://www.winehq.org/download/ubuntu").

Hope that helps.

---

### Post by Nyakitty on 2013-03-12
> **kostkon said:**
> Search for *winetricks* in your dash, launch it and install *DirectPlay*.

If you can't find it in the dash, the try to do the above using the terminal, i.e.:
```
winetricks directplay
```

Also, try installing the latest version of Wine; instructions are [here]("http://www.winehq.org/download/ubuntu").

Hope that helps.

Thank you very much, that fixed it. :P I'm surprised the solution was so simple.

I seem to now be having trouble getting the game to recognize the disk; it says "Place cd 2 in drive D:\ and doesn't do anything when I insert the second disk. I think I'll probably be able to figure this out, though.

---

