---
title: "gtk engine request"
date: 2007-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by komensky on 2007-10-22
does anyone have a deb of the aurora gtk2-engine for gutsy amd64?

---

### Post by wikiguy on 2007-10-24
Hey man, download this package and everything would work like charm.


cheers

---

### Post by komensky on 2007-10-25
gracias amigo ;)

---

### Post by wikiguy on 2007-10-31
No problem :guitar:.

---

### Post by Ravensky on 2007-11-06
Hey guys, I tried installing this and I get the message that libpango is an unsatisfied dependancy but Synaptic shows it is indeed installed...any ideas?

Thanks!

Raven

---

### Post by wikiguy on 2008-01-14
Well actually you must uninstall any aurora gtk engine , then intall aurora deb package,  if this doesnt work you can compile it yourself by doing in ubuntu:


$ sudo apt-get install build-essential checkinstall

then CD to the source dir :)

for example:

cd /home/user/aurorasource

ok we are almost done

$  ./configure --prefix=/usr -enable-animation
$  make

and finally

$ sudo checkinstall

this will build your deb package and install it.


By the way heres the new aurora1.4 deb for amd 64 .

cheers

---

### Post by wikiguy on 2008-01-14
here sorry.

---

### Post by fonsi2099 on 2008-01-23
amigos, I've got the following input, this was by installing googleearth.

(setup.gtk2:11897): Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory
any idea to fix that:confused:
many thanks:guitar:

---

