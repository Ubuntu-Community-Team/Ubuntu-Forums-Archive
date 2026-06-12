---
title: "Dosbox 0.71 problems"
date: 2007-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by boss429 on 2007-08-15
I downloaded "dosbox-0.71-1mdv2008.0.x86_64.rpm" and converted it using alien.  I then installed the *.deb and everything seemed to work fine.  however when I run "dosbox" in a terminal I get this:
```
$ dosbox
dosbox: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by dosbox)

```
So then I tried compilinge the Dosbox 0.71 source myself.  When I ran "./cofigure" and this happened:
```
$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
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
checking how to run the C preprocessor... gcc -E
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
checking for ranlib... ranlib
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!

```
I have these packages checked in the Synaptic Package Manager:
libsdl1.2debian
libsdl1.2debian-all
libsdl-image1.2
libsdl-net1.2
libsdl-sound1.2
libpng12-0
libpng12-dev

Does anybody know how to fix either of these problems?

Thanks.

---

### Post by Kilz on 2007-08-15
> **boss429 said:**
> I downloaded "dosbox-0.71-1mdv2008.0.x86_64.rpm" and converted it using alien.  I then installed the *.deb and everything seemed to work fine.  however when I run "dosbox" in a terminal I get this:
```
$ dosbox
dosbox: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by dosbox)

```
So then I tried compilinge the Dosbox 0.71 source myself.  When I ran "./cofigure" and this happened:
```
$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
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
checking how to run the C preprocessor... gcc -E
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
checking for ranlib... ranlib
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!

```
I have these packages checked in the Synaptic Package Manager:
libsdl1.2debian
libsdl1.2debian-all
libsdl-image1.2
libsdl-net1.2
libsdl-sound1.2
libpng12-0
libpng12-dev

Does anybody know how to fix either of these problems?

Thanks.

Is there some reason why you are not using the version in the repositories?

---

### Post by boss429 on 2007-08-15
when I run "apt-get dosbox" it installs v0.65.  It works fine but v0.70 was a huge inprovement in speed.

---

### Post by Chaotic Thought on 2007-08-15
Right, for something like DOSbox you might have to get the latest source. But looking at your output, you don't have the development tools installed. Use apt-get or Synaptic and install the following:

**build-essential**
**libsdl1.2-dev**
(Any required dependencies)

That will at least let you try compiling it. There might be other requirements. The **./configure** script will tell you if something is missing. And then there's the README that's included with the source. Basically to compile on Debian-based distributions you have to install the appropriate **-dev** package. So for "libsdl" you need "libsdl-dev" or something closely named.

---

### Post by Kilz on 2007-08-16
> **boss429 said:**
> when I run "apt-get dosbox" it installs v0.65.  It works fine but v0.70 was a huge inprovement in speed.

If you are running Feisty, can enable the Feisty-backports repository in your /etc/apt/sources.list  by removing the ##'s from the backports lines. Then you can install version .70 from the repo's.

---

### Post by boss429 on 2007-08-23
Thanks!  After enabling the backport repos DosBox v.70 installed successfully.

---

### Post by MaindotC on 2007-12-23
I enabled the backports and it didn't show up.  Synaptic and apt kept offering .65.  I'm trying to go the "./configure" route - not much success as of yet...

Update: I installed the recommended development files and configured, make, and make installed!  It works and I am watching the intro to NHL 96 in PERFECT clarity and game speed!  Oh thank god!

How do you switch between dosbox and other windows on the desktop?

---

