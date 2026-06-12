---
title: "restricted drivers manager"
date: 2007-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Predrag on 2007-07-30
hi boys i have a little problem.i have tried to compile something.and than i wanted to go my restricted drivers manager but i cant.
console:
Traceback (most recent call last):
  File "/usr/bin/restricted-manager", line 45, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 43, in <module>
    "PyGTK requires PyGObject 2.11.1 or higher, but %s was found" % (ver,))
ImportError: PyGTK requires PyGObject 2.11.1 or higher, but () was found

can u help me please?

---

### Post by praxis22 on 2007-07-30
I'm in windows at present, but go into synaptic and see what you can find.

if you do a search you'll likely find the package you need: "pygobject" select it for installation then press apply and the try your command again.

---

### Post by Predrag on 2007-07-30
but i have the newies version of python gobject-dev 2.12.3 and it still doesn go.do u have some idea?

---

### Post by praxis22 on 2007-07-30
What are you trying to compile and how are you configuring it?

---

### Post by Predrag on 2007-07-30
i have tried to compiled gDesklets 0.34 and i need some other liberies.so i have download glib 2.8.6 and many other libaries
./configure
make 
sudo make install checkinstall
sudo chceckinstall

---

### Post by praxis22 on 2007-07-30
Why not just download it, I'm sure it'll be in apt-get somewhere, if not you can get a 64bit ubuntu version from 2005 here:

[http://dir.filewatcher.com/d/Ubuntu/amd64/gnome/gdesklets_0.34.3-0ubuntu2_amd64.deb.369690.html](http://dir.filewatcher.com/d/Ubuntu/amd64/gnome/gdesklets_0.34.3-0ubuntu2_amd64.deb.369690.html)

failing that try this:

apt-get install gdesklets

Which should install everything required along with it.

---

### Post by Predrag on 2007-07-31
thanks

---

