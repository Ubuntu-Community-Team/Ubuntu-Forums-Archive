---
title: "Cedega 4.4 error with Breezy and AMD 64"
date: 2005-10-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by gmatt on 2005-10-06
hey i get the following error when trying to install a program through cedega:

useri@ubuntu:~$ Point2Play
/usr/lib/transgaming_point2play/Point2Play_gui.py:1576: GtkDeprecationWarning: gtk.timeout_add is deprecated, use gobject.timeout_add instead
  gtk.timeout_add( 1000, self.reap_children )
/usr/lib/transgaming_point2play/Point2Play_gui.py:1992: GtkDeprecationWarning: gtk.timeout_add is deprecated, use gobject.timeout_add instead
  gtk.timeout_add( 2000, self.monitor_cb )
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
Could not load graphics driver 'x11drv'
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
Could not load graphics driver 'x11drv'
Could not load graphics driver 'x11drv'
Could not load graphics driver 'x11drv'
Could not load graphics driver 'x11drv'
Could not load graphics driver 'x11drv'
Could not load graphics driver 'x11drv'
Could not load graphics driver 'x11drv'
Missing symbol {Error%dOpening%s}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {ContactTechSupport}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {Error%dOpening%s}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {ContactTechSupport}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {Error%dOpening%s}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {ContactTechSupport}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {Error%dOpening%s}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {ContactTechSupport}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {Error%dOpening%s}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {ContactTechSupport}! (SymbolTable::UnmappedSymbolSubstitution)
Could not load graphics driver 'x11drv'

I have no idea what that means but my nvidia card is setup properly.

---

### Post by Perfect Storm on 2005-10-06
You shouldbug report it so they can fix it before they release breezy.

---

### Post by gmatt on 2005-10-08
Not a bug, its just another one of those things in linux that takes time to figure out. After googling around some obscure forums ( that is how 99.99% of linux users figure things out I bet!) I read some person having a similar error. Someone had asked them if they had the XFree and Xorg dev packages installed. So I went and installed the xorg dev packages and VIOLA! it works it made me happy :D

Anyhow here is  a simple way to install the xorg dev packages in ubuntu (if you are reading this and use a different distro and have the same problem you gotta find out how to install xorg dev packages on your distro):

apt-get install xorg.*dev

the xorg.*dev is a regular expression that matches packages that contain the words xorg and dev in that order and installs them.

---

