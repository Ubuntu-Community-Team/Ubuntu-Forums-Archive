---
title: "Skype hates me"
date: 2009-03-11
forum: x86 64-bit Users
---

### Post by rdingram on 2009-03-11
So after trying every tutorial on Skype and 64bit I have really messed it up some how. This is what I get when trying to run from the shell..

```

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Fatal: Cannot mix incompatible Qt libraries
Aborted (core dumped)

```

Any ideas?

Thanks for any help and if this is somewhere else and I missed it I apologize in advance.

---

### Post by marcelkoopman on 2009-03-11
Did you install skype from the medibuntu repositories?
If not remove skype and skype-common and reinstall.

See [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by rdingram on 2009-03-11
Installed skype-static amd64 from medibuntu and it solved my qt problems.

---

### Post by unarmedninja on 2009-03-15
thank you! skype-static fixed this problem for me too. fyi running jaunty 64bit.

---

