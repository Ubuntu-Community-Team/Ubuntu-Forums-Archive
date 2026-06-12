---
title: "Gdesklets do not seem to run in hardy 64bit"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by Saubazi on 2008-05-04
Just upgraded to hardy and gdesklets stopped running.
Tried putting python2.4 in various files as seemed to be the
resolution from gutsy but no go.

For example, for gdesklets shell I get:

 /usr/lib/gdesklets/libdesklets/system/gtop.so: undefined symbol: Py_InitModule4_64
System in /usr/lib/gdesklets/Controls/System is NOT a valid plugin!

For gdesklets configure I get:
Could not import tiling module!

and so on...

---

### Post by Sam Lars on 2008-05-17
For me gdesklets just sits on connecting to the daemon and then times out.

---

### Post by Mindless Automata on 2008-05-17
[http://ubuntuforums.org/showthread.php?t=785806](http://ubuntuforums.org/showthread.php?t=785806) is my problem

Unfortunately, it doesn't seem anyone is interested in fixing this, because it's been this way for awhile and nobody seems to reply when these threads come up.

---

### Post by Cuppa-Chino on 2008-05-24
> **Sam Lars said:**
> For me gdesklets just sits on connecting to the daemon and then times out.

me too -- it goes off looking for the daemon and never comes back...

---

### Post by Yellow Pasque on 2008-05-24
The search function is our friend:
[http://ubuntuforums.org/showthread.php?t=582721](http://ubuntuforums.org/showthread.php?t=582721)

---

### Post by araz_233 on 2009-08-24
the problem with tiling module occures with python2.6 and is fixed with this patch: [http://repos.archlinux.org/viewvc.cgi/gdesklets/repos/extra-x86_64/](http://repos.archlinux.org/viewvc.cgi/gdesklets/repos/extra-x86_64/) (no-import-overide.patch) 
the patch just comments some module import code: lines 115-128 of this file: /usr/lib/gdesklets/utils/ErrorFormatter.py (if installed by apt)

from: [https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/344079](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/344079)

---

