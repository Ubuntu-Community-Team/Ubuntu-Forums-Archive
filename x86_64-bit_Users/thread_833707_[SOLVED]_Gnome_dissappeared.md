---
title: "[SOLVED] Gnome dissappeared"
date: 2008-06-18
forum: x86 64-bit Users
---

### Post by rothbert on 2008-06-18
Currently I can only get gnome working by logging in with the gnome failsafe option. Everything seems to be working ok when so logged in.

Otherwise (with standard login) all I get are desktop icons which seem to work. Have to exit with cntl-alt-backspace.

Began after a random lockup.

I suspect the solution lies in tweaking /.gnome2/session but not sure exactly what i should do there. Don't want to break it any further :-)

Running Ubuntu 8.04 on an AMD64 machine, 4GB ram, system up to date.

Have done some searching on this with no luck.

Would really appreciate some help, bit of a newbie etc. 

Cheers

---

### Post by bford16 on 2008-06-19
This used to happen to me all the time.  The easiest way to fix it is to log in to Failsafe GNOME, then move ~/.gnome2 and ~/.gnome2_private to trash.  Once you have your regular session loaded again, you can add back the contents of those two directories (do not overwrite files).  I never bothered to figure out what was corrupted, because it is very easy to restore the contents of the two directories.

If you don't want to do something so drastic, you could try deleting ~/.gnome2/session first.

---

### Post by rothbert on 2008-06-19
Cheers bford16!
Removed ~/.gnome2/session and that seems to have done the trick.
many thanks :-)

---

