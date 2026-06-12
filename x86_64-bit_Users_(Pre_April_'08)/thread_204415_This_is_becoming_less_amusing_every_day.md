---
title: "This is becoming less amusing every day"
date: 2006-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Beamerboy on 2006-06-27
I have been having issues for about a week now and despite spending hours upon hours scouring the forums and googling for solutions, everything I try has failed to work.

**_First is the locale issue_**
Here is an example of the problem using ooffice -writer

First hereis the output from locale
```

paladine@main:~$ locale
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=
paladine@main:~$

```

Now the output from locale -a
```

paladine@main:~$ locale -a
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX
paladine@main:~$

```

Now for the warnings when I launch writer from a terminal using ooffice -writer
```

paladine@main:~$ ooffice -writer

(process:5776): Gdk-WARNING **: locale not supported by Xlib

(process:5776): Gdk-WARNING **: cannot set locale modifiers

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(soffice.bin:5776): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(soffice.bin:5776): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(soffice.bin:5776): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(soffice.bin:5776): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(soffice.bin:5776): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Pango-WARNING **: No builtin or dynamically
loaded modules were found. Pango will not work correctly.
This probably means there was an error in the creation of:
  '/etc/pango/pango.modules'
You should create this file by running pango-querymodules.

(soffice.bin:5776): Pango-WARNING **: pango_shape called with bad font, expect ugly output

(soffice.bin:5776): Pango-WARNING **: pango_font_get_glyph_extents called with bad font, expect ugly output

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(soffice.bin:5776): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported
paladine@main:~$

```

I believe the above issue is what is causing the following issue in all Open Office "Save As" dialogs (strangly no other dialogs are effected)

[img]http://www.paladine.org.uk/funky-saveas-dialog.jpg[/img]

**_Second problem is a TK issue_**

Another problem I am coming across a great deal is this:

```

paladine@main:~$ ./cxoffice/bin/cxinstallwizard
./cxoffice/bin/cxinstallwizard:error: error initializing Tk: 'this isn't a Tk applicationunknown color name "Black"'. Check the DISPLAY variable (:0.0) and your access permissions (see xauth or xhost).
paladine@main:~$

```

Again, the above issue is not just limited to "Crossover", I get this error a lot from lots of different apps, just using "Crossover" for illustrative purposes.

The issues described in this post are really starting to make my experience with Ubuntu less and less enjoyable, so if anyone can help, I would be very grateful.

BeamerBoy

---

### Post by Beamerboy on 2006-06-29
bump?

---

