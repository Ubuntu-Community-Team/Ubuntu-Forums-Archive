---
title: "Word crashes since Hardy upgrade"
date: 2008-07-11
forum: Wine
---

### Post by bsmith1051 on 2008-07-11
I had Word 2000 running just fine on my original setup, Ubuntu 7.10 with Crossover 6.2 (and Wine 1.1, though I understand that Crossover uses it's own copy of Wine).

Then I upgraded to Ubuntu 8.04.1 and now Word will forcibly close about 2 seconds after opening.  There's no error message.

Is there a log file I can check to see what's wrong?
Do I just need to reinstall it, and if so how?

---

### Post by bsmith1051 on 2008-07-13
Figured it out. It was the 'vm.mmap_min_addr' issue.  Since I'd waited until the release of 8.04.1 to upgrade I'd missed all the discussion about it back in March.

---

