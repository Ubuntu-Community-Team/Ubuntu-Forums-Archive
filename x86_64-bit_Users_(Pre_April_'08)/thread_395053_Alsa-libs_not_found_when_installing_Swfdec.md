---
title: "Alsa-libs not found when installing Swfdec"
date: 2007-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Vegetarianrage on 2007-03-27
I'm trying to install flash support for Firefox2 64bit without resorting to the 32bit app. I did some research here and there and found [http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/) as a possibility. I'm attempting to follow their tutorial at [http://lists.freedesktop.org/archives/swfdec/2007-March/000134.html](http://lists.freedesktop.org/archives/swfdec/2007-March/000134.html) , but when I try to run ./configure I get the following errors.
```
john@eleanor:~/Desktop/swfdec-0.4.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works..
. yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking to see if compiler understands -Wall... yes
checking to see if compiler understands -Wextra -Wno-missing-field-initializers -Wno-unused-parameter... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
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
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for PANGO... yes
checking for GTK... yes
checking for ALSA... configure: error: Package requirements (alsa >= 1.0) were not met:

No package 'alsa' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALSA_CFLAGS
and ALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
john@eleanor:~/Desktop/swfdec-0.4.3$
```

So you can see at the end that 'alsa' isn't found, but I'm sure it's installed. It's my audio mixer and I'm using it literally right now. I can type alsamixer in the terminal as well use the gui in Gnome. I anyone else familiar with this problem? Is there a way to redirect the script to look wherever alsa happens to be?

---

### Post by CrazyG on 2007-03-28
Sorry, I can't help you.  I am running Dapper (total newbie here), and just want to  say I am getting the same error message.  I haven't used Alsa yet, but searched my system using Synaptic and I do have it installed.  I am using Firefox 1.5.0.11. and an AMD64 processor.

Anybody else have any ideas???

(I am also having a lot of other issues installing Ubuntu, and don't know if these may be affecting installation of swfdec.  As time permits I am slowly working my way through these forums looking for answers.)

---

### Post by prince_niceguy on 2007-03-29
search for alsa in synaptic. install the -dev package. I think the alsa development header files are not present.

---

### Post by MonkeyWrench32 on 2007-03-30
I'm getting the same error.  I've tried installing many different ALSA related packages, but nothing seems to work.  Please help!

---

### Post by johnficca on 2007-03-30
Hi I think you might need to install libsound2-dev  or lib32sound2-dev or both, try that and tell me if it works.

---

### Post by MonkeyWrench32 on 2007-03-31
Well, I installed lib**a**sound2-dev and lib32**a**sound2-dev and I was able to compile, make and install the packages.  Unfortunately, whenever I try to view any Flash content, I see two lines in the Flash area (like a big "pause" sign) and the browser crashes.

Thanks, though.

---

### Post by CrazyG on 2007-04-01
I managed to get past the "Alsa not installed" message by searching for alsa dev files in Synaptic and installing (apparently) the right one, then got a message about "liboil" (or something similar) missing, installed that one too, and then got stuck on "cairo is missing".  I downloaded and installed whichever files I could find that had the word "cairo" in them - none of these resolved the issue.  All the available repositories listed in Synaptic were enabled before I did any of this downloading/installing.  I am not asking for help here, am a bit frustrated with the amount of time this is taking (am a newbie) so am going to take a break for a while now before I throw my computer out the window.  :)

And no, I am NOT going back to Windows.  I will stick with Linux even if it kills me.  :mrgreen:

---

### Post by simonbowen on 2008-01-15
Hey, I am having problems compiling swfdec as well, I have got to a point in the ./configure part where it needs gstreamer 0.10.11. I can't seem to find this in the packages at all, and as far as I can see I have almost all of the latest gstreamer stuff installed, has anyone got any ideas?

---

