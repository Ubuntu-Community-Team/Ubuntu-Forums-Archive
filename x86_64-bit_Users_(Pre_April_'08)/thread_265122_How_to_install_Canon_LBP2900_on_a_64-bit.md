---
title: "How to install Canon LBP2900 on a 64-bit ?"
date: 2006-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by ulefr01 on 2006-09-25
How to install Canon LBP2900 on a 64-bit ?

---

### Post by Kilz on 2006-09-25
> **ulefr01 said:**
> How to install Canon LBP2900 on a 64-bit ?

[https://wiki.ubuntu.com/Canon_LBP_2900_HowTo](https://wiki.ubuntu.com/Canon_LBP_2900_HowTo)

---

### Post by ulefr01 on 2006-09-26
I have tried it but i had problems with step 2 : the 'alien -c' , i get  :
sudo alien -c cndrvcups-capt-1.30-1.i386.rpm 
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/cndrvcups-capt
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find path for libcaepcm.so.1
dpkg-shlibdeps: warning: format of libcaiowrap.so not recognized
dpkg-shlibdeps: warning: format of libcaiowrap.so not recognized
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcncaptnpm.so.1
dpkg-shlibdeps: warning: could not find path for libgtk-1.2.so.0
dpkg-shlibdeps: warning: could not find path for libgdk-1.2.so.0
dpkg-shlibdeps: warning: could not find path for libgmodule-1.2.so.0
dpkg-shlibdeps: warning: could not find path for libglib-1.2.so.0
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find any packages for  (libcaepcm.so.1)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcaepcm (soname 1, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml2 (soname 2, path /usr/lib32/libxml2.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml2 (soname 2, path /usr/lib32/libxml2.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml2 (soname 2, path /usr/lib32/libxml2.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libz (soname 1, path /usr/lib32/libz.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml2 (soname 2, path /usr/lib32/libxml2.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libz (soname 1, path /usr/lib32/libz.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libgtk-1.2.so.0)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-1.2 (soname 0, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libgdk-1.2.so.0)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-1.2 (soname 0, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libgmodule-1.2.so.0)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-1.2 (soname 0, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libglib-1.2.so.0)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-1.2 (soname 0, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXi (soname 6, path /usr/lib32/libXi.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/lib32/libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml2 (soname 2, path /usr/lib32/libxml2.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libz (soname 1, path /usr/lib32/libz.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Fout 1
find: cndrvcups-capt-1.30: Onbekend bestand of map

---

### Post by Kilz on 2006-09-26
> **ulefr01 said:**
> I have tried it but i had problems with step 2 : the 'alien -c' , i get  :
sudo alien -c cndrvcups-capt-1.30-1.i386.rpm 
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/cndrvcups-capt
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find path for libcaepcm.so.1
dpkg-shlibdeps: warning: format of libcaiowrap.so not recognized
dpkg-shlibdeps: warning: format of libcaiowrap.so not recognized
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcncaptnpm.so.1
dpkg-shlibdeps: warning: could not find path for libgtk-1.2.so.0
dpkg-shlibdeps: warning: could not find path for libgdk-1.2.so.0
dpkg-shlibdeps: warning: could not find path for libgmodule-1.2.so.0
dpkg-shlibdeps: warning: could not find path for libglib-1.2.so.0
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find any packages for  (libcaepcm.so.1)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcaepcm (soname 1, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml2 (soname 2, path /usr/lib32/libxml2.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml2 (soname 2, path /usr/lib32/libxml2.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml2 (soname 2, path /usr/lib32/libxml2.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libz (soname 1, path /usr/lib32/libz.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml2 (soname 2, path /usr/lib32/libxml2.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libz (soname 1, path /usr/lib32/libz.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libgtk-1.2.so.0)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgtk-1.2 (soname 0, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libgdk-1.2.so.0)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgdk-1.2 (soname 0, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libgmodule-1.2.so.0)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgmodule-1.2 (soname 0, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libglib-1.2.so.0)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libglib-1.2 (soname 0, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXi (soname 6, path /usr/lib32/libXi.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/lib32/libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libxml2 (soname 2, path /usr/lib32/libxml2.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libz (soname 1, path /usr/lib32/libz.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path , dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Fout 1
find: cndrvcups-capt-1.30: Onbekend bestand of map

It looks like its 32bit dependant.

---

### Post by ulefr01 on 2006-09-26
can i use dchroot to apply this 32 bit driver ?

---

### Post by ulefr01 on 2006-09-28
can i use this printer as network printer ?

---

### Post by ulefr01 on 2006-10-02
problem is solved now.

do [https://wiki.ubuntu.com/Canon_LBP_2900_HpwTo](https://wiki.ubuntu.com/Canon_LBP_2900_HpwTo) under dchroot -d

---

