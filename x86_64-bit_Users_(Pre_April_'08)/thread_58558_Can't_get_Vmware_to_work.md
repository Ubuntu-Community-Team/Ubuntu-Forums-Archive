---
title: "Can't get Vmware to work"
date: 2005-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by pep100 on 2005-08-20
I have a dual boot ubuntu/winxp pro. I loaded vmware 5 in ubuntu Hoary on hdb. I set up a virtual machine for the EXISTING winxp pro on hda. When I was finished gurb would not load.

Loading Stabge 1.5... "error 21". Below is from the terminal:

(vmware:10062): Gdk-WARNING **: locale not supported by Xlib

(vmware:10062): Gdk-WARNING **: can not set locale modifiers

(vmware:10062): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10062): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10062): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory

(vmware:10062): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared object file: No such file or directory

(vmware:10074): Gdk-WARNING **: locale not supported by Xlib

(vmware:10074): Gdk-WARNING **: can not set locale modifiers

(vmware:10074): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10074): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10074): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory

(vmware:10074): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10074): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10074): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10074): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:10074): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:10074): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10074): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10074): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10074): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10074): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(vmware:10074): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

All suggestions appreciated.

---

### Post by Velox Letum on 2005-08-20
Not an expert here, but do you have the ISO-8859-1 charset enabled?

---

### Post by el_oscuro on 2008-02-06
I had a different problem in which my GUI desktop would not load, and this message along with other locale related messages appeared in the daemon.log.  When the desktop tried to load, there was a red X error dialog with unprintable characters and nothing worked.

Using diagnostics mode, I eventually found that the permissions in /usr had been deleted, so it was permission denied for everything.  No wonder nothing worked!.  I had installed Oracle SQL Developer and apparently the file extraction clobbered the permissions.

---

