---
title: "Gtk-engines on an Ubuntu Edgy System"
date: 2006-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by pibarnas on 2006-10-31
Folks:

Did you try to install gtk-engines on an Ubuntu Edgy for adm64 system?!? I tried so many times, but I can't!!! Can you help me??

The most common error:

checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... configure: error: GTK+-2.8 is required to compile murrine
pibarnas@hal9000:~/MyDownloads/murrine-0.21$   :confused:

---

### Post by RAOF on 2006-10-31
You probably don't have libgtk2.0-dev installed.

---

### Post by sethx on 2006-11-16
i had the same problem and installing libgtk2.0-dev worked for me :)

---

