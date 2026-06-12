---
title: "Howto make debian standard debs from scratch"
date: 2005-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tamir on 2005-07-22
Hi,
Thanks to [Debian's guide](http://www.debian.org/doc/maint-guide/).
lets start.

_**How to make a debian package in 10 minutes** _
Few things you need:
a. a debian/ubuntu system with apt
b. you need to know how to do a basic compile
c. a little project to make deb of, check if this project already build on: [http://packages.ubuntu.com](http://packages.ubuntu.com)
d. few programes to install: apt-get install build-essential dh-make debhelper devscripts 

_**Getting your little projcet source code** _
a. Download your project source code (usually tar.bz2/tar.gz)
b. Untar it:

tar.bz2 files:
```
tar xvjf myproject-1.2.tar.bz2
``` 
tar.gz files:
```
tar xvzf myproject-1.2.tar.gz
```

myproject-1.2.tar.bz2 - which means:
- The package name: myproject
- The version: 1.2

c. after extracting usually you will see a directory named: myproject-1.2
(by debian standards: the .tar.bz2 and the directory the extracted from it, should name like that always: **packagename-version**, if it doesn't, change it)

d. lets move this to our enviroment directory. for example:
```
cp -r myproject-1.2 /home/myusername/packages/myproject/
cp myproject-1.2.tar.bz2 /home/myusername/packages/myproject/

```

now, you should have:
/home/myusername/packages/myproject/myproject-1.2
/home/myusername/packages/myproject/myproject-1.2.tar.bz2

if you don't, make it happen.
change directory there
```
cd /home/myusername/packages/myproject/
``` 

_**Making a debian enviroment to the package** _
first thing you should check is: does myproject-1.2 have a configure file?
if it doesn't you should make it, but we will not talk about it in this guide

so we have a configure file, great. lets start.
a. change directory to you myproject-1.2 directory
```
cd myproject-1.2
```
dh_make is a tool that generates an enviroment to our package, lets use it:
```
dh_make -e youremail@site.org -f ../myproject-1.2.tar.bz2
 Type of package: single binary, multiple binary, library, or kernel module?
  [s/m/l/k]
``` 
(change [email]yourmail@site.org[/email] to your real email ofcource)

now, it will ask if myproject-1.2 is a
s = [single binary] - a normal one package deb
l = [library] - choose that you are making package of something like **libmyproject-dev** 
m = [multiple] - multiple binary packages
k = [kernel module] - a kernel module

now it will ask:
```
 Maintainer name : firstname lastname
 Email-Address   : youmail@site.org
 Date            : Thu, 21 Jul 2005 18:52:02 +0000
 Package Name    : myproject
 Version         : 1.2
 Type of Package : Single Binary
 Hit <enter> to confirm:

``` 

if all true, hit enter/return
```
ls
``` 
as you can see, dh_make created a directory named - **debian**.
there are many files in debian/ directory, files that you need to edit/remove.

Lets start with [COLOR=Gray]control[/COLOR].
Edit this file with your favorite editor (I usually use nano).
```

       1  Source: myproject
       2  Section: unknown
       3  Priority: optional
       4  Maintainer: firstname lastname <yourmail@site.org>
       5  Build-Depends: debhelper (>> 3.0.0)
       6  Standards-Version: 3.6.1
       7
       8  Package: myproject
       9  Architecture: any
       10 Depends: ${shlibs:Depends}
       11 Description: <insert up to 60 chars description>
       12  <insert long description, indented with spaces>

```
Line 1 - your source package name
Line 2 - what kind of package - games, sound, gnome, kde, x11...
Line 3 - How important is the package (you can keep like that)
Line 4 - you first, last name and your email on <>
Line 5 - all of the -dev packages that you need to compile this package, for exampe - libnothing-dev, you can check these depends with a script that Debian made: 
-create new text file and paste this
```

       strace -f -o /tmp/log ./configure
       # or make instead of ./configure, if the package doesn't use autoconf
       for x in `dpkg -S $(grep open /tmp/log|\
                           perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
                           grep "^/"| sort | uniq|\
                           grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
                           cut -f1 -d":"| sort | uniq`; \
             do \
               echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2 -d":"` "), "; \
             done

```
save this file on myproject-1.2 directory, call it "script".
run this script:
```
sh ../script
``` 
(the ../ is because I guess you are in debian/ direcotory)
now in the end of the script you will see all the depends of the package, copy to line 5 only the packages that end with -dev
Line 6 - the version of [Debian Policy](http://www.debian.org/devel/).
Line 7 - a space
Line 8 - the new package name, I keep it like the source one (Line 1)
Line 9 - Any which means every architecture that you are trying to compile on, if you want only amd64, put there **amd64**
Line 10 - run the script that we made again, and fill here every package that doesn't end with -dev.
Line 11 - a short description up to 60 chars.
Line 12 - as you can see, there is a space before the description, keep it like that!
and fill there a full description. if you want to do a space between 2 lines fill a . (dot).

After an edit:
```

       1  Source: myproject
       2  Section: gnome
       3  Priority: optional
       4  Maintainer: firstname lastname <yourmail@site.org>
       5  Build-Depends: debhelper (>> 3.0.0), libnothing-dev
       6  Standards-Version: 3.6.1
       7
       8  Package: myproject
       9  Architecture: amd64 i386 powerpc
       10 Depends: ${shlibs:Depends}, mozilla-firefox, gnome-core
       11 Description: My project is a web-browser.
       12  You can -
             * surf in the internet
             * enter to google site!
             * download ubuntu
             * buy from the internet an amd64 box!
              .
             * another text....

```

 :-P Save. we move to the file: [COLOR=Gray]changelog[/COLOR], edit it.
```

       1  myproject (1.2-1) unstable; urgency=low
       2
       3   * Initial Release.
       4
       5  -- firstname lastname <yourmail@site.org>  Thu, 21 Jul 2005 18:52:02 +0000

       6

```
Line 1 - you package name, version:
[list]
[*]"When working with a package which originated in Debian, use a version number derived from the Debian version number with ubuntu<revision> appended. i.e. Debian 1.0-2 becomes 1.0-2ubuntu1, followed by 1.0-2ubuntu2, etc.
[*]Packages not in debian yet should end with revision -0ubuntu1"
[/list]
(from [https://wiki.ubuntu.com/DeveloperResources](https://wiki.ubuntu.com/DeveloperResources))

, the dist - change to warty/hoary/breezy
Line 2 - a space
Line 3 - * what you did to the package, what is that for.
Line 4 - a space
Line 5 - your firstname, lastname, <email>, and a full date.

**After an edit (if my package originated in Debian):**
```

       1  myproject (1.2-1ubuntu1) hoary; urgency=low
       2
       3   * ubuntu linux amd64 package for hoary hedgedog.
            * a stable relese.
       4
       5  -- firstname lastname <yourmail@site.org>  Thu, 21 Jul 2005 18:52:02 +0000

       6

```

**After an edit (if my package did not originate in Debian):**
```

       1  myproject (1.2-0ubuntu1) hoary; urgency=low
       2
       3   * ubuntu linux amd64 package for hoary hedgedog.
            * a stable relese.
       4
       5  -- firstname lastname <yourmail@site.org>  Thu, 21 Jul 2005 18:52:02 +0000

       6

```

Save. lets move to the file: [COLOR=Gray]copyright[/COLOR], edit it.
```

       1  This package was debianized by firstname lastname <yourmail@site.org> on
       2  Thu, 21 Jul 2005 18:52:02 +0000
       3
       4  It was downloaded from <fill in ftp site>
       5
       6  Upstream Author(s): <put author(s) name and email here>
       7
       8  Copyright:
       9
       10 <Must follow here>

```
Line 1 - fill your firstname, lastname, <email>.
Line 2 - the full date
Line 3 - a space
Line 4 - where did you download the source from?
Line 5 - a space
Line 6 - The authors, usually the is a file named - AUTHORS on the main directory
Line 7 - a space
Line 8 - the licence type, who made the source, and when.
Line 9 - a space
Line 10 - the full licence

After an edit:
```

      1  This package was debianized by firstname lastname <yourmail@site.org> on
       2  Thu, 21 Jul 2005 18:52:02 +0000
       3
       4  It was downloaded from: http://thesource-site.com/files/
       5
       6  Upstream author: Author full name <hisemail@site.org>
       7
       8  This software is copyright (c) 2005-08 by Author full name, Obsession
       9  Development.
       10
       11 You are free to distribute this software under the terms of
       12 the GNU General Public License.
       13 On Debian systems, the complete text of the GNU General Public
       14 License can be found in the file `/usr/share/common-licenses/GPL'.

```

Save. if you are compiling this package by - ./configure; make; make install, you should not change the file [COLOR=Gray]rules[/COLOR], but lets explain:
```

       1  #!/usr/bin/make -f
       2  # Sample debian/rules that uses debhelper.
       3  # GNU copyright 1997 to 1999 by Joey Hess.
       4
       5  # Uncomment this to turn on verbose mode.
       6  #export DH_VERBOSE=1
       7
       8  # This is the debhelper compatibility version to use.
       9  export DH_COMPAT=4
       10 
       11 CFLAGS = -g
       12 ifneq (,$(findstring noopt,$(DEB_BUILD_OPTIONS)))
       13 CFLAGS += -O0
       14 else
       15 CFLAGS += -O2
       16 endif
       17
       18 build: build-stamp
       19 build-stamp:
       20        dh_testdir
       21
       22        # Add here commands to compile the package.
       23        $(MAKE)
       24        #docbook-to-man debian/myproject.sgml > myproject.1
       25
       26        touch build-stamp
       27
       28 clean:
       29        dh_testdir
       30        dh_testroot
       31        rm -f build-stamp
       32
       33        # Add here commands to clean up after the build process.
       34        -$(MAKE) clean
       35
       36        dh_clean
       37
       38 install: build
       39        dh_testdir
       40        dh_testroot
       41        dh_clean -k
       42        dh_installdirs
       43
       44        # Add here commands to install the package into debian/gentoo.
       45        $(MAKE) install DESTDIR=$(CURDIR)/debian/myproject
       46
       47 # Build architecture-independent files here.
       48 binary-indep: build install
       49 # We have nothing to do by default.
       50
       51 # Build architecture-dependent files here.
       52 binary-arch: build install
       53        dh_testdir
       54        dh_testroot
       55 #      dh_installdebconf
       56        dh_installdocs
       57        dh_installexamples
       58        dh_installmenu
       59 #      dh_installlogrotate
       60 #      dh_installemacsen
       61 #      dh_installpam
       62 #      dh_installmime
       63 #      dh_installinit
       64        dh_installcron
       65        dh_installman
       66        dh_installinfo
       67 #      dh_undocumented
       68        dh_installchangelogs ChangeLog
       69        dh_link
       70        dh_strip
       71        dh_compress
       72        dh_fixperms
       73 #      dh_makeshlibs
       74        dh_installdeb
       75 #      dh_perl
       76        dh_shlibdeps
       77        dh_gencontrol
       78        dh_md5sums
       79        dh_builddeb
       80
       81 binary: binary-indep binary-arch
       82 .PHONY: build clean binary-indep binary-arch binary install

```
Line 11 - add the cflags you are compiling with
Line 22 - add compiling commands
Line 33 - add clean commands
Line 44 - add installation commands

Save.

we did 80%.
now, there are some another files.
Lets edit the file: [COLOR=Gray]README.debian[/COLOR] 
```

myproject for Debian
---------------

**<possible notes regarding this package - if none, delete this file>**

 -- firstname lastname <yourmail@site.org>, Thu, 21 Jul 2005 18:52:02 +0000

```

if you don't have what to write, remove the file.
after edit:
```

myproject for Debian
---------------

this package is an open source code, do what ever you want.
feel free to send any bugs, questions to yourmail@site.org.

 -- firstname lastname <yourmail@site.org>, Thu, 21 Jul 2005 18:52:02 +0000

```

[COLOR=Gray]emacsen-*.ex[/COLOR] - If your package doesn't supply Emacs files that can be bytecompiled at package installation time - Remove these files

[COLOR=Gray]init.d.ex[/COLOR] - If your package is a daemon that needs to be run at system startup, keep this file, if not, remove.

[COLOR=Gray]manpage.1.ex, manpage.sgml.ex[/COLOR] - if your program has man pages, you can remove these, if doesn't, you can fill it.

[COLOR=Gray]postinst.ex, preinst.ex, postrm.ex, prerm.ex[/COLOR]
These files are called maintainer scripts. They are scripts which are put in the control area of the package and run by dpkg when your package is installed, upgraded or removed.

For now, you should try to avoid any manual editing of maintainer scripts if you possibly can because they tend to get complex

_**Building the .deb file** _

for full build of the package (build source, deb, clean...) run:
```

dpkg-buildpackage -rfakeroot

```

Instead if you have a big package, you can also build only the deb file with:
```

fake root debian/rules binary

```

If you don't have problems, you will get these 5 files on:
/home/myusername/packages/myproject/

- myproject_1.2.orig.tar.gz - the original source code tarball

- myproject_1.2-1.diff.gz - this file contains all the changes you made to the original source code.

- myproject_1.2-1.dsc - generated file from debian/control, contains summary of the contents of the source code

- myproject_1.2-1_amd64.deb - this is the debian binary package you made!

- myproject_1.2-1_amd64.changes - like a changlog file.

:) You made your first deb!
please send every amd64 package that you made + .orig.tar.gz, .dsc, .diff to [email]tamir@nooms.de[/email]. I will upload to my repository.

---

### Post by filterban on 2005-07-22
Wow.   Thanks for the guide.  This is really helpful.   I'll start using it to make .debs the right way.  Let's keep those requests coming!

Question, though - when you say "standart", do you mean "standard"?

---

### Post by Tamir on 2005-07-22
[QUOTE=filterban]Wow.   Thanks for the guide.  This is really helpful.   I'll start using it to make .debs the right way.  Let's keep those requests coming!

Question, though - when you say "standart", do you mean "standard"?[/QUOTE]
 Yeah sorry, I thought it's standart :)
My english is not very well.

---

### Post by Terracotta on 2005-07-22
[QUOTE=Tamir]Hi,
Thanks to [Debian's guide](http://www.debian.org/doc/maint-guide/).
lets start.

_**How to make a debian package in 10 minutes** _
Few things you need:
a. a debian/ubuntu system with apt
b. you need to know how to do a basic compile
c. a little project to make deb of, check if this project already build on: [http://packages.ubuntu.com](http://packages.ubuntu.com)
d. few programes to install: apt-get install build-essential dh_make debhelper devscripts 
[/QUOTE]
Euhm, I'm a bit embarrased to ask, but how does one do a basic compile? I know I've tried it before, but I never succeeded, and I barely knew what I was doing. I was just typing some letters, does anyone know of a how to or so, since I can't find one.

---

### Post by jon_gunnar on 2005-07-22
[QUOTE=Tamir]Hi,
Thanks to [Debian's guide](http://www.debian.org/doc/maint-guide/).
lets start.

dh_make[/QUOTE]

Excuse my ignorance, but were did you get a suitable dh_make
I don't find it in the usual repositories?

Great work with the guide. You do a lot of good work for the Ubuntu community.

---

### Post by filterban on 2005-07-22
[QUOTE=Terracotta]Euhm, I'm a bit embarrased to ask, but how does one do a basic compile? I know I've tried it before, but I never succeeded, and I barely knew what I was doing. I was just typing some letters, does anyone know of a how to or so, since I can't find one.[/QUOTE]

Basically this is what is involved in a compilation:

 - Download and extract the source code of the program you want to build.
 - Change to its directory.
 - Type "./configure".  This sets up a configure file so the "make" program knows how to compile the program for your computer.
 - Type "make"  - this performs the compilation.  "make" will compile the program according to your configure script in the current directory.

---

### Post by Tamir on 2005-07-22
[QUOTE=jon_gunnar]Excuse my ignorance, but were did you get a suitable dh_make
I don't find it in the usual repositories?[/QUOTE]

I am sorry, I was wrong, the package called dh-make, and the commande is dh_make.

---

### Post by ArBaDaCarBa on 2005-07-22
If I may add just one small trick...

[QUOTE=Tamir]
 :-P Save. we move to the file: [COLOR=Gray]changelog[/COLOR], edit it.
[/QUOTE]

For that you could use the command **dch -i** (or debchange) that creates the skeleton of the entry, just don't forget to set the environment variables DEBFULLNAME and DEBEMAIL (read the man page).

---

### Post by Tamir on 2005-07-22
Ok, I didn't know it, thanks. I have to ask - is that Yoda from starwars on your avatar?

---

### Post by Jet2k5 on 2005-07-22
This is awesome!!!!!

---

### Post by DancingSun on 2005-07-22
[QUOTE=Tamir]Ok, I didn't know it, thanks. I have to ask - is that Yoda from starwars on your avatar?[/QUOTE]

I think that's just some space alien.  :roll:

---

### Post by ArBaDaCarBa on 2005-07-26
[QUOTE=Tamir]Ok, I didn't know it, thanks. I have to ask - is that Yoda from starwars on your avatar?[/QUOTE]

Mine ? It's one of the aliens from Toy Story.

---

### Post by Tamir on 2005-07-26
Oh, I thought it is Yoda (Jedi Master) from star wars.

---

### Post by pailhead on 2005-07-27
I'm trying to build my first package which is clearlooks 0.6.2.  I'm trying to run "dpkg-buildpackage -rfakeroot and I'm getting the following:

```
pailhead@ubuntu:~/packages/clearlooks/clearlooks-0.6.2$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is clearlooks
dpkg-buildpackage: source version is 0.6.2-1
dpkg-buildpackage: source maintainer is pailhead <pailhead@ph-productions.com>
dpkg-buildpackage: host architecture is amd64
 fakeroot debian/rules clean
/usr/bin/dpkg-buildpackage: line 175: fakeroot: command not found
```

Any idea what is causing this? Is there something more I need to download?

---

### Post by Octane on 2005-07-28
this is a grade A post. Thanks!

---

### Post by az on 2005-07-28
[QUOTE=pailhead]I'm trying to build my first package which is clearlooks 0.6.2.  I'm trying to run "dpkg-buildpackage -rfakeroot and I'm getting the following:

```
pailhead@ubuntu:~/packages/clearlooks/clearlooks-0.6.2$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is clearlooks
dpkg-buildpackage: source version is 0.6.2-1
dpkg-buildpackage: source maintainer is pailhead <pailhead@ph-productions.com>
dpkg-buildpackage: host architecture is amd64
 fakeroot debian/rules clean
/usr/bin/dpkg-buildpackage: line 175: fakeroot: command not found
```

Any idea what is causing this? Is there something more I need to download?[/QUOTE]


Install fakeroot.

sudo apt-get install fakeroot.

---

### Post by pailhead on 2005-07-28
[QUOTE=azz]Install fakeroot.

sudo apt-get install fakeroot.[/QUOTE]

 ](*,) Ahh .. I didn't think of that. :) Well I'll hvae to do that tonight.. 

Thanks...

---

### Post by xbaez on 2005-08-05
which is the correct way to place the dependencies?
is this correct for amarok?
Depends: kdelibs4, (>= ), libkdepim1 (>= 4 )...

---

### Post by Tamir on 2005-08-06
[QUOTE=xbaez]which is the correct way to place the dependencies?
is this correct for amarok?
Depends: kdelibs4, (>= ), libkdepim1 (>= 4 )...[/QUOTE]
 Depends: package (>= version). another-package (>= version), last-package (>= version)

:)

---

### Post by pailhead on 2005-08-07
What is involved with creating a 64bit deb for ndiswrapper?  I'm looking at the debian directory and there is a control.module, control.source, and control.utils.  There is no control file but those there. What is to be done with the those?  Do I edit those the same way I would just edit the plain control file?

And can I create a 64bit module from the 386 based sources?

Thanks...

---

### Post by Tamir on 2005-08-07
[QUOTE=pailhead]What is involved with creating a 64bit deb for ndiswrapper?  I'm looking at the debian directory and there is a control.module, control.source, and control.utils.  There is no control file but those there. What is to be done with the those?  Do I edit those the same way I would just edit the plain control file?

And can I create a 64bit module from the 386 based sources?

Thanks...[/QUOTE]
 I think you should paste all those templates in one file and call it control (I think!).

Or You could instead
```

apt-get source ndiswrapper-source

```

---

### Post by pailhead on 2005-08-07
[QUOTE=Tamir]I think you should paste all those templates in one file and call it control (I think!).

Or You could instead
```

apt-get source ndiswrapper-source

```[/QUOTE]
 Where does the source reside when I do an apt-get source?  I have never grabbed source that way, so I'm not too familiar with it.

---

### Post by Tamir on 2005-08-07
It is saving 3 files in your in the directory you already in (.dsc, .orig.tar.gz, .diff), and the it is extracting those file to a directory (dpkg-source -x *.dsc)

---

### Post by pailhead on 2005-08-07
ok so am I allowed since it's already got a maintainer to create the deb for the repo?

---

### Post by xbaez on 2005-08-07
There is one problem with your script
check at this:

Package `libmusicbrainz4-dev,' is not installed and no info is available.

For some files, it inserts the comma right after the end of the file, and then I can't get the version of it

---

### Post by Tamir on 2005-08-08
[QUOTE=pailhead]ok so am I allowed since it's already got a maintainer to create the deb for the repo?[/QUOTE]
 Yes but add your name only in file "debian/changelog", not in control or something else :).

---

### Post by kb_ganesh on 2005-09-09
in the final step (dpkg-buildpackage -rfakeroot), i get..

```
root@njiggs:/home/normal/dcdeb/dclib-0.3.7 # dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is dclib
dpkg-buildpackage: source version is 0.3.7-0ubuntu1
dpkg-buildpackage: source maintainer is K.B.Ganesh <kb_ganesh@iitm.ac.in>
dpkg-buildpackage: host architecture is amd64
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/normal/dcdeb/dclib-0.3.7'
Making distclean in dclib
make[2]: Entering directory `/home/normal/dcdeb/dclib-0.3.7/dclib'
Making distclean in hash
make[3]: Entering directory `/home/normal/dcdeb/dclib-0.3.7/dclib/hash'
rm -f *.bchecktest.cc *.bchecktest.cc.class a.out
rm -f libhash_la.all_cpp.cpp
rm -rf .libs _libs
test -z "libhash.la" || rm -f libhash.la
rm -f "./so_locations"
rm -f *.o core *.core
rm -f *.lo
rm -f *.tab.c
rm -rf ./.deps
rm -f Makefile
rm -f libtool
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
make[3]: Leaving directory `/home/normal/dcdeb/dclib-0.3.7/dclib/hash'
Making distclean in core
make[3]: Entering directory `/home/normal/dcdeb/dclib-0.3.7/dclib/core'
rm -f *.bchecktest.cc *.bchecktest.cc.class a.out
rm -f libcore_la.all_cpp.cpp
rm -rf .libs _libs
test -z "libcore.la" || rm -f libcore.la
rm -f "./so_locations"
rm -f *.o core *.core
rm -f *.lo
rm -f *.tab.c
rm -rf ./.deps
rm -f Makefile
rm -f libtool
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
make[3]: Leaving directory `/home/normal/dcdeb/dclib-0.3.7/dclib/core'
Making distclean in .
make[3]: Entering directory `/home/normal/dcdeb/dclib-0.3.7/dclib'
rm -f *.bchecktest.cc *.bchecktest.cc.class a.out
rm -f libdc_la.all_cpp.cpp
test -z "libdc.la" || rm -f libdc.la
rm -f "./so_locations"
rm -rf .libs _libs
rm -f *.o core *.core
rm: cannot remove `core': Is a directory
make[3]: [mostlyclean-compile] Error 1 (ignored)
rm -f *.lo
rm -f *.tab.c
rm -rf ./.deps
rm -f Makefile
rm -f libtool
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
make[3]: Leaving directory `/home/normal/dcdeb/dclib-0.3.7/dclib'
make[2]: Leaving directory `/home/normal/dcdeb/dclib-0.3.7/dclib'
Making distclean in .
make[2]: Entering directory `/home/normal/dcdeb/dclib-0.3.7'
rm -f *.bchecktest.cc *.bchecktest.cc.class a.out
rm -rf .libs _libs
rm -f *.lo
rm -f Makefile dclib.spec dclib.lsm dclib.pc
rm -f config.h stamp-h1
rm -f libtool
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
make[2]: Leaving directory `/home/normal/dcdeb/dclib-0.3.7'
rm -f config.status config.cache config.log configure.lineno
make[1]: Leaving directory `/home/normal/dcdeb/dclib-0.3.7'
dh_clean
 dpkg-source -b dclib-0.3.7
dpkg-source: building dclib using existing dclib_0.3.7.orig.tar.gz

gunzip: stdin: not in gzip format
dpkg-source: failure: gzip gave error exit status 1
```

wheres the problem?

---

### Post by Corbelius on 2005-09-09
It's better if the source are in .tar.gz not .tar.bz2 ;)

---

### Post by xbaez on 2005-09-10
How can I make a .deb file that's compatible with Ubuntu?

I will like to make a .deb file called:
amarok%2_1.3

the version should be
amarok
version
2:1_3

---

### Post by zarathustra on 2005-09-10
I decided to have a crack at making a package to see if I could help out, but the script you've made to list dependencies doesn't seem to be working for me:

> nick@kitsune:~/downloads/k3b/k3b-0.12.4/debian$ sh ../script
strace: ./configure: command not found


I've cutted and pasted the commands and made the file and there is a configure file, so what am I doing wrong?

---

### Post by kb_ganesh on 2005-09-10
[QUOTE=zarathustra]I decided to have a crack at making a package to see if I could help out, but the script you've made to list dependencies doesn't seem to be working for me:



I've cutted and pasted the commands and made the file and there is a configure file, so what am I doing wrong?[/QUOTE]
 try changing to the k3b-0.12.3 and running "sh ./script"..i too got the same error but this solved my problem

---

### Post by zarathustra on 2005-09-10
They released a new package due to a compile bug, but I've tried 0.12.4a and it still doesn't work! Shall try 0.12.3.

---

### Post by zarathustra on 2005-09-10
Doesn't work for 0.12.3 either...

---

### Post by markuman on 2005-09-20
there is no .deb

```

 dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is xfce4taskmanager
dpkg-buildpackage: source version is 0.3.1-1
dpkg-buildpackage: source changed by Markus Bergholz <markuman@gmail.com>
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Gehe in Verzeichnis »/home/markuman/Desktop/xfce4taskmanager-0.3.1«
make[1]: *** Keine Regel, um »distclean« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis »/home/markuman/Desktop/xfce4taskmanager-0.3.1«
make: [clean] Fehler 2 (ignoriert)
cp -f /usr/share/misc/config.sub config.sub
cp -f /usr/share/misc/config.guess config.guess
dh_clean
 dpkg-source -b xfce4taskmanager-0.3.1
dpkg-source: building xfce4taskmanager using existing xfce4taskmanager_0.3.1.orig.tar.gz
dpkg-source: building xfce4taskmanager in xfce4taskmanager_0.3.1-1.diff.gz
dpkg-source: cannot represent change to backup-092020051417-pre-xfcetaskmanager.tgz: binary file contents changed
dpkg-source: cannot represent change to backup-092020051420-pre-xfce4-taskmanager-0.3.1.tgz: binary file contents changed
dpkg-source: building xfce4taskmanager in xfce4taskmanager_0.3.1-1.dsc
dpkg-source: unrepresentable changes to source

```

wtf? where is the mistake?

###EDIT###

with fakeroot debian/rules binary it seems to work...

---

### Post by markuman on 2005-09-20
the debs i made are alway realy short - only a few kbs....

```

dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)

```

why? help!

---

### Post by Corbelius on 2005-09-21
[QUOTE=markuman]the debs i made are alway realy short - only a few kbs....

```

dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)

```

why? help![/QUOTE]

Control the ./configure output, or try to compile the source in the normal mode, ./configure, make and now use checkinstall to create a deb package: [https://wiki.ubuntu.com/CheckInstall?highlight=%28checkinstall%29](https://wiki.ubuntu.com/CheckInstall?highlight=%28checkinstall%29)

---

### Post by kodox on 2005-09-30
anyone build .deb with php+mysql 
i want to buid my web application like phpmyadminXXXXX.deb howto to that ?
pls guide me......

thx

---

### Post by agem on 2005-10-27
[QUOTE=zarathustra]I decided to have a crack at making a package to see if I could help out, but the script you've made to list dependencies doesn't seem to be working for me:

```
 nick@kitsune:~/downloads/k3b/k3b-0.12.4/debian$ sh ../script
 strace: ./configure: command not found
```

I've cutted and pasted the commands and made the file and there is a configure file, so what am I doing wrong?[/QUOTE]

Try this :
 
```
chmod +x script
```

fixed the problem for me.

---

### Post by Efwis on 2005-10-30
> first thing you should check is: does myproject-1.2 have a configure file?
if it doesn't you should make it, but we will not talk about it in this guide


can anyone point me to a howto on making the config file?
When I do a google on it there really is no direct answer that I can find.

---

### Post by wantilles on 2005-11-07
1. The script to find the dependencies cannot be run from the debian directory. If it is run from there, it says it cannot find the "configure" file. It must be run from the "my-project-1.2" directory (the parent directory of the "debian" directory).

2. The script if run from the parent directory of the "debian" directory, it does produce a lot of output.

3. Can I redirect this output to a text file of my choice using ">>"?

4. I was trying to make a package that had about six dozen occurences of the string "-dev" in that output. Is there an easy way to find all these and put them in a single line of text in a text file?

---

### Post by ubuntu_demon on 2005-11-09
Is this only for AMD64 ?

Either way it should be moved to howto section but the question is whether AMD64 should be in the title or not.

(haven't read the thread just modding now)

---

### Post by kkass on 2005-11-15
First of all I have to say this is a very good HOWTO.  I have used it to successfully create a deb package, but I am having issues with the permissions.

I am using Kubuntu on some build systems, and I am recompiling sudo without the '--with-secure-path' option.  I want to maintain a package history on my systems, and I will also need to install the modified build on some other machines.

As I said, it seems to build properly, however it does not install with the correct permissions.  (/usr/bin/sudo has -wrxw-xw-x instead of ---s--x--x.)  I can see in the build output where it claims to install the file with the correct permissions.

```

/bin/sh ./install-sh -c -O 0 -G 0 -M 4111 -s sudo /home/username/package/sudo-1.6.8p12/debian/sudo/usr/bin/sudo

```

However, when I check the file 'debian/sudo/usr/bin/sudo' the permissions are wrong.  Additionally, when I run the command 'dpkg-deb -c <debfile>.deb' it displays the wrong permissions as well.

Another puzzling thing is the deb file says sudo is a link to sudoedit.

```

hrwxr-xr-x root/root         0 2005-11-15 00:03:45 ./usr/bin/sudo link to ./usr/bin/sudoedit

```

When the build says sudoedit should be a link to sudo.

```

ln /home/username/package/sudo-1.6.8p12/debian/sudo/usr/bin/sudo /home/username/package/sudo-1.6.8p12/debian/sudo/usr/bin/sudoedit

```

---

### Post by alynx on 2006-02-22
i get a strange error when running the : dhmake -e "mail address" -f "filename"

Source file is a bz2 but bzip2 or gzip not available at /usr/bin/dh_make line 409, <STDIN> line 2.

and I have installed bzip2 

can someone please help me?

Im making a deb package of a configured and patched wine that runs world of warcraft smooth

---

### Post by alynx on 2006-02-23
maybe i should make that tar.bz instead of tar.bz2 ?? :confused:

---

### Post by hoowe on 2006-02-23
[QUOTE=alynx]i get a strange error when running the : dhmake -e "mail address" -f "filename"

Source file is a bz2 but bzip2 or gzip not available at /usr/bin/dh_make line 409, <STDIN> line 2.

and I have installed bzip2 

can someone please help me?

Im making a deb package of a configured and patched wine that runs world of warcraft smooth[/QUOTE]


There are 2 errors, first look in /usr/bin/dh_make edit it with yor favorite editor on line 409. The path to gzip sais /usr/bin/gizp but should be /usr/bin/gzip. :) But there is no /usr/bin/gzip so you can either change to /bin/gzip or do *ln -s /bin/gzip /usr/bin/gzip*.

My 2 cents...

---

### Post by alynx on 2006-02-24
thanks a million hoowe , it worked :) \\:D/ \\:D/ 

i am so happy now .  . . . .

---

### Post by Mustard on 2006-03-24
Is there a Breezy Badger version of this HOW TO?  I'm just curious, as I wonder how many people would still be looking through the Hoary Hedgehog section of the forum for tips and tricks.

---

### Post by dudus on 2006-04-10
just have to say thanx for this ;)

---

### Post by errr on 2006-04-10
Im trying to make a deb of an app with no configure script, and nothing to compile.. Its pretty much just a python module. All it has is a setup.py file. Im not sure where to get started on this, can someone give me a hand?

[http://fluxstyle.berlios.de/](http://fluxstyle.berlios.de/)  this is what I want to make a package of. 

Thanks.

---

### Post by kkass on 2006-04-13
This thread was a very good rescource for me when I first started making Debian packages.  If you need more information than that, I can reccomend a book to read that has a very informative chapter on the whole process.

Debian GNU/Linux 3.1 Bible  ISBN 0-7645-7644-5

It is available from Amazon or any large Bookstore.

Another suggestion to help you learn to make Debian packages is to look at existing packages.      Lets say I wanted to repackage python for some reason.  A good place to start is to download the python source from APT.

```
fakeroot apt-get source python
```

*If you are not familiar with fakeroot, it is a substitution for sudo in some cases.  It makes the system think you are root, without actually giving you root access.  It works here because apt-get wants you to be root , but you do not actually need to be root to download the source.  If you used fakeroot to install something it would not work, because you really need to be root to install.  If you do not have this, install it with apt-get.*

After apt-get is finished, you should have a new directory called python2.4-2.4.2.  This is basically the same source you would downlad from the python website.  The difference that is important to you is python2.4-2.4.2/debian.  This directory holds all the information that will eventually be used to make python into a debian package.

I am not going to go into much more detail here.  You can use some of the information previously mentioned in this thread, or the book I mentioned.

After you have made any changes to the python source, run the following commands.

```

sudo apt-get build-dep python
dpkg-buildpackage -rfakeroot -uc -us

```

The first line will have apt-get install any dependencies you require to build python.  The second line will build the python source into debian packages.

I hope this helps.  It really only touches the surface.

---

### Post by dlai on 2006-05-15
I tried compiling xawtv-cvs to a deb package... but it is not working. I managed to make the deb without errors but it does not install anything!
Can anybody help me?

---

### Post by sas on 2006-06-22
[QUOTE=errr]Im trying to make a deb of an app with no configure script, and nothing to compile.. Its pretty much just a python module. All it has is a setup.py file. Im not sure where to get started on this, can someone give me a hand?

[http://fluxstyle.berlios.de/](http://fluxstyle.berlios.de/)  this is what I want to make a package of. 

Thanks.[/QUOTE]

You need to run the setup.py file inside debian rules.

Try getting the gaussum source package for an example

[QUOTE=kkass]
```
fakeroot apt-get source python
```

*If you are not familiar with fakeroot, it is a substitution for sudo in some cases.  It makes the system think you are root, without actually giving you root access.  It works here because apt-get wants you to be root , but you do not actually need to be root to download the source.  If you used fakeroot to install something it would not work, because you really need to be root to install.  If you do not have this, install it with apt-get.*

[/QUOTE]

apt-get source does not require you to use sudo or be root (and if you were it'd mess up permissions anyway)

---

### Post by tribaal on 2006-07-07
Hoi all

First of all sorry for the thread necromancy, but I think this wuestion belongs here more than anywhere else:

How do you make a .deb package from a web application? Like someone already asked, like the phpmyadmin package (only php files that require php4/5 and mysql 4/5)? 
I would like to repackage the egroupware groupware application since the version available in the repos depends on php4 and mysql 4, both of which are deprecated on the Ubuntu server LAMP install (it comes with php5 and mysql5)...

Any thoughts? I tried to look around but cannot find anything approaching...

Thanks a lot

- trib'

---

### Post by kkass on 2006-07-07
Try to download the source packages for what you want to build and experiment with its dependencies.  You may be able to get it to build from the new stuff.

```
apt-get source egroupware
```

---

### Post by sas on 2006-07-08
The file you want to mess around with for dependancies is debian/control

See the packaging guide that comes with the system for tutorials on packaging.

---

### Post by blasco51 on 2006-08-08
I'm trying to build a package for the CUPS driver of my Epson Printer.
Epson distributes only rpm amd tarfile. I'm building this package starting from the tarfile.
But I get some errors near the end of configure. What can I do?
```
blasco@yoga:/usr/local/src/pips-sc67-2.6.3$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is pips-sc67
dpkg-buildpackage: source version is 2.6.3-1ubuntu1
dpkg-buildpackage: source changed by Antonio-Blasco Bonito <blasco.bonito@gmail.com>
dpkg-buildpackage: host architecture amd64
dpkg-checkbuilddeps: Unmet build dependencies: autotools-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
blasco@yoga:/usr/local/src/pips-sc67-2.6.3$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is pips-sc67
dpkg-buildpackage: source version is 2.6.3-1ubuntu1
dpkg-buildpackage: source changed by Antonio-Blasco Bonito <blasco.bonito@gmail.com>
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/usr/local/src/pips-sc67-2.6.3'
Making distclean in .
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3'
rm -f config.h
rm -f TAGS ID
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3'
Making distclean in pixmaps
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/pixmaps'
rm -f TAGS ID
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/pixmaps'
Making distclean in doc
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/doc'
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/doc'
Making distclean in redhat
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/redhat'
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/redhat'
Making distclean in setup
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/setup'
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/setup'
Making distclean in ppd
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/ppd'
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/ppd'
Making distclean in po
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/po'
rm -f core core.* *.pox pips-sc67.po *.new.po
rm -fr *.o
rm -f Makefile Makefile.in POTFILES *.mo
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/po'
Making distclean in lib
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/lib'
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/lib'
Making distclean in layout_script
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/layout_script'
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/layout_script'
Making distclean in intl
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/intl'
rm -f *.a *.la *.o *.lo core core.*
rm -f libintl.h charset.alias ref-add.sed ref-del.sed
rm -f -r .libs _libs
rm -f Makefile ID TAGS
if test "pips-sc67" = gettext; then \
          rm -f ChangeLog.inst VERSION; \
        else \
          : ; \
        fi
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/intl'
Making distclean in freset
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/freset'
rm -f *.tab.c
rm -f TAGS ID
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
test -z "freset" || rm -f freset
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.o
rm -f *.lo
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/freset'
Making distclean in ekpstm
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/ekpstm'
rm -f *.tab.c
rm -f TAGS ID
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
test -z "ekpstm" || rm -f ekpstm
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.o
rm -f *.lo
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/ekpstm'
Making distclean in ekpnavi
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/ekpnavi'
rm -f *.tab.c
rm -f TAGS ID
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
test -z "ekpnavi" || rm -f ekpnavi
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.o
rm -f *.lo
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/ekpnavi'
Making distclean in ekpd
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/ekpd'
Making distclean in .
make[3]: Entering directory `/usr/local/src/pips-sc67-2.6.3/ekpd'
rm -f *.tab.c
rm -f TAGS ID
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
test -z "ekpd" || rm -f ekpd
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.o
rm -f *.lo
rm -f libtool
make[3]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/ekpd'
Making distclean in rc
make[3]: Entering directory `/usr/local/src/pips-sc67-2.6.3/ekpd/rc'
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
rm -f libtool
make[3]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/ekpd/rc'
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/ekpd'
Making distclean in dtrfilter
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/dtrfilter'
rm -f *.tab.c
rm -f TAGS ID
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
test -z "dtrfilter" || rm -f dtrfilter
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.o
rm -f *.lo
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/dtrfilter'
Making distclean in src
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/src'
rm -f *.tab.c
rm -f TAGS ID
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
test -z "libcutils.la" || rm -f libcutils.la
rm -rf .libs _libs
test -z "pips-sc67" || rm -f pips-sc67
test -z "ekplp" || rm -f ekplp
test -z "rastertopips pipstoprinter" || rm -f rastertopips pipstoprinter
rm -f *.o core *.core
rm -f *.o
rm -f *.lo
rm -f ./filter-sc67
rm -f libtool
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/src'
Making distclean in libltdl
make[2]: Entering directory `/usr/local/src/pips-sc67-2.6.3/libltdl'
rm -f config.h
rm -f *.tab.c
rm -f TAGS ID
rm -f Makefile
rm -f config.cache config.log stamp-h stamp-h[0-9]*
test -z "" || rm -f
test -z "libltdlc.la" || rm -f libltdlc.la
rm -rf .libs _libs
test -z "libltdl.la libltdlc.la" || rm -f libltdl.la libltdlc.la
rm -f *.o core *.core
rm -f *.o
rm -f *.lo
rm -f libtool
rm -f config.status
make[2]: Leaving directory `/usr/local/src/pips-sc67-2.6.3/libltdl'
rm -f config.status
make[1]: Leaving directory `/usr/local/src/pips-sc67-2.6.3'
cp -f /usr/share/misc/config.sub config.sub
cp -f /usr/share/misc/config.guess config.guess
dh_clean
 dpkg-source -b pips-sc67-2.6.3
dpkg-source: building pips-sc67 using existing pips-sc67_2.6.3.orig.tar.gz
dpkg-source: building pips-sc67 in pips-sc67_2.6.3-1ubuntu1.diff.gz
dpkg-source: building pips-sc67 in pips-sc67_2.6.3-1ubuntu1.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
CFLAGS="-Wall -g -O2 -Wl,-z,defs" ./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for x86_64-linux-gnu-gcc... x86_64-linux-gnu-gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether x86_64-linux-gnu-gcc accepts -g... yes
checking for x86_64-linux-gnu-gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... nm
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... file_magic ELF [0-9][0-9]*-bit [LM]SB (shared object|dynamic lib )
checking command to parse nm output... ok
checking how to run the C preprocessor... x86_64-linux-gnu-gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for x86_64-linux-gnu-file... no
checking for file... /usr/bin/file
checking for x86_64-linux-gnu-ranlib... no
checking for ranlib... ranlib
checking for x86_64-linux-gnu-strip... no
checking for strip... strip
checking for objdir... .libs
checking for x86_64-linux-gnu-gcc option to produce PIC... -fPIC
checking if x86_64-linux-gnu-gcc PIC flag -fPIC works... yes
checking if x86_64-linux-gnu-gcc static flag -static works... yes
checking if x86_64-linux-gnu-gcc supports -c -o file.o... no
checking if we can lock with hard links... yes
checking if x86_64-linux-gnu-gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for cups-config... yes
checking for dlopen in -ldl... yes
checking for pthread_create in -lpthread... yes
checking for gtk-config... no
checking for GTK - version >= 0.99.7... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for strerror in -lcposix... no
checking for x86_64-linux-gnu-gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for off_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for pid_t... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... (cached) yes
checking for working vfork... (cached) yes
checking whether x86_64-linux-gnu-gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for working malloc... yes
checking for working memcmp... yes
checking return type of signal handlers... void
checking for alarm... yes
checking for gettimeofday... yes
checking for memset... yes
checking for mkfifo... yes
checking for select... yes
checking for socket... yes
checking for strcspn... yes
checking for strstr... yes
checking for ranlib... (cached) ranlib
checking for inline... inline
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for limits.h... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for feof_unlocked... yes
checking for fgets_unlocked... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for stpcpy... yes
checking for strchr... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for iconv... yes
checking for iconv declaration...
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for GNU gettext in libc... yes
checking for dcgettext... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for bison... bison
checking version of bison... 2.1, ok
checking for catalogs to be installed...  de en es fr it ja nl pt ko zh zh_TW
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating dtrfilter/Makefile
config.status: creating ekpd/Makefile
config.status: creating ekpd/rc/Makefile
config.status: creating ekpnavi/Makefile
config.status: creating ekpstm/Makefile
config.status: creating freset/Makefile
config.status: creating intl/Makefile
config.status: creating layout_script/Makefile
config.status: creating lib/Makefile
config.status: creating pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating ppd/Makefile
config.status: creating setup/Makefile
config.status: creating redhat/Makefile
config.status: creating doc/Makefile
config.status: creating config.h
config.status: executing default-1 commands
config.status: executing default-2 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
configure: configuring in libltdl
configure: running /bin/sh './configure' --prefix=/usr  '--host=x86_64-linux-gnu' '--build=x86_64-linux-gnu' '--prefix=/usr' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' 'CFLAGS=-Wall -g -O2 -Wl,-z,defs' 'build_alias=x86_64-linux-gnu' 'host_alias=x86_64-linux-gnu' --enable-ltdl-convenience --cache-file=/dev/null --srcdir=.
configure: warning: CFLAGS=-Wall -g -O2 -Wl,-z,defs: invalid host type
configure: warning: build_alias=x86_64-linux-gnu: invalid host type
configure: error: can only configure for one host and one target at a time
configure: error: /bin/sh './configure' failed for libltdl
make: *** [config.status] Error 1

```

---

### Post by pazzz on 2006-08-17
Tamir, nice work! 10x ;)

---

### Post by ym1983 on 2006-08-29
[FONT="Arial"][SIZE="4"]Hi.I am trying tp create a deb.This is what I get after runing :

dpkg-buildpackage -rfakeroot -uc -us 

---------------------------------------------

dpkg-buildpackage: source package is nbx-base2
dpkg-buildpackage: source version is 1.0-1
dpkg-buildpackage: source changed by ym1983[SIZE="3"][/SIZE] <u0ym2@localhost>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/home/u0ym2/Desktop/MyDocuments/nbx-base2-1.0'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/home/u0ym2/Desktop/MyDocuments/nbx-base2-1.0'
make: [clean] Error 2 (ignored)
dh_clean
        rm -f debian/nbx-base2.substvars
        rm -f debian/nbx-base2.*.debhelper
        rm -rf debian/nbx-base2
        rm -f debian/files
        find .  \( \( -type f -a \
                \( -name '#*#' -o -name '.*~' -o -name '*~' -o -name DEADJOE \
                 -o -name '*.orig' -o -name '*.rej' -o -name '*.bak' \
                 -o -name '.*.orig' -o -name .*.rej -o -name '.SUMS' \
                 -o -name TAGS -o -name core -o \( -path '*/.deps/*' -a -name '*.P' \) \
                \) -exec rm -f {} \; \) -o \
                \( -type d -a -name autom4te.cache -prune -exec rm -rf {} \; \) \)
 dpkg-source -b nbx-base2-1.0
dpkg-source: building nbx-base2 in nbx-base2_1.0-1.tar.gz
dpkg-source: building nbx-base2 in nbx-base2_1.0-1.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: Entering directory `/home/u0ym2/Desktop/MyDocuments/nbx-base2-1.0'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/u0ym2/Desktop/MyDocuments/nbx-base2-1.0'
make: *** [build-stamp] Error 2


The tar.gz and the dsc file do get created but in 1 directory above.Can someone help me please .[/SIZE][/FONT][SIZE="4"][/SIZE][SIZE="2"][SIZE="3"][/SIZE][/SIZE]

---

### Post by Loïc2 on 2006-09-24
Thanks for the howto.

I'm trying to build a package from sources I downloaded on the program's site (qGo).

However, when I do  dpkg-buildpackage -rfakeroot
I get the following error :

```
dpkg-buildpackage: source package is qgo
dpkg-buildpackage: source version is 1.5.1-1ubuntu1
dpkg-buildpackage: source changed by Loïc Martin <loic.martin3@gmail.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: entrant dans le répertoire « /home/t3g/packages/qgo/qgo-1.5.1 »
cd . && /bin/sh /home/t3g/packages/qgo/qgo-1.5.1/admin/missing --run aclocal-1.6
/home/t3g/packages/qgo/qgo-1.5.1/admin/missing: line 46: aclocal-1.6 : commande introuvable
WARNING: `aclocal-1.6' is needed, and you do not seem to have it handy on your
         system.  You might have modified some files without having the
         proper tools for further handling them.  Check the `README' file,
         it often tells you about the needed prerequirements for installing
         this package.  You may also peek at any GNU archive site, in case
         some other package would contain this missing `aclocal-1.6' program.
make[1]: *** [aclocal.m4] Erreur 1
make[1]: quittant le répertoire « /home/t3g/packages/qgo/qgo-1.5.1 »
make: [clean] Erreur 2 (ignorée)
dh_clean
 dpkg-source -b qgo-1.5.1
dpkg-source: building qgo using existing qgo_1.5.1.orig.tar.gz
dpkg-source: building qgo in qgo_1.5.1-1ubuntu1.diff.gz
dpkg-source: warning: ignoring deletion of file admin/configure.in.min~
dpkg-source: warning: ignoring deletion of file configure.in~
dpkg-source: warning: ignoring deletion of file configure~
dpkg-source: warning: ignoring deletion of file ChangeLog~
dpkg-source: warning: ignoring deletion of file qgo.spec~
dpkg-source: building qgo in qgo_1.5.1-1ubuntu1.dsc
 debian/rules build
dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: entrant dans le répertoire « /home/t3g/packages/qgo/qgo-1.5.1 »
cd . && /bin/sh /home/t3g/packages/qgo/qgo-1.5.1/admin/missing --run aclocal-1.6
/home/t3g/packages/qgo/qgo-1.5.1/admin/missing: line 46: aclocal-1.6 : commande introuvable
WARNING: `aclocal-1.6' is needed, and you do not seem to have it handy on your
         system.  You might have modified some files without having the
         proper tools for further handling them.  Check the `README' file,
         it often tells you about the needed prerequirements for installing
         this package.  You may also peek at any GNU archive site, in case
         some other package would contain this missing `aclocal-1.6' program.
make[1]: *** [aclocal.m4] Erreur 1
make[1]: quittant le répertoire « /home/t3g/packages/qgo/qgo-1.5.1 »
make: *** [build-stamp] Erreur 2

```

I've looked in the configure file, but with no avail. What am I missing?

---

### Post by kkass on 2006-09-26
Your build seems to be looking for aclocal-1.6, which you probably do not have.  (My Breezy and Dapper machines both have aclocal-1.9).  There are a few things you can try.

1. Have apt-get install all the build dependencies.  This may not work if you downloaded the source directly.
```
sudo apt-get build-deb qgo
```

2. Manually change all occurrences of 'aclocal-1.6' to 'aclocal-1.9'.  (This could cause funny things I have not tried it before.)  Sed may work to make it easy for you.

3. You can try creating a symlink to another version of aclocal.  (Not sure if this is a good idea either.)
```
sudo ln -s /usr/bin/aclocal-1.9 /usr/bin/aclocal-1.6
```

---

### Post by runelord99 on 2006-11-26
great how to 
does anyone know what the required changes to debian/rules are if the source code that i'm creating a .deb for has these commands for compiling from source:  
(they are in the order that they need to be issued in)
./configure
make depend
make 
make install
i'm assuming that we are still using dh-make with the -s command here
thanks

---

### Post by rkrishc on 2006-12-31
> **Tamir said:**
> Hi,
Thanks to [Debian's guide](http://www.debian.org/doc/maint-guide/).
lets start.
```

       strace -f -o /tmp/log ./configure
       # or make instead of ./configure, if the package doesn't use autoconf
       for x in `dpkg -S $(grep open /tmp/log|\
                           perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
                           grep "^/"| sort | uniq|\
                           grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
                           cut -f1 -d":"| sort | uniq`; \
             do \
               echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2 -d":"` "), "; \
             done

```

The above does not work correctly, because dpgk search sometimes returns a comma separated list.  I have small fix for that below, and also to take into account any epoch in the version

```

       strace -f -o /tmp/log ./configure
       # or make instead of ./configure, if the package doesn't use autoconf
       for x in `dpkg -S $(grep open /tmp/log|\
                           perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
                           grep "^/"| sort | uniq|\
                           grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
                           cut -f1 -d":" | tr "," "\n" | tr -d " "| sort | uniq`; \
             do \
               echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2- -d":"` "), "; \
             done

```

However, this returns a list of dependenceis that does not look right for what I'm trying to make a .deb for - OFX 0.8.2.  Here is a partial list of dependencies
```

libssl-dev (>= 0.9.8b-2ubuntu2 ), libstdc++6-4.1-dev (>= 4.1.1-13ubuntu5 ), libtasn1-3-dev (>= 0.3.5-1 ), libvorbis-dev (>= 1.1.2-1ubuntu1 ), libx11-dev (>= 2 ), libxau-dev (>= 1 ), libxcursor-dev (>= 1.1.7-0ubuntu1 ), libxdmcp-dev (>= 1 ), libxext-dev (>= 2 ), libxfixes-dev (>= 1 ), libxft-dev (>= 2.1.10-1ubuntu1 ), libxi-dev (>= 2 ), libxinerama-dev (>= 2 ), libxml2-dev (>= 2.6.26.dfsg-2ubuntu4 ), libxmu-dev (>= 2 ), libxrandr-dev (>= 2 ), libxrender-dev (>= 1 ), libxslt1-dev (>= 1.1.17-2build1 ), libxt-dev (>= 1 ), linux-libc-dev (>= 2.6.17.1-10.34 ), x11proto-core-dev (>= 7.0.7-1 ), x11proto-fixes-dev (>= 1 ), x11proto-input-dev (>= 1.3.2-3ubuntu1 ), x11proto-kb-dev (>= 1.0.3-0ubuntu1 )

```
I'm not sure if libofx does not depend on libxinerama-dev.  I'm not sure what I'm doing wrong.  Appreciate any help in this direction.

Thanks,
RK.

---

### Post by reacocard on 2007-02-04
Thanks for the guide, I've been wanting to learn how to do this. Is there any way to compile for multiple architectures at the same time? I'd like to get debs for i386, amd64 and powerpc all at the same time.

Also, if anyone has any debs built this way that they'd like to share with everyone, I can put them in my repository (see my sig). Just PM or e-mail me.

---

### Post by RAOF on 2007-02-05
> **reacocard said:**
> Thanks for the guide, I've been wanting to learn how to do this. Is there any way to compile for multiple architectures at the same time? I'd like to get debs for i386, amd64 and powerpc all at the same time.
...

You can, quite easily, with pbuilder.  As long as you actually can run that architecture.  So, my AMD64 system has a i386 pbuilder on it, so I can build i386 debs as well as AMD64 debs.

To get PPC you need to use a cross compiler, and I'm not sure how to get that happening.

---

### Post by reacocard on 2007-02-05
> **RAOF said:**
> You can, quite easily, with pbuilder.  As long as you actually can run that architecture.  So, my AMD64 system has a i386 pbuilder on it, so I can build i386 debs as well as AMD64 debs.

To get PPC you need to use a cross compiler, and I'm not sure how to get that happening.

Well, I don't have a 64-bit CPU or use pbuilder(tried it, couldn't get it to work), so that's out.  Thanks anyway.

---

### Post by eternalsword on 2007-04-05
Neither of the scripts provided here have listed any dependencies, which I am positive is wrong.  All the ./configure output is fine but there's no other output afterwards.  Any help would be appreciated.

Perhaps this is because I am using edgy.  Currently, there's a preinstalled script called dpkg-depcheck that works as such 

dpkg-depcheck ./configure

but it only lists the package names, not version requirements.

---

### Post by Yuske on 2007-09-20
> **Tamir said:**
> for full build of the package (build source, deb, clean...) run:
```

dpkg-buildpackage -rfakeroot

```

Instead if you have a big package, you can also build only the deb file with:
```

fake root debian/rules binary

```

I couldn't use "fake root debian/rules binary", but "fakeroot debian/rules binary" worked. any problem with this detail?

---

### Post by Yuske on 2007-09-20
> **rkrishc said:**
> The above does not work correctly, because dpgk search sometimes returns a comma separated list.  I have small fix for that below, and also to take into account any epoch in the version

```

       strace -f -o /tmp/log ./configure
       # or make instead of ./configure, if the package doesn't use autoconf
       for x in `dpkg -S $(grep open /tmp/log|\
                           perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
                           grep "^/"| sort | uniq|\
                           grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
                           cut -f1 -d":" | tr "," "\n" | tr -d " "| sort | uniq`; \
             do \
               echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2- -d":"` "), "; \
             done

```

However, this returns a list of dependenceis that does not look right for what I'm trying to make a .deb for - OFX 0.8.2.  Here is a partial list of dependencies
```

libssl-dev (>= 0.9.8b-2ubuntu2 ), libstdc++6-4.1-dev (>= 4.1.1-13ubuntu5 ), libtasn1-3-dev (>= 0.3.5-1 ), libvorbis-dev (>= 1.1.2-1ubuntu1 ), libx11-dev (>= 2 ), libxau-dev (>= 1 ), libxcursor-dev (>= 1.1.7-0ubuntu1 ), libxdmcp-dev (>= 1 ), libxext-dev (>= 2 ), libxfixes-dev (>= 1 ), libxft-dev (>= 2.1.10-1ubuntu1 ), libxi-dev (>= 2 ), libxinerama-dev (>= 2 ), libxml2-dev (>= 2.6.26.dfsg-2ubuntu4 ), libxmu-dev (>= 2 ), libxrandr-dev (>= 2 ), libxrender-dev (>= 1 ), libxslt1-dev (>= 1.1.17-2build1 ), libxt-dev (>= 1 ), linux-libc-dev (>= 2.6.17.1-10.34 ), x11proto-core-dev (>= 7.0.7-1 ), x11proto-fixes-dev (>= 1 ), x11proto-input-dev (>= 1.3.2-3ubuntu1 ), x11proto-kb-dev (>= 1.0.3-0ubuntu1 )

```
I'm not sure if libofx does not depend on libxinerama-dev.  I'm not sure what I'm doing wrong.  Appreciate any help in this direction.

Thanks,
RK.
your script returned exactly the same thing to me...

same output as the script Tamir posted

---

### Post by nikoPSK on 2007-10-28
ummm, when you say download your code or whatever. So I have this bzr here:

```
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
```

And I want to make a .deb out of it. Is there any way to do that? Sorry I don't understand much. And I might of missed this but can I add dependencies?

---

### Post by nikoPSK on 2007-11-04
okay.. Im further now. So I am at the part where you edit control and changelog.... I am making a .deb for awn-curves. In the control and changelog this was there:

Source: avant-window-navigator
Section: gnome
Priority: optional
Maintainer: Julien Lavergne <julien.lavergne@gmail.com>

pre done... Can I change that to

Source: avant-window-navigator-curves
Section: gnome
Priority: optional
Maintainer: ... <...@....com>?

Or is that the second line... thanks!

---

### Post by Devo66 on 2007-11-08
I have built a package from stock source into a deb file, but when I install that deb it doesn't create any items in the menu or icons on the desktop.  How can I make it do that?

---

### Post by darkmaster on 2007-11-26
Hello everyone, I would like to create a deb package for a number of files (gtk themes and icons) that are not a binary and therefore cannot be compiled. I tryed to follow the guide using single binary as the choice on the thirst commands, but the final command doesn't work, it only created 4 files and not the deb file. 

How can I create very basic deb files for themes and icons? That is, for anything that doesn't need to be compiled???

---

### Post by reacocard on 2007-11-26
> **darkmaster said:**
> Hello everyone, I would like to create a deb package for a number of files (gtk themes and icons) that are not a binary and therefore cannot be compiled. I tryed to follow the guide using single binary as the choice on the thirst commands, but the final command doesn't work, it only created 4 files and not the deb file. 

How can I create very basic deb files for themes and icons? That is, for anything that doesn't need to be compiled???

Just write a quick Makefile for them that installs them to their proper locations and run the deb creator on that.

---

### Post by chrisccoulson on 2007-12-20
I'm having an issue with the script that gets the dependencies of the package. I've tried two source packages now (Pidgin and Gimpshop), and the list of dependencies looks wrong. In fact, the list of dependencies for Pidgin ended up being what looked like every package installed on my system. For Gimpshop, it isn't as bad, but still seems wrong. Here is some of the output:

```
binutils (>= 2.18-0ubuntu3 ), coreutils (>= 5.97-5.3ubuntu3 ), file (>= 4.21-1 ), gcc-3.4 (>= 3.4.6-6ubuntu2 ), gettext (>= 0.16.1-2ubuntu3 ), grep (>= 2.5.1.ds2-6build1 ), libacl1 (>= 2.2.42-1ubuntu1 ), libart-2.0-dev (>= 2.3.19-3 ), libatk1.0-0 (>= 1.20.0-0ubuntu1 ), libatk1.0-dev (>= 1.20.0-0ubuntu1 ), libattr1 (>= 1 ), libc6 (>= 2.6.1-1ubuntu10 ), libc6-dev (>= 2.6.1-1ubuntu10 ), libcairo2 (>= 1.4.10-1ubuntu4.4 ), libcairo2-dev (>= 1.4.10-1ubuntu4.4 ), libexpat1 (>= 1.95.8-4ubuntu1 ), libfontconfig1 (>= 2.4.2-1.2ubuntu4 ), libfontconfig1-dev (>= 2.4.2-1.2ubuntu4 ), libfreetype6 (>= 2.3.5-1ubuntu4 ), libfreetype6-dev (>= 2.3.5-1ubuntu4 ), libglib2.0-0 (>= 2.14.1-1ubuntu1 ), libglib2.0-dev (>= 2.14.1-1ubuntu1 ), libgtk2.0-0 (>= 2.12.0-1ubuntu3 ), libgtk2.0-dev (>= 2.12.0-1ubuntu3 ), Package `libgtkextra-x11-2.0-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgtkextra-x11-2.0-dev, (>= ), Package `libart-2.0-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libart-2.0-dev, (>= ), Package `libsexy-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libsexy-dev, (>= ), Package `libglib2.0-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libglib2.0-dev, (>= ), Package `libfreetype6-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libfreetype6-dev, (>= ), Package `librsvg2.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
librsvg2.0-cil, (>= ), Package `libopencdk8-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libopencdk8-dev, (>= ), Package `libxcursor-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxcursor-dev, (>= ), Package `libglade2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libglade2-dev, (>= ), Package `libxcomposite-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxcomposite-dev, (>= ), Package `libbonoboui2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libbonoboui2-dev, (>= ), Package `x11proto-xf86misc-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-xf86misc-dev, (>= ), Package `libgnutls-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgnutls-dev, (>= ), Package `libmono-cecil0.5-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libmono-cecil0.5-cil, (>= ), Package `libpcre3-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libpcre3-dev, (>= ), Package `xfonts-utils,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
xfonts-utils, (>= ), Package `libgnome2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgnome2-dev, (>= ), Package `libneon25,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libneon25, (>= ), Package `libgsl0,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgsl0, (>= ), Package `libbonobo2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libbonobo2-dev, (>= ), Package `f-spot,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
f-spot, (>= ), Package `libgnome-vfs2.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgnome-vfs2.0-cil, (>= ), Package `monodevelop,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
monodevelop, (>= ), Package `libbeagle-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libbeagle-dev, (>= ), Package `libesd0-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libesd0-dev, (>= ), Package `python-pygtksourceview,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
python-pygtksourceview, (>= ), Package `x11proto-composite-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-composite-dev, (>= ), Package `libgtop2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgtop2-dev, (>= ), Package `libglib2.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libglib2.0-cil, (>= ), Package `libxmu-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxmu-dev, (>= ), Package `libx11-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libx11-dev, (>= ), Package `xtrans-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
xtrans-dev, (>= ), Package `x11proto-damage-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-damage-dev, (>= ), Package `comerr-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
comerr-dev, (>= ), Package `gnome-screensaver,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
gnome-screensaver, (>= ), Package `gnome-system-tools,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
gnome-system-tools, (>= ), Package `xserver-xorg-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
xserver-xorg-dev, (>= ), Package `libnm-glib-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libnm-glib-dev, (>= ), Package `libgnomevfs2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgnomevfs2-dev, (>= ), Package `python-notify,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
python-notify, (>= ), Package `libxxf86vm-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxxf86vm-dev, (>= ), Package `python-gtkglext1,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
python-gtkglext1, (>= ), Package `libgtkhtml2.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgtkhtml2.0-cil, (>= ), Package `python-gst0.10,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
python-gst0.10, (>= ), Package `libmono-cairo1.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libmono-cairo1.0-cil, (>= ), Package `x11proto-core-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-core-dev, (>= ), Package `x11proto-resource-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-resource-dev, (>= ), Package `libssl-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libssl-dev, (>= ), Package `libxss-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxss-dev, (>= ), Package `libglade2.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libglade2.0-cil, (>= ), Package `libgconf2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgconf2-dev, (>= ), Package `libdbus-1-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libdbus-1-dev, (>= ), Package `libavahi-qt3-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libavahi-qt3-dev, (>= ), Package `libwnck-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libwnck-dev, (>= ), Package `libgecko2.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgecko2.0-cil, (>= ), Package `pkg-config,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
pkg-config, (>= ), Package `liblua50-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
liblua50-dev, (>= ), Package `libxml2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxml2-dev, (>= ), Package `gnome-utils,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
gnome-utils, (>= ), Package `xbitmaps,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
xbitmaps, (>= ), Package `libqt3-mt-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libqt3-mt-dev, (>= ), Package `libxau-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxau-dev, (>= ), Package `python-compizconfig,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
python-compizconfig, (>= ), Package `libgmime2.2-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgmime2.2-cil, (>= ), Package `libgstreamer-plugins-base0.10-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgstreamer-plugins-base0.10-dev, (>= ), Package `libnss3-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libnss3-dev, (>= ), Package `libhal-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libhal-dev, (>= ), Package `libopenexr-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libopenexr-dev, (>= ), Package `libhal-storage-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libhal-storage-dev, (>= ), Package `libpng12-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libpng12-dev, (>= ), Package `deskbar-applet,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
deskbar-applet, (>= ), Package `tomboy,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
tomboy, (>= ), Package `x11proto-record-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-record-dev, (>= ), Package `libavahi-glib-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libavahi-glib-dev, (>= ), Package `libdbus-glib-1-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libdbus-glib-1-dev, (>= ), Package `screem,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
screem, (>= ), Package `liblualib50-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
liblualib50-dev, (>= ), Package `compiz-fusion-plugins-main,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
compiz-fusion-plugins-main, (>= ), Package `monodoc-base,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
monodoc-base, (>= ), Package `libcompizconfig0-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libcompizconfig0-dev, (>= ), Package `x11proto-kb-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-kb-dev, (>= ), Package `libxres-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxres-dev, (>= ), Package `x11proto-xinerama-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-xinerama-dev, (>= ), Package `librsvg2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
librsvg2-dev, (>= ), Package `libxdamage-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxdamage-dev, (>= ), Package `libndesk-dbus-glib1.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libndesk-dbus-glib1.0-cil, (>= ), Package `libmono-addins0.2-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libmono-addins0.2-cil, (>= ), Package `libgtk2.0-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgtk2.0-dev, (>= ), Package `libgtkspell-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgtkspell-dev, (>= ), Package `libstartup-notification0-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libstartup-notification0-dev, (>= ), Package `x11proto-xf86vidmode-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-xf86vidmode-dev, (>= ), Package `x11proto-render-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-render-dev, (>= ), Package `gnome-mount,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
gnome-mount, (>= ), Package `gnome-pilot,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
gnome-pilot, (>= ), Package `libgnome-keyring-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgnome-keyring-dev, (>= ), Package `libxt-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxt-dev, (>= ), Package `libgdiplus,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgdiplus, (>= ), Package `libxft-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxft-dev, (>= ), Package `compiz-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
compiz-dev, (>= ), Package `x11proto-randr-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-randr-dev, (>= ), Package `libfontconfig1-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libfontconfig1-dev, (>= ), Package `libsm-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libsm-dev, (>= ), Package `libgnomecanvas2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgnomecanvas2-dev, (>= ), Package `libidn11-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libidn11-dev, (>= ), Package `libice-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libice-dev, (>= ), Package `libmono-addins-gui0.2-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libmono-addins-gui0.2-cil, (>= ), Package `x11proto-fixes-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-fixes-dev, (>= ), Package `libgnome-desktop-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgnome-desktop-dev, (>= ), Package `libtrackerclient-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libtrackerclient-dev, (>= ), Package `libselinux1-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libselinux1-dev, (>= ), Package `libcroco3-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libcroco3-dev, (>= ), Package `libxrandr-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxrandr-dev, (>= ), Package `network-manager-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
network-manager-dev, (>= ), Package `libmono-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libmono-dev, (>= ), Package `libxtst-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxtst-dev, (>= ), Package `x11proto-xext-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-xext-dev, (>= ), Package `libtasn1-3-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libtasn1-3-dev, (>= ), Package `libxi-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxi-dev, (>= ), Package `gnome-doc-utils,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
gnome-doc-utils, (>= ), Package `libgconf2.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgconf2.0-cil, (>= ), Package `libndesk-dbus1.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libndesk-dbus1.0-cil, (>= ), Package `libgsf-1-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgsf-1-dev, (>= ), Package `libxdmcp-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxdmcp-dev, (>= ), Package `libasound2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libasound2-dev, (>= ), Package `libpango1.0-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libpango1.0-dev, (>= ), Package `libgnome-window-settings-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgnome-window-settings-dev, (>= ), Package `libgail-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgail-dev, (>= ), Package `libart2.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libart2.0-cil, (>= ), Package `libidl-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libidl-dev, (>= ), Package `libxxf86misc-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxxf86misc-dev, (>= ), Package `libxfixes-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxfixes-dev, (>= ), Package `libdecoration0-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libdecoration0-dev, (>= ), Package `libxext-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxext-dev, (>= ), Package `liborbit2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
liborbit2-dev, (>= ), Package `libxslt1-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxslt1-dev, (>= ), Package `libgnome-menu-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgnome-menu-dev, (>= ), Package `x11proto-scrnsaver-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-scrnsaver-dev, (>= ), Package `libaudiofile-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libaudiofile-dev, (>= ), Package `libxrender-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxrender-dev, (>= ), Package `libcairo2-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libcairo2-dev, (>= ), Package `liblog4net1.2-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
liblog4net1.2-cil, (>= ), Package `eog,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
eog, (>= ), Package `libgtk2.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgtk2.0-cil, (>= ), Package `libavahi-client-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libavahi-client-dev, (>= ), Package `liblcms1-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
liblcms1-dev, (>= ), Package `libxinerama-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libxinerama-dev, (>= ), Package `libgnomeui-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgnomeui-dev, (>= ), Package `libnotify-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libnotify-dev, (>= ), Package `libnspr4-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libnspr4-dev, (>= ), Package `libgnome2.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgnome2.0-cil, (>= ), Package `libsepol1-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libsepol1-dev, (>= ), Package `libgstreamer0.10-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgstreamer0.10-dev, (>= ), Package `libatk1.0-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libatk1.0-dev, (>= ), Package `libgtksourceview2.0-cil,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libgtksourceview2.0-cil, (>= ), Package `x11proto-input-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
x11proto-input-dev, (>= ), Package `libnm-util-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libnm-util-dev, (>= ), Package `libvorbis-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libvorbis-dev, (>= ), Package `libogg-dev,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
libogg-dev, (>= ), Package `python-dbus,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
python-dbus, (>= ), libusb-dev (>= 2 ), libjpeg62-dev (>= 6b-14 ), libmagic1 (>= 4.21-1 ), libmng-dev (>= 1.0.9-1 ), libncurses5 (>= 5.6+20070716-1ubuntu3 ), libpango1.0-0 (>= 1.18.3-0ubuntu1 ), libpango1.0-dev (>= 1.18.3-0ubuntu1 ), libpng12-0 (>= 1.2.15~beta5-2ubuntu0.1 ), libpng12-dev (>= 1.2.15~beta5-2ubuntu0.1 ), librsvg2-dev (>= 2.18.2-1 ), libselinux1 (>= 2.0.15-2ubuntu1 ), libsepol1 (>= 2.0.3-1 ), libtiff4-dev (>= 3.8.2-7ubuntu2 ), libx11-6 (>= 2 ), libx11-dev (>= 2 ), libxau6 (>= 1 ), libxau-dev (>= 1 ), libxcomposite1 (>= 1 ), libxcomposite-dev (>= 1 ), libxcursor1 (>= 1 ), libxcursor-dev (>= 1 ), libxdamage1 (>= 1 ), libxdamage-dev (>= 1 ), libxdmcp6 (>= 1 ), libxdmcp-dev (>= 1 ), libxext6 (>= 2 ), libxext-dev (>= 2 ), libxfixes3 (>= 1 ), libxfixes-dev (>= 1 ), libxi6 (>= 2 ), libxi-dev (>= 2 ), libxinerama1 (>= 2 ), libxinerama-dev (>= 2 ), libxml-parser-perl (>= 2.34-4.3 ), libxmu-headers (>= 2 ), libxrandr2 (>= 2 ), libxrandr-dev (>= 2 ), libxrender1 (>= 1 ), libxrender-dev (>= 1 ), linux-libc-dev (>= 2.6.22-14.47 ), locales (>= 2.6.1-1 ), perl-base (>= 5.8.8-7ubuntu3.1 ), Package `shared-mime-info,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
shared-mime-info, (>= ), Package `compiz-bcop,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
compiz-bcop, (>= ), Package `chemical-mime-data,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
chemical-mime-data, (>= ), Package `gnome-mime-data,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
gnome-mime-data, (>= ), Package `gnome-icon-theme,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
gnome-icon-theme, (>= ), Package `pkg-config,' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
pkg-config, (>= ), iso-codes (>= 1.0a-1ubuntu1 ), x11proto-composite-dev (>= 1 ), x11proto-core-dev (>= 7.0.10-2 ), x11proto-damage-dev (>= 1 ), x11proto-fixes-dev (>= 1 ), x11proto-input-dev (>= 1.4.2-1 ), x11proto-kb-dev (>= 1.0.3-2ubuntu1 ), x11proto-randr-dev (>= 1.2.1-2 ), x11proto-render-dev (>= 2 ), x11proto-xext-dev (>= 7.0.2-5ubuntu1 ), x11proto-xinerama-dev (>= 1.1.2-4ubuntu1 ), xutils-dev (>= 1 ), zlib1g (>= 1 ), zlib1g-dev (>= 1 ), 
```

I can't believe it depends on f-spot, tracker, libncurses, libdecoration etc....

---

### Post by ChameleonDave on 2008-01-04
Thank you for this great guide!

I've just spent some time following it and putting together my first DEB.  I'm now learning how to make a repository to put it on (I just need to work out how to iron out the problems with "filesize mismatch", and then I'll have finished).

Type this code to add my repo (i386):

```
sudo echo "deb http://linux.pro-reason.info gutsy partner" >> /etc/apt/sources.list
```

---

### Post by SpookyET on 2008-04-08
Wow, that's complicated. It makes you appreciated how is it easy to make packages for pacman with just a [http://wiki.archlinux.org/index.php/PKGBUILD]("http://wiki.archlinux.org/index.php/PKGBUILD") and "makepkg".

---

### Post by Argonimion on 2008-05-12
hi there!
i had a few problems with this script, too

now this is my version:

```
#!/bin/sh

LOG="/tmp/$(basename $(pwd)).log"

FIRST=1

if test $# -ne 1
then
  echo "wrong parameter count" >&2
  exit 1
fi


case "$1" in
  dev)
    PATTERN="grep -e -dev"
    ;;
  nodev)
    PATTERN="grep -v -e -dev"
    ;;
  all)
    PATTERN="cat"
    ;;
  *)
    echo "illegal pattern" >&2
    exit 1
    ;;
esac

if test ! -s "$LOG"
then
  strace -f -o $LOG sh $(pwd)/configure
fi

for x in `dpkg -S $(grep open $LOG |\
  perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
  grep "^/"| sort | uniq|\
  grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
  cut -f1 -d":"| sort | uniq | $PATTERN` ; \
do \
  x=`echo $x | sed -e s/,//g`; \

  if test $FIRST -ne 1
  then
    echo -n ", "
  fi
  FIRST=0

  echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2 -d":"` ")"; \
done

echo ""
```

changes:
- there is no need to put it in the same dir as configure
- it calls configure just once
- you can specify the kind of packages
```
../script dev
``` outputs only -dev packages
```
../script nodev
``` outputs non -dev packages
```
../script all
``` outputs all packages
```
../script
``` outputs an error :P

I hope this will help someone

Anyway this is a great howto. thanks for that!
it works fine :D

---

### Post by soxs on 2008-05-19
Sorry, if interfere, but I am going to build wine 0.9.45 (with some patches) for 64bit.

So according to the winehowto, I have to link several libraries in order to compile correctly.
```
mkdir -p `pwd`/lib32 
ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so 
ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so 
ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so 
ln -s /usr/lib32/libfontconfig.so.1 `pwd`/lib32/libfontconfig.so 
ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so 
ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so 
ln -s /usr/lib32/libXrender.so.1 `pwd`/lib32/libXrender.so 
ln -s /usr/lib32/libXinerama.so.1 `pwd`/lib32/libXinerama.so 
ln -s /usr/lib32/libXxf86vm.so.1 `pwd`/lib32/libXxf86vm.so 
ln -s /usr/lib32/libXi.so.6 `pwd`/lib32/libXi.so 
ln -s /usr/lib32/libXrandr.so.2 `pwd`/lib32/libXrandr.so 
ln -s /usr/lib32/liblcms.so.1 `pwd`/lib32/liblcms.so 
ln -s /usr/lib32/libpng12.so.0 `pwd`/lib32/libpng.so 
ln -s /usr/lib32/libcrypto.so.0.9.8 `pwd`/lib32/libcrypto.so 
ln -s /usr/lib32/libssl.so.0.9.8 `pwd`/lib32/libssl.so 
ln -s /usr/lib32/libxml2.so.2 `pwd`/lib32/libxml2.so 
ln -s /usr/lib32/libjpeg.so.62 `pwd`/lib32/libjpeg.so 
ln -s /usr/lib32/libXcomposite.so.1 `pwd`/lib32/libXcomposite.so 
ln -s /usr/lib32/libcups.so.2 `pwd`/lib32/libcups.so 
ln -s /usr/lib32/libXcursor.so.1 `pwd`/lib32/libXcursor.so 
ln -s /usr/lib32/libdbus-1.so.3 `pwd`/lib32/libdbus-1.so 
ln -s /usr/lib32/libhal.so.1 `pwd`/lib32/libhal.so 
ln -s /usr/lib32/libsane.so.1 `pwd`/lib32/libsane.so 
ln -s /usr/lib32/libgphoto2.so.2 `pwd`/lib32/libgphoto2.so 
ln -s /usr/lib32/libgphoto2_port.so.0 `pwd`/lib32/libgphoto2_port.so 
ln -s /usr/lib32/libldap-2.4.so.2 `pwd`/lib32/libldap.so 
ln -s /usr/lib32/libldap_r-2.4.so.2 `pwd`/lib32/libldap_r.so 
ln -s /usr/lib32/liblber-2.4.so.2 `pwd`/lib32/liblber.so 
ln -s /usr/lib32/libxslt.so.1 `pwd`/lib32/libxslt.so 
ln -s /usr/lib32/libcapi20.so.3 `pwd`/lib32/libcapi20.so 
ln -s /usr/lib32/libjack.so.0 `pwd`/lib32/libjack.so 
ln -s /usr/lib32/libodbc.so.1 `pwd`/lib32/libodbc.so
```
Patch it so it works for my phenom:
```
patch -Np1 < ./../phenom.patch && tools/make_requests
```
I have to admit several ./configure options aswell.
```
CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v
```

Do I have to add these options somewhere in some files?

EDIT: is make install a required step?

---

### Post by maq21 on 2008-06-11
when i was applying the steps there was an error which its :
 
tail: cannot open `debian/changelog' for reading: No such file or directory


but its exist i dont know what to do plz help me as soon as possible

---

### Post by Skerit on 2008-07-23
Is it possible to create a debian file with kernel modules?

Currently, with debians made with checkinstall, the system keeps complaining it's going to overwrite files in the linux-image-2.6.24-20-generic package. 

How can I fix this? How else can you make debians out of modules (drivers)?

---

