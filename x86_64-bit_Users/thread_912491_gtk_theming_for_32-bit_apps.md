---
title: "gtk theming for 32-bit apps"
date: 2008-09-06
forum: x86 64-bit Users
---

### Post by Amranu on 2008-09-06
Installed Firefox 3.1 32-bit nightly build (in Debian Sid), however it does not register the gtk theme and instead has that wonderful blocky theme. 

The specific error is:
```
(firefox-bin:8003): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64
```

Any way to fix this?

---

### Post by Kilz on 2008-09-07
> **Amranu said:**
> Installed Firefox 3.1 32-bit nightly build (in Debian Sid), however it does not register the gtk theme and instead has that wonderful blocky theme. 

The specific error is:
```
(firefox-bin:8003): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64
```

Any way to fix this?

Yes if you want to do it manually. But it may take a lot of work.
Get the deb file that contains the gtk-2.0/2.10.0/engines/libmurrine.so files and all requirements. Right click on the deb file and choose extract here. Inside you will see data.tar.gz, right click on it and choose extract here. A small copy of the file tree will extract with the files it installs. copy the files in /usr/lib in that tree to /usr/lib32 in your system. Do this with all requirements.
Do not, under any circumstances, in any way shape or form force install a library.

---

