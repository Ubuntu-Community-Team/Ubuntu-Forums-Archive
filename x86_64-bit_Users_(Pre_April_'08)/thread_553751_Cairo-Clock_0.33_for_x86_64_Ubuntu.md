---
title: "Cairo-Clock 0.33 for x86_64 Ubuntu?"
date: 2007-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Uber Nooblett on 2007-09-18
Hey Guys & Gals,

I've been using Cairo-clock 0.32 as available via current sources through Synaptic/Adept in Ubuntu/Kubuntu, I would however like very much to use the latest version with all the nice shiny new skins etc. 

The problem seems to be that there is only an i386 version for Ubuntu...

Is there any way to install Cairo-Clock 0.33 from source? if so please could someone give me a tut on this? pretty please! :D

Many thanks in advance

JJ

---

### Post by John.Michael.Kane on 2007-09-18
> **Uber Nooblett said:**
> Hey Guys & Gals,

I've been using Cairo-clock 0.32 as available via current sources through Synaptic/Adept in Ubuntu/Kubuntu, I would however like very much to use the latest version with all the nice shiny new skins etc. 

The problem seems to be that there is only an i386 version for Ubuntu...

Is there any way to install Cairo-Clock 0.33 from source? if so please could someone give me a tut on this? pretty please! :D

Many thanks in advance

JJ

Download the [release 0.3.3 - source-tarball]("http://macslow.thepimp.net/projects/cairo-clock/cairo-clock_0.3.3-1.tar.gz"), and make sure you have build-essential/check install installed.

```
gksudo aptitude install build-essential checkinstall
```

1) cd Desktop 

2) tar zxvf cairo-clock_0.3.3-1.tar.gz

3) cd cairo-clock-0.3.3

4) ./configure

5) make

6) sudo checkinstall -D "This will install it, and give you deb file, As well."

---

### Post by Uber Nooblett on 2007-09-18
Thanks :)

However, one slight snag when I got to the './configure' step:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for intltool >= 0.23... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

```

Any ideas?

---

### Post by Uber Nooblett on 2007-09-18
nvm, got that prob sorted, now another lol

```
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.10.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by Uber Nooblett on 2007-09-18
ironed out all the creases and got it installed :D

thank you very much for your help! :)

---

### Post by Uber Nooblett on 2007-09-18
bah, I spoke too soon. It wont start, I just get:

```
(cairo-clock:6439): librsvg-CRITICAL **: rsvg_handle_render_cairo_sub: assertion `handle != NULL' failed

```

repeatedly in the terminal when I try to start

---

### Post by Uber Nooblett on 2007-09-18
Solved, needed to run as root for some reason :D

Thanks very much for your help with the installing SD-Plissken :)


JJ

---

### Post by Pandemic187 on 2007-10-23
Apparently I still don't understand how to use make. Something else has to be typed other than JUST "make" right? Because when I type "make" I get...
```
bob@BobsLaptop:~/Desktop/cairo-clock-0.3.2$ make
make: *** No targets specified and no makefile found.  Stop.
```
What do I have to do so this will work?

---

### Post by John.Michael.Kane on 2007-10-23
> **Pandemic187 said:**
> Apparently I still don't understand how to use make. Something else has to be typed other than JUST "make" right? Because when I type "make" I get...
```
bob@BobsLaptop:~/Desktop/cairo-clock-0.3.2$ make
make: *** No targets specified and no makefile found.  Stop.
```
What do I have to do so this will work?
Did you run ./configure before running make?

Also you are doing this on and older version.

---

### Post by Pandemic187 on 2007-10-23
1. Yes I ran ./configure.

2. I'm using 7.04 right now.

---

