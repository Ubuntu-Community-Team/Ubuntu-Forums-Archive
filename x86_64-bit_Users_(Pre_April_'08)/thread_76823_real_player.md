---
title: "real player"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by gsaathoff on 2005-10-15
Has anyone had any success getting real player to work?  I try to use mplayer when I can, but for some internet streams I need real-player.

When I run the installer it says that everything went ok, but running the program gives me this:

~~

(realplay.bin:29167): Gdk-WARNING **: locale not supported by Xlib

(realplay.bin:29167): Gdk-WARNING **: cannot set locale modifiers

(realplay.bin:29167): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:29167): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:29167): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(realplay.bin:29167): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(realplay.bin:29167): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(realplay.bin:29167): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory
Failed to load pixbuf file: /home/graham/realplayer/share/realplay/icon.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

(realplay.bin:29167): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:29167): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:29167): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:29167): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/usr/bin/realplay: line 75: 29167 Aborted                 $REALPLAYBIN "$@"

~~

Any ideas?

Thanks,
-g

---

### Post by jamesrw on 2005-12-13
i get asimilar message:
```
(realplay.bin:26395): Gdk-WARNING **: locale not supported by Xlib

(realplay.bin:26395): Gdk-WARNING **: cannot set locale modifiers

(realplay.bin:26395): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:26395): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:26395): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory
Failed to load pixbuf file: /usr/bin/RealPlayer/share/realplay/icon.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

(realplay.bin:26395): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:26395): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:26395): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:26395): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/usr/bin/realplay: line 75: 26395 Aborted                 $REALPLAYBIN "$@"

```

---

### Post by RAOF on 2005-12-13
It looks like the same problem you have to solve to get firefox32 running.  Maybe you could try modifying [that howto]("http://www.ubuntuforums.org/showthread.php?t=90106&highlight=firefox+flash+chroot").

---

