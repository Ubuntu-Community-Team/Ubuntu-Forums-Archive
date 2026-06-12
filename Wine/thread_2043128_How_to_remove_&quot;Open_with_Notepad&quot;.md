---
title: "How to remove &quot;Open with Notepad&quot;?"
date: 2012-08-15
forum: Wine
---

### Post by crixtiano on 2012-08-15
I just removed wine, I want it completely removed from my system (Ubuntu 12.04). 

I installed it and removed it using the Software Center. 

However I still have associated options in the Nautilus context menu. For example when I right click any text file I have "Open With notepad" as an option.

Please, how to remove this from my computer?

---

### Post by wojox on 2012-08-15
Look in ```
~/.local/share/applications/mimeinfo.cache
``` and remove the Notepad reference. :P

---

### Post by Toz on 2012-08-15
Moved to Wine.

---

