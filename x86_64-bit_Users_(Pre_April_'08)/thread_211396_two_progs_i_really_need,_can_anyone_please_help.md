---
title: "two progs i really need, can anyone please help"
date: 2006-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2006-07-08
hi guys.

ok amd64 dapper is cool but some progs are older than what i installed on 32bit.

so i've made files and used documents i can not use now, even though the programs are there, they're not new enough!! it's awful cos i can't get into my files i used on my old system!

can anyone please help me update scribus from 1.2 to scribus 1.3.3.2 - 1.2 has no undo feature and also i can't open up my newsletter templates which i really need.

and also tellico collection manager to the latest version as i can't open up my catalogues!

please help.

thanks.

---

### Post by hajk on 2006-07-08
Two possibilities that you could pursue:

1. Check whether the newer packages are already in Edgy and, if so, put in a request for them to be backported to Dapper AMD64.

2. Get the source code of the newer versions (SourceForge? etc), then compile them yourself. 

It is also possible that others on the forums desperately want these newer versions, then you could bundle your efforts in compiling them and transforming them to deb-packages in some alternative repository.

But then, I realize, these may not be the answers that you expected...

---

### Post by jonah1980 on 2006-07-08
how do i go about finding/requesting for these backports?

tried downloading newer version and compiling my self but had problems with that too, they don't compile, says it can't make the make file or somehting.

---

### Post by Kilz on 2006-07-09
> **jonah1980 said:**
> how do i go about finding/requesting for these backports?

tried downloading newer version and compiling my self but had problems with that too, they don't compile, says it can't make the make file or somehting.

Can you please copy/paste the errors into a post if you are still having problems.

---

### Post by jonah1980 on 2006-07-09
i get this for tellico:

jonah@jonah-desktop:~$ cd /home/jonah/Desktop/tellico-1.1.6
jonah@jonah-desktop:~/Desktop/tellico-1.1.6$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
checking whether g++ supports -fno-reorder-blocks... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output...
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... no
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 8
checking for char *... yes
checking size of char *... 8
checking for dlopen in -ldl... yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 8
checking for unsigned long... yes
checking size of unsigned long... 8
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

And scribus won't let me add the repository!

---

### Post by Kilz on 2006-07-10
> **jonah1980 said:**
> i get this for tellico:

jonah@jonah-desktop:~$ cd /home/jonah/Desktop/tellico-1.1.6
jonah@jonah-desktop:~/Desktop/tellico-1.1.6$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
checking whether g++ supports -fno-reorder-blocks... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output...
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... no
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 8
checking for char *... yes
checking size of char *... 8
checking for dlopen in -ldl... yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 8
checking for unsigned long... yes
checking size of unsigned long... 8
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

And scribus won't let me add the repository!
[Try this]("http://mirrors.kernel.org/debian/pool/main/t/tellico/tellico_1.1.6-1_amd64.deb") Download it and open with gdebi package installer. [URL="http://mirrors.kernel.org/debian/pool/main/t/tellico/tellico-data_1.1.6-1_all.deb"]You might also need this.
[/URL]Can you download the scribus .deb file?

---

### Post by jonah1980 on 2006-07-10
thanks, first it said i need the tellico-data file so downloaded and installed that but now there is another error stopping me from installing the tellico.deb file you've provided. it says:

Dependency is not satisfiable: kdelibs4c2a

but this seems to be installed when i checked in synaptic package manager, so is it not new enough or something??

thanks

---

### Post by Kilz on 2006-07-10
> **jonah1980 said:**
> thanks, first it said i need the tellico-data file so downloaded and installed that but now there is another error stopping me from installing the tellico.deb file you've provided. it says:

Dependency is not satisfiable: kdelibs4c2a

but this seems to be installed when i checked in synaptic package manager, so is it not new enough or something??

thanks
The packages were debian packages, sometimes they work without problems. The thing is they depend on a newer version of kdelibs4c2a that isnt in Ubuntu yet, and when I try and upgrade it conflicts with other packages.
I did find 2 ubuntu packages though
Try these 
[URL="http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Funiverse%2Ft%2Ftellico%2Ftellico_1.1.6-1ubuntu1_amd64.deb&md5sum=0e264f424df0ed8c356a7d365243e588&arch=amd64&type=main"]tellico data
[/URL][tellico]("http://ubuntu.secs.oakland.edu/pool/universe/t/tellico/tellico-data_1.1.6-1ubuntu1_all.deb")
But I think they have the same problem. Perhaps the kdelibs4c2a will be updated soon

---

### Post by jonah1980 on 2006-07-11
they don't work either, i removed the tellico-data and tried the one you've found then when i tried to install tellico 1.1.6 you also found it says:

 Error Dependency is not satisfiable: tellico-data

so i tried the other tellico-data but that gives me the other error from before still.

so still don't have scribus or tellico to use with the files from my previous computer!

thanks for trying to help me out, any other ideas?

---

### Post by jonah1980 on 2006-07-20
hi i just wondered if any word on backports or repositories for these two progs as i still can't get them to work! thanks for any help

---

### Post by parys on 2006-07-26
[INDENT]Maybe [http://www.imalip.info/tellico/]("http://http://www.imalip.info/tellico/") has what you need?[/INDENT]

EDIT: Never mind, I don't see amd64 debs there.

---

### Post by jonah1980 on 2006-07-26
don't worry guys, RAOF kindly added them to this new 64bit repository:

[http://www.ubuntuforums.org/showthread.php?t=196093](http://www.ubuntuforums.org/showthread.php?t=196093)

---

### Post by LeslieL on 2006-08-06
Keeping the pressure up. I need any version of tellico newer than 1.1, and I get the kdelibs dependency problem when I try installing it.

---

### Post by Kilz on 2006-08-06
> **LeslieL said:**
> Keeping the pressure up. I need any version of tellico newer than 1.1, and I get the kdelibs dependency problem when I try installing it.

According to the [tellico website]("http://periapsis.org/tellico/") 1.1.6 is the current version. RAOF's repository seems to be offline right now. [http://raof.dyndns.org/falcon](http://raof.dyndns.org/falcon) but jonah1980 says they are there. It should be back up soon.

---

