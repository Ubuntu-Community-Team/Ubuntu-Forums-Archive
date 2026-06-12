---
title: "gtk2 needed for a make"
date: 2007-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmallery on 2007-05-24
hi

while installing a tarball (an eBay sniping program) i get the following:

lab64:~/bidwatcher-1.3.17> ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for glib-config... no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find Gtk+
lab64:~/bidwatcher-1.3.17> 


so what do i have to install to get the gtk2 development enfironment??

many thanks in advance

dave mallery  (amd64, ubuntu 4.10)

---

### Post by gbesso on 2007-05-24
```

sudo apt-get install libgtk2.0-dev libglib2.0-dev
```

---

### Post by dmallery on 2007-05-25
hi

lab64:~>> apt-get install libgtk2.0-dev libglib2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
libgtk2.0-dev set to manual installed.
libglib2.0-dev is already the newest version.
libglib2.0-dev set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

so that's not the problem as the ./configure still gives the same complaint about gtk2:

checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find Gtk+

stuck in new mexico

dave

---

