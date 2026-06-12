---
title: "new to ubuntu just saying hi, few questions"
date: 2007-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mercenary(FH) on 2007-06-27
Hi guys Im new to the whole linux scene and ubuntu seemed like a great way to start.

i had a few questions about ubuntu tho, i really want to learn to write my own linux code and learn how to use it. im assuming ubuntu allows this?

and I've read through all the guides and stuff but obviously i'll have to learn as time goes on and it will take some time.

but does ubuntu allow for like security cracks, my school has sort of a lan wars like hack thing, where you try to break into other people's security systems they've set up using whatever you can, would ubuntu have any tools to use to do that cause I've always wanted to partipate in it (my friend does but he's in florida now :()


yeah I know ton of questions but lol

well ill hopefully be around here alot
thx!

---

### Post by dreadlord_chris on 2007-06-27
> **Mercenary(FH) said:**
> Hi guys Im new to the whole linux scene and ubuntu seemed like a great way to start.

i had a few questions about ubuntu tho, i really want to learn to write my own linux code and learn how to use it. im assuming ubuntu allows this?

and I've read through all the guides and stuff but obviously i'll have to learn as time goes on and it will take some time.

but does ubuntu allow for like security cracks, my school has sort of a lan wars like hack thing, where you try to break into other people's security systems they've set up using whatever you can, would ubuntu have any tools to use to do that cause I've always wanted to partipate in it (my friend does but he's in florida now :()


yeah I know ton of questions but lol

well ill hopefully be around here alot
thx!

Ubuntu is a flavor of Linux - so, yes, pretty much any code that will run on any other Linux, will run under Ubu.

As for your *[Penetration Testing]("http://en.wikipedia.org/wiki/Penetration_Testing")* games - Linux is what pen-testing was born on and matured on - 99.9% of the utilities for it were written for Linux - although, alot have been ported to Windows.

---

### Post by praxis22 on 2007-06-27
Hi,

You want nubuntu: [http://www.nubuntu.org/](http://www.nubuntu.org/)

Only a small distro but loaded with tools for network surveillance, etc.

As for compiling you likely will need:

gcc
bin-utils
auto-make
auto-conf
libtool
lex
yacc
bison
M4
Perl
Python
Java

Throw any of these into google, or have a look though synaptic, (the package manager) and you'l find out what they do and how to install them etc. For the more obscure stuff look here:
[http://dinosaur.compilertools.net/](http://dinosaur.compilertools.net/)

Basically, download the source, cd into the directory, run **./configure --help** this will list the switches you can use, (if you want to configure the build) or you can just type **./configure** and it should then print out a load of stuff, and then exit cleanly, or it will complain that it can't find something or cant compile something and bail out.

When this happens you will usually have to install either a program, or some headers (all those packages marked in synaptic as "development") and then run the configure again. If you have the headers, etc. and it's still complaining, then you'll need to tell auto-conf where to find the stuff, (by using switches) finally, it should exit cleanly.

Then you type:
[B]
make depend
make
make test
make install
[/B]
and it should build everything, run any test harness included to test your new build, and then install the  package. 

Take a look at the contents of *makefile* or *Makefile*, (UNIX is case sensitive) and see what it says, in older programs or ad-hoc stuff without auto-conf support you may have to write/edit your own Makefile.

With very simple programs all you really have to do is:

**gcc -o ***<filename> <filename.c>*

This will compile a simple "hello world" program into an executable binary, if you don't specify -o it will create the output file as filename.o Some older compliers will generate *a.out*  all of them are executable, but then you have to rename them.

If you follow this, (carefully) then you should see a build process in full effect that is more or less guaranteed to work, this will build a new kernel, (which you don't have to use) but it's useful to see what a build looks like.

[http://howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://howtoforge.com/roll_a_kernel_debian_ubuntu_way)

In essence, any build goes through a few stages:
Configure environment, and check dependencies
build object files, and create libraries.
Compile object code into a binary, and then link it against either static (library.a) or dynamic (library.so) libraries.
Install binaries and any ancillary scripts and support code, documentation, etc. Into the live OS.

A static library, is a monolithic block of code that is appended to the binary, (make the final binary bigger) a dynamic (shared) library, is linked at run-time, which makes the final binary smaller, and reduces the memory overhead, but can't be copied from one system to another without including the libraries too.
On a system like ubuntu, it should then be ready to use.

Take a look at this page and pages that link from it for more info:
[http://en.wikipedia.org/wiki/Make](http://en.wikipedia.org/wiki/Make)

Enjoy

---

