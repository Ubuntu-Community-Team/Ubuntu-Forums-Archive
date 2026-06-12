---
title: "ePSXe on Ubuntu 9.04 64-bit"
date: 2009-05-18
forum: x86 64-bit Users
---

### Post by jediken21 on 2009-05-18
Hey, I'm running 64-bit Ubuntu 64-bit and trying to get ePSXe to work. So far I've tried this guide [http://ubuntuforums.org/archive/index.php/t-571967.html](http://ubuntuforums.org/archive/index.php/t-571967.html) (it's a little old I think) and that didn't work. I'm a linux newb so any help would be...helpfull! :P

---

### Post by nicocarbone on 2009-06-20
Hi jediken21. Try this:
-Install getlibs (it shoulbe available through synaptics)
-In a terminal insert this command:
"getlibs libgtk-1.2.so.0 libglib-1.2.so.0" (without the quotes)
-Try running ePSXe.
Hope this helps.

P.S. You can also try with this emulator, is a .deb for amd64: [http://www.mediafire.com/file/n4wyknrdidt/psx32_1.13-5_ubuntu-amd64.deb]("http://www.mediafire.com/file/n4wyknrdidt/psx32_1.13-5_ubuntu-amd64.deb") You have to install a library too, you can do this with this command: "getlibs libgtkglext-x11-1.0.so.0"

---

### Post by crepito on 2009-06-22
You can get "getlibs" from here: [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)

---

### Post by warnec on 2009-06-22
have you seen that there's new version ? ;) Maybe they support 64bit now?

[http://www.epsxe.com/](http://www.epsxe.com/)

---

