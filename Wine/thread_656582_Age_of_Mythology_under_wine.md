---
title: "Age of Mythology under wine"
date: 2008-01-02
forum: Wine
---

### Post by metalpancake on 2008-01-02
Hi! I was wondering if anyone else has tried to get Age of Mythology running under wine in Gutsy. I have tried but straight after it asks me for the product key it tells me it could not find 'pidgin.dll'.

here is the output of the terminal:```
err:module:import_dll Library MFC42.DLL (which is needed by L"D:\\pidgenx.dll") not found

```

I have done a search on google, and this seems to be a common problem. Apparently there is a way to fix the problem but I couldn't find it.

I looked at the files on the disk and I did find one called 'pidgenx.dll if this is any help.

Thanks in Advance for the help!

---

### Post by metalpancake on 2008-01-03
bump...

---

### Post by metalpancake on 2008-01-06
bump again

---

### Post by happyhamster on 2008-01-06
Best place too look is the Wine Application Database:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1979](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1979)

Anyway, you'll need to get a native windows file: mfc42.dll
Get it from a windows pc, or download it from somewhere and put it in your system32 folder. (It's a hidden folder in your home dir, usually: .wine/drive_c/windows/system32).

Age of Mythology should run fine, although some people (including myself) encounter major sound stuttering. Good luck.

---

### Post by metalpancake on 2008-01-08
Thanks! will do. :)

---

