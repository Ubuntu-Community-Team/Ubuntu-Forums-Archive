---
title: "32 bit Firefox looking in wrong place for library on x64 system"
date: 2008-11-07
forum: x86 64-bit Users
---

### Post by jpeasy on 2008-11-07
When running 32 bit firefox I see: 

(firefox-bin:15609): Gtk-WARNING **: Error loading theme icon 'gtk-go-back-ltr' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

But I have the 32 bit version of the library installed: 

/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so

How do I get the dynamic linker to go to the right place? I thought it would do this automatically?

---

