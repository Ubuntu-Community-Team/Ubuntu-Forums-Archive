---
title: "MOL error on setup"
date: 2005-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by tmeier on 2005-11-10
I'm following the wiki article on how to setup MOL on my powerbook.  I get to the following command and get an error 

tmeier@Thomas-Meier-ubuntu:/usr/src/modules/mol$ sudo debian/rules build
dh_testdir
make: dh_testdir: Command not found
make: *** [build-stamp] Error 127

Was wondering if anybody had any ideas?  I followed the directions from the beginning in the wiki and no luck so far.  This would be cool to use if I can make it work.

---

### Post by ushooz on 2005-11-10
You need to add debhelper

apt-get install debhelper

---

### Post by tmeier on 2005-11-14
That helped but now am getting this ??????  


 sudo debian/rules build
dh_testdir
/usr/bin/make
make[1]: Entering directory `/usr/src/modules/mol'
/usr/bin/make -C src/kmod
make[2]: Entering directory `/usr/src/modules/mol/src/kmod'
+ Entering Linux

 --- Error: Unconfigured kernel source!
 --- (missing file: /include/linux/config.h)

make[3]: *** [kernelcheck] Error 1
make[2]: *** [sub-Linux-all] Error 2
make[2]: Leaving directory `/usr/src/modules/mol/src/kmod'
make[1]: [src/kmod] Error 2 (ignored)
/usr/bin/make -C src/netdriver
make[2]: Entering directory `/usr/src/modules/mol/src/netdriver'

 --- Error: Unconfigured kernel source!
 --- (missing file: /include/linux/config.h)

make[2]: *** [kernelcheck] Error 1
make[2]: Leaving directory `/usr/src/modules/mol/src/netdriver'
make[1]: [src/netdriver] Error 2 (ignored)
make[1]: Leaving directory `/usr/src/modules/mol'
touch build-stamp
tmeier@Thomas-Meier-ubuntu:/usr/src/modules/mol$ sudo debian/rules binary-mol-modules
dh_testdir
dh_testroot
dh_clean
dh_installdirs
/usr/bin/make DESTDIR=`pwd`/debian/mol-modules- install
make[1]: Entering directory `/usr/src/modules/mol'
install -d -m 755 -o 0 /usr/src/modules/mol/debian/mol-modules-/lib/modules/`uname -r`/misc
for file in `find mollib -type f`; do \
        install -m 644 -o 0 $file /usr/src/modules/mol/debian/mol-modules-/lib/modules/`uname -r`/misc; \
done
find: mollib: No such file or directory
make[1]: Leaving directory `/usr/src/modules/mol'
touch install-stamp
dh_testdir
dh_testroot
dh_installdocs
dh_installmodules
dh_installchangelogs
Use of uninitialized value in hash element at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 369.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
Use of uninitialized value in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
Use of uninitialized value in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
found eof where expected first heading at /usr/lib/dpkg/parsechangelog/debian line 136.
dh_installchangelogs: changelog parse failure
make: *** [binary-mol-modules] Error 1


Doesn't make a lot of sense to me, being new to Linux and all.  You guys are great with all your help.

---

### Post by ssam on 2005-11-14
have you installed build-essential ?

actually it looks more like a problem with the kernel source.

---

### Post by tmeier on 2005-11-14
Sam,  I agree I think it is a Kernel issue.  In checking my files I don't have a /usr/src/moduels/mol/src/kmod/include/linux/ config.h
I get to /usr/src/modules/mol/src/kmod/include  It has a ppc and an osx folder but not no linux folder at that location.  I started from scratch to see if I could make this work and this is where I got to so far.  I appreciate everyone's help with this.

---

### Post by tmeier on 2005-11-14
I got the first part to work.  I re-installed the linux-header files.  Now here is what I'm looking at in the next phase of the MOL how to

sudo debian/rules binary-mol-modules
dh_testdir
dh_testroot
dh_clean
dh_installdirs
/usr/bin/make DESTDIR=`pwd`/debian/mol-modules-2.6.12-9-powerpc install
make[1]: Entering directory `/usr/src/modules/mol'
install -d -m 755 -o 0 /usr/src/modules/mol/debian/mol-modules-2.6.12-9-powerpc/lib/modules/2.6.12-9-powerpc/misc
for file in `find mollib -type f`; do \
        install -m 644 -o 0 $file /usr/src/modules/mol/debian/mol-modules-2.6.12-9-powerpc/lib/modules/2.6.12-9-powerpc/misc; \
done
find: mollib: No such file or directory
make[1]: Leaving directory `/usr/src/modules/mol'
touch install-stamp
dh_testdir
dh_testroot
dh_installdocs
dh_installmodules
dh_installchangelogs
Use of uninitialized value in hash element at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 369.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
Use of uninitialized value in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
Use of uninitialized value in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
found eof where expected first heading at /usr/lib/dpkg/parsechangelog/debian line 136.
dh_installchangelogs: changelog parse failure
make: *** [binary-mol-modules] Error 1

What is my next step.

---

### Post by tmeier on 2005-11-15
Sorr folks.  I'm slow.  I did not get the first part to work correctly, it just had a lot of text, so I thought I did.  Anyway.  I have since removed MOL using synaptic package manager.  re-installed my linux-headers and started the process as if from scratch and following the directions from the HOWTO.  I get back to basically the same point of :

 sudo debian/rules build
dh_testdir
/usr/bin/make
make[1]: Entering directory `/usr/src/modules/mol'
/usr/bin/make -C src/kmod
make[2]: Entering directory `/usr/src/modules/mol/src/kmod'
+ Entering Linux
  AS [x]   /usr/src/modules/mol/src/kmod/Linux/../build/_traps.o
/bin/sh: m4: command not found
make[5]: *** [/usr/src/modules/mol/src/kmod/Linux/../build/_traps.o] Error 127
make[4]: *** [_module_/usr/src/modules/mol/src/kmod/Linux/../build] Error 2
nm: '../build/mol.ko': No such file
nm: '../build/mol.ko': No such file
checker.pl failed
rm: cannot remove `../build/mol.ko': No such file or directory
make[3]: *** [all-local] Error 1
make[2]: *** [sub-Linux-all] Error 2
make[2]: Leaving directory `/usr/src/modules/mol/src/kmod'
make[1]: [src/kmod] Error 2 (ignored)
/usr/bin/make -C src/netdriver
make[2]: Entering directory `/usr/src/modules/mol/src/netdriver'
  Building modules, stage 2.
  MODPOST
ln: creating hard link `../../mollib/modules/2.6.12-9-powerpc//sheep.ko' to `build/sheep.ko': No such file or directory
make[2]: *** [all-local] Error 1
make[2]: Leaving directory `/usr/src/modules/mol/src/netdriver'
make[1]: [src/netdriver] Error 2 (ignored)
make[1]: Leaving directory `/usr/src/modules/mol'
touch build-stamp

Not sure what is causing this what I'm missing or don't have installed.  If I can make this work, it will be a life saver for me.  I did find though when you get the error of "Nothing to be done for build" you can remove the build-stamp file and then you can try building again.  Thanks.  Sorry for the misleading stuff above.  I will try not to mess with it until I hear more.

---

### Post by tmeier on 2005-11-17
Looking through my post, I found my problem.  I did not have M4 installed, didn't know that I needed it or it was even a program.  However I ran across it as I was scrolling through the Synaptic package manager and so I installed it and went through the wiki howto and low and behold it is working (sort of).  I have os 10.4.2 on my os x side, so will downgrade back to 10.3.3 and see if I can make it work, unless others have made it work in something else.

---

