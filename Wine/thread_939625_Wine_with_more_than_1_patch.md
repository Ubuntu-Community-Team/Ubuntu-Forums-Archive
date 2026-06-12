---
title: "Wine with more than 1 patch"
date: 2008-10-06
forum: Wine
---

### Post by thefishki345 on 2008-10-06
Hi, I have wine 1.0 with the cod4 patch (the one to get it working) but would also like to recompile the most recent wine version with another patch (one that gives assassins creed mouse catch) is it possible to compile wine with multiple patches? I know how to compile it with just 1, that is easy, but is it just a simple matter as to patch them all on and get all the hunks 1 2 3 4 to work for both of them AND THEN do make install?

thanks

---

### Post by jim_24601 on 2008-10-06
It'll almost certainly apply, and probably work. There is a lot of code in Wine, and most patches only affect a few lines of it, so unless you're very unlucky they won't overlap. Similarly with functionality--it's possible that two patches will affect functionality even if they don't alter the same physical location in the source, but again quite unlikely.

Best advice: try it and see. ;)

---

### Post by thefishki345 on 2008-10-06
ok thanks, will do

I shall try it and report back

---

