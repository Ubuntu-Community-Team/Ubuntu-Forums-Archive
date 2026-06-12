---
title: "Compiling source as 32bit on 64bit Hardy"
date: 2008-05-11
forum: x86 64-bit Users
---

### Post by sipickles on 2008-05-11
Hi,

After a recent hardware failure, I 'upgraded' my system to x64 dual core.

I compiled stackless python and twisted internet from svn, and they seem to work fine.

I have one small problem tho. My debugger, WingIDE, only runs as 32 bit
at present (using --force-architecture during install). This means it
baulks at my shiny 64bit stackless python build.  :( 

Until a version of WingIDE which supports x64 stackless is available
(there is one in the pipeline apparently), I may need to build stackless
and twisted as 32 bit, to permit debugging. Can anyone give me a hint as
to how to compile as x86 on a x64 platform? x64 is a little
new to me. Is there a flag I can set in the configure file to make gcc compile as 32 bit?

Thanks

Simon

---

### Post by Grishka on 2008-05-11
"-m32" flag should do the trick.

---

### Post by Yellow Pasque on 2008-05-11
You may need to install the gcc-multilib and/or gcc-4.2-multilib packages to get the -m32 flag to work.

---

### Post by sipickles on 2008-05-12
I guess the -m32 flag is for make:

./configure
make -m32
sudo make install

I get an error doing this:

simon@simon-ubuntu:~/Source/release25-maint$ make -m32
make: invalid option -- 3
make: invalid option -- 2
Usage: make [options] [target] ...
Options:
  -b, -m Ignored for compatibility.


so the -m flag is ignored? hmm.... Has me stumped
-----

EDIT

Doh, the -m32 is a compiler flag for configure:

./configure CFLAGS=-m32

Lets see what happens!

----

EDIT Damn!

Include/pyport.h:761:2: error: #error "LONG_BIT definition appears wrong for platform (bad gcc/glibc config?)."

I am trying to build stackless python as 32 bit, since my WingIDE is not 64 bit compatible (yet)

---

### Post by Grishka on 2008-05-12
you may want to try setting your library flags to 32-bit libraries. umm maybe something like this?

CC="gcc -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure

I've used something like this to compile 32-bit Wine. dunno if this will work for you. you probably don't have to set all of this. then maybe you need to set something else.
if that won't help, maybe you'll find something in GCC manual: [http://gcc.gnu.org/onlinedocs/](http://gcc.gnu.org/onlinedocs/).

---

### Post by sipickles on 2008-05-13
Well, it looks more promising until I do the make:

gcc -m32 -pthread -DNDEBUG -g  -O3 -Wall -Wstrict-prototypes -L/lib32 -L/usr/lib32  Parser/acceler.o Parser/grammar1.o Parser/listnode.o Parser/node.o Parser/parser.o Parser/parsetok.o Parser/bitset.o Parser/metagrammar.o Parser/firstsets.o Parser/grammar.o Parser/pgen.o Objects/obmalloc.o Python/mysnprintf.o Parser/tokenizer_pgen.o Parser/printgrammar.o Parser/pgenmain.o -lpthread -ldl  -lutil -o Parser/pgen
collect2: ld terminated with signal 11 [Segmentation fault]
/usr/bin/ld: i386: x86-64 architecture of input file `Parser/tokenizer_pgen.o' is incompatible with i386 output
/usr/bin/ld: i386: x86-64 architecture of input file `Parser/printgrammar.o' is incompatible with i386 output
/usr/bin/ld: i386: x86-64 architecture of input file `Parser/pgenmain.o' is incompatible with i386 output
make: *** [Parser/pgen] Error 1

---

### Post by knicki on 2008-05-27
On Suse 10 all it takes is:
CC="gcc -m32" CXX="c++ -m32" ./configure
make

Your errors reported are raised by c++ trying to link 32-bit objects like 64-bit ones. LD flags are not needed on Suse and will  cause troubles later on. 

Hope that helps.

---

