---
title: "Can't browse &quot;C-drive&quot; under 12.04"
date: 2012-10-05
forum: Wine
---

### Post by XEtedBear on 2012-10-05
It's been a while since I needed to use WINE. In the meantime I upgraded from 11.10 to 12.04. Now I cannot do: <Applications><WINE><Browse C-drive>. In fact WINE is not even listed as an application in the dash, although it is available from the context menu on any file. However I need to do some file manipulation under 'Windows'. 

How do I browse my 'C-drive' ?

---

### Post by doorknob60 on 2012-10-05
To browse to it manually, open ~/.wine/drive_c in your file browser.

---

### Post by XEtedBear on 2012-10-06
Thanks for this advice. Any idea why this was made so difficult to find in 12.04, or less easy to use than the approach of 11.10?

---

### Post by thatguruguy on 2012-10-06
> **XEtedBear said:**
> Thanks for this advice. Any idea why this was made so difficult to find in 12.04, or less easy to use than the approach of 11.10?

To the best of my recollection, it's always been that way.

By the way, now that you have your answer, you should mark this thread as "solved."

---

### Post by cwwilson721 on 2012-10-06
You may want to upgrade/update wine, too.
Read the stickies in this forum on adding the repo, then

```
sudo apt-get install wine1.5
```

---

