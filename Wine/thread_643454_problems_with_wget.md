---
title: "problems with wget"
date: 2007-12-17
forum: Wine
---

### Post by CanadianGuitarist on 2007-12-17
so im trying to download wine and wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add - doesnt seem to do anything for me. is there another way to do what that line is supposed to do?

EDIT: or if there is another thread on this topic, could i be directed to that?

---

### Post by wharp on 2007-12-17
Is there a reason the wine package in the repo's does not work?

Also, do you get any error message or other output?

---

### Post by CarpKing on 2007-12-17
The Wine repository has been timing out for me for a few days.  This is probably the reason for your problems (I just tried that command, and got the same result- nothing.  If you let it sit long enough it will probably give a timeout error).  Unless there's a problem we're both having, you'll have to wait until the repository gets straightened out.

---

### Post by CanadianGuitarist on 2007-12-17
will  that happen anytime soon?

---

