---
title: "Anyone got Realplayer/Helix player working"
date: 2004-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by yatesco on 2004-10-14
Hi all,

Anyone got realplayer or helixplayer working?  I keep getting errors about missing libs :(

I am really missing my bbc radio 2 :)

---

### Post by mcz on 2004-11-10
Yes.
I have also Suse 9.1 installed. So I copied the Suse directory /usr/lib/RealPlayer8 in the Ubuntu directory /usr/lib32.
And work.

mcz

---

### Post by jayclark on 2004-11-11
Mine did install flawlessly. It will throw out various errors if you don't install with sudo. Such as sudo ./realplayxxxx.bin. If thats not it check for the libs with apt-get or synaptic I found out sometimes the libs will be named different. So if you can't find them with apt-get try to search with synaptic with the base name of the lib.

---

### Post by Vlammend on 2004-11-16
I keep getting the following below mentioned message, when installing RealPlayer10, whether I install as Sudo or not, I installed everything I could find which was somehow connected to the mentioned library's. Although i could not find PangoX in the Ubuntu repositories.

What Can I do to install Realplayer 10?
How do I update the system library paths?
```

Some required libraries seem to be missing from your system.  Installation
can continue without them, but you will be unable to run the HelixPlayer
without them.  You will need to install them (or if they are already present
you may simply need to update your system's library paths or LD_LIBRARY_PATH
environment variable.
        GTK+ 2.0 (libgtk-x11-2.0.so)
        ATK 1.0 (libatk-1.0.so)
        Pango 1.0 (libpango-1.0.so)
        PangoX 1.0 (libpangox-1.0.so)
continue with installation? [y/n]: n
```

---

### Post by gratefulfrog on 2005-03-06
I'm running Hoary array-5 on AMD64 and was able to install the RealPlayer 10 Gold, but get the following errors on exectution:
Any ideas?

```

(realplay.bin:8072): Gdk-WARNING **: locale not supported by Xlib

(realplay.bin:8072): Gdk-WARNING **: can not set locale modifiers

(realplay.bin:8072): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:8072): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:8072): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(realplay.bin:8072): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(realplay.bin:8072): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(realplay.bin:8072): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(realplay.bin:8072): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(realplay.bin:8072): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory
Failed to load pixbuf file: /opt/RealPlayer/share/realplay/icon.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

(realplay.bin:8072): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:8072): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:8072): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:8072): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:8072): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:8072): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed
Failed to load pixbuf file: /opt/RealPlayer/share/realplay/icon.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

** (realplay.bin:8072): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8072): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8072): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8072): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8072): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8072): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8072): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8072): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8072): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8072): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8072): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:8072): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (realplay.bin:8072): CRITICAL **: file pango-engine.c: line 68 (_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed

** ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/usr/bin/realplay: line 75:  8072 Aborted                 $REALPLAYBIN "$@"

```

---

### Post by Jaro on 2005-03-09
I have recently installed Ubuntu Hoary on an AMD x86_64 machine and am having exactly the same problem as gratefulfrog, with the same error message.

Any help would be appreciated. [-o< 

Cheers
Jaro

P.s.  Nice OS otherwise though!  Its got me in a 'tug of war' with SUSE 9.2 at this very moment!

---

### Post by mthaddon on 2005-03-23
I'm in exactly the same boat. Any help appreciated.

Thanks, Tom

---

### Post by dmatrix on 2005-03-23
Same problem here. Only way I could figure out howto get RealPlayer10 running on AMD64 was with a 32bit chroot. I got it installed like some others did on AMD64, but ran into all the weird pango error messages.

[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

---

### Post by mathijs on 2005-12-03
Same here, is there any news on how to get this working?

---

### Post by Aphorism on 2006-03-05
Bump?

Anyone got helix to compile on amd64?  Need to get crappy real support on the amd64 box.

---

### Post by High Plains Drifter on 2006-03-16
> I had the same problem - the BBC have their own radio player, which needs Realplayer to be configured correctly. After installing Realplayer, you need to copy the files nphelix.so and nphelix.xpt from /usr/lib/mozilla/plugins to your .firefox and .mozilla plugins folders in /home/username/.firefox/plugins and /home/username/.mozilla/plugins.

Then you restart firefox and away you go!

ok

---

