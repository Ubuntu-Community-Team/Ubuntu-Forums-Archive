---
title: "SDL problem"
date: 2006-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Matrixy on 2006-08-24
Hi,
I have tried to install ALeph and it says this:
"configure: error: You need SDL 1.2 to run Aleph One."
i tried all known packeges i can think of 
and still got no sdl 1.2
how the hell i do it?
please help

---

### Post by Kilz on 2006-08-24
> **Matrixy said:**
> Hi,
I have tried to install ALeph and it says this:
"configure: error: You need SDL 1.2 to run Aleph One."
i tried all known packeges i can think of 
and still got no sdl 1.2
how the hell i do it?
please help

The problem is that the game is 32 bit. [You need to install the 32bit sdl package ]("http://packages.ubuntu.com/dapper/libs/ia32-libs-sdl")for the amd64 version.

---

### Post by Matrixy on 2006-08-25
This is wht i get after installing all the packges shown on ur link.

```
neo@neo:/media/Ubuntu/Gamez/Rubicon X ƒ/AlephOne$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/sh: /media/Ubuntu/Gamez/Rubicon: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for egrep... grep -E
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
checking for unistd.h... (cached) yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: You need SDL 1.2 to run Aleph One.
```

Still not working wht to do??

---

### Post by Grey Dog on 2007-01-05
sudo apt-get install libsdl1.2-dev libsdl-mixer1.2-dev libsdl-net1.2-dev

---

### Post by tupesadilla on 2007-01-05
i have the SAME problem i get the same error. "SDL 1.2 not found" or whatever. but a little different.. i get 

** Could not run SDL test program, checking why...
** Test program failed to compile or link
**blah blah blah
** configure error. SDL version 1.2.0 not found!

althought it IS in there and i know it.

---

