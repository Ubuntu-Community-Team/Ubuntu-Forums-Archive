---
title: "Compiling 32-bit apps on 64"
date: 2007-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lucretia9 on 2007-07-17
Hi,

I'm new to Ubuntu (previously on Gentoo) and 64-bit. Now I want to compile some of the NeHe samples but they require either porting or 32-bit compile. As I just want to test the 3D card, I'd rather just use a 32-bit compiler. I've tried -m32 but it throws up the following error:

```

gcc -Wall -pedantic -ansi -m32 lesson06.c -o lesson06 -L/usr/X11R6/lib32 -L/usr/lib32 -lGL -lGLU -lXxf86vm
In file included from /usr/include/features.h:346,
                 from /usr/include/stdio.h:28,
                 from lesson06.c:13:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
make: *** [all] Error 1

```

Did a search, HDD and these forums, nothing about this file on feisty. Synaptic doesn't have any ia32-libs-dev package.

I'd also like a 32-bit GNAT as I have some source I'd like to get working again. Is there support for this?

Thanks,
Luke.

---

### Post by stmiller on 2007-07-17
You could possibly just fetch the 32bit GNAT deb and install that.

[http://packages.ubuntu.com/feisty/devel/gnat](http://packages.ubuntu.com/feisty/devel/gnat)

if that would work. And install with $ dpkg -i --force-architeture packagename.deb

Or possibly extract the 32bit executable from that 32bit deb and run it.


And Debian has debs for ia32-libs-dev: (interesting that Ubuntu does not!?)

here: [ia32-libs-dev]("http://packages.debian.org/cgi-bin/search_packages.pl?keywords=ia32-libs-dev&searchon=names&subword=1&version=all&release=all")

You can install those Debian packages in Ubuntu.

---

### Post by NiN on 2007-07-17
You need the libc6-dev-i386 package.

There is a nifty little tool you want to know: apt-file :)

```

 apt-file search stubs-32.h
libc6-dev-i386: usr/include/i486-linux-gnu/gnu/stubs-32.h

```

The package for apt-file is in the repos.
Have fun.

[edit]
fixed typo and noted package location
[/edit]

---

### Post by Lucretia9 on 2007-07-18
> **NiN said:**
> You need the libc6-dev-i386 package.

There is a nifty little tool you want to know: apt-file :)

```

 apt-file search stubs-32.h
libc6-dev-i386: usr/include/i486-linux-gnu/gnu/stubs-32.h

```


Yeah, great!

```

$ apt-file search stubs-32.h
$

```

That worked.

> **NiN said:**
> 
The package for apt-file is in the repos.
Have fun.

[edit]
fixed typo and noted package location
[/edit]

Yeah, but the file that was in the previous version of ubuntu which has this file in, isn't!

Luke.

---

### Post by Lucretia9 on 2007-07-20
Just to point out that installing this "Debian" package libc6-dev-i386 works, but then you have to create symlinks in /usr/lib32 to make the compiles go, usually from *.so.1 -> *.so

Everything else in the previous post was not helpful at all. They may as well have said "RTFM"

Luke.

---

### Post by MatiasZ on 2007-11-09
> **Lucretia9 said:**
> Just to point out that installing this "Debian" package libc6-dev-i386 works, but then you have to create symlinks in /usr/lib32 to make the compiles go, usually from *.so.1 -> *.so

Everything else in the previous post was not helpful at all. They may as well have said "RTFM"

Luke.
Hi, sorry to revive this, but I'm having the same trouble as you did, but I can't seem to get it to work, and I think it has something to do with what you said in your last post. After installing libc6-dev-i386, the compiling error changed from the 'stubs-32.h' missing file to this:

> /usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libgcc.a when searching for -lgcc


I see that I should create the symlinks but have no idea at all how to do this correctly. Could you give me a hand with this??

Thanks in advance ;)

Matias

---

### Post by rwalk on 2008-03-26
See [http://ubuntuforums.org/showthread.php?t=614403](http://ubuntuforums.org/showthread.php?t=614403) for the solution. That is, install the "multilib" package.

---

### Post by Yellow Pasque on 2008-03-26
> **rwalk said:**
> See [http://ubuntuforums.org/showthread.php?t=614403](http://ubuntuforums.org/showthread.php?t=614403) for the solution. That is, install the "multilib" package.
rwalk, thank you for registering and providing a solution in an older thread that's bound to get hits from the internal and external search engines.

---

