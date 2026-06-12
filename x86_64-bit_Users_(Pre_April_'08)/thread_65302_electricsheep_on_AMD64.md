---
title: "electricsheep on AMD64"
date: 2005-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by casperlingus on 2005-09-13
I'm trying to get electric sheep on my AMD64 machine, but things don't seem to be working out.  Running

*sudo apt-get install electricsheep*

installs an old version of electricsheep that is incompatible with the sheepserver.  I removed it, and since then have tried numerous things to get it working.

I downloaded electricsheep_2.6.3-1_amd64.deb and attempted to dpkg it.  I got the following results:

[I]**$ sudo dpkg -i --force-overwrite electricsheep_2.6.3-1_amd64.deb**
Selecting previously deselected package electricsheep.
(Reading database ... 70295 files and directories currently installed.)
Unpacking electricsheep (from electricsheep_2.6.3-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of electricsheep:
 [B]electricsheep depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.[/B]
dpkg: error processing electricsheep (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 electricsheep[/I]

Of course I did an apt-get install on libc6 and it told me that it was up-to-date.  I found a posting on here for the identical situation telling me to add a line to my sources list and to try apt-get install libc6 again.  Other people claimed that it worked for them.  I believe, though, it doesn't work for me because I have AMD64:

[I]**$ sudo apt-get install libc6**
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://demudi.agnula.org](http://demudi.agnula.org) testing/main Packages (/var/lib/apt/lists/demudi.agnula.org_packages_demudi_dists_testing_main_**binary-amd64**_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://demudi.agnula.org](http://demudi.agnula.org) testing/main Packages (/var/lib/apt/lists/demudi.agnula.org_packages_demudi_dists_testing_main_**binary-amd64**_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems[/I]

I downloaded a new libc6 debian package, but it requires a newer version of initrd.  I realized, after reading through forums that libc6 is heavily rooted in my kernel, and that updating all my packages to make this work might end up with a kernel recompile.  I decided to give up on the debian package and install electricsheep from source.  Unfortunately, a ./configure gives me the error:

[I]...
checking for XML_ParserCreate in -lexpat... no
configure: error: The expat xml library is required.[/I]

I did an apt-get on expat, and new packages were installed, but it I still get the same ./configure error.  I have definitely run into a brick wall here.  

What do I try next?  Any other respositories I should try?  How do I go about suggesting electricsheep be updated in the repositories...?  (my /etc/apt/sources.list looks exactly as it is described at ubuntuguide.org)

Casper...

---

### Post by mlomker on 2005-09-13
Upgrading libc6 will toast your box.  Trust me on that one.  Compiling from source is the way to go.

Do you have libexpat1-dev installed?

---

### Post by casperlingus on 2005-09-13
Yeah, I figured updating libc6 would not be a good idea.

I did just make another leap...I think.

I decided to search for expat and I found another debian package, and was able to install that fine.  Now I get past the expat error and get this one:

[I]...
checking for XML_ParserCreate in -lexpat... yes
checking for jpeg_start_compress in -ljpeg... no
configure: error: The jpeg library is required.
configure: error: /bin/sh './configure' failed for flam3
[/I]

I found another debian package:

libjpeg62_6b-9_amd64.deb

and installed that, but apparently that's not what it was looking for.  Unfortunately "jpeg library" is kind of a broad term and I can't seem to find this package... 

Anyone know where I can get this library?

Casper...

---

### Post by mlomker on 2005-09-13
Probably libjpeg62-dev.

Hint:  It's usually going to be a -dev when ./configure is complaining.

If you can't find it then check your repositories (/etc/apt/sources.list) and make sure all of the lines are **main restricted universe multiverse**.

---

### Post by casperlingus on 2005-09-14
Okay so I succeeded using your advice, and was able to configure the electricsheep.  I ran make which worked without errors, but "sudo make install" was not so fortunate (DAMNIT I'm so close!)

Here's the tail of the output... I have NO IDEA what to make of it:

[I]...
make[3]: Entering directory `/home/casper/download/electricsheep-2.6.3/mpeg2dec'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/casper/download/electricsheep-2.6.3/mpeg2dec'
make[2]: Leaving directory `/home/casper/download/electricsheep-2.6.3/mpeg2dec'
make[1]: Leaving directory `/home/casper/download/electricsheep-2.6.3/mpeg2dec'
make[1]: Entering directory `/home/casper/download/electricsheep-2.6.3'
make[2]: Entering directory `/home/casper/download/electricsheep-2.6.3'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'electricsheep' '/usr/local/bin/electricsheep'
  /usr/bin/install -c 'electricsheep-voter' '/usr/local/bin/electricsheep-voter'test -e /share/control-center/screensavers && /usr/bin/install -c electricsheep.xml /share/control-center/screensavers
make[2]: *** [install-data-local] Error 1
make[2]: Leaving directory `/home/casper/download/electricsheep-2.6.3'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/casper/download/electricsheep-2.6.3'
make: *** [install-recursive] Error 1[/I]

Anyone know what those 'test's are?  I'm so frustrated with the amount of effort I've put into this, these better be some damn cool sheep when I'm done with it!

Casper...

---

### Post by Corbelius on 2005-09-14
[QUOTE=casperlingus]Okay so I succeeded using your advice, and was able to configure the electricsheep.  I ran make which worked without errors, but "sudo make install" was not so fortunate (DAMNIT I'm so close!)

Here's the tail of the output... I have NO IDEA what to make of it:

[I]...
make[3]: Entering directory `/home/casper/download/electricsheep-2.6.3/mpeg2dec'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/casper/download/electricsheep-2.6.3/mpeg2dec'
make[2]: Leaving directory `/home/casper/download/electricsheep-2.6.3/mpeg2dec'
make[1]: Leaving directory `/home/casper/download/electricsheep-2.6.3/mpeg2dec'
make[1]: Entering directory `/home/casper/download/electricsheep-2.6.3'
make[2]: Entering directory `/home/casper/download/electricsheep-2.6.3'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'electricsheep' '/usr/local/bin/electricsheep'
  /usr/bin/install -c 'electricsheep-voter' '/usr/local/bin/electricsheep-voter'test -e /share/control-center/screensavers && /usr/bin/install -c electricsheep.xml /share/control-center/screensavers
make[2]: *** [install-data-local] Error 1
make[2]: Leaving directory `/home/casper/download/electricsheep-2.6.3'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/casper/download/electricsheep-2.6.3'
make: *** [install-recursive] Error 1[/I]

Anyone know what those 'test's are?  I'm so frustrated with the amount of effort I've put into this, these better be some damn cool sheep when I'm done with it!

Casper...[/QUOTE]


Post the ./configure --help and ur configure give it.

---

### Post by casperlingus on 2005-09-14
I'm not quite sure what you want me to post... I won't post the output of ./configure because that is *freakin long*.  

I'll post the output of "./configure --help" but I didn't think that was program-specific...  The error I got was during the "sudo make install" after everything else compiled without errors... I guess I'm still a n00b in this respect.  What am I looking for to figure out how to fix the make-install problem...?

Casper...


[I]$ ./configure --help
`configure' configures this package to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR           user executables [EPREFIX/bin]
  --sbindir=DIR          system admin executables [EPREFIX/sbin]
  --libexecdir=DIR       program executables [EPREFIX/libexec]
  --datadir=DIR          read-only architecture-independent data [PREFIX/share]
  --sysconfdir=DIR       read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR   modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR    modifiable single-machine data [PREFIX/var]
  --libdir=DIR           object code libraries [EPREFIX/lib]
  --includedir=DIR       C header files [PREFIX/include]
  --oldincludedir=DIR    C header files for non-gcc [/usr/include]
  --infodir=DIR          info documentation [PREFIX/info]
  --mandir=DIR           man documentation [PREFIX/man]

Program names:
  --program-prefix=PREFIX            prepend PREFIX to installed program names
  --program-suffix=SUFFIX            append SUFFIX to installed program names
  --program-transform-name=PROGRAM   run sed PROGRAM on installed program names

X features:
  --x-includes=DIR    X include files are in DIR
  --x-libraries=DIR   X library files are in DIR

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-x                use the X Window System

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  CPPFLAGS    C/C++ preprocessor flags, e.g. -I<include dir> if you have
              headers in a nonstandard directory <include dir>
  CPP         C preprocessor

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.[/I]

---

### Post by mlomker on 2005-09-14
Things might be hosed due to the failed attempts.

Try this, if you haven't already.

```

su
make clean
./configure
make 
make install

```

---

