---
title: "Komodo Problems (Perl, PHP etc Editor)"
date: 2005-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by 76thParadox on 2005-05-15
When trying to run Komodo (an IDE for opensource languages like Perl, PHP and Python) from ActiveState ([http://www.activestate.com](http://www.activestate.com)) I am finding that it crashes and ceases execution immediatly after start up.  It draws the main application GUI on the screen for a split second then disappears and ends execution.  I am including the verbose output from the execution of Komodo below and would appreciate any guidance as to how I might fix the problem.  It appears to run correctly on my 32 bit installation of Hoary, hence the post being in this forum.

 ---

bjl@hephaistos:~$ /opt/Komodo-3.1/komodo -v
/opt/Komodo-3.1/komodo: commandments FIFO name:
'/home/bjl/.komodo/3.1/host-hephaistos/commandments.fifo'
/opt/Komodo-3.1/komodo: starting lock name:
'/home/bjl/.komodo/3.1/host-hephaistos/starting.lock'
/opt/Komodo-3.1/komodo: running lock name:
'/home/bjl/.komodo/3.1/host-hephaistos/running.lock'
/opt/Komodo-3.1/komodo: Starting Komodo.
/opt/Komodo-3.1/komodo: Writing startup environment to
'/home/bjl/.komodo/3.1/host-hephaistos/startup-env.tmp'.
/opt/Komodo-3.1/komodo: setting KOMODO_INSTALLDIR=/opt/Komodo-3.1
/opt/Komodo-3.1/komodo: setting KOMODO_HOSTNAME=hephaistos
/opt/Komodo-3.1/komodo: setting
PATH=/opt/Komodo-3.1/Mozilla:/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
/opt/Komodo-3.1/komodo: setting
PATH=/opt/Komodo-3.1/python/bin:/opt/Komodo-3.1/Mozilla:/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
/opt/Komodo-3.1/komodo: setting PYTHONHOME=/opt/Komodo-3.1/python
/opt/Komodo-3.1/komodo: setting
PYTHONPATH=/opt/Komodo-3.1/Mozilla/python:/opt/Komodo-3.1/python/lib/python2.3/site-packages
/opt/Komodo-3.1/komodo: Waiting for Komodo to startup.

(komodo-bin:9580): Gdk-WARNING **: locale not supported by Xlib

(komodo-bin:9580): Gdk-WARNING **: can not set locale modifiers

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gtk-WARNING
**: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared
object file: No such file or directory

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported
WARN:koInitService:cannot reset LOCALE set to en_AU.UTF-8 : _locale
emulation only supports "C" locale

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported
bjl@hephaistos:~$
(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

(komodo-bin:9580): Gdk-WARNING **: Error converting from UTF-8 to
STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not
supported

** (komodo-bin:9580): WARNING
**: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared
object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (komodo-bin:9580): WARNING
**: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared
object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (komodo-bin:9580): WARNING
**: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared
object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (komodo-bin:9580): WARNING
**: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared
object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (komodo-bin:9580): WARNING
**: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared
object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (komodo-bin:9580): WARNING
**: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared
object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (komodo-bin:9580): WARNING
**: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared
object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (komodo-bin:9580): WARNING
**: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared
object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (komodo-bin:9580): WARNING
**: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared
object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (komodo-bin:9580): WARNING
**: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared
object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (komodo-bin:9580): WARNING
**: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared
object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(komodo-bin:9580): GLib-GObject-CRITICAL **: file gobject.c: line 1561
(g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (komodo-bin:9580): CRITICAL **: file pango-engine.c: line 68
(_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed

** ERROR **: file shape.c: line 75 (pango_shape): assertion failed:
(glyphs->num_glyphs > 0)
aborting...
/opt/Komodo-3.1/Mozilla/run-komodo.sh: line 159:  9580 Aborted
"$prog" ${1+"$@"}

---

### Post by 76thParadox on 2005-05-25
Here's a response I received from the good people at ActiveState.  This might be of interest to others:

----------

Hi Bernard,

I've looked into the Ubuntu / AMD 64 issue a bit more closely, and discovered
 the cause of the problem and a workaround. I have updated the bug here:

[http://bugs.activestate.com/show_bug.cgi?id=38886](http://bugs.activestate.com/show_bug.cgi?id=38886)

Basically, try symlinking pango-basic-fc.so to where pango is looking for it:

sudo ln -sf /usr/lib32/pango/1.4.0/modules/pango-basic-fc.so
/usr/lib/pango/1.4.0/modules/pango-basic-fc.so

Let me know if you have any further questions or comments.

best regards,

Jeff Griffiths
Technical Support Engineer
ActiveState - Dynamic Tools for Dynamic Languages
[http://www.ActiveState.com](http://www.ActiveState.com)

---

