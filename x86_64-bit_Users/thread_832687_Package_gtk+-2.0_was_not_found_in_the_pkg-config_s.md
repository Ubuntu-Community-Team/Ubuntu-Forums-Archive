---
title: "Package gtk+-2.0 was not found in the pkg-config search path."
date: 2008-06-17
forum: x86 64-bit Users
---

### Post by Bezi on 2008-06-17
I get the following when I use the ./configure command:

checking for glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Please help me with that.
thanks

---

### Post by Kilz on 2008-06-18
> **Bezi said:**
> I get the following when I use the ./configure command:

checking for glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Please help me with that.
thanks

Its telling you it cant find the package, do you have it installed?

---

### Post by b0n60 on 2008-09-27
haha ... i got the same error while installing airsnort Kilz please let these comments out... i searches for the package and gtk2 for 2 weeks and it made more and more depenencies. the search for gtk 2 or gtk2 gives at least 200 lines packages that isnt the way ...

[SIZE="2"]please help if you know what the package is needed[/SIZE]

---

### Post by XErMeSX on 2009-02-10
have you tried : sudo aptitude install libgtk2.0-dev ?

---

