---
title: "Beagle on kubuntu 64 bit?"
date: 2008-05-12
forum: x86 64-bit Users
---

### Post by LK_gandalf_ on 2008-05-12
Hi, I'd like to install Beagle on kubuntu Hardy Heron 64 bit. From repo I have an old version, so I have to install the tarball form the official site. But there is a problem in the "nake".

./configure does this:

```

$ ./configure --disable-docs
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking for bash... /bin/bash
checking for zip... /usr/bin/zip
checking for mono... /usr/bin/mono
checking for gmcs... /usr/bin/gmcs
checking for mono.pc... found
checking pkg-config is at least version 0.9.0... yes
checking for MONO... no
missing mono >= 1.9. Searching for mono >= 1.2.4
checking for MONO... yes
checking for Mono.Data.Sqlite.dll... found
checking for Mono.Posix.dll... found
checking for System.Data.dll... found
checking for System.Web.dll... found
checking for ICSharpCode.SharpZipLib.dll... found
checking for NDESK_DBUS... yes
checking for NDESK_DBUS_GLIB... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for desktop-launch... no
checking for xdg-open... /usr/bin/xdg-open
checking for intltool >= 0.35.0... 0.37.1 found
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for SQLITE3... yes
checking for X... libraries , headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking X11/extensions/scrnsaver.h usability... no
checking X11/extensions/scrnsaver.h presence... no
checking for X11/extensions/scrnsaver.h... no
checking for XScreenSaverQueryExtension in -lXss... no
checking for System.Security.dll (needed by Google backends)... found
checking for GNOME_VFS... yes
checking for BEAGLE_UI... yes
checking for UIGLUE... yes
checking for LIBTRAYICON... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for OPEN_WITH... yes
checking for EVO... no
checking for GSF_SHARP... yes
checking for WV1... no
checking for TAGLIB_SHARP... yes
checking for BEAGLED... yes
checking for Epiphany...
checking for Epiphany 2.22... no
checking for Epiphany 2.20... no
checking for Epiphany 2.19... no
checking for Epiphany 2.18... no
checking for Epiphany 2.17... no
checking for Epiphany 2.16... no
checking for Epiphany 2.15... no
checking for Epiphany 2.14... no
checking for Epiphany 1.8... no
checking for Epiphany 1.6... no
checking for GALAGO... yes
checking for AVAHI_SHARP... yes
checking for kde-config... /usr/bin/kde-config
checking for chm_open in -lchm... no
configure: not building Beagle csharp API documentation
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Util/Makefile
config.status: creating glue/Makefile
config.status: creating BeagleClient/Makefile
config.status: creating beagled/Makefile
config.status: creating Filters/Makefile
config.status: creating tools/Makefile
config.status: creating tools/beagle-settings.desktop.in
config.status: creating search/Makefile
config.status: creating search/icons/Makefile
config.status: creating search/beagle-search.desktop.in
config.status: creating ImLogViewer/Makefile
config.status: creating epiphany-extension/Makefile
config.status: creating firefox-extension/Makefile
config.status: creating thunderbird-extension/Makefile
config.status: creating doc/Makefile
config.status: creating doc/api/Makefile
config.status: creating conf-data/Makefile
config.status: creating beagle-0.0.pc
config.status: creating beagle-daemon.pc
config.status: creating beagle-ui-0.0.pc
config.status: creating beagle.spec
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

        Beagle version:           0.3.7
        Target OS:                linux
        Inotify:                  yes

        Prefix:                   /usr/local
        GNOME prefix:             /usr
        KDE prefix:               /usr

        evolution-sharp?          no (missing dependencies)
        gsf-sharp?                yes
        galago-sharp?             yes
        avahi-sharp               no (disabled)
        wv1?                      no
        libchm?                   no

        Firefox Extension?        yes
        Epiphany Extension?       no (Epiphany not installed)
        Thunderbird Extension?    yes
        Google Backends?          yes

        Local taglib-sharp?       no

        Monitor screensaver       no
        beagle-search GUI         yes

        Qt beagle-settings GUI    no

        Build docs?               no

```


make is the error, I cannot understand what to do. I copy the last part:
```

  at Mono.CSharp.Expression.MemberLookup (System.Type container_type, System.Type qualifier_type, System.Type queried_type, System.String name, Location loc) [0x00000]
  at Mono.CSharp.MemberAccess.DoResolve (Mono.CSharp.EmitContext ec, Mono.CSharp.Expression right_side) [0x00000]
  at Mono.CSharp.MemberAccess.DoResolve (Mono.CSharp.EmitContext ec) [0x00000]
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext ec, ResolveFlags flags) [0x00000]
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext ec) [0x00000]
  at Mono.CSharp.Binary.DoResolve (Mono.CSharp.EmitContext ec) [0x00000]
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext ec, ResolveFlags flags) [0x00000]
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext ec) [0x00000]
  at Mono.CSharp.Expression.ResolveBoolean (Mono.CSharp.EmitContext ec, Mono.CSharp.Expression e, Location loc) [0x00000]
  at Mono.CSharp.If.Resolve (Mono.CSharp.EmitContext ec) [0x00000]
  at Mono.CSharp.Block.Resolve (Mono.CSharp.EmitContext ec) [0x00000]
  at Mono.CSharp.EmitContext.ResolveTopBlock (Mono.CSharp.EmitContext anonymous_method_host, Mono.CSharp.ToplevelBlock block, Mono.CSharp.Parameters ip, IMethodData md, System.Boolean& unreachable) [0x00000]
make[2]: *** [UiUtil.dll] Error 1
make[2]: Leaving directory `/home/doc/programmi/compilati/beagle-0.3.7/Util'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/doc/programmi/compilati/beagle-0.3.7'
make: *** [all] Error 2

```

Thank you for the help.

---

### Post by Half-Left on 2008-05-12
Try ```
./configure --prefix=/usr
``` and install libqt3-headers(You may need libqt3-mt-dev for the UI)

If you still get the same error, try ./configure --help and see if there is a disable-docs option.

---

### Post by LK_gandalf_ on 2008-05-12
this doesn't seems to change the error.

But I've tried --disable-gui and now the make goes until the end without error.
but what are the consequences now? 
Can I use Kerry as a kde-fronted?

---

### Post by Half-Left on 2008-05-12
I think you'll need the packages I said to build the Qt UI frontend, Yes Kerry is the KDE beagle Frontend. Watch out though, if you install Kerry one of the deps maybe Beagle in the repos,

---

### Post by dbera on 2008-05-12
> **LK_gandalf_ said:**
> this doesn't seems to change the error.

But I've tried --disable-gui and now the make goes until the end without error.
but what are the consequences now? 


From [http://beagle-project.org/Installing_prerequisites](http://beagle-project.org/Installing_prerequisites)
if you pass --disable-gui, then the included Gnome UI is not built. So I guess you can still use it with kerry.

---

### Post by LK_gandalf_ on 2008-05-13
Well I think I'll use the version from the repos, it's quite more simple.
But I actually would like to understand a things...

I've tried beagle + kerry from Repos, and they worked well. But the version of beagle was quite old.

So, i've tried to compile beagle...and it misses a lot of dependencies. Why the beagle from repos worked without all these dependences?

the same now with kerry...I'ìm trying to install it....no KDE header found. :confused:

how is it possible that, the same program, works if installed with Adept and misses dependencies if compiled...?

P.S. What is the **best search tool for Kubuntu**? I mean, one where I can use a graphical interface, better if integrated with the kicker or with the desktop.

---

### Post by Half-Left on 2008-05-13
Your missing kdelibs4-dev, remember you have to have all the dev packages installed(for whatever your building for) when compiling because it looks for their headers. Binary packages from the repos are already built from them.

---

### Post by dbera on 2008-05-13
> **LK_gandalf_ said:**
> What is the **best search tool for Kubuntu**? I mean, one where I can use a graphical interface, better if integrated with the kicker or with the desktop.

Don't know about best. But FYI, for beagle there is a beagle kio-slave (kio-beagle) and a kicker applet (kbeaglebar) as far as desktop integration goes.

---

### Post by LK_gandalf_ on 2008-05-16
thank you. I've succeded compiling beagle and kerry, but I cannot find kerry in the menu K nor launch it from konsole. 
i have only beagle control in the menu, and I can start the indexing and configure it.

I've compiled kbeaglebar too, but where can I found it and how use?

---

### Post by dbera on 2008-05-16
This might be helpful.
[www.linux-magazine.com/issue/70/KTools_Beagle_Helpers.pdf](www.linux-magazine.com/issue/70/KTools_Beagle_Helpers.pdf)

---

### Post by LK_gandalf_ on 2008-05-17
well, the problem is:

i've installed kerry, but it doesn't appear in the Menu K.
 if i launch it from shell, it says that kerry is not installed, and to use "apt-get install kerry". But if I install kerry from the repo, it calls up the old version of beagle too!!

probably we must use only the programs from repo, even if they are old :( but it's quite sad.

---

### Post by dbera on 2008-05-19
> **LK_gandalf_ said:**
> well, the problem is:

i've installed kerry, but it doesn't appear in the Menu K.
 if i launch it from shell, it says that kerry is not installed, and to use "apt-get install kerry".

I can only guess that you didnt install kerry with the right prefix. You probably installed it as /usr/local/bin/kerry

> **LK_gandalf_ said:**
> But if I install kerry from the repo, it calls up the old version of beagle too!!

probably we must use only the programs from repo, even if they are old :( but it's quite sad.

There could be a way to "force" install a package without installing its dependencies when you know you have the right dependencies installed. Ask in the ubuntu IRC channels, someone there might know.

---

### Post by Julius on 2008-05-19
mm I think
apt-get install build-dep beagle
should download all the packages you need in order to compile beagle by yourself. if it's not that command, then it is just "apt-get build-dep beagle"

as for forcing apt to ignore the depedencies, I think it is:
apt-get install --force-all package

or you could extract the .deb file, edit the file that contains the dependencies and drop the ones it keeps asking for

although neither is advised, I guess!

---

