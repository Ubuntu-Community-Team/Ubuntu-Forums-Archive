---
title: "tools for running 32bit software on 64bit system"
date: 2009-05-13
forum: x86 64-bit Users
---

### Post by pixel :-) on 2009-05-13
the purpose of the thread is to eventually create a sticky about installing 32bit software in 64bit os.

for executables

dpkg -i --force--architecture packagei386.deb

shared 32 libraries for 64 system "ia32-libs" should resolve most issues with dependencies

experimental:

"ia32-apt-get" converts on the fly i386 pakages, i never used it, any body knows any documentation on this? And why on the fly? we should have ia32 packages in the repositories, ubuntu schould be mainly 64 bit, and in the forums a "x86 32-bit Users" thread. :confused:

"ia32-libs-tools" (used by the above) the script "/usr/lib/ia32-libs-tools/convert" seems very interesting on its own.

the problem with getlibs, is that it bypasses apt-get control system
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

with convert
/usr/lib/ia32-libs-tools/convert amd64 packagei386.deb (if on amd64)
then if it works
dpkg -b debian/ia32-package ia32-package.deb

and hopefully you have a nice package ready to be installed.

Problems with conflicting libraries? A little wrapper script
#!/bin/sh
export LD_LIBRARY_PATH=/usr/local/my_lib:$LD_LIBRARY_PATH
exec /usr/bin/my_program.orig $*

or

#!/bin/sh
/lib/ld-linux.so.2 --library-path PATH $*

just find a lib that works from any where, ubuntu, redhat, suse, santaclaus os, escimo os, chainsaw os, compile it your self, in the garbage, in an old scratched cd, anywhere, place it in /usr/local/my_lib and case closed. It will be used by only that program. Of caurse the tric remains valid for 64 bit programs too.

to inspect dependencies
ldd executable
thats ok
libmad.so.0 => /usr/lib32/libmad.so.0 (0xf7ebd000)
thats not
libdv.so.4 => not found

ia32-apt-get tries to be an "official" program, weal behaved, that follow the standards, ect... and is rather buggy and complicated and it will probably be sometime before its acceptable. So i would propose to hack together convert+getlibs+"dpkg -b"+"dpkg -i" set installation location "/usr/local/lib32" and strip all the fancy bells and whistles to a bugles little script.

:guitar: You see, no need to install 32bit os, 64bit os can run 32 bit stuff.

Slightly off topic, about the sticky on java.

java-6-openjdk : its the opensource package, 99% complete, but not 100%
sun-java6-bin :the official VM from java in 64 bit, buggy
ia32-sun-java6-bin and sun-java6-plugin : 32 bit package of official VM from java, i think this is as good as it gets. If you what compatibility, without braking your head, just install this. We should recommend by default this, motivated peopol can dig further on there own.

---

### Post by Cappy on 2009-05-13
If you took the dependencies required for the i386 package you could then look up the libraries inside each of those package and see if they are installed somewhere in /usr/lib32. If they aren't then you need that i386 package. You would need to do it like this because libraries are just thrown into ia32-libs. The only requirement would be that you would need the amd64 package to be installed so that you could list the files that are in that package.

I haven't looked much into the abilities of the ia32-lib-tools yet. I'm wondering if the fetch is similar to how I did it in getlibs (without the library to package name lookup that getlibs had to use due to the fact getlibs needed to be pointed at a binary).

---

### Post by pixel :-) on 2009-05-13
ia32-lib-tools don't fetch any thing, they just convert, ia32-apt-get is supposed do the job, the same way as standard apt-get. It downloads them, convert the libraries, installs them, takes care of the dependencies as you expect from apt-get.

ia32-libs are just thrown in? why they simply didn't let them in separate packages? This is a hack, not an official package. Is it really that hard to just repackage 32bit packages with some dependencies changed? The auto-generated packages should simply be set to conflict with ia32-libs, ia32-libs buy buy. This would be beter for compatibility, since every ia32-lib will be capable to update to new versions as they comme out. With ia32-libs, when a lib is too old you do what? ia32-libs-tools alredy pays some attention at what stuff should stay native.

From synaptic, only ia32-sun-java6/5 depends explicitly on ia32-libs. I guess a quick look at the dependencies of the normal 32bit package should fix its dependencies. A quick fix, would be a metapackage  of hier version, pointing to all the contained packages

Also the convert as it stands is geared for libraries, all stuff in */bin are deleted. So for executables packages we could simply convert a i386 package, by simply changing its dependencies(ia32-*) and renaming it self ia32-* , then it proceeds in installing the rest of the dependencies.

Ubuntu should have done something like this from the start.

---

### Post by tiepolo on 2009-09-22
Hello, trying to convert two closed applications I get : dpkg-parsechangelog: failure: tail of debian/changelog gave error 

do you have an idea to solve this problems? 

Thx,

Paolo

---

