---
title: "ConsoleOne 32 bit on 9.04 64-bit beg for help..."
date: 2009-06-16
forum: x86 64-bit Users
---

### Post by tixetsal on 2009-06-16
Does anyone know how to get consoleone 32 bit rpms running on 64-bit ubuntu?  I was able to use alien to get conone working perfectly on 8.10 32-bit, but alien keeps telling me on 9.04 64:

Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/ndsbase
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: couldn't find library libccs2.so needed by debian/ndsbase/usr/bin/ndssch (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libccs2.so needed by debian/ndsbase/usr/lib/libspmclnt.so (its RPATH is '/usr/lib').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libccs2.so needed by debian/ndsbase/usr/lib/libndssdk.so.1.0.0 (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libccs2.so needed by debian/ndsbase/usr/bin/ndslogin (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: symbol DSunicmp used by debian/ndsbase/usr/lib/libsch.so.1.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol WPutAlign32 used by debian/ndsbase/usr/lib/libsch.so.1.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol DDSExit used by debian/ndsbase/usr/lib/libsch.so.1.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol DDCReadToBuffer used by debian/ndsbase/usr/lib/libsch.so.1.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol DSuniindex used by debian/ndsbase/usr/lib/libsch.so.1.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol DDCGetEntryInfo used by debian/ndsbase/usr/lib/libsch.so.1.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol PutHiLo16 used by debian/ndsbase/usr/lib/libsch.so.1.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol UniFromLocal used by debian/ndsbase/usr/lib/libsch.so.1.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol DDCGetDefaultAddress used by debian/ndsbase/usr/lib/libsch.so.1.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol DDCSetContextEntryID used by debian/ndsbase/usr/lib/libsch.so.1.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: 54 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: dependency on libm.so.6 could be avoided if "debian/ndsbase/usr/bin/ndssch debian/ndsbase/usr/bin/ndslogin" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libnsl.so.1 could be avoided if "debian/ndsbase/usr/lib/libsal.so.1.0.0" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on librt.so.1 could be avoided if "debian/ndsbase/usr/bin/ndssch debian/ndsbase/usr/bin/ndslogin debian/ndsbase/usr/lib/libJClient.so.1.0.0" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libspmclnt.so could be avoided if "debian/ndsbase/usr/lib/libndssdk.so.1.0.0 debian/ndsbase/usr/bin/ndslogin" were not uselessly linked against it (they use none of its symbols).
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
	find NDSbase-8.7.3.7 -type d -exec chmod 755 {} ;
find: `NDSbase-8.7.3.7': No such file or directory
	rm -rf NDSbase-8.7.3.7

---

### Post by pixel :-) on 2009-06-16
alien can't make packages of 32 bit on a 64 bit system

but it can help you make a quick and dirty package

alien -g pakage.rpm

in the generated folder "pakage" (not .orig)
rename debian to DEBIAN
in DEBIAN edit control

Architecture: amd64 (from i386)
Version: "add here manually the verion"

delete:
Depends: ${shlibs:Depends}
and remove the empty line

if you whant change the name
Package: ia32-package

dpkg -b pakage ia32-package.deb

sudo dpkg -i package_name.deb

then use getlibs, to fix the dependencies

[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

---

### Post by tixetsal on 2009-06-17
pixel,

Thanks a bunch for the assistance.  I ran through the process that you described, and it seemed to work on an .rpm.  The problem that I now have, is that ConsoleOne is made up of 63 different .rpms!  
Is there some way to script this process for multiple .rpms?  I am not a scripting god yet, and I am just cutting teeth on sed and awk.  
Thanks again.  I learned a great deal from your last post.


alien can't make packages of 32 bit on a 64 bit system

but it can help you make a quick and dirty package

alien -g pakage.rpm

in the generated folder "pakage" (not .orig)
rename debian to DEBIAN
in DEBIAN edit control

Architecture: amd64 (from i386)
Version: "add here manually the verion"

delete:
Depends: ${shlibs:Depends}
and remove the empty line

if you whant change the name
Package: ia32-package

dpkg -b pakage ia32-package.deb

sudo dpkg -i package_name.deb

then use getlibs, to fix the dependencies

[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)[/QUOTE]

---

### Post by tixetsal on 2009-07-24
I later discovered that ConsoleOne could be dissected to 24 rpms, if you removed all of the other languages, but I had already reinstalled 32-bit o/s instead.  It ended up not really making a difference, because it seems that a recent jaunty update has created problems with ConsoleOne on 9.04 i386.  I have strange artifacting and other weirdness going on in the right pane on more than one jaunty machine at work.  I tried downgrading ConsoleOne, but it did not help.  We'll be off of netware soon.

---

