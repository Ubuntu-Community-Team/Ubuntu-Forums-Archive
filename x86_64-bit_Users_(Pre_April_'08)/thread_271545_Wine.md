---
title: "Wine"
date: 2006-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Draknats on 2006-10-04
I've been trying on-and-off to get Wine up and running.  I've been unsuccessful through-and-through.  I have an AMD Athlon 64 3500 and am on Dapper Drake.  I've been following the instructions on the Wine website (compiling the source and such).  Any ideas as to what I'm doing wrong?  This is the error I get in the console:

draknats@draknats-desktop:~$ sudo apt-get --build source wine
Reading package lists... Done
Building dependency tree... Done
Skipping already downloaded file 'wine_0.9.22~winehq0~ubuntu~6.06-1.dsc'
Skipping already downloaded file 'wine_0.9.22~winehq0~ubuntu~6.06.orig.tar.gz'
Skipping already downloaded file 'wine_0.9.22~winehq0~ubuntu~6.06-1.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in wine-0.9.22~winehq0~ubuntu~6.06
dpkg-buildpackage: source package is wine
dpkg-buildpackage: source version is 0.9.22~winehq0~ubuntu~6.06-1
dpkg-buildpackage: source changed by Scott Ritchie <scott@open-vote.org>
dpkg-buildpackage: host architecture amd64
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/draknats/wine-0.9.22~winehq0~ubuntu~6.06'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/draknats/wine-0.9.22~winehq0~ubuntu~6.06'
make: [clean] Error 2 (ignored)
#-/usr/bin/make -C documentation clean
dh_clean
 debian/rules build
dh_testdir
# Add here commands to configure the package.
CFLAGS="-Wall -g -O2" ./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for x86_64-linux-gnu-gcc... gcc -m32
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [config.status] Error 77
Build command 'cd wine-0.9.22~winehq0~ubuntu~6.06 && dpkg-buildpackage -b -uc' f ailed.
E: Child process failed

---

### Post by Kilz on 2006-10-04
> **Draknats said:**
> I've been trying on-and-off to get Wine up and running.  I've been unsuccessful through-and-through.  I have an AMD Athlon 64 3500 and am on Dapper Drake.  I've been following the instructions on the Wine website (compiling the source and such).  Any ideas as to what I'm doing wrong?  This is the error I get in the console:

draknats@draknats-desktop:~$ sudo apt-get --build source wine
Reading package lists... Done
Building dependency tree... Done
Skipping already downloaded file 'wine_0.9.22~winehq0~ubuntu~6.06-1.dsc'
Skipping already downloaded file 'wine_0.9.22~winehq0~ubuntu~6.06.orig.tar.gz'
Skipping already downloaded file 'wine_0.9.22~winehq0~ubuntu~6.06-1.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in wine-0.9.22~winehq0~ubuntu~6.06
dpkg-buildpackage: source package is wine
dpkg-buildpackage: source version is 0.9.22~winehq0~ubuntu~6.06-1
dpkg-buildpackage: source changed by Scott Ritchie <scott@open-vote.org>
dpkg-buildpackage: host architecture amd64
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/draknats/wine-0.9.22~winehq0~ubuntu~6.06'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/draknats/wine-0.9.22~winehq0~ubuntu~6.06'
make: [clean] Error 2 (ignored)
#-/usr/bin/make -C documentation clean
dh_clean
 debian/rules build
dh_testdir
# Add here commands to configure the package.
CFLAGS="-Wall -g -O2" ./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for x86_64-linux-gnu-gcc... gcc -m32
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [config.status] Error 77
Build command 'cd wine-0.9.22~winehq0~ubuntu~6.06 && dpkg-buildpackage -b -uc' f ailed.
E: Child process failed


There is a sticky in the 64bit section "Sticky: How to get specific programs to run under Dapper Drake 64-bit edition" you may have overlooked. It has links to howto's for some of the more common hard to install programs for 64bit. Inside is a link to my wine howt. You might want to remember ths sticky as it can save you hitting your head into a wall. ](*,)

---

### Post by kircher on 2006-10-04
have you tried installing from a synaptic or apt-get? or using another binary?

---

### Post by Kilz on 2006-10-04
> **kircher said:**
> have you tried installing from a synaptic or apt-get? or using another binary?

One of the common problems with the 64bit version is that there is no wine in syanptic/apt for it.

---

### Post by kircher on 2006-10-04
oh right... I didn't realise that

---

### Post by confusimo on 2006-10-05
Ya but doesn't synaptic have an option to add download packages?

Thanks,
Confusimo

---

### Post by fabertawe on 2006-10-05
Follow Kilz's How-To or [build it yourself]("http://wiki.winehq.org/WineOn64bit"). I have done both with no problem.

Paul

---

### Post by Kilz on 2006-10-05
> **kircher said:**
> oh right... I didn't realise that
No problem. Just letting you know so you can point people to the information instead.

> **confusimo said:**
> Ya but doesn't synaptic have an option to add download packages?

Thanks,
Confusimo

If you know of a Wine package for the amd64 version please link to it. As far as I know no such package exists. The i386 package must be forced in and libraries manually added. That is what my howto explains how to do.

---

