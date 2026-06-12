---
title: "Eclipse on Kubuntu edgy 64"
date: 2007-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by tikal26 on 2007-01-08
I installed java and eclipse, but It won't start here is what i get
using specified vm: /usr/lib/jvm/java-1.5.0-sun/
kdialog: Unknown option '--warning'.
kdialog: Use --help to get a list of available command line options.

---

### Post by jlsheehan on 2007-01-19
> **tikal26 said:**
> I installed java and eclipse, but It won't start here is what i get
using specified vm: /usr/lib/jvm/java-1.5.0-sun/
kdialog: Unknown option '--warning'.
kdialog: Use --help to get a list of available command line options.


Hi,

I have just discovered the same problem.  It seems that the eclipse startup script is suffering because the arugments to kdialog are slightly different to whatever dialog program is used in Gnome/Ubunutu.

I modified the wrapper script slightly so that it would work, however you can avoid the problem completely by running /usr/lib/eclipse/eclipse instead of /usr/bin/eclipse.

Perhaps you could change the KDE menu to refer to /usr/lib/eclipse/eclipse instead of /usr/bin/eclipse or make /usr/bin/eclipse a symlink to /usr/lib/eclipse/eclipse.

I hope this make sense for you, I am going to submit a bug about this.

Jeff

---

