---
title: "Abiword 2.8.1 Trouble"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by odysseusjak on 2009-11-01
**[SOLVED] - Arand's post (post #10) did the trick!  Thanks Arand!**

I'm trying to install the latest version of Abiword.  Since Abiword hasn't posted an update the the PPA, nor has GetDeb come up with a deb, I am having to compile it myself (first time ever).  I am a lot out of my zone here and I need some help please.

When I extract the tar, I try to configure it by using './configure'.  I get and error stating that libpng needs to be installed.  I checked, and libpng IS installed (I even installed another versions just to make sure).  I re-ran the command and get the same errors.  Any suggestions?

Here is a copy of the script message:

[INDENT]./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to disable maintainer-specific portions of Makefiles... yes
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for a BSD-compatible install... /usr/bin/install -c
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) no
checking whether g++ accepts -g... (cached) no
checking dependency style of g++... (cached) none
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for bash... /bin/bash
checking if dolt supports this host... yes, replacing libtool
checking whether ln -s works... yes
checking for platform and toolkit... unix / gtk
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for working strtod... yes
checking for uint32_t... yes
checking for alarm... yes
checking for gettimeofday... yes
checking for localeconv... yes
checking for strcspn... yes
checking for strncasecmp... yes
checking for strtoul... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether gcc understands -Wall... no
checking whether gcc understands -Wextra... no
checking whether gcc understands -Wsign-compare... no
checking whether gcc understands -Wpointer-arith... no
checking whether gcc understands -Wchar-subscripts... no
checking whether gcc understands -Wwrite-strings... no
checking whether gcc understands -Wmissing-noreturn... no
checking whether gcc understands -Wunused... no
checking whether gcc understands -Wpointer-arith... no
checking whether gcc understands -Wshadow... no
checking png.h usability... no
checking png.h presence... no
checking for png.h... no
configure: error: `png.h' not found, install libpng or specify CPPFLAGS to include custom locations[/INDENT]

Thanks in advance!

---

### Post by nikgare on 2009-11-01
Make sure that the corresponding development files are install (dev files)
In this case it should be libpng12-dev

---

### Post by iamhimay on 2009-11-03
You can do: 

apt-get build-dep abiword

and that should bring in most of what you need. Make sure you have the sources repo checked in synaptic sources. I'll be trying a build soon. Would be nice to have it in a ppa. Good luck.

---

### Post by odysseusjak on 2009-11-04
Yeah, I haven't tried this yet.  I tried the other way and had to install a bunch of other devs but it never ran.  I get a filesharing/file does not exist error.

I'll try this next.  But I agree, I wish they would update the PPA.

---

### Post by odysseusjak on 2009-11-04
Okay, I tried the command 'apt-get build-dep abiword' (which seemed to work great) and got this error when trying to run it:

abiword: error while loading shared libraries: libabiword-2.8.so: cannot open shared object file: No such file or directory

Any more thoughts?

---

### Post by hrizzy on 2009-11-05
> **odysseusjak said:**
> Okay, I tried the command 'apt-get build-dep abiword' (which seemed to work great) and got this error when trying to run it:

abiword: error while loading shared libraries: libabiword-2.8.so: cannot open shared object file: No such file or directory

Any more thoughts?


Absolutely the same trouble I had yesterday's evening. Still looking for solution...

---

### Post by iamhimay on 2009-11-07
Not quite sure what you're doing. build-dep brings in the build dependencies, like all those -dev packages. You still have to get the source, untar it, then cd into the directory and then follow the build directions. In this case that would be:
./configure --with-plugins --with-templates

then, if that completes successfully, 

make

make install

Which builds the binary file (runnable program) from the sources. 

A different approach might be to run checkinstall in the source directory after you've run make(skipping the "make install" step above), to create and install a .deb file that's easily uninstallable. Those "--with-*" parts of the configure command are directions to the compiler as to what options you want to include in the final product. I'm mid-build right now. I'm only at the make stage atm; compiling takes a while. I'll check back here with my results, and to see how it went for you. I'm stumped as to why nobody has binaries built for this yet. Good luck. 

PS: Here's a link about checkinstall:

[http://shibuvarkala.blogspot.com/2009/10/howto-make-deb-file-from-source-code-in.html](http://shibuvarkala.blogspot.com/2009/10/howto-make-deb-file-from-source-code-in.html)

---

### Post by iamhimay on 2009-11-07
One more thing: probably a good idea to uninstall abiword if you had it installed from the ubuntu repository, to avoid confusion.

---

### Post by iamhimay on 2009-11-07
Whoops, I get it. The default directories if you build from source are in /usr/local/, hence /usr/local/bin/abiword is the binary executable file and it needs the file libabiword-2.8.so which normally (on ubuntu) is found in /lib but now it's in /usr/local/lib. I'll work on some directions to build a better package that puts everything where an ubuntu system expects it to be, but for now, try this: 

sudo ln -sf /usr/lib/libabiword-2.8.so /lib/

And try running abiword from command line to see any errors it might give. But it should start right up.

---

### Post by Arand on 2009-11-10
I was trying to compile this on jaunty, and here is my hassly route:

1. Get the source from [http://www.abisource.com/downloads/abiword/2.8.1/source/](http://www.abisource.com/downloads/abiword/2.8.1/source/)
2. unpacking it
3. Get the build-deps```
sudo apt-get build-dep abiword
```
4. running ./configure in the source dir **didn't** work, failing on the checking if gcc & g++ supports -static flag.
5. I blindly assumed that they do on ubuntu, and edited the configure file to reflect this blind assumption:
6. Replacing each of the two lines:```
if test "${lt_cv_prog_compiler_static_works_CXX+set}" = set; then
``````
if test "${lt_cv_prog_compiler_static_works+set}" = set; then
```with simply```
if $TRUE; then
```(Very kludge, but very effective)

7. Now the configure worked out alright.
8. Note that the --with-* flags mentioned by iamhimay should be --enable-* instead. However I didn't use them in my case.
9. running make - long but problem-free
10. used sudo checkinstall, followed instructions, no problems.
11. To get the lib links working alright I followed iamhimay's hints, the command given seems erroneous however, so this is what I did instead (not sure if it might be enough just to link the *.so file):```
cd /lib
sudo ln -s /usr/local/lib/libabiword-2.8.a
sudo ln -s /usr/local/lib/libabiword-2.8.la
sudo ln -s /usr/local/lib/libabiword-2.8.so
sudo ln -s /usr/local/lib/abiword-2.8/
```

12. And now it should just be a matter of```
abiword
```


- Arand

---

### Post by jimmy the saint on 2009-11-11
my mistake

---

### Post by iamhimay on 2009-11-13
Oh yeah, whoops on the configure flags. My bad.

I'm on karmic, maybe different compiler versions?

As for linking the .so from /usr/local/ to the system /lib that was all I needed to do. Also, I included support for gnome vfs so I needed a few more libraries. It was only a few so I just ran ./configure and added what I needed by the errors. 

Been using it a week or so now. Seems ok. Still haven't tried all the new features. 

Best!

---

