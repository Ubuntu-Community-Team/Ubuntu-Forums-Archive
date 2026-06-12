---
title: "HOWTO: Wine Team PPA, New Wine development releases, older versions of Wine"
date: 2008-07-27
forum: Wine
---

### Post by YokoZar on 2008-07-27
**Installing Wine**
To install the Wine package that's already included with Ubuntu, just [click this link](apt://wine).

**Wine Team PPA**
There are two reasons to use the Wine Team PPA: frustration with the included package, and using Wine beta releases.  To enable the PPA, [follow these instructions](http://www.winehq.org/site/download-deb).  You may be prompted to do a partial upgrade - this is normal.

**Wine Beta releases**
If the included stable version of Wine doesn't work for the application you want to use, you can try using a beta release instead.

Unlike the stable version of Wine, Wine betas are *not substantially tested and prone to [regressions](http://wiki.winehq.org/Regression)*.  This means that for your application a newer Wine release could be *worse* than an older one, including the stable Wine available by default.

To get the latest beta release of Wine and receive automatic updates, enable the PPA as indicated above and then [install the *wine1.5* package](apt://wine1.5).


**Older Wines:**
Very occasionally, you may want to try installing an older Wine into a new Ubuntu.  This is something you only want to bother with if you're trying to use an application that suffers from an (as yet unfixed) regression.

If this is what you need, you can go here for specific packages: [http://wine.budgetdedicated.com/archive](http://wine.budgetdedicated.com/archive)

If the Wine package you want is so old that it's only available for older versions of Ubuntu, then you can try installing the package for the old version directly.  Packages built for one release of Ubuntu often work in the next.

---

