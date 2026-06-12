---
title: "Canon Printer/Scanner drivers?"
date: 2008-07-22
forum: x86 64-bit Users
---

### Post by s_spiff on 2008-07-22
I'm on a x64 Hardy Heron Setup. I just bought a Canon Pixma MP 145 all in one printer. I need drivers for the system. As of yet, what I've done is, force-installed the 32bit drivers from the deb's provided by Canon  here : 
[http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20MP145%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20MP145%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&)

Although this has got the printer working perfectly, the scanner simply doesn't function. Can someone help me out? 

Also, the link above gives the source to those drivers, but I can't understand what to compile in it. Its got several folders, and several make files.

Any help is appreciated.

---

### Post by Sef on 2008-07-22
> Also, the link above gives the source to those drivers, but I can't understand what to compile in it.

Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by s_spiff on 2008-07-22
hi, thanks for the link, but it doesn't really solve my issue of which part of the whole tarball to compile and install. I do know the usual method to install source, in this case, I don't know what part of the source should I install. Thanks anyways. :D

P.S ok, I may be missing the point, but incase I'm wrong, please let me know.

---

### Post by s_spiff on 2008-07-22
ok.. chuck it.. I think i figured out which folder and where. thanks anyways.

---

### Post by harvey186 on 2008-07-22
> **s_spiff said:**
> ok.. chuck it.. I think i figured out which folder and where. thanks anyways.

Hi, is your scanner now working ?

---

### Post by s_spiff on 2008-07-22
well unfortunately, nopes. I am not able to compile the source, some error which I can't figure out. :

> 
spiff@spiffed:~/Desktop/Canon Drivers/source/scangearmp-common-1.10/scangearmp$ ./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Making ./aclocal.m4 writable ...
Running aclocal  ...
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:         [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake --gnu  ...
backend/Makefile.am:11: Libtool library used but `LIBTOOL' is undefined
backend/Makefile.am:11:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
backend/Makefile.am:11:   to `configure.in' and run `aclocal' and `autoconf' again.
backend/Makefile.am:11:   If `AC_PROG_LIBTOOL' is in `configure.in', make sure
backend/Makefile.am:11:   its definition is in aclocal's search path.
src/Makefile.am:13: compiling `main.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.in'
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/spiff/Desktop/Canon: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
./configure: line 2261: AC_PROG_LIBTOOL: command not found
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for ranlib... ranlib
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... yes
checking for GIMP... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking libgimp/gimp.h usability... no
checking libgimp/gimp.h presence... no
checking for libgimp/gimp.h... no
checking libgimp/gimpcompat.h usability... no
checking libgimp/gimpcompat.h presence... no
checking for libgimp/gimpcompat.h... no
checking sane/sane.h usability... no
checking sane/sane.h presence... no
checking for sane/sane.h... no
checking for usb_get_busses in -lusb... yes
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes
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
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  cs da de el es fi fr hu id it ja ko nl nb pl pt ru sv th tr zh zh_TW
configure: creating ./config.status
config.status: error: cannot find input file: Makefile.in



I'll be trying it with a sudo, although it means good chance that I'll have loads of undeleteable junk around. Cuz anyways, this thing has given me soo much headache that I plan to dump the x64 for sometime now :|

---

