---
title: "[SOLVED] Remove 32-bit package from 64-bit system?"
date: 2007-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by sci-fi guy on 2007-11-02
How can I remove a package that I have previously installed with 'dpkg force-architecture -i'?

---

### Post by FG123 on 2007-11-02
sudo apt-get remove PACKAGE_NAME

Should be as simple as removing any other package, it's no different.

---

### Post by sci-fi guy on 2007-11-03
Not working. Maybe I'm typing something wrong?. The package in question is 'opera_9.24-20071015.6-shared-qt_en_i386.deb'

---

### Post by sethvath on 2007-11-03
Synaptic package manager, remove + purge

---

### Post by sci-fi guy on 2007-11-03
It does not appear in Synaptic. And where is the purge option, anyways?

---

### Post by rsambuca on 2007-11-03
If you downloaded and installed it, there should be an 'uninstall' file in the opera directory somewhere.

---

### Post by Cappy on 2007-11-03
The command is ```
sudo dpkg -r opera
```

---

### Post by sci-fi guy on 2007-11-04
Thanks!

---

