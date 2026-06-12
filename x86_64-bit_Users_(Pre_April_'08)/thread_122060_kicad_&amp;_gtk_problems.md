---
title: "kicad &amp; gtk problems"
date: 2006-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Buenaventura Durruti on 2006-01-26
Hello,

I've installed a binary distribution of kicad but I've problems. I've created the following startup script:

```

#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
linux32 /usr/local/kicad/linux/kicad

```

But even when GTK_PATH is set to /usr/lib32/... kicad icons and pixmap buttons are not showed and it shows following error repeated when running it:


> (kicad:8362): GdkPixbuf-WARNING **: Error loading XPM image loader: No es posible cargar el módulo de carga de imágenes: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: no se puede abrir el fichero del objeto compartido: No existe el fichero o el directorio

Error messages are in spanish, but I think that's not relevant, the point is that its trying to use /usr/**lib**/gtk-2.0... instead of /usr/**lib32**/gtk-2.0... and I think this may be the cause of the problem so... does anybody knows how to solve this?

TIA

---

### Post by Buenaventura Durruti on 2006-01-26
Ok, I've got it. I've added this line to the startup script:

export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders32

I've also done this to create gdk-pixbuf.loaders32 from gdk-pixbuf.loaders:

$ cat /etc/gtk-2.0/gdk-pixbuf.loaders | sed 's/\/usr\/lib/\/usr\/lib32/g' > /etc/gtk-2.0/gdk-pixbuf.loaders32

And by the way I've done the same for gtk.inmodules getting a gtk.inmodules32. I do not know if this is really neccesary.

My inspiration comes from [this post]("http://ubuntuforums.org/showthread.php?t=119971&highlight=linux32+gtk") so many thanks to awi.

---

