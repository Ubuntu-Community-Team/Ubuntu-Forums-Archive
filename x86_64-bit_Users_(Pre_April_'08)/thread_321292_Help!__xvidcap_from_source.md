---
title: "Help!  xvidcap from source"
date: 2006-12-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by tonyisntcreative on 2006-12-18
Back when I was using the i386 kernel I used xvidcap for a while.  I don't remember how exactly I went about installing it, but I believe I simply found an i386 .deb for it and had it installed in a matter of seconds.  But now that I'm on the amd64 kernel I run into problems.  There are no amd64 .debs that I've found that will work.  To add to it, I can't seem to compile it on my own.

The archive untars without a hitch.  When I cd to the new directory and run ./configure, it works fine for a while but then spits this out at me...
```
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.4.0 libglade-2.0 glib-2.0 gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'glib-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
From a quick check in synaptic it seems like these are all installed but just named a little bit differently.  I tried ./configure --help to see if I could figure out what it was trying to tell me to do and got this...
```
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
  --enable-maintainer-mode  enable make rules and dependencies not useful
                          (and sometimes confusing) to the casual installer
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-x                use the X Window System
  --with-forced-embedded-ffmpeg
                          don't look for available ffmpeg, also links
                          statically

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  CPPFLAGS    C/C++ preprocessor flags, e.g. -I<include dir> if you have
              headers in a nonstandard directory <include dir>
  CPP         C preprocessor
  PKG_CONFIG  path to pkg-config utility
  PACKAGE_CFLAGS
              C compiler flags for PACKAGE, overriding pkg-config
  PACKAGE_LIBS
              linker flags for PACKAGE, overriding pkg-config

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.
```
Between PKG_CONFIG_PATH, PACKAGE_CFLAGS, PACKAGE_LIBS and pkg-config I'm a little bit confused.  I'm assuming one of these things can tell ./configure that those packages are somewhere where it isn't looking, but I don't really know for sure.

I've only been on Linux for a little over a year and only installed a few apps from source, so I'm no expert.  I'm running Dapper.

---

### Post by xopher on 2006-12-19
Just apt get these packages and you should be fine. (Extracted them from a .dsc-file I found so they should be good)

```
sudo apt-get install debhelper libgtk2.0-dev libglade2-dev liblame-dev ffmpeg libxml-parser-perl scrollkeeper libxmu-dev
```

After this ./configure should finish nicely.

Edit, Just to clarify, about the error that configure spits out at you. It basically tells you you don't have the needed packages installed for building xvidcap, then lists the ones you are lacking.

---

### Post by tonyisntcreative on 2006-12-20
Thanks so much!  

Now that it's working I can actualy see that it works *better* than than when I used it on the 386 kernel.  Some of the features in the newest version are a lot nicer, too.

---

### Post by KLineD on 2006-12-20
I installed the deb from here: deb [http://www.jarre-de-the.net/computing/debian/](http://www.jarre-de-the.net/computing/debian/) stable main (official xvidcap repo I think) and it installed fine. However when I try to run it I get:

> cesar@frodo:~$ xvidcap
xvidcap: error while loading shared libraries: libpng.so.2: cannot open shared object file: No such file or directory


I searched with apt and installed libpng3 and libpng12-0 was already installed in my system but still get the same message. Any clues?

---

### Post by significants on 2006-12-25
I had the same exact error message when trying to install xvidcap, but using that command you recommendd didn't work for me.
(first post, so bear with me if I chose the wrong tags for displaying this..)

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
scrollkeeper is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
E: Broken packages

```

I'm fairly new to linux, but I'm thinking that working over my head will be good for learning (and stress management.)

---

### Post by braddcadd on 2007-02-25
FYI:

I just tried 1.1.5 and had trouble with dependancies.  But I tried 1.1.4 and it worked OK (so far).  I am running Dapper :)

---

### Post by charly4711 on 2007-04-23
@significants:
Something is broken with your apt config. You should clean up your repositories in /etc/apt/sources.list, then do an update in dselect or aptitude (because that does more than apt-get updated) and try again. Normally installing the devel package as you attempted should pull the required packages along.

---

