---
title: "Scilab 4 (Edgy)"
date: 2006-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bill Cosby on 2006-11-05
Hello everyone,

I recently tried to install the Scilab 4 package, the problem is:
The scilab **4.0-2** package depends on a scilab-bin **3.0-12** package, which is weird to begin with, I then get the following error when I try to install it:

Depends: scilab-bin but it is not going to be installed.

is this sometihng I should post as a bug?

Thanks in advance,
Bill

---

### Post by TestUser on 2006-11-05
Hi

I have no help for the strange error message you get. If you like to install DL the file from scilab.org instead and:
 2. Launch the following commands :
    [$SHELL] cd <scilab-path>
    [$SHELL] tar xzf scilab-4.0.bin.linux-i686.tar.gz
    [$SHELL] cd scilab-4.0
    [$SHELL] make

3. To launch Scilab :
    [$SHELL] cd <scilab-path>/scilab-4.0
    [$SHELL] bin/scilab

taken from here:
[http://www.scilab.org/download/index_download.php](http://www.scilab.org/download/index_download.php)

TU

---

### Post by .t. on 2006-11-05
File a bug on the package:[http://bugs.ubuntu.com](http://bugs.ubuntu.com)

---

### Post by kleeman on 2006-11-05
Or grab the missing deb from here:

[http://www.yourfilelink.com/get.php?fid=206898](http://www.yourfilelink.com/get.php?fid=206898)

Compiled on a reltively clean edgy amd64 os

---

### Post by penvzila on 2007-02-21
I'm pleased to report this bug STILL EXISTS in the edgy repository.

---

