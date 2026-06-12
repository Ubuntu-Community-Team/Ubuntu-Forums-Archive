---
title: "How do I compile source code on an iMac?"
date: 2006-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by shubox357 on 2006-04-17
Hey Everybody!
I would like to compile some source code for 2 programs, 1) Samba and 2)Wired. The only problem is, i dont know how to compile source code (](*,) )! Is it difficult? What must I type into the command line? Thanks!

---

### Post by Miguel on 2006-04-17
**READ FIRST:** Samba is on the repositories. Installing from them via synaptic is faster and way easier than compiling from source.

Compiling things from source isn't that difficult... once you learn it. It is just a bit tedious to learn... and a bit of trial and error. 

The first thing you need is a compiler and the basic development libraries (the ones named lib****-dev). To do this, just type (or install via Synaptic)
```

$ sudo apt-get install build-essential

```

This will install  C and C++ compiler, gnu make (to automate compilations) and the development parts of libc. The next thing you must do is reading thoroughly the README and INSTALL files of the package you have downloaded. These explain installations and configure possibilies on compilation. In general, this procedure is usually

```

$ cd folder-containing-the-source
$ ./configure
$ make
$ make install

```

Where you should watch for errors. For a system-wide install, the only step that needs root privileges is the make install one, which usually copies files to /usr/local.

Please note that on Debian, Fedora and most other derived distro's ./configure will terminate with errors. This is because libraries do not include the development headers.

**Exapmle:** compiling FreeCiv 2.1.0-beta from source

I first download the source from freeciv.org and untar it in ~/freeciv-2.1.0-beta1/. I then cd to that folder and will configure it. Let's suppose that I want it to use the Xaw widgets for the client:
```

miguel@ubuntu:~/freeciv-2.1.0-beta1$ ./configure --help
[...]
Optional Features:
  --enable-client=no/yes/xaw3d/xaw/gtk/win32/sdl/ftwl
                          compile a client default=yes (if yes, guess type)
[...]
miguel@ubuntu:~/freeciv-2.1.0-beta1$ ./configure --enable-client=xaw
[here go many, many lines until...]
configure: error: specified client 'xaw' not configurable -- need Xpm library and development headers; perhaps try/adjust --with-xpm-lib

```

Look at the name: xpm library. This means that I either don't have libxpm installed or the development version libxpm-dev. I now would run synaptic and see if I have it installed or not. As it turns out, I have libxpm4 installed, but not libxpm-dev. I will install it and then reissue the configure command (I will suppose we are at the same dir, thus ommiting the "miguel@ubuntu:~/freeciv-2.1.0-beta1" part). Well, it turned out I needed a couple of more libs. After installing them all, the result was:
```

$ sudo apt-get install libxpm-dev
$ ./configure --enable-client=xaw
[many lines and ends up with...]
config.status: executing fc_default-1 commands
extending po/Makefile
config.status: executing fc_default-2 commands
silencing po/Makefile
config.status: executing fc_default-4 commands
modifying po/Makefile add-comments/escape
config.status: executing fc_default-5 commands
config.status: executing default commands

```

We have configured the source, and are ready to compile (or build) it. To do this, I'll issue the make command (some programs allow to build just parts of the program, with commands such as make name-of-part). Let's hope it doesn't give us any errors, as these are harder to fix:

```

$ make
[lines and lines of undecipherable text...]
make[2]: se sale del directorio `/home/miguel/freeciv-2.1.0-beta1'
make[1]: se sale del directorio `/home/miguel/freeciv-2.1.0-beta1'
$

```

Well, output is in spanish but... No errors!!! We have just compiled our first program, and are nearly ready to kick AI a$$ and rule the world muahahaha. I say nearly, because I still need to install it. For that, I would do
```

$ sudo make install

```

because I'm installing it to a place where my user has no privileges, and I want all my users to lose against me on a freeciv game :twisted:.  Of course, I will not install it, as I have it already installed, using the GTk client (which is, IMHO nicer). And that's it. The last thing you should know is that there are some programs easier to compile than others, and that some code that compiles OK in x86 doesn't in Mac (blame the developers). 

Hope it helps,

Miguel

PS: I have the feeling I have re-written a HOWTO: compile from source. Or... HOWTO: compile freeciv from source.

---

### Post by linear on 2006-04-17
[quote=Miguel]I have the feeling I have re-written a HOWTO: compile from source.[/quote]
Yes, and a very good one too!
 
I'd also point to the wiki: [CompilingSoftware]("https://wiki.ubuntu.com/CompilingSoftware"), and mention the use of **[checkinstall]("https://wiki.ubuntu.com/CheckInstall") **instead of **make install** - allows easy removal if you change your mind.

---

### Post by plush on 2006-04-17
I need some help from my fellow powerpc64 users.  Here's what I get when trying to compile the latest 2.6.16 kernel....

> "ld: drivers/built-in.o section .init.text exceeds stub group size
ld: arch/powerpc/kernel/built-in.o section .init.text exceeds stub group
size
ld: init/built-in.o section .init.text exceeds stub group size
ld: net/built-in.o section .text exceeds stub group size
ld: drivers/built-in.o section .text exceeds stub group size
ld: block/built-in.o section .text exceeds stub group size
ld: security/built-in.o section .text exceeds stub group size
ld: ipc/built-in.o section .text exceeds stub group size
ld: fs/built-in.o section .text exceeds stub group size
ld: mm/built-in.o section .text exceeds stub group size
ld: kernel/built-in.o section .text exceeds stub group size
ld: arch/powerpc/platforms/built-in.o section .text exceeds stub group
size
ld: arch/powerpc/kernel/built-in.o section .text exceeds stub group size
ld: arch/powerpc/kernel/head_64.o section .text exceeds stub group size
drivers/built-in.o: In function `.platinumfb_probe':platinumfb.c:(.text
+0x84a1c): undefined reference to `.nvram_read_byte'
:platinumfb.c:(.text+0x84ac0): undefined reference to `.nvram_read_byte'
drivers/built-in.o: In function `.imsttfb_probe':imsttfb.c:(.text
+0x88344): undefined reference to `.nvram_read_byte'
:imsttfb.c:(.text+0x88368): undefined reference to `.nvram_read_byte'
drivers/built-in.o: In function `.control_init':controlfb.c:(.init.text
+0x52ec): undefined reference to `.nvram_read_byte'
drivers/built-in.o:controlfb.c:(.init.text+0x54dc): more undefined
references to `.nvram_read_byte' follow
"

I have installed:  libqt3-mt-dev libncurses-dev build-essential fakeroot kernel-package bin86.  Also, I have I have gcc-3.4, gcc++ 3.4, gcc, gcc 3.3, gcc 3.3 base, gcc 3.4 base, gcc 4.0 + base and binutils.

Please help!  I tried to use my configure file from /boot, by copying it into /usr/src/linux, and then doing either "make xconfig" or "make oldconfig".  I always get the same message (above) after like 10 minutes of compiling...  ](*,)

---

### Post by Miguel on 2006-04-17
Thanks for the link to the wiki, Linear. It covers a few more things than what I did. And, after reading the wiki (actually, after checking your link) I nearly busted in laughs. I should check the wiki more often ;)

* To Plush:*

Alan Modra answered [this question](http://ozlabs.org/pipermail/linuxppc64-dev/2005-December/007281.html) with the following:
[quote=Alan Modra]
> I never saw those before, so i wonder if this are harmless messages coming

They are harmless.  I made ld a little too paranoid on 2005-09-19, and
cured the paranoia on 2005-11-18.  If you update to current binutils the
warnings should disappear, I think
[/quote]

The other messages referring nvram_read_byte seem to suggest that you have left unchecked a certain option during configure. However, if these messages appear with the default config, it is likely all this is harmless warning. Anyway, please note that the only 64 bit code I have compiled is PWscf (a GPL quantum calculations package) on an Itanium2 cluster.

---

### Post by plush on 2006-04-18
Thanks Miguel, great Avatar btw hahahaha.  Yeah I know those messages about the stubs are harmless, and strangely enough they still appear even after installing binutils.  It's that damn nv_ram_byte message!  I wish I knew what the hell it meant.  :-k

---

### Post by plush on 2006-04-18
Removed

---

