---
title: "32 bit in 64 bit ubuntu?"
date: 2005-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by techn9ne on 2005-03-26
If you install ubuntu on a 64 bit system like amd64 or xeon64 can you run 32 bit software at all in emulation mode or does it have to be compiled for 64 bit ubuntu?

---

### Post by wmcbrine on 2005-03-26
You can run almost everything, transparently. The only hangup is libraries -- you can't link across the bit divide. Hence, for example, proprietary web plugins (implemented as libraries), distributed only as 32-bit object code, will not work; but you can get around that by using a 32-bit browser. Also, in Ubuntu, the 32-bit compatibility libraries are not as complete as the 64-bit libraries, so that limits what you can run, unless you supplement them. And finally, DOSEmu will apparently not run, because virtual x86 mode is not supported in the 64-bit Linux kernel.

---

### Post by HiddenWolf on 2005-03-26
So I take it java and flash in firefox won't work?

Anything else? codecs? Skype?

What is the real advantage in 64b over 32? Speed?

---

### Post by Pse on 2005-03-27
Well, supposedly. By using the 64-bit extensions provided by the CPU, you get access to a new set of registers... Some benchmarks get up to 20% speed increases, others, none... Generally, you'll not be able to notice the difference...

---

### Post by wmcbrine on 2005-03-27
Speed, and access to larger amounts of memory -- but that part won't really come into play for most people just yet.

The speed increase is real, but it varies with the application. It's even possible (though very rare) for a particular application to slow down when compiled for 64-bit, if it has to move more data (8-byte pointers and longs vs. 4-byte).* But some apps can speed up dramatically, even threefold or more. (I've seen this particular number in connection with ssh, not sure of the implementation.)

In my case, I've done no formal benchmarks, but the system feels much snappier than 32-bit Mandrake on the same hardware. However, that probably has at least as much to do with my Mandrake being an outdated distro as with the switch to 64-bit mode. I haven't quite compared like with like (32-bit vs. 64-bit Ubuntu Hoary, say).

* Of course, in the rare case that you do find an app that degrades in 64-bit, you can just recompile it for 32-bit, and still run it at full speed in your 64-bit distro. :)

---

### Post by mthaddon on 2005-03-27
Is there any reason that I haven't been able to compile RealPlayer? From the sounds of it this should work fine, but I get the following:

mthaddon@ubuntu:~$ realplay

(realplay.bin:9413): Gdk-WARNING **: locale not supported by Xlib

(realplay.bin:9413): Gdk-WARNING **: can not set locale modifiers

(realplay.bin:9413): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:9413): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:9413): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(realplay.bin:9413): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(realplay.bin:9413): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory

(realplay.bin:9413): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: cannot open shared object file: No such file or directory
Failed to load pixbuf file: /usr/local/RealPlayer/share/realplay/icon.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

(realplay.bin:9413): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:9413): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:9413): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:9413): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:9413): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:9413): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

** (realplay.bin:9413): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9413): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9413): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9413): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9413): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:9413): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (realplay.bin:9413): CRITICAL **: file pango-engine.c: line 68 (_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed

** ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/usr/bin/realplay: line 75:  9413 Aborted                 $REALPLAYBIN "$@"

---

### Post by raid517 on 2005-04-11
Sorry to butt in on the thread - but I installed the 64Bit version of Ubuntu last night. But I can't find a win32 codec package for it. Where can I get this or do I somehow have to use the 32Bit codecs? If so is there anything special I need to know about installing them? (E.G do I have to do any kind of forcing?)

GJ

---

### Post by raid517 on 2005-04-11
Also I notice here that someone said that it is possible to run a 32Bit browser on a 64Bit platform? How exactly do I do this? The Firefox installer isn't working for me.

GJ

---

### Post by mips on 2005-04-11
> Also I notice here that someone said that it is possible to run a 32Bit browser on a 64Bit platform? How exactly do I do this? The Firefox installer isn't working for me.

GJ 

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

