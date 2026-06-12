---
title: "Stuck compiling mol-modules . . ."
date: 2006-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by paulsomm on 2006-03-16
Following the directions from [https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto) I get as far as running "sudo debian/rules build", where I'm greeted with:

m4 -DKVERS="2.6.12-10-powerpc" -DKSRC="/usr/src/linux-headers-2.6.12-10-powerpc" -DKEMAIL="paulsomm@panix.com" -DKMAINT="Aaron Dodd" -DKDREV="ubuntu0" -DDEBDATE="Thu, 16 Mar 2006 17:00:25 -0500" debian/control.m4 > debian/control
m4 -DKVERS="2.6.12-10-powerpc" -DKSRC="/usr/src/linux-headers-2.6.12-10-powerpc" -DKEMAIL="paulsomm@xxxxx.com" -DKMAINT="Aaron Dodd" -DKDREV="ubuntu0" -DDEBDATE="Thu, 16 Mar 2006 17:00:25 -0500" debian/changelog.m4 > debian/changelog
touch configure-stamp
dh_testdir
/usr/bin/make
make[1]: Entering directory `/usr/src/modules/mol'
/usr/bin/make -C src/kmod
make[2]: Entering directory `/usr/src/modules/mol/src/kmod'
+ Entering Linux
Makefile:486: .config: No such file or directory
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/_kuname.o
In file included from include/linux/autoconf.h:1,
                 from include/linux/config.h:4,
                 from /usr/src/modules/mol/src/kmod/Linux/../build/_kuname.c:17:include/linux/err_kernel_only.h:6:23: error: asm/errno.h: No such file or directory
/usr/src/modules/mol/src/kmod/Linux/../build/_kuname.c:18:27: error: linux/version.h: No such file or directory
/usr/src/modules/mol/src/kmod/Linux/../build/_kuname.c:26:40: error: missing binary operator before token "("
/usr/src/modules/mol/src/kmod/Linux/../build/_kuname.c:38: error: syntax error before ‘UTS_RELEASE’
make[5]: *** [/usr/src/modules/mol/src/kmod/Linux/../build/_kuname.o] Error 1
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
Makefile:486: .config: No such file or directory
  CC [M]  /usr/src/modules/mol/src/netdriver/build/kuname.o
In file included from include/linux/autoconf.h:1,
                 from include/linux/config.h:4,
                 from /usr/src/modules/mol/src/netdriver/build/kuname.c:17:
include/linux/err_kernel_only.h:6:23: error: asm/errno.h: No such file or directory
/usr/src/modules/mol/src/netdriver/build/kuname.c:18:27: error: linux/version.h: No such file or directory
/usr/src/modules/mol/src/netdriver/build/kuname.c:27:40: error: missing binary operator before token "("
/usr/src/modules/mol/src/netdriver/build/kuname.c:39: error: syntax error before ‘UTS_RELEASE’
make[4]: *** [/usr/src/modules/mol/src/netdriver/build/kuname.o] Error 1
make[3]: *** [_module_/usr/src/modules/mol/src/netdriver/build] Error 2
make[2]: Leaving directory `/usr/src/modules/mol/src/netdriver'
make[1]: Leaving directory `/usr/src/modules/mol'
touch build-stamp


I'm not sure what the problem was.  I was originally getting the error that "linux/config.h" was missing, so I installed the kernel headers thanks to a post on the forums here.  The above output lists things like "asm/errno.h" as missing, but if a do a "localte errno.h" I see a result from "/usr/include/asm/errno.h", similiar results for the other "missing" files.

I'm running Ubuntu 5.10 with the latest updates as of 3/16/06.  I've installed build-essential, the mol- packages and their dependencies, and the packages referenced in the link at the top of this post.

Can anyone help me?  Thanks much!

---

### Post by ssam on 2006-03-16
could you try installing the package
```
gcc-3.4
```
i think that might be necissary for compiling kernels in breezy.

or if you can wait until dapper is released installing MOL gets a whole lot easier see [https://wiki.ubuntu.com/MacOnLinuxHowtoDapper](https://wiki.ubuntu.com/MacOnLinuxHowtoDapper) .

---

### Post by paulsomm on 2006-03-16
[QUOTE=ssam]could you try installing the package
```
gcc-3.4
```
i think that might be necissary for compiling kernels in breezy.

or if you can wait until dapper is released installing MOL gets a whole lot easier see [https://wiki.ubuntu.com/MacOnLinuxHowtoDapper](https://wiki.ubuntu.com/MacOnLinuxHowtoDapper) .[/QUOTE]


Wow, well, Dapper looks like this will be much simpler.

Thanks for the gcc 3.4 pointer. I did indeed have it installed, but /usr/bin/gcc was symlinked to gcc4.  I switched the link to 3.4 and the modules compiled and MOL now launches for me.  Woohoo :)

Thanks ssam!

---

### Post by ssam on 2006-03-17
i added a note about gcc 3.4 to the wiki page.

---

