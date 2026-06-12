---
title: "AMD64, Hoary and OpenOffice.org"
date: 2005-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by GeBo on 2005-03-13
For weeks now, I have been unable to use OpenOffice.org in a fully updated Hoary. OpenOffice.org starts, and then closes on its own. Starting oowriter from the command line, I get the following message:

(soffice.bin.real:27720): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

sh: error while loading shared libraries: /usr/lib32/libpangohack.so.0.0: cannot open shared object file: No such file or directory

(soffice.bin.real:27720): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared object file: No such file or directory

(soffice.bin.real:27720): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (soffice.bin.real:27720): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'

(soffice.bin.real:27720): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (soffice.bin.real:27720): CRITICAL **: file pango-engine.c: line 68 (_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed

** ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
sh: error while loading shared libraries: /usr/lib32/libpangohack.so.0.0: cannot open shared object file: No such file or directory

(process:27720): Gdk-WARNING (recursed) **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported
aborting...


Fatal exception: Signal 6


I've search continually on this Ubuntu forum and I've googled a lot, but till today, no solution... It seems like I am the only one with this problem...   

What concerns the output:
- The files that seems to be missing (pango-basic-fc.so and libpangohack.so.0.0), are both available in the appropriate path.


Can anyone give me a hint?

Thanks in advance!
Gert

---

### Post by ggt on 2005-05-27
I am kind of experiencing a similar problem. Openoffice itself is OK, I am able to open and edit documents etc, but it's when I go to print I get the

sh: error while loading shared libraries: /usr/lib32/libpangohack.so.0.0: cannot open shared object file: No such file or directory

error. I can print to file OK and then manually do "lp filename" to get the file printed.

Possibly a related problem is the oopadmin crashes if I try to reconfigure the printer setting through the GUI.

This is on an AMD64 that was installed as Ubuntu Warty the upgraded to Hoary.

---

### Post by equivsys on 2005-09-11
-GeBo

Did you every find a fix for this.  I have just installed Horay on a new amd64 and I am running into the same problem.  It all works find on my 32bit machine and I am just having no luck fixing this.

---

### Post by Beamerboy on 2006-06-29
[QUOTE=equivsys]-GeBo

Did you every find a fix for this.  I have just installed Horay on a new amd64 and I am running into the same problem.  It all works find on my 32bit machine and I am just having no luck fixing this.[/QUOTE]

Same problem here with OOo on 64bit Dapper although mine doesn't crash, it gives the following warning (over and over again):
```

(soffice.bin:29693): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

```

Everything seems to work once writer starts, however, the font in the Save As dialog is completely screwed, the entire dialog consists of nothing but squares.

Anyone managed to find a fix for these issues yet?

---

### Post by kuttan on 2006-07-13
[COLOR="Red"]Pango warning..Fixed!![/COLOR]:D 

Gimp and acroread used to crash on my laptop with error messages
GIMP:
gimp:6135): Pango-CRITICAL **: pango_cairo_show_glyph_string: assertion `PANGO_IS_CAIRO_FONT (font)' failed

(script-fu:6300): LibGimpBase-WARNING **: script-fu: wire_read(): error

For Acroread:

(acroread:5883): Pango-WARNING **: No builtin or dynamically
loaded modules were found. Pango will not work correctly.
This probably means there was an error in the creation of:
  '/usr/local/etc/pango/pango.modules'
You should create this file by running pango-querymodules.

(acroread:5883): Pango-WARNING **: pango_shape called with bad font, expect ugly output

(acroread:5883): Pango-WARNING **: pango_font_get_glyph_extents called with bad font, expect ugly output

(acroread:5883): Pango-CRITICAL **: pango_cairo_show_glyph_string: assertion `PANGO_IS_CAIRO_FONT (font)' failed

I don't know whether this is the right solution, but I copied /var/lib/pango/pango.modules to /usr/local/etc/pango/. It is working now!! Seems the pango.modules in /usr/local/etc/pango was corrupted, some how.
cheers
:D

---

