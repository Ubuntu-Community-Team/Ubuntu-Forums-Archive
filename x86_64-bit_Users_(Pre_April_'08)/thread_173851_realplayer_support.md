---
title: "realplayer support"
date: 2006-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by jamesrw on 2006-05-11
anyone got realplayer working on amd64 breezy? 

stuck here:

> [SIZE="1"](realplay.bin:7445): Gdk-WARNING **: locale not supported by Xlib

(realplay.bin:7445): Gdk-WARNING **: cannot set locale modifiers

(realplay.bin:7445): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:7445): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:7445): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory
Failed to load pixbuf file: /usr/bin/RealPlayer/share/realplay/icon.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

(realplay.bin:7445): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:7445): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:7445): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:7445): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/usr/bin/realplay: line 75:  7445 Aborted                 $REALPLAYBIN "$@"[/SIZE]

---

### Post by dud on 2006-05-11
I haven't got much interest in Real Player myself, but perhaps you can get their Helix Player to work?
[https://common.helixcommunity.org/2004/downloads/](https://common.helixcommunity.org/2004/downloads/)
It seems pretty much dead in the water since 2004, but at least it has source code...

---

### Post by John Jason Jordan on 2006-05-11
[QUOTE=jamesrw]anyone got realplayer working on amd64 breezy? stuck here:[/QUOTE]
I had the same issues. I futzed around for days with it and finally gave up. From everything I read it seemed that the simplest thing to do was to install a 32-bit chroot environment. I did that (pretty easy, even for a Linux n00bie like me). Then I installed 32-bit Firefox in it and also RealPlayer. Both work fine now. And I also used the chroot environment for Adobe Reader 7.0, which I could never get installed either. All are working fine, except that I haven't been able to get Firefox to call Adobe Reader. But that's OK, because Firefox can't figure out how to print to my PostScript printer anyway. (Don't get me started.)

---

### Post by crwban on 2006-05-12
[QUOTE=jamesrw]anyone got realplayer working on amd64 breezy?[/QUOTE]
Yes, it can be set up to work perfectly...

The information for this comes from [https://wiki.ubuntu.com/FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava"), [http://www.ubuntuforums.org/showthread.php?t=128757]("http://www.ubuntuforums.org/showthread.php?t=128757") and [http://www.ubuntuforums.org/showthread.php?t=167526]("http://www.ubuntuforums.org/showthread.php?t=167526").

First, you need to install some packages:
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32
```
I assume that you have already installed realplayer, so we can skip that step...

Next, we need to edit a pango configuration file - open a terminal, and type:
```
sudo gedit /etc/pango32/pangorc
```
and we need to add the following lines to the *end* of the file:
```
[Pango]
ModuleFiles=/etc/pango32/pango.modules
[PangoX]
AliasFiles=/etc/pango/pangox.aliases
```

We need to modify another file as well - open *another* terminal, and in this terminal type:
```
sudo -i
cp /etc/gtk-2.0/gdk-pixbuf.loaders /etc/gtk-2.0/gdk-pixbuf.loaders.32
sed 's:/usr/lib/:/usr/lib32/:' < /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders.32
```
Now, close the terminal that you just opened, and go back to the other terminal.

Now... we create another file:
```
sudo gedit /usr/local/bin/realplay32
```
and we put the following lines into it:
```
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32
linux32 /usr/local/RealPlay/realplay $@
```
if you installed RealPlay somewhere other than "/usr/local/RealPlay", you must replace the last line to point to wherever you installed it.

Then, we make this file executable:
```
sudo chmod +x /usr/local/bin/realplay32
```
Now, we test if it is working...
```
realplay32
```
If that all worked ok, you should be able to run realplayer whenever you want by typing 'realplay32'.

---

