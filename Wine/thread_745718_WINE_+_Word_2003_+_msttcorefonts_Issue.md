---
title: "WINE + Word 2003 + msttcorefonts Issue"
date: 2008-04-04
forum: Wine
---

### Post by c-ron on 2008-04-04
When using Microsoft Word 2003 under Wine in Hardy, all of the fonts included with the msttcorefonts package always display as if they're bolded. Bolding and unbolding them does not change their appearance. The other fonts available display normally, and the same fonts in Abiword act as they should.
Has anyone else run into this?

---

### Post by c-ron on 2008-04-07
BUMP

Hope I didn't get the 'Windows User' tag just from this! :-D

---

### Post by cogadh on 2008-04-07
This is a known bug with Word in Wine:
[http://bugs.winehq.org/show_bug.cgi?id=11347](http://bugs.winehq.org/show_bug.cgi?id=11347)

There is a possible workaround listed on the Bugzilla page and the AppDB page for Word, but it only works for some fonts:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2735](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2735)

On a side note, is there a particular reason you need to use Word and can't use a Linux native alternative like OpenOffice?

---

### Post by jjk7288 on 2008-04-08
> **cogadh said:**
> On a side note, is there a particular reason you need to use Word and can't use a Linux native alternative like OpenOffice?

Does it matter? Maybe he just wants to use Word.

---

### Post by cogadh on 2008-04-08
It does matter if he needs something that "just works" and doesn't want to deal with the trouble of trying to run it with Wine. It is almost always better to find a native product that suits your needs, than to try and get something to work in Wine; especially in situations like this where the problem he is having is a known bug in Wine that cannot actually be corrected by the user.

---

### Post by c-ron on 2008-04-21
> **jjk7288 said:**
> Does it matter? Maybe he just wants to use Word.

Actually, I hate Word. I'd much rather use OO.org Writer, or even Abiword, but my roommate uses my computer too, and he has some kind of weird **M**a**S**ochistic Word fetish.

---

### Post by benbuntu on 2008-04-23
c-ron, I originally reported this bug back in wine 0.9.53.  Happily, it has just been fixed in wine 0.9.60.  Please post if the new version does not fix it for you.

-Ben

---

