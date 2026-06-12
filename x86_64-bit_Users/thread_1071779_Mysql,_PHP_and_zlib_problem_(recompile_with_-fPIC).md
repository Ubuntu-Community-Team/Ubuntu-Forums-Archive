---
title: "Mysql, PHP and zlib problem (recompile with -fPIC)"
date: 2009-02-16
forum: x86 64-bit Users
---

### Post by moron on 2009-02-16
Howdy.  I use my desktop for web development and so have source installed  versions of Apache, MySQL and PHP running on it.  I recently needed to install some PEAR libraries so I could do some testing with a client's existing web app when I ran into a complaint related to zlib:

> /usr/local/bin/php: relocation error: /usr/local/bin/php: symbol gzdopen, version libmysqlclient_15 not defined in file libmysqlclient.so.15 with link time reference

My assumption here was that the issue was due to something external changing with zlib so I recompiled MySQL (after a make clean of course) and then tried re-compiling PHP. This resulted in:

> /usr/bin/ld: /usr/local/lib/mysql/libz.a(compress.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/mysql/libz.a: could not read symbols: Bad value

This is a hardish one to search for on Google due to how they filter things but as far as I can tell, this seems to be a problem with how zlib was compiled.  Since zlib is linked to all over the place I likely cannot just download zlib and compile that without re-compiling pretty much the entire system from scratch.

Anyone hit this before an find a solution?  Using the PHP package is not an option (I need more control over what modules and such are enabled).

Any help here appreciated.

Cheers

---

### Post by moron on 2009-02-16
Looks like I have found a solution.  When installing MySQL choosing the following configure option avoids the library conflict:

./configure --with-zlib-dir=bundled

The downside of course is that you will have to hope that the bundled zlib version is up to date (I know there have been some security issues recently with zlib).  

After a make && make install of MySQL, it was possible to build PHP and everything now appears to be working. 

Cheers

---

