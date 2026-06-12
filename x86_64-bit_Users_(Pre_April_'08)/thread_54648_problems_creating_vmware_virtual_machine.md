---
title: "problems creating vmware virtual machine"
date: 2005-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by pep100 on 2005-08-05
I have a dual boot ubuntu/winxp pro. I loaded vmware 5 in ubuntu Hoary. I tried to set up a virtual machine for winxp pro. When I was finished gurb would not load "error 21". Below is from the terminal:

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

---

### Post by freelsjd on 2005-09-07
Same problem here.  Did you ever get this fixed ?

---

### Post by mlomker on 2005-09-08
[QUOTE=freelsjd]Same problem here.  Did you ever get this fixed ?[/QUOTE]

I'm curious where you're seeing this error?  Are you saying that GDM is now failing to boot into gnome?  

I don't dual-boot and I run KDE, but I run VMWare workstation 5 on my machine.

Is this the first virtual machine that you've tried to create?

---

### Post by xodeus on 2005-09-09
Don't you miss some gtk libs?
Try to apt-cache search libgtk and install them all.
then try run vmware again.

---

