---
title: "Openoffice on feisty 64 wont install"
date: 2007-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by jobsonandrew on 2007-06-18
I just installed Ubuntu Feisty 7.04 64bit desktop edition and im getting an error in the terminal when using this method to install OO:

[http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370)

Here is the terminal output:

andy@andylaptop:~$ cd OO
andy@andylaptop:~/OO$ cd RPMS
andy@andylaptop:~/OO/RPMS$ sudo alien -d --scripts *.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
xargs -0 -r -i cp -a {} debian/jre
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: format of `NEEDED libjli.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjli.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjli.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjli.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjli.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjli.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjli.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjli.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjli.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libverify.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjli.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libmlib_image.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libawt.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libawt.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libmlib_image.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libawt.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libnet.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libmlib_image.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libawt.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libmawt.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libmlib_image.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libawt.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libodbcinst.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libodbc.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjava.so' not recognised
dpkg-shlibdeps: warning: format of `NEEDED libjvm.so' not recognised
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libX11.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libnsl.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libnsl (soname 1, path libnsl.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libX11.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libnsl.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libnsl (soname 1, path libnsl.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libX11.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libnsl.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libnsl (soname 1, path libnsl.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libXext.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libX11.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libXtst.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXtst (soname 6, path libXtst.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libXi.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXi (soname 6, path libXi.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libasound.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libasound (soname 2, path libasound.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libnsl.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libnsl (soname 1, path libnsl.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libX11.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libXext.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libnsl.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libnsl (soname 1, path libnsl.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libstdc++.so.5
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgcc_s.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgcc_s (soname 1, path libgcc_s.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libnsl.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libnsl (soname 1, path libnsl.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpthread.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpthread (soname 0, path libpthread.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libX11.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libX11.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libXp.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXp (soname 6, path libXp.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libXtst.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXtst (soname 6, path libXtst.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libXext.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libX11.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libXi.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXi (soname 6, path libXi.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libm.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libX11.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libX11.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libdl.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: jre-1.6.0: No such file or directory
andy@andylaptop:~/OO/RPMS$

Anyone know what the problem is? It looks like i have to install something else first.. but I dont know

Please help

---

### Post by capecove on 2007-06-18
Open Office was already installed for me when I ran Feisty 64 bit install. Did you look under applications menu to be sure it wasn't already installed? Also, could you please tell us what version of Open Office you are attempting to install?

---

### Post by jobsonandrew on 2007-06-18
I do already have the openoffice that comes with Ubuntu but its very unstable, has missing features and bugs, so Im trying to install the official version from [www.openoffice.org](www.openoffice.org) (version 2.2.1)

---

### Post by capecove on 2007-06-18
Sorry, I don't have personal experience with this, but found this which may be helpful...

[https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/5441](https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/5441)

Let us know if this helps...

---

### Post by jobsonandrew on 2007-06-18
This is a different error, which i have experienced before and fixed.. see my post in this thread on the oo forum:
[http://www.oooforum.org/forum/viewtopic.phtml?t=57039&highlight=](http://www.oooforum.org/forum/viewtopic.phtml?t=57039&highlight=)

its caused by some screwed up font files that need deleting...
I'll just have to use the bundled crappy version of OO for now, until theres a way of installing the proper one

---

### Post by Rui Pais on 2007-06-18
hi,
since Oo is a 32bits app shouldn't you "alienage" (sorry the neologism) the package under a 32b environment and only after that install at you 64b (eventually needing --force-architecture for dpkg or/and copu some libs from 32b to your /usr/lib32)?

Just a suggestion.  I have done that one for an close source app (iscan for epson scanners)...


*EDIT*
Another suggestion. Seems that all missing libs are java related. Have you tried to install java 32b and redo the conversion process?

---

