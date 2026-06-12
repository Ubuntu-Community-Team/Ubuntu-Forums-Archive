---
title: "ATI driver"
date: 2006-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by eigenman on 2006-08-20
Hi,

I recently upgraded my ati firegl drivers to version 8.27.10 in the hope that
some of their bugs is fixed. But now, when I run glxinfo, I get an error
that libGL.so.1 not found. The library is installed, and running 
"ldconfig -v" shows the library in the list. libGL.so.1 is installed in
/usr/X11R6/lib, as far as I can tell.

Any ideas what's going on?

Eigenman

---

### Post by majesticturkey on 2006-08-20
I had a lot of problems getting my ATI driver working right, and in doing all the research it took to eventually get it working, I found out that there's lots of little glitches in that libGL.so. Check the official ATI drivers wiki: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

And try seeing if it's looking in a *different* place for libGL.so.1...if so, you've got the same problem I did, and you just need to set up a symbolic link.

---

