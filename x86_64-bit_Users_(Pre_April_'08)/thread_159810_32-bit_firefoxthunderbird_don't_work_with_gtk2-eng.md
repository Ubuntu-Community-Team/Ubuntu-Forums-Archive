---
title: "32-bit firefox/thunderbird don't work with gtk2-engines-gtk-qt"
date: 2006-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by awry on 2006-04-13
I'm running Breezy, and to take advantage of some key features in the 1.5 series of Tbird and Firefox, I've installed the 32-bit binaries from mozilla.org.  I created a wrapper script like this to call them, since they require 32-bit gtk2 libs:

```
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0/
export PANGO_RC_FILE=/etc/pango32/pangorc
sh /opt/firefox/firefox
```

This works fine, except that as a KDE user, I would like to have QT do all the widget drawing, which is exactly what the gtk2-engines-gtk-qt package is supposed to do.

When I run the 64-bit firefox-1.0.7 that comes packaged in Breezy, the gtk-qt engine works great, just as expected.

When I run either of my 32-bit 1.5.x binaries downloaded from mozilla, the gtk-qt engine doesn't do anything at all, and I am left with my standard "boxy" ff/tb windows.

It looks like maybe the gtk-qt engine only works for apps linked against the 64-bit gtk2 libs.

Does anyone know of a solution/workaround?

---

### Post by cypher35 on 2007-05-17
Sorry to resurrect an old thread, but I've got this same problem.  Is there any fix?

---

### Post by Kilz on 2007-05-17
> **cypher35 said:**
> Sorry to resurrect an old thread, but I've got this same problem.  Is there any fix?

The fix is to get the 32bit package, use ```
dpkg -x TheNameOfTheDeb.deb
``` to extract the contents of the deb file. Then copy it into place. You will have to change some of the locations. If any of the contents of the i386 package are in the /usr/lib folder they go in /usr/lib32 on an amd64 system.

---

