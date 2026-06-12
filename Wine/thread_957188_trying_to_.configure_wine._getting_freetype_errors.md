---
title: "trying to ./configure wine. getting freetype errors..."
date: 2008-10-24
forum: Wine
---

### Post by gsrcrxsi on 2008-10-24
so im trying to install wine 1.1.2 from the source. 

running ./configure, i get this:

```

configure: error: FreeType development files not found.
Fonts will not be built. Dialog text may be invisible or unaligned.
Use the --without-freetype option if you really want this.

```

now i have libfreetype6-dev installed. im really at a loss here. i did this EXACT compile/make/install on this EXACT system with this EXACT same OS (mythbuntu_x64). 

yes, i have ia32-libs installed.

any ideas? google turned up nothing relevant.

---

### Post by sonofusion82 on 2008-10-24
unless you want to apply specific patches to wine and build from source yourself, how about installing wine deb packages from [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")?

anyway, this seem to be a link that might help u. [http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit")

---

### Post by gsrcrxsi on 2008-10-24
i want to build from source myself. and i already have build-dep wine done.

i just dont understand why it says it cant find the dev files when they are installed. secondly i dont understand why im having this issue at all, it didnt happen before.

---

### Post by gsrcrxsi on 2008-10-25
anyone?

---

### Post by Kazuki on 2008-10-25
This seams to clear up most of the errors for me, the 32bit libs need to be linked from .so.6 to .so, still got some errors about cups libhal and another one. I will get back to after the make and make install to let you know if this works(as in I can run games/programs in wine.)

you can copy and paste in a terminal

```

sudo ln -s /usr/lib32/libX11.so.6 /usr/lib32/libX11.so
sudo ln -s /usr/lib32/libXext.so.6 /usr/lib32/libXext.so
sudo ln -s /usr/lib32/libfreetype.so.6 /usr/lib32/libfreetype.so
sudo ln -s /usr/lib32/libfontconfig.so.1 /usr/lib32/libfontconfig.so
sudo ln -s /usr/lib32/libGL.so.1 /usr/lib32/libGL.so
sudo ln -s /usr/lib32/libGLU.so.1 /usr/lib32/libGLU.so
sudo ln -s /usr/lib32/libXrender.so.1 /usr/lib32/libXrender.so
sudo ln -s /usr/lib32/libXinerama.so.1 /usr/lib32/lib32/libXinerama.so
sudo ln -s /usr/lib32/libXxf86vm.so.1 /usr/lib32/libXxf86vm.so
sudo ln -s /usr/lib32/libXi.so.6 /usr/lib32/libXi.so
sudo ln -s /usr/lib32/libXrandr.so.2 /usr/lib32/libXrandr.so
sudo ln -s /usr/lib32/liblcms.so.1 /usr/lib32/liblcms.so
sudo ln -s /usr/lib32/libpng12.so.0 /usr/lib32/libpng.so
sudo ln -s /usr/lib32/libcrypto.so.0.9.8 /usr/lib32/libcrypto.so
sudo ln -s /usr/lib32/libssl.so.0.9.8 /usr/lib32/libssl.so
sudo ln -s /usr/lib32/libxml2.so.2 /usr/lib32/libxml2.so
sudo ln -s /usr/lib32/libjpeg.so.62 /usr/lib32/libjpeg.so
sudo ln -s /usr/lib32/libXcomposite.so.1 /usr/lib32/libXcomposite.so
sudo ln -s /usr/lib32/libcups.so.2 /usr/lib32/libcups.so
sudo ln -s /usr/lib32/libXcursor.so.1 /usr/lib32/libXcursor.so
sudo ln -s /usr/lib32/libdbus-1.so.3 /usr/lib32/libdbus-1.so
sudo ln -s /usr/lib32/libhal.so.1 /usr/lib32/libhal.so
sudo ln -s /usr/lib32/libsane.so.1 /usr/lib32/libsane.so
sudo ln -s /usr/lib32/libgphoto2.so.2 /usr/lib32/libgphoto2.so
sudo ln -s /usr/lib32/libgphoto2_port.so.0 /usr/lib32/libgphoto2_port.so
sudo ln -s /usr/lib32/libldap-2.4.so.2 /usr/lib32/libldap.so
sudo ln -s /usr/lib32/libldap_r-2.4.so.2 /usr/lib32/libldap_r.so
sudo ln -s /usr/lib32/liblber-2.4.so.2 /usr/lib32/liblber.so
sudo ln -s /usr/lib32/libxslt.so.1 /usr/lib32/libxslt.so
sudo ln -s /usr/lib32/libcapi20.so.3 /usr/lib32/libcapi20.so
sudo ln -s /usr/lib32/libjack.so.0 /usr/lib32/libjack.so
sudo ln -s /usr/lib32/libodbc.so.1 /usr/lib32/libodbc.so
sudo ln -s /usr/lib32/libgnutls.so.13 /usr/lib32/libgnutls.so


```

---

### Post by Kazuki on 2008-10-25
in eve-online still seems to be no text and scratchy audio, cant even login because of that.

---

