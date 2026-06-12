---
title: "Error installing fuse file system on Jaunty Jackalope"
date: 2009-11-16
forum: x86 64-bit Users
---

### Post by chandershivdasani on 2009-11-16
Hi Guys,

I am planning to write a small file system and for that i need to install FUSE. The readme file suggests three steps:

./configure
make 
make install

The first 2 commands run properly, when i try to do "sudo make install", it gives me the following error:

```
make[1]: Entering directory `/home/chander/Desktop/Fuse File System/fuse-2.8.1/include'
make[2]: Entering directory `/home/chander/Desktop/Fuse File System/fuse-2.8.1/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/fuse" || /bin/mkdir -p "/usr/local/include/fuse"
 /usr/bin/install -c -m 644 'fuse.h' '/usr/local/include/fuse/fuse.h'
 /usr/bin/install -c -m 644 'fuse_compat.h' '/usr/local/include/fuse/fuse_compat.h'
 /usr/bin/install -c -m 644 'fuse_common.h' '/usr/local/include/fuse/fuse_common.h'
 /usr/bin/install -c -m 644 'fuse_common_compat.h' '/usr/local/include/fuse/fuse_common_compat.h'
 /usr/bin/install -c -m 644 'fuse_lowlevel.h' '/usr/local/include/fuse/fuse_lowlevel.h'
 /usr/bin/install -c -m 644 'fuse_lowlevel_compat.h' '/usr/local/include/fuse/fuse_lowlevel_compat.h'
 /usr/bin/install -c -m 644 'fuse_opt.h' '/usr/local/include/fuse/fuse_opt.h'
 /usr/bin/install -c -m 644 'cuse_lowlevel.h' '/usr/local/include/fuse/cuse_lowlevel.h'
test -z "/usr/local/include" || /bin/mkdir -p "/usr/local/include"
 /usr/bin/install -c -m 644 'old/fuse.h' '/usr/local/include/fuse.h'
 /usr/bin/install -c -m 644 'ulockmgr.h' '/usr/local/include/ulockmgr.h'
make[2]: Leaving directory `/home/chander/Desktop/Fuse File System/fuse-2.8.1/include'
make[1]: Leaving directory `/home/chander/Desktop/Fuse File System/fuse-2.8.1/include'
Making install in lib
make[1]: Entering directory `/home/chander/Desktop/Fuse File System/fuse-2.8.1/lib'
make[2]: Entering directory `/home/chander/Desktop/Fuse File System/fuse-2.8.1/lib'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libfuse.la' '/usr/local/lib/libfuse.la'
libtool: install: /usr/bin/install -c .libs/libfuse.so.2.8.1 /usr/local/lib/libfuse.so.2.8.1
libtool: install: (cd /usr/local/lib && { ln -s -f libfuse.so.2.8.1 libfuse.so.2 || { rm -f libfuse.so.2 && ln -s libfuse.so.2.8.1 libfuse.so.2; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libfuse.so.2.8.1 libfuse.so || { rm -f libfuse.so && ln -s libfuse.so.2.8.1 libfuse.so; }; })
libtool: install: /usr/bin/install -c .libs/libfuse.lai /usr/local/lib/libfuse.la
libtool: install: /usr/bin/install -c .libs/libfuse.a /usr/local/lib/libfuse.a
libtool: install: chmod 644 /usr/local/lib/libfuse.a
libtool: install: ranlib /usr/local/lib/libfuse.a
/bin/bash: /home/chander/Desktop/Fuse: No such file or directory
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libulockmgr.la' '/usr/local/lib/libulockmgr.la'
libtool: install: /usr/bin/install -c .libs/libulockmgr.so.1.0.1 /usr/local/lib/libulockmgr.so.1.0.1
libtool: install: (cd /usr/local/lib && { ln -s -f libulockmgr.so.1.0.1 libulockmgr.so.1 || { rm -f libulockmgr.so.1 && ln -s libulockmgr.so.1.0.1 libulockmgr.so.1; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libulockmgr.so.1.0.1 libulockmgr.so || { rm -f libulockmgr.so && ln -s libulockmgr.so.1.0.1 libulockmgr.so; }; })
libtool: install: /usr/bin/install -c .libs/libulockmgr.lai /usr/local/lib/libulockmgr.la
libtool: install: /usr/bin/install -c .libs/libulockmgr.a /usr/local/lib/libulockmgr.a
libtool: install: chmod 644 /usr/local/lib/libulockmgr.a
libtool: install: ranlib /usr/local/lib/libulockmgr.a
/bin/bash: /home/chander/Desktop/Fuse: No such file or directory
make[2]: *** [install-libLTLIBRARIES] Error 127
make[2]: Leaving directory `/home/chander/Desktop/Fuse File System/fuse-2.8.1/lib'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/chander/Desktop/Fuse File System/fuse-2.8.1/lib'
make: *** [install-recursive] Error 1

```
I'm not sure why does it access /home/chander/Desktop/FUSE ..there is no such file or directory on my drive .. how does this file/directory gets created?

Thanks,

Chander

---

