---
title: "Wine on 8.04 64bit?"
date: 2008-05-03
forum: x86 64-bit Users
---

### Post by cooltuyul on 2008-05-03
i can't seem to run wine on 8.04 64bit version. help is appreciated.

---

### Post by jespdj on 2008-05-03
It would be easier to help you if you provided some more information.

For example: What did you try and what happened? Did you get error messages? If so, then what are the error messages?

---

### Post by Half-Left on 2008-05-03
WINE works fine in 64bit version, are you opening the .exe with WINE?

---

### Post by Perfect Storm on 2008-05-03
Here's something you can chew on if you're new to wine: [http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)

---

### Post by felker2 on 2008-05-03
> **cooltuyul said:**
> i can't seem to run wine on 8.04 64bit version. help is appreciated.

Well, *I* can wine on 8.04 64-bit ... ;-)

---

### Post by ptn107 on 2008-05-03
It's better [for AMD64] if you use the version provided by [http://winehq.org/](http://winehq.org/) and not from Ubuntu's repositories.

See [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) for info.

---

### Post by cooltuyul on 2008-05-05
the wine i have doesn't show up under accessories but it has its own little tab under apps., but theres no file searcher! just notepad and to uninstall file converted by wine.

---

### Post by stephenb on 2008-05-09
No, when it comes to WINE, nothing at all is working for me. 

If I run "wine notepad++.exe" from a terminal, I get back "Segmentation fault"
And in syslog, I'll get this message: May  9 13:13:46 server1 kernel: [49772.689804] wine[27222]: segfault at 4a6c3f68 rip 4a6c3f68 rsp ff88530c error 15

It's the same for everything I run. This happens with version 0.9.59 and 0.9.61

I have never experienced this in Ubuntu until I upgraded to Hardy. I'm pretty disappointed at the moment. I didn't expect to go backwards with an upgrade.

Not sure what to try other than wait for a fix.

---

