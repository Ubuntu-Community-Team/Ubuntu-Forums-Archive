---
title: "Compiler Error.. config.log shows.."
date: 2007-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by xeocub on 2007-02-25
Can't compile anything, with the common "Compiler cannot create executables" Error. I've followed all the other threads, doing 
apt-get update, upgrade
install build-essentials, xorg-dev... basically what people usually tell to do.

None of it works, however.. and when I check the config.log it tells me this:

> 
/bin/arch              = x86_64
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown


What does it mean that everything is unknown.. is this part of my problem?

---

### Post by RAOF on 2007-02-26
What is it that you're trying to compile?  It sounds like it's Wine.  Well:
[list]
[*]It's easier to just install an i386 .deb
[*]You need to install the libc-386-dev package
[/list]

---

### Post by xeocub on 2007-02-26
> **RAOF said:**
> What is it that you're trying to compile?  It sounds like it's Wine.  Well:
[list]
[*]It's easier to just install an i386 .deb
[*]You need to install the libc-386-dev package
[/list]

It doesn't matter what I am trying to install. And it wasn't wine. 

I am unable to compile anything basically... always the same error.

For example, when trying to install ntfs-3g drivers : 
> 
ulrich@clearboxlx:~/downloads/ntfs-3g-1.0$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables


---

### Post by RAOF on 2007-02-26
Well, it can help to know what you're trying to install, if only to make me not guess "wine" :).

And you have definitely got build-essential installed?  Or, more particularly, you have the following packages installed:
[list]
[*]libc6-dev
[*]gcc
[*]make
[/list]
And possibly the **libstdc++6-dev** package installed?

---

