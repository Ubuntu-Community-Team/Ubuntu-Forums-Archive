---
title: "xfce file"
date: 2006-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by kariopto on 2006-06-07
Hi.. I'm trying to compile a plugin for the xfce4-panel, and it says: 
```
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking for pango >= 1.8.0... yes
checking PANGO_CFLAGS... -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking PANGO_LIBS... -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for xfce4-panel-1.0 >= 4.0.0... Package xfce4-panel-1.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `xfce4-panel-1.0.pc' to the PKG_CONFIG_PATH environment variable No package 'xfce4-panel-1.0' found
configure: error: Library requirements (xfce4-panel-1.0 >= 4.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```
Apparently it needs the file xfce4-panel-1.0.pc, and I can't find it, I know its in xfce4-panel-dev on i386, but on AMD64, the package searcher doesn't find anything!.. does anybody have any ideas on how to compile this??
Thanks in advance!.

---

### Post by bonzodog on 2006-06-10
hrm..I have xfce4-panel-dev in my repo list. Search synaptic for 'xfce', and scroll through the list. You will see it.

---

