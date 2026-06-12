---
title: "Upgrade to hardy and can not open any of my pdf files..."
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by Saubazi on 2008-05-06
Great, yet another thing that went wrong with upgrade. The document viewer absolutely refuses to open any pdf files that I have - worked just fine before update. I installed kpdf so that I can at least open but I'd like to have the stuff working when doubleclicking the docs from nautilus.

Such a nuisance. Should have made the tedious reinstall on free partition and made sure the thing works instead of upgrading a perfectly working gutsy...

---

### Post by fjgaude on 2008-05-06
Do you have evince installed? That the normal program to read pdf files.

---

### Post by Saubazi on 2008-05-08
Yes, of course I do. Isn't evince there as default on ubuntu-desktop. Anyway, before update - evince opened the pdf's quite normally - now it does not. Also, if I start evince and try to open a pdf file it does not even offer pdf as an alternative and won't show pdf files in a directory before I choose filter option "All Files", if I choose a pdf file it complains about unhandled MIME type - it is as if evince had forgotten everything about pdf...

---

### Post by Saubazi on 2008-05-08
Here is somebody having similar issue with debian...

[http://www.debianhelp.org/node/9885](http://www.debianhelp.org/node/9885)

---

### Post by Sef on 2008-05-08
Have you tried another pdf viewer?  Applications > Add/Remove > Search: PDF and choose the one you want.

---

### Post by Saubazi on 2008-05-15
Said so in my opening - kpdf works - it is only that I have to search it again and again when for example browser wants to open a pdf - evince is offered as a default.

Anyway, I noticed from the debian bit that I had problems with this mime stuff and it had only entries about gdesklets - well I installed a gdesklet package for hardy from a .deb of unknown origin. Gdesklets worked but apparently broke something else. After removing gdesklets the evince problem was resolved. Don't have running gdesklets for Hardy now, though :/

---

