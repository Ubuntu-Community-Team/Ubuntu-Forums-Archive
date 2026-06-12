---
title: "how can i install counter strike on ubuntu gutsy?"
date: 2007-12-08
forum: Wine
---

### Post by cc93 on 2007-12-08
hello i have just downloaded steam but file's type is  .msi and wine doesnt opens it
well what can i do?

---

### Post by dudeofthedead on 2007-12-08
```
wine msiexec /i yourfile.msi 
```

---

### Post by AJLChase on 2007-12-09
I am having the same exact problem. It's saved to my desktop and when i tried to run the command I got.


wine msiexec /i steaminstall.msi
err:msi:copy_package_to_temp failed to copy package L"steaminstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"steaminstall.msi

---

### Post by cogadh on 2007-12-09
Don't save the file to your desktop, save it in your home folder. If you save it to your desktop, you first need to change directories to the dektop, then run the command.

There is a decent Steam how-to in Wine's Application Database:
[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

---

### Post by MickLionheart on 2007-12-09
Also don't forget Linux gets picky about capitals and lowercase.

---

