---
title: "fl studio stopped working under WINE"
date: 2017-09-07
forum: Wine
---

### Post by adrianr2 on 2017-09-07
So this all has to do with the wine program.
Recently my program fl studio stopped working all of a sudden.
I tried to open it one day and it brought up a prompt saying "program error, due to program or deficiency in wine".
The program is fl studio.
I deleted everything that had to do with wine and fl studio.
I re-downloaded both applications multiple times and to no avail.
Nothing has worked. The same prompt pops up.
I need help plz if someone can help me out or give me advice it would be greatly appreciated.
Thank you!

---

### Post by wildmanne39 on 2017-09-07
*Thread moved to **Wine for a better fit**.*

---

### Post by yoshii on 2017-09-11
Try invoking FL Studio from a terminal, using something similar to (not exactly sure) $ wine start "FL.exe" from within the directory of FL Studio.  While it's starting, look at the terminal's output.  It should let you know if a DLL is missing or something.  Often, if a DLL is missing, you can copy it from Windows or download from the internet and put it where it needs to go (usually C:\Windows\System32).  Let me know if this helps.  

Also ask them at [URL="http://winehq.org"]http://winehq.org

[/URL]

---

