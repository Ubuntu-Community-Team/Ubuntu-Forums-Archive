---
title: "Zoo Tycoon 2: Zookeeper Collection"
date: 2008-06-22
forum: Wine
---

### Post by Affrikka on 2008-06-22
I am running 8.04 "Hefty"

on AppDB it says Zoo Tycoon 2 runs without many problems, with the exception of the mouse graphics, but that doesn't really bother me.
I installed it under WINE and searched around my computer looking for it.
Under the Wine tab in "Applications" The only ZT2 thing I have is "Zoo Tycoon 2 Profiles"

I clicked on it and on my task bar it showed 'Starting zt2 Profiles'
then about 8 seconds later it jsut closed out before it even started.

This is the only thing I can find for ZT2, and I know it should work because AppDB says it does.


I guess my question is how do I make it run?

EDIT: I stumbled upon something in the actual files on ZT, and clicked on it.. I'm not sure if it was 'Startup.exe' or 'ZT2.exe' but then the little screen that shows up when loading it popped up.

Now, when it's loading up the game I keep getting a message just saying
005D
on it.

---

### Post by Affrikka on 2008-06-22
anyone?

---

### Post by AlienWolf on 2008-11-23
You need to copy MFC42.DLL into ~/.wine/drive_c/windows/system32
You can get the file (version 6) from this page [http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html")

~ AlienWolf

---

### Post by poisonkiller on 2008-11-23
> **AlienWolf said:**
> You need to copy MFC42.DLL into ~/.wine/drive_c/windows/system32
You can get the file (version 6) from this page [http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html")

~ AlienWolf
Thank you so much!!! I thought I'd never get ZT2 running. :)

EDIT: You should post this fix to Wine AppDB, too.

---

