---
title: "wineboot.exe filling up memory"
date: 2017-02-22
forum: Wine
---

### Post by wjbmd48 on 2017-02-22
Hi:

I recently did a reinstall of lubuntu 16.04 64-bit, and everything worked fine, including my wine/Microsoft Office 2003. Then, after a kernel upgrade, every time I fire up an Office program, the memory fills up with wineboot.exe and I can't load files into the Office apps, "insufficient memory."

I've tried winepurge and uninstalling/reinstalling wine, no joy.

Any ideas?

Thanks!

Bill

---

### Post by howefield on 2017-02-22
Thread moved to the "*Wine*" forum.

---

### Post by ajgreeny on 2017-02-26
Try renaming the hidden .wine folder in your home and then reinstalling the applications you have in the wine subsystem; it may be the applications that are causing the problems for you, not wine itself, though I have not used wine for years so could be wrong.

---

### Post by wjbmd48 on 2017-02-26
Amazing, I didn't expect it to work, since even opening wine settings set it off, also. 

But work it did, thanks so much!

Marked solved,

Bill

---

