---
title: "MythTV compilation problems"
date: 2006-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by t0bb3 on 2006-01-03
Hi

I'm trying to compile MythTV from source, as I can't install it using apt-get.
I have downloaded mythtv_0.18.1-5.dsc, mythtv_0.18.1.orig.tar.gz and mythtv_0.18.1-5.diff.gz from here: [http://packages.ubuntu.com/breezy/graphics/mythtv](http://packages.ubuntu.com/breezy/graphics/mythtv)
I placed all three files in /opt/ and untared mythtv_0.18.1.orig.tar.gz so I ended up with a mythtv-0.18.1 directory. I then unpacked the diff file with ```
gunzip -d mythtv_0.18.1-5.diff.gz
```. After that I applied the patch by running ```
sudo patch -i mythtv_0.18.1-5.diff -p0
```
I went in to /opt/mythtv-0.18.1/debian and edited the "rules" file. All I changed was line 28 so it looked like this: > --cpu=x86_64 --tune=generic --enable-mmx \I then tried to run ```
sudo dpkg-buildpackage -rfakeroot -b
``` but that gave me a lot of unmet build dependencies. I resolved all of them, and also installed fakeroot.

Now when I run sudo dpkg-buildpackage -rfakeroot -b I get this message:> htpc@htpc:/opt/mythtv-0.18.1$ sudo dpkg-buildpackage -rfakeroot -b
dpkg-buildpackage: source package is mythtv
dpkg-buildpackage: source version is 0.18.1-5
dpkg-buildpackage: source changed by Matt Zimmerman <mdz@ubuntu.com>
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
/usr/bin/fakeroot: line 150: debian/rules: Permission denied

What did I do wrong?

EDIT:
I just had to run```
sudo chmod +x debian/rules
```

---

### Post by t0bb3 on 2006-01-03
so I ran```
sudo dpkg -i *.deb
```to install all the .deb files I got from the earlier steps.
This is what happend> Selecting previously deselected package libmyth-0.18.1.
(Reading database ... 92645 files and directories currently installed.)
Unpacking libmyth-0.18.1 (from libmyth-0.18.1_0.18.1-5_amd64.deb) ...
Selecting previously deselected package libmyth-0.18.1-dev.
Unpacking libmyth-0.18.1-dev (from libmyth-0.18.1-dev_0.18.1-5_amd64.deb) ...
Selecting previously deselected package mythtv.
Unpacking mythtv (from mythtv_0.18.1-5_all.deb) ...
Selecting previously deselected package mythtv-backend.
Unpacking mythtv-backend (from mythtv-backend_0.18.1-5_amd64.deb) ...
Selecting previously deselected package mythtv-common.
Unpacking mythtv-common (from mythtv-common_0.18.1-5_all.deb) ...
Selecting previously deselected package mythtv-database.
Unpacking mythtv-database (from mythtv-database_0.18.1-5_all.deb) ...
Selecting previously deselected package mythtv-debug.
Unpacking mythtv-debug (from mythtv-debug_0.18.1-5_amd64.deb) ...
Selecting previously deselected package mythtv-doc.
Unpacking mythtv-doc (from mythtv-doc_0.18.1-5_all.deb) ...
Selecting previously deselected package mythtv-frontend.
Unpacking mythtv-frontend (from mythtv-frontend_0.18.1-5_amd64.deb) ...
dpkg: dependency problems prevent configuration of libmyth-0.18.1:
 libmyth-0.18.1 depends on libqt3-mt-mysql | libqt3c102-mt-mysql; however:
  Package libqt3-mt-mysql is not installed.
  Package libqt3c102-mt-mysql is not installed.
dpkg: error processing libmyth-0.18.1 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmyth-0.18.1-dev:
 libmyth-0.18.1-dev depends on libmyth-0.18.1 (= 0.18.1-5); however:
  Package libmyth-0.18.1 is not configured yet.
dpkg: error processing libmyth-0.18.1-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on libmyth-0.18.1; however:
  Package libmyth-0.18.1 is not configured yet.
dpkg: error processing mythtv-backend (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-common:
 mythtv-common depends on pwgen; however:
  Package pwgen is not installed.
dpkg: error processing mythtv-common (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-database:
 mythtv-database depends on mythtv-common (= 0.18.1-5); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-database (--install):
 dependency problems - leaving unconfigured
Setting up mythtv-doc (0.18.1-5) ...
dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on mythtv-common (= 0.18.1-5); however:
  Package mythtv-common is not configured yet.
 mythtv-frontend depends on libmyth-0.18.1; however:
  Package libmyth-0.18.1 is not configured yet.
dpkg: error processing mythtv-frontend (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.18.1-5); however:
  Package mythtv-database is not configured yet.
 mythtv depends on mythtv-frontend (= 0.18.1-5); however:
  Package mythtv-frontend is not configured yet.
 mythtv depends on mythtv-backend (= 0.18.1-5); however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-debug:
 mythtv-debug depends on libmyth-0.18.1 (= 0.18.1-5) | mythtv-frontend (= 0.18.1-5) | mythtv-backend (= 0.18.1-5); however:
  Package libmyth-0.18.1 is not configured yet.
  Package mythtv-frontend is not configured yet.
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-debug (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmyth-0.18.1
 libmyth-0.18.1-dev
 mythtv-backend
 mythtv-common
 mythtv-database
 mythtv-frontend
 mythtv
 mythtv-debug
What is going on here?

EDIT:
Just had to install libqt3-mt-mysql and pwgen. After that I got in to the MythTV set up program :)

---

