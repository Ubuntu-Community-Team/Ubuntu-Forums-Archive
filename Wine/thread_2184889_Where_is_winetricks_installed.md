---
title: "Where is winetricks installed???"
date: 2013-10-31
forum: Wine
---

### Post by steve8 on 2013-10-31
hello i downloaded winetricks but its nowhere to be found anyone know where i can find it?

---

### Post by ian-weisser on 2013-10-31
To find out which files and where that a package installs:

```
$ dpkg -L winetricks
/.
/usr
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/winetricks.1.gz
/usr/share/doc
/usr/share/doc/winetricks
/usr/share/doc/winetricks/README.Debian
/usr/share/doc/winetricks/changelog.Debian.gz
/usr/share/doc/winetricks/copyright
/usr/share/winetricks
/usr/share/winetricks/applications
/usr/share/winetricks/applications/winetricks.desktop
/usr/share/winetricks/icons
/usr/share/winetricks/icons/hicolor
/usr/share/winetricks/icons/hicolor/scalable
/usr/share/winetricks/icons/hicolor/scalable/apps
/usr/share/winetricks/icons/hicolor/scalable/apps/winetricks.svg
/usr/bin
/usr/bin/winetricks

```

---

### Post by cramshaw227 on 2013-11-06
Files for applications are usually scattered all over linux but if you go to the home folder and press **Ctrl+h** it shows hidden files like **.wine** and **.cache** there is a **winetricks** in** .cache** which contains DLL's installed via winetricks.

---

