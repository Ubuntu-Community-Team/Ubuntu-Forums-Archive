---
title: "gDesklets doesn't work in feisty AMD64"
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2007-04-26
Hi here is the bug I've submitted for my problems:

[https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103)

can anyone please help...

and here is what i get when trying to compile from source downloaded from gdesklets website:

> jonah@jonah-desktop:~/Desktop/gDesklets-0.35.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking how to run the C++ preprocessor... gcc -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by gcc... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... no
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for more debugging including macro expansion... no
checking for more warnings... no
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking /usr/include/python2.5/Python.h usability... yes
checking /usr/include/python2.5/Python.h presence... yes
checking for /usr/include/python2.5/Python.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GDESKLETS... configure: error: Package requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) were not met:

No package 'pygtk-2.0' found
No package 'pyorbit-2' found
No package 'gnome-python-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDESKLETS_CFLAGS
and GDESKLETS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

jonah@jonah-desktop:~/Desktop/gDesklets-0.35.4$

---

### Post by jamesford on 2007-04-26
gdesklets is dead for me too so i searched for alternatives, and found screenlets, which are superior to gdesklets anyway
[http://forum.compiz.org/viewtopic.php?t=358&postdays=0&postorder=asc&highlight=screenlets+mail&start=0&sid=8d2fa25a89878daa5408f1117316b84e](http://forum.compiz.org/viewtopic.php?t=358&postdays=0&postorder=asc&highlight=screenlets+mail&start=0&sid=8d2fa25a89878daa5408f1117316b84e)
repository: [http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/)

---

### Post by jonah1980 on 2007-04-26
thanks, tried screenlets out but i don't find it to be nearly as good as gdesklets so will have to wait until it gets fixed or someone else can help.

---

### Post by Kilz on 2007-04-26
> **jonah1980 said:**
> Hi here is the bug I've submitted for my problems:

[https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103)

can anyone please help...

and here is what i get when trying to compile from source downloaded from gdesklets website:

Taking a look at it, it tells you you need to install some packages. 

No package 'pygtk-2.0' found
No package 'pyorbit-2' found
No package 'gnome-python-2.0' found

You should also look for the -dev packages and install them

pygtk-2.0-dev
pyorbit-2-dev
gnome-python-2.0-dev

---

### Post by ronacc on 2007-04-26
I filed a bug on that months ago  during feisty testing. To get the source to compile you need to pull in some dependencies. I dont remember all of them , just keep runnung ./configure and install what it asks for, it may take 2 or 3 trys to get them all. and then download the deb for ubuntus gdesklets data and extract (not install) them and put them in the directory that your local install made , its different from the one that the gdesklet.deb uses.

---

### Post by jonah1980 on 2007-04-29
well now at least the bug has been confirmed that i also posted, so hopefully the devs should now get on it...

---

### Post by garrison on 2007-05-02
if you want to compile gDesklets from source, try:

```
sudo aptitude install python-gnome2-dev python-pyorbit-dev python-gtk2-dev libgtop2-dev librsvg2-dev
```

---

### Post by garrison on 2007-05-03
A kind of workaround package (compiled with --disable-dependency-tracking) has been posted on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103").

---

### Post by jonah1980 on 2007-05-04
ok i'll check it out - i wonder why a real fix isnt here yet

---

### Post by mikkokupsu on 2007-05-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**Using this .deb below gDesklets work!**

[http://librarian.launchpad.net/7542161/gdesklets_0.35.4-1ubuntu1_amd64.deb](http://librarian.launchpad.net/7542161/gdesklets_0.35.4-1ubuntu1_amd64.deb)

**Thank you Dizzi!!! **

Copied link from: [https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103)

---

### Post by jonah1980 on 2007-05-05
yup i can confirm it's working for me too with this new deb file. all needed now is a better dock than starterbar for it, as it doesnt allow autohide and you can't add trashcan etc to it. does anyone know if anything is in dev. as gdesklets seems much nicer to me than beryl/compiz alternatives for docks and widgets....

---

### Post by jonah1980 on 2007-05-05
only problem is i've now lost all file associations for everything since installing this: 

[http://ubuntuforums.org/showthread.php?p=2599591](http://ubuntuforums.org/showthread.php?p=2599591)

---

### Post by rsambuca on 2007-05-05
Darn.  Lost all my mime-type file associations too.  All my desktop program launchers open up in gedit now.

---

### Post by Meir on 2007-05-06
What I did which seems to be working was install gdesklets via synaptic (its broken but it gets everything installed). Then I extracted the .data.tar.gz/usr/lib/gdesklets from the deb posted here to my /usr/lib/gdesklets and it works and so do my mime.

---

### Post by rsambuca on 2007-05-06
> **Meir said:**
> What I did which seems to be working was install gdesklets via synaptic (its broken but it gets everything installed). Then I extracted the .data.tar.gz/usr/lib/gdesklets from the deb posted here to my /usr/lib/gdesklets and it works and so do my mime.

Hey, great job!  That seems to have done the trick.  Now if I could just get it to work with beryl...

---

### Post by Meir on 2007-05-06
Its working fine with beryl for me. What type of problems are you having.

---

### Post by rsambuca on 2007-05-06
It seems to be working with Beryl now, but only if I start the gdesklets after I start beryl.

---

### Post by abhishek456 on 2007-05-19
it's working for me after installing 64bit version

---

### Post by The other One on 2007-05-31
The .deb on page 1 worked perfectly for me too.

---

### Post by s_spiff on 2007-08-23
> **Meir said:**
> What I did which seems to be working was install gdesklets via synaptic (its broken but it gets everything installed). Then I extracted the .data.tar.gz/usr/lib/gdesklets from the deb posted here to my /usr/lib/gdesklets and it works and so do my mime.

Rocking!!! thanks for this.. you should make a howto of this.. make life easy for newbs :P
:guitar:

Thanks again.

---

