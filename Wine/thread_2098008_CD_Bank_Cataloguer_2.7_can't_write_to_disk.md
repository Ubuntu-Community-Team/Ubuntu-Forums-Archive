---
title: "CD Bank Cataloguer 2.7 can't write to disk"
date: 2012-12-25
forum: Wine
---

### Post by Holmes.Sherlock on 2012-12-25
I am trying to run [CD Bank Cataloguer 2.7]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5091") on Wine 1.4 on ubuntu 12.04.  When I am trying to import from an archive, it prompts that "Can't write to disk". Any idea on how to proceed?

---

### Post by Holmes.Sherlock on 2012-12-31
Does anybody know about any such equivalent software which runs on Ubuntu to catalog large number of CD/DVD ?

---

### Post by dino99 on 2012-12-31
maybe you'll get more chance using wine1.5 from ppa
and glance at your logs for possible usefull warnings/errors.

---

### Post by fdrake on 2012-12-31
> **Holmes.Sherlock said:**
> I am trying to run [CD Bank Cataloguer 2.7]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5091") on Wine 1.4 on ubuntu 12.04.  When I am trying to import from an archive, it prompts that "Can't write to disk". Any idea on how to proceed?
what kind of archive?

also are you tryng to save , write something somewhere also?

---

### Post by Holmes.Sherlock on 2012-12-31
> **fdrake said:**
> what kind of archive?

CD Bank Cataloguer exports application data to .CBA archive in some proprietary format. It can be restored/imported onto a new installation.

---

### Post by fdrake on 2012-12-31
where are you trying to export/save it?

---

### Post by Holmes.Sherlock on 2012-12-31
> **fdrake said:**
> where are you trying to export/save it?
I exported the .CBA from Windows installation of CD Bank and tring to import in CD Bank on Wine on Ubuntu 12.04

---

### Post by fdrake on 2012-12-31
> **Holmes.Sherlock said:**
> I exported the .CBA from Windows installation of CD Bank and tring to import in CD Bank on Wine on Ubuntu 12.04

try with "gksudo wine cdbank(or watever is the name of the program)"
it's not very elegant but if it doesn't work it's another kind of problem not a permission issue.

---

