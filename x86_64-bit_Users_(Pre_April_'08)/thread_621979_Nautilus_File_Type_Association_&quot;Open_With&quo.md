---
title: "Nautilus: File Type Association &quot;Open With&quot; bug?"
date: 2007-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by GrammatonCleric on 2007-11-24
Not sure if this is a bug or not...

Hardware: Dell D820 laptop
Ubuntu Version: 7.10 AMD64 with all current updates installed

I recently did a fresh install of my laptop using the 64bit version of Gutsy.  One of the things I noticed was that I could not associate new applications to file types via Nautilus.  The process I'm trying is...


1. Open **Nautilus.**

2. Browse to a file that you want to associate to a new applications (i.e. MP3 and Audacious).

3.  **Right click** on the  file, in this case an mp3, and select Properties.

4. Now click on the **Open With** tab.

5. Now here's where the problem is.  If I try to select the radial button next to the application that I want to associate with, again in this case MP3s, file type I can highlight the application but I can not enable the radial button to the left of the application that I want to use.  So I can not change the application associated with the file type.

Can anyone else confirm the issue?

For me this is not limited to just MP3 but any file type.

-GC

---

### Post by drs305 on 2007-11-24
I'm running the same setup (7.10 AMD64)  but do not have the problem you are experiencing. Everything works normally so it must be something within your setup.

Good luck.

---

### Post by GrammatonCleric on 2007-11-24
Thanks!   Managed to fix the issue by removing the file...
```


rm -f .local/share/applications/defaults.list


```

...and rebooting.

-GC

---

