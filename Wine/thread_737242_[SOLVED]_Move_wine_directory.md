---
title: "[SOLVED] Move wine directory?"
date: 2008-03-27
forum: Wine
---

### Post by djbon2112 on 2008-03-27
Title says it all: I don't want my wine install to be in /home/<me>/.wine, I want it to be (permanently) in /usr/wine . Is there a way to move it like this? I know about wine prefixes, but that's not what I want: I want to move the default wine directory to the new location, not just create a prefix there.

---

### Post by aashay on 2008-03-27
move it wherever you want, put a symlink in its place.
If you want to move only the drives, try 'winecfg'. Just type it in a terminal

---

### Post by djbon2112 on 2008-03-27
Makes sense, wonder why I didn't think of that!

Solved.

---

### Post by BFG on 2009-05-12
Sorry to drag up an old thread, but I also need to do this.

Will this approach work for multiple users on the same machine, with them all being able to use the wine apps?

---

### Post by djbon2112 on 2009-05-12
> **BFG said:**
> Sorry to drag up an old thread, but I also need to do this.

Will this approach work for multiple users on the same machine, with them all being able to use the wine apps?

If you point all the symlinks in all their /home/<user> folders to the same place (e.g. /usr/wine as I use), then yes.

---

