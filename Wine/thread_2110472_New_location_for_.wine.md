---
title: "New location for .wine"
date: 2013-01-30
forum: Wine
---

### Post by ooleyguy on 2013-01-30
If I mount a partition at /home/[user]/.wine will all the installed programs, settings, etc. be placed on that partition (that is on another physical hard drive) instead of in my /home/user folder on my main hard drive? or should I mount it at /home/[user]?

---

### Post by Tweak42 on 2013-01-30
> **ooleyguy said:**
> If I mount a partition at /home/[user]/.wine will all the installed programs, settings, etc. be placed on that partition (that is on another physical hard drive) instead of in my /home/user folder on my main hard drive? or should I mount it at /home/[user]?

Yes, the .wine directory will physically be on that partition. You can also do that with the entire user directory, or even further up to the entire home directory.

Things to take in consideration are ability to login if mount gets broken such as from a harddrive failure.

Another option is to use symlinks to link .wine or any other large directories to a formatted partition that has more space.

---

### Post by dmallion on 2013-01-31
You could mount it anywhere and just change the wine prefix location.
```
export WINEPREFIX=/mnt/hd/
```

---

