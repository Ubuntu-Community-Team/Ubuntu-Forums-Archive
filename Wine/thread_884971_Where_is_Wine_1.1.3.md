---
title: "Where is Wine 1.1.3?"
date: 2008-08-09
forum: Wine
---

### Post by BoneSmash on 2008-08-09
I keep checking back at WineHQ to see if they released the latest version yet and nothing has happened.  I'm just curious if anybody knows why there has been a delay, because as far as I know a new release is supposed to be out every other Friday, it is now Saturday.
Thanks

---

### Post by YokoZar on 2008-08-09
Alexandre Julliard, the lead developer, took the week off (last commit was on Monday), so the next release gets delayed a week.

---

### Post by Cope57 on 2008-08-09
You having patch release blues?

---

### Post by BoneSmash on 2008-08-09
Haha, maybe a little.  It's just been something that I've started to look forward to at the end of the week, it seems like Wine is finally taking shape and working well more often than not.

---

### Post by Brebs on 2008-08-09
Do a git checkout, e.g.:
```
git clone git://source.winehq.org/git/wine.git wine
tar -cvjf wine-git20080804.tar.bz2 wine
```

---

### Post by BoneSmash on 2008-08-09
I actually know nothing about Git, thanks for pointing it out.  From what I can tell it just gives me the latest submitted patches before an official release?  I might be totally wrong.

---

### Post by YokoZar on 2008-08-10
> **BoneSmash said:**
> Haha, maybe a little.  It's just been something that I've started to look forward to at the end of the week, it seems like Wine is finally taking shape and working well more often than not.
You look forward to it, and I look forward to the off weekends when I don't have a whole new Wine to package, test, and upload.  People wonder why I spend my entire Friday in front of the computer ;)

---

### Post by mellery on 2008-08-10
I'm looking forward to trying out Spore, hopefully this patch makes it into 1.1.3! [http://bugs.winehq.org/show_bug.cgi?id=13988](http://bugs.winehq.org/show_bug.cgi?id=13988)

---

