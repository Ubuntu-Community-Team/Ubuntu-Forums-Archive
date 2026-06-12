---
title: "Batch files STILL exist?"
date: 2008-08-25
forum: Wine
---

### Post by CastilleV on 2008-08-25
I was testing around with some batch files.
```

@echo on
title This is a test batch file
echo this is a test!
pause
msg * This file will terminate itself
pause
del *.bat
pause
echo goodbye!
exit

```
And the file no longer shows. But when I try ti upload images via imageshack it shows that the batch file is still there.

---

### Post by lisati on 2008-08-25
A couple of suggestions to get the discussion started:

Part of this could be that when you delete files, it is common not to actually delete the file, but to alter the pointers in the directory structure. Another possibility is that there is some kind of directory caching present.

---

### Post by sonofusion82 on 2008-08-25
it might be possible that the file is locked, you can't delete the batch file itself while it is still being accessed

---

