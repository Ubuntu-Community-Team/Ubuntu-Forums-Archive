---
title: "32-Bit Applications &amp; Feisty Fawn?"
date: 2007-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Crypto-138 on 2007-04-22
While I was upgrading to Feisty, the updater froze and I had to finish installing packages with
```
sudo dpkg --configure -a
```

For some reason a lot of packages became "unused". And I kept getting errors about ia32-openoffice.org or something.

I figured the package was unused, and uninstalled it as I installed the rest of the ia32 libraries. But for some reason, some applications don't work without prepending linux32 to them in the console.

Wine and Firefox32 work, but Realplayer requires linux32, and Acroread won't work even with Linux32.

I probably broke something, and I have no idea how to fix it.

Does anyone know of a solution to my problem?

Here's what I get when use realplay:```
$ realplay

(realplay.bin:10659): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory

** ERROR **: file accessible.c: line 550 (spi_accessible_construct): assertion failed: (o)
aborting...
Aborted (core dumped)

```

I get this when using Linux32 to bypass the "gail" error:
```
(acroread:10738): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so: wrong ELF class: ELFCLASS64

```

---

### Post by Kilz on 2007-04-22
> **Crypto-138 said:**
> While I was upgrading to Feisty, the updater froze and I had to finish installing packages with
```
sudo dpkg --configure -a
```

For some reason a lot of packages became "unused". And I kept getting errors about ia32-openoffice.org or something.

I figured the package was unused, and uninstalled it as I installed the rest of the ia32 libraries. But for some reason, some applications don't work without prepending linux32 to them in the console.

Wine and Firefox32 work, but Realplayer requires linux32, and Acroread won't work even with Linux32.

I probably broke something, and I have no idea how to fix it.

Does anyone know of a solution to my problem?

A clean install, that or reinstall all the ia32 libs and linux32.

---

### Post by Crypto-138 on 2007-04-22
the ia32 libs are installed, but I think I'm missing one. It was the openoffice one, I think.

Everything else works perfectly, and I'd hate to have to download the dvd all over again. (I only have a dapper dvd)

Can someone find out about that particular package?
It doesn't appear in synaptic anymroe.

This is what I get when I use realplay.

```
$ realplay

(realplay.bin:10659): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory

** ERROR **: file accessible.c: line 550 (spi_accessible_construct): assertion failed: (o)
aborting...
Aborted (core dumped)

```

---

### Post by kleeman on 2007-06-11
It's

ia32-libs-openoffice.org

and it was in edgy but not feisty. Why it was pulled beats me....

---

