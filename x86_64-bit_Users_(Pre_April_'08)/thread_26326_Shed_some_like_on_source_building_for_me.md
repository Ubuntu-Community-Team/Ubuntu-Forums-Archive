---
title: "Shed some like on source building for me"
date: 2005-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by capriciousmind on 2005-04-12
Hi, I want to install firestarter on my ubuntu 64 system since it is the easiest I know of and I am a newb.  I looked on the firestarter website and they have a x86_64.rpm files but not a deb, etc, for ubuntu amd64.  Can I just compile from source and it will run in 64 bit or how does that work exactly?

---

### Post by az on 2005-04-12
It is in Universe.

[http://packages.ubuntu.com/hoary/admin/firestarter](http://packages.ubuntu.com/hoary/admin/firestarter)


But to answer your question, yes, if you have the source for an application that has not been packaged, you should be able to compile it for yourself.

Typically, you download the source tarball

tar xvzf <package>`.tar.gz
cd package*
/.configure
make
make install

You should read the Readme to know what the app needs to compile properl;y (development packages, like xlibs-dev....)

---

### Post by Klin'Targ on 2005-04-12
Another way to get rpms installed is to use alien to turn .rpms into .debs. Beware however that alien will remove all dependancy info, so for anything complex or depended upon by other packages, it is safer to build from source.

---

### Post by capriciousmind on 2005-04-12
Thanks for the fast response.  It have to admit the Hoary 64 install has been a challenge but I am really having a lot of fun and expect to see great results.

---

