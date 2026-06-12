---
title: "gaim-xfire not compiling for pidgin in 64 bit"
date: 2008-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2008-01-08
When trying to compile gaim-xfire-0.6.1~20071109 in Ubuntu 7.10 64 bit, I get this message. It is looking for gaim and not finding Pidgin. How can I get this to work?

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/user/gaim-xfire-0.6.1~20071109/missing: Unknown `--run' option
Try `/home/user/gaim-xfire-0.6.1~20071109/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB2... yes
checking for LIBPURPLE... no
checking for GAIM... configure: error: Package requirements (gaim) were not met:

No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAIM_CFLAGS
and GAIM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
Sent at 10:27 PM on Tuesday
```

---

### Post by sethfc on 2008-01-09
good luck getting help

i am newb, running 64 bit also, and i cant get this ******* to install either

---

### Post by Cappy on 2008-01-09
This has been solved here:
[http://ubuntuforums.org/showthread.php?t=226456&page=9](http://ubuntuforums.org/showthread.php?t=226456&page=9)

---

