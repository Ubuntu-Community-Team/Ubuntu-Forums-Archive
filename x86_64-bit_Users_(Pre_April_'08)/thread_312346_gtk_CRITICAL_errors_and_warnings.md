---
title: "gtk CRITICAL errors and warnings"
date: 2006-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by arminbw on 2006-12-04
I am using Dapper Drake, 6.06, 64 bit.

Sometimes firefox needs ages to start up. Sometimes not. No problems with Konqueror.
When I am starting firefox from the console I get a huge list of errors like those:
> Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `gdk_window_is_viewable (src)' failed
...
GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


I gave swiftfox a chance, using 32bit libs, **which works fine**. Starting from the console i get those errors:

> Gtk-WARNING **: Unable to locate theme engine in module_path: "qtengine",

Gtk-WARNING **: Unable to locate theme engine in module_path: "qtengine",
GConf Error: Failed to launch configuration server: Failed to execute child process "/usr/lib/libgconf2-4/gconfd-2" (No such file or directory)

Any ideas, where this gtk-troubles come from?

Thanx,
 Armin

---

### Post by kuja on 2006-12-04
I do believe that is saying that the GTK-QT engine is not installed, and it probably isn't, seeing as you need the 32-bit GTK-QT engine, and you likely have only the 64-bit one installed. I never resolved that, but perhaps you should try firefox32 ... I lost the link, but I do recall it is in the user Kilz's signature.

---

