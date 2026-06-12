---
title: "Just ordered a AMD64."
date: 2005-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by AndersAA on 2005-01-28
Just wondering if I can change the repositories around and script a little something to reinstall all packages?  To somehow allow me to reinstall every package without reinstalling the system :p

(yes... I'm a lazy lazy person :p ).

I figure I could change the repositories and script something to apt-get reinstall everything.  Anyone see any big bumps along the road for me here?

---

### Post by valadil on 2005-01-28
Wouldn't it be easier to make a list of the packages you have and apt-get install those on the new system?  

If you really want to back up your changes just back up /etc and /home and you should be all set.  This is why I keep a separate partition for /home btw.  No need to redo my desktop.  Ever.

---

### Post by AndersAA on 2005-01-29
my homedir is on a seperate encrypted partition anyway, so no sweat there... hmm.. maybe I should just install the latest hoary snapshot.  And switch to xfs while I'm at it, using reiserfs now, I much prefer xfs, but there was a warning about using it on boot in warty I believe.

---

### Post by valadil on 2005-01-29
The warning just says that you make a boot partition (I used 100mb) and put ext3 on it.  No biggie.

---

