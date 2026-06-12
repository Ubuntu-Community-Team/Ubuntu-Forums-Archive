---
title: "3dmark2006 and wine 1.0?"
date: 2008-06-23
forum: Wine
---

### Post by wolfe on 2008-06-23
I see a few threads about how to get this app running on older versions of wine.  Is there a way I can get it to run with the new 1.0 version of wine?

I'm on 64 bit ubuntu.  TIA

---

### Post by wolfe on 2008-06-23
anyone? any ideas where to start?

---

### Post by FlyingIsFun1217 on 2008-06-23
Check to see if the [AppDB]("http://appdb.winehq.com/") has anything on it.

FlyingIsFun1217

---

### Post by wolfe on 2008-06-24
I've already checked the wineappdb, it just says that it works with 8.04, no details.

---

### Post by FlyingIsFun1217 on 2008-06-24
The [AppDB page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6612&iTestingId=21658") shows it as being rated as 'Garbage' (and I doubt much has changed in the two releases from 1.0-rc4 to 1.0 stable).

On top of that, the maintainer left a note that to run correctly, it needs MSVC++ 2005 (sp1) runtime libraries. Make sure you have these installed if you want to run the program.

FlyingIsFun1217

---

### Post by wolfe on 2008-06-24
I have installed that already.  I read the appdb before I posted here.

and I see the rating as bronze for my 8.04

---

### Post by FlyingIsFun1217 on 2008-06-25
Yes, but it's also rated for bronze on Wine version 0.9.61, and since I'm assuming your using the latest one (v1.0 stable), your results should more closely match those of the test with Wine 1.0-rc4 (which is 'Garbage').

Try running it under Wine v0.9.61, as that seems to yield decent results. You cannot rely on the version of your OS for this sort of thing, as Wine is the compatibility layer that is running the program (in a twisted sense).

FlyingIsFun1217

---

