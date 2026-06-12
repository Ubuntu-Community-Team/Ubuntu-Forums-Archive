---
title: "php-gtk       on Ubuntu 8.10 (64)"
date: 2009-02-27
forum: x86 64-bit Users
---

### Post by dgoosens on 2009-02-27
hi people,

I hope somebody will be able to help me out with this.
I have spent like hours on trying to install php-gtk [http://gtk.php.net]("http://gtk.php.net") on my Ubuntu 8.10 (64bit) and it just wont work...

So I was wondering if any of you encountered the same difficulties and whether you might know a solution...

As yet, when trying to launch the ./builconf, I get the following output:

```
$ sudo ./buildconf --enable-html --enable-scintilla --enable-sourceview --enable-spell --enable-libsexy --enable-mozembed --enable-gtk+ --enable-skeleton --with-phpize=/usr/bin/phpize

Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
rebuilding aclocal.m4
rebuilding configure
configure.in:77: warning: LTOPTIONS_VERSION is m4_require'd but not m4_defun'd
aclocal.m4:2912: LT_INIT is expanded from...
aclocal.m4:2947: AC_PROG_LIBTOOL is expanded from...
configure.in:77: the top level
configure.in:77: warning: LTSUGAR_VERSION is m4_require'd but not m4_defun'd
configure.in:77: warning: LTVERSION_VERSION is m4_require'd but not m4_defun'd
configure.in:77: warning: LTOBSOLETE_VERSION is m4_require'd but not m4_defun'd
configure:12242: error: possibly undefined macro: m4_ifval
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure:15849: error: possibly undefined macro: _LT_SET_OPTIONS
configure:15849: error: possibly undefined macro: LT_INIT
make[1]: *** [configure] Error 1
make: *** [all] Error 2

```

so that does not look good... 
If I do launch the ./configure after this, it obviously fails and spits out the following:

```
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib
checking for PHP extension directory... /usr/lib/php5/20060613
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... re2c
checking for re2c version... 0.13.3 (ok)
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for PHP-GTK support... yes, shared
checking for PHP executable in /usr/bin... found version 5.2.6-2ubuntu4.1
checking for gawk... (cached) nawk
checking whether to include debugging symbols... no
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.6.0... yes (version 2.18.2)
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.6.0... yes (version 2.14.4)
checking for atk >= 1.9.0... yes
checking ATK_CFLAGS... -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking ATK_LIBS... -latk-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
checking for pango >= 1.8.0... yes
checking PANGO_CFLAGS... -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking PANGO_LIBS... -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
checking for gtkextra support... no
checking for html support... no
checking for libglade support... yes
checking for libglade-2.0 >= 2.4.0... yes
checking LIBGLADE_CFLAGS... -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking LIBGLADE_LIBS... -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
checking for libsexy support... no
checking for GtkMozEmbed support... no
checking for scintilla support... no
checking for sourceview support... no
checking for spell support... no
creating main/php_gtk_ext.c
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
./configure: line 12147: LTOPTIONS_VERSION: command not found
./configure: line 12148: LTSUGAR_VERSION: command not found
./configure: line 12149: LTVERSION_VERSION: command not found
./configure: line 12150: LTOBSOLETE_VERSION: command not found
checking for a sed that does not truncate output... (cached) /bin/sed
./configure: line 12240: syntax error near unexpected token `lt_decl_varnames,'
./configure: line 12240: `lt_if_append_uniq(lt_decl_varnames, SED, , ,'

```

Any ideas ?

thanks a lot in advance !

---

### Post by Yellow Pasque on 2009-02-27
It just looks like you're missing a bunch of dependencies.
```
sudo apt-get install m4 gawk build-essential libgtksourceview2.0-dev libgtkextra-x11-2.0-dev libsexy-dev xulrunner-dev libqscintilla2-dev libgtkhtml3.14-dev libgtkspell-dev
```

---

### Post by dgoosens on 2009-02-27
hi Temüjin,

thanks...
but I figured it out...
the problem was not my dependencies or anything on my distro... but the php-gtk package itself

after spending quite some time searching online, I found this site...
[http://blog.pabluk.com.ar/2009/01/compilando-php-gtk2-en-ubuntu-810.html]("http://blog.pabluk.com.ar/2009/01/compilando-php-gtk2-en-ubuntu-810.html")
although it is in Spanish, it appears there is an issue with the 2.0.1 package...
and indeed, I just managed to install the 2.0.0 package without any problems...

thanks a lot though !

---

