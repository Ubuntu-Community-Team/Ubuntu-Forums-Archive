---
title: "Help installing 32-bit programs (such as ZSNES)"
date: 2008-06-20
forum: x86 64-bit Users
---

### Post by mr_nodge on 2008-06-20
Hi.  I am new to Linux and have been trying for days how to install a program called ZSNES.  The way I am wanting to do this is by not relying on some form of automatic downloads... as in manually installing the 32-bit dependencies so that I can get ZSNES (and any other software that is 32-bit for that matter) working on a computer that has no Internet connection.

For example, SDL refuses to install from source.  The install notes say to simply run ./configure then make, but configure fails.

Alien will not let me convert the 32-bit binaries to deb also.

I also see no point in setting up a chroot (never done that before anyway) because that even relies on repositories (from an automatic download), although in the --help, it mentioned a way to install necessary files from a tarball instead and I have had no success with that also.

Anyone managed to do any of this?

---

### Post by pixel :-) on 2008-06-20
you can't compile it,there are stuff that are not portable in the code thats why it's not in the repositories.I tried to install it with ia32-libs but

*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib32/libc.so.6(__fortify_fail+0x48)[0xf7c8b3b8]
/lib32/libc.so.6[0xf7c89a50]
zsnes[0x8056c1b]
........

install wine, and launch the windows version[http://prdownloads.sourceforge.net/zsnes/zsnesw151.zip]("http://prdownloads.sourceforge.net/zsnes/zsnesw151.zip") under it.The easiest by far.You'll need to install wine also [http://www.mininova.org/tor/1512836]("http://www.mininova.org/tor/1512836").

try to install wine,it will complain about dependencies,note them down and download them from here [http://archive.ubuntu.com/ubuntu/pool/]("http://archive.ubuntu.com/ubuntu/pool/").Olmost certain they are in main and universe.Warning,this step may get painfull,as you may have other dependencies that must be satisfied by the new pakages,and you have to install them in the right order with "sudo dpkg -i pakage.deb".

Hope it's not to buggy

---

