---
title: "[SOLVED] Compiling Wine No X"
date: 2008-03-01
forum: Wine
---

### Post by Faud on 2008-03-01
Hello, I wanted to try and compile wine myself as a little challenge. After doing ./configure and adding what it said it need; it compiled and then said that it couldnt find my X server and that is probaly not what I want (lol no kidding). Is there something else that I need to install or does it make a difference what directory I complie wine from ?

---

### Post by mc4man on 2008-03-01
When i configured I used
```
./configure --with-x --prefix=/usr
```
worked fine

---

### Post by Faud on 2008-03-01
Thank you so much I'll try that when I get home.

---

### Post by mc4man on 2008-03-01
actually what I posted above is maybe irreverent - I just included it in my last build for curiosity sake - when i saw your post i thought there might be connection. You could try it anyway.
> it compiled I assumed your make was successful - I'm thinking now _maybe_ your missing some build depends.
A good place to look  _after _the configure is in config.h (it's in the include folder) There'll be a long list of items - look for ones that are undefined. Most that are undefined aren't needed, though you may see some that are needed or wanted
Since feisty I add  (after build-dep) 
```
sudo apt-get install libglib1.2 libglib1.2-dev libltdl3 libltdl3-dev libmad0-dev libxcomposite-dev libxv-dev render-dev x11proto-composite-dev x11proto-video-dev
```  maybe unnecessary but i always get good builds

---

### Post by Faud on 2008-03-02
Did what you suggested and Im still getting this as a response to ./configure
[/code]
configure: libxcursor development files not found, the Xcursor extension won't be supported.
configure: libxi development files not found, the Xinput extension won't be supported.
configure: libxxf86vm development files not found, XFree86 Vidmode won't be supported.
configure: libxrender development files not found, XRender won't be supported.
configure: libxrandr development files not found, XRandr won't be supported.
configure: libxinerama development files not found, multi-monitor setups won't be supported.
configure: libxml2 development files not found, XML won't be supported.
configure: libxslt development files not found, xslt won't be supported.
configure: libhal development files not found, no dynamic device support.
configure: lib(n)curses development files not found, curses won't be supported.
configure: libsane development files not found, scanners won't be supported.
configure: libgphoto2 development files not found, digital cameras won't be supported.
configure: liblcms development files not found, Color Management won't be supported.
configure: libldap (OpenLDAP) development files not found, LDAP won't be supported.
configure: libcapi20 development files not found, ISDN won't be supported.
configure: libcups development files not found, CUPS won't be supported.
configure: fontconfig development files not found, fontconfig won't be supported.
configure: OpenSSL development files not found, SSL won't be supported.
configure: libjpeg development files not found, JPEG won't be supported.
configure: libpng development files not found, PNG won't be supported.

configure: WARNING: OpenGL development headers not found.
OpenGL and Direct3D won't be supported.

configure: WARNING: FontForge is missing.
Fonts will not be built. Dialog text may be invisible or unaligned.

configure: Finished.  Do 'make depend && make' to compile Wine.
[/code]any ideas ?

---

### Post by Faud on 2008-03-02
The lib files Im assuming Im can do 
```
sudo apt-get install libxcursor-dev
```
but what do I do with the OpenSSL ?

---

### Post by happyhamster on 2008-03-02
You can get almost all dependencies by running:

sudo apt-get build-dep wine

Note that it helps if you have the wine repository loaded before running that command. If you don't have it yet, follow the instructions on this page: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
(Add key, add repo, run 'sudo apt-get update')

sudo apt-get build-dep wine

And perhaps this will help too (don't know if they will be pulled in automatically):

sudo apt-get install xserver-xorg-dev libxcomposite-dev gcc-4.2-multilib

---

### Post by Faud on 2008-03-04
Just wanted to say thanks guys Ive dont my first build of wine and its running great. Thank you all for the help

---

