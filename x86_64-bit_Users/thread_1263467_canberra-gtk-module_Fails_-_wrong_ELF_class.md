---
title: "canberra-gtk-module Fails - wrong ELF class"
date: 2009-09-11
forum: x86 64-bit Users
---

### Post by beastrace91 on 2009-09-11
Alrighty, so the issue I am having is with running the Pandora One Adobe Air application. I get the following error message when I try to load it: ```
jeff@sager-lintop:~$ '/opt'/'Pandora'/bin/'Pandora'
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

```

The oddest thing is that it was working for a long while... I am not sure what exactly I installed/changed to cause it to break all of the sudden. I am open to suggestions on how to make it work again, I miss my Pandora One xD

~Jeff

---

### Post by Yellow Pasque on 2009-09-11
32-bit versions of Firefox often throw that error, but that doesn't stop them from working. Is your program really not working?
You could fix the error by getting 32-bit versions of the shared libraries the program is asking for using getlibs. Obtain/install getlibs from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
```
sudo getlibs /opt/Pandora/bin/Pandora
```

---

### Post by beastrace91 on 2009-09-11
It was indeed preventing the application from loading, how ever it appears rebooting resolved the issue... Odd

~Jeff

---

