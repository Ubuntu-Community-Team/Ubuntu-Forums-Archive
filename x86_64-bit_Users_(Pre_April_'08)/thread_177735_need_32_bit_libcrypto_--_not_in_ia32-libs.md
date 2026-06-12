---
title: "need 32 bit libcrypto -- not in ia32-libs*"
date: 2006-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by LazyBoy on 2006-05-16
Hi,

I'm compiling a 32bit app and need libcrypto, which is from the libssl package.  I don't find it in any of the ia32-libs* packages or anywhere else.

Any ideas?

---

### Post by Sutekh on 2006-05-16
They should be in the repositories, but you can always downlaod the package and dependencies from [here]("http://packages.ubuntu.com"). Fortunately there are only 3 dependant packages; lib32gcc1, lib32z1 and lsb-release

[Ubuntu Packages - ia32-libs]("http://packages.ubuntu.com/breezy/libs/ia32-libs")

[Ubuntu Packages - lib32gcc1]("http://packages.ubuntu.com/breezy/libs/lib32gcc1")

[Ubuntu Packages - lib32z1]("http://packages.ubuntu.com/breezy/libs/lib32z1")

[Ubuntu Packages - lsb-release]("http://packages.ubuntu.com/breezy/misc/lsb-release")


 You can install them manually with
 ```
sudo dpkg -i ia32-libs_1.4ubuntu4_amd64.deb
``` And so on


And in case you need the development libraries
 
 [Ubuntu Packages - ia32-libs-dev]("http://packages.ubuntu.com/breezy/libdevel/ia32-libs-dev")

---

### Post by LazyBoy on 2006-05-17
Thanks, but I don't think you understood.

I **have** those libraries.
**They** don't have /usr/lib32/libcrypto.a.

LB

---

### Post by Sutekh on 2006-05-17
Sorry I misread.   The ia32-libs-dev contain libcrypt.a, but not libcrypto.a.  [libssl-dev]("http://packages.ubuntu.com/breezy/libdevel/libssl-dev") contains libcrypto.a.  

On the [Ubuntu Packages]("http://packages.ubuntu.com") web page you can search for packages containing specified files.

---

### Post by LazyBoy on 2006-05-17
Thanks again, but I'm still not getting through.

Summary of problem:
I'm running X86_64.  
I'm trying to compile a 32-bit app which needs a 32-bit version of libcrypto.a or libcrypto.so.
The Ubuntu Packages web page shows only libssl has providing libcrypto, but that's the 64-bit version.
ia32-libs* does not have any libcrypto.
No package for x86_64 seems to have the 32-bit libcrypto.

I've already started using chroot to solve this.

Thanks for the pointer to the web-based content search though.  I hadn't found that yet.  Can one of the apt- tools find the package that installed a given file?

LB

---

### Post by Sutekh on 2006-05-17
I know what you are trying to do, the i386 version of libssl-dev has the libcrypto.a file

[libssl-dev - list of files - i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libssl-dev&version=breezy&arch=i386&page=1&number=all)

If you only need that file (or some others), why not download and extract it (and others) from the source?  Then add it (them) to /usr/lib32?

I'm not sure about the searching package contents with apt-get, try the man page.

---

