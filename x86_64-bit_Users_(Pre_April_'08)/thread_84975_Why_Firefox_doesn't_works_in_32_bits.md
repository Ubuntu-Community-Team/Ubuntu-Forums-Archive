---
title: "Why Firefox doesn't works in 32 bits ?"
date: 2005-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by tux61 on 2005-11-01
Hi,

Because of flash and realplayer I want to install firefox 32 bits (I know it's possible because previously I used Gentoo).
But when I want to install, I encountered messages :
```
./firefox-installer

(firefox-installer-bin:19746): Gdk-WARNING **: locale not supported by Xlib

(firefox-installer-bin:19746): Gdk-WARNING **: cannot set locale modifiers

(firefox-installer-bin:19746): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-installer-bin:19746): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-installer-bin:19746): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object fi le: No such file or directory

(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object f ile: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:19746): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
./firefox-installer: line 56: 19746 Aborted                 ./${BINNAME}-bin $@

```

Any idea ?
Thanks

---

### Post by tux61 on 2005-11-01
I respond myself because I just found a solution :
```
export GTK_PATH=/usr/lib32/gtk-2.0/
export PANGO_RC_FILE=/etc/pango32/pangorc
firefox
``` 

With the 32 bits version I can use flash, realplayer 10 and java. :p

---

