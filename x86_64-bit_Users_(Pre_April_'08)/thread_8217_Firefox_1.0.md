---
title: "Firefox 1.0"
date: 2004-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by tranceConscious on 2004-12-15
When I try to install firefox 1.0 i get this:

root@ubuntu:/home/billy # ls
Desktop  firefox-1.0.installer.tar.gz  firefox-installer  wired-0.11.tar.gz
root@ubuntu:/home/billy # cd firefox-installer/
root@ubuntu:/home/billy/firefox-installer # ls
config.ini         firefox-installer-bin  install.ini  watermark.png
firefox-installer  header.png             license.txt  xpi
root@ubuntu:/home/billy/firefox-installer # sh firefox-installer
./firefox-installer-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory


?????

---

### Post by zAo on 2004-12-15
Did you install:
libgtk2.0-dev - Development files for the GTK+ library

---

### Post by tranceConscious on 2004-12-15
Yes I did, but still the same error.

(Do I have to restart afte installing these libraries? I don't think so)

---

### Post by jdong on 2004-12-15
Running 32-bit firefox binaries requires 32-bit GTK libraries. Does ubuntu have emulation libs for GTK+?

---

### Post by Averatec5400 on 2004-12-15
I have not used the 64bit Ubuntu, but on Suse I could type linux32 appname and execute it at 32bit, can you do it with ubuntu, it is worth a try anyway.

---

### Post by eClaire on 2004-12-27
I have the same error and no solution...

---

