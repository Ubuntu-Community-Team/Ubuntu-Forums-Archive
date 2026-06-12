---
title: "recent wine (1.5?) on lucid: how to ?"
date: 2012-09-16
forum: Wine
---

### Post by jan123 on 2012-09-16
I am using ubuntu lucid (LTS - long term support) on my production machines.
I want to try new windows software, but this fails.
The current packaged wine on lucid is 1.4, compiled in march 2012

I have seen that newer wine versions are available in precise.
On lucid, I can only install packages up to oneiric (dependencies in precise are for newer versions of libraries).
The oneiric wine 1.5 is dated april 2012, thus not very recent either.

How can I obtain / compile a newer package for lucid (or oneiric) ?
Would it be possible to keep compiling  lucid or oneiric with some frequency till their end-of-support

---

### Post by vexorian on 2012-09-16
Not even ubuntu-wine PPA is packaging 1.5 for lucid.

You will have to compile WINE's source tar.gz yourself.

Get the WINE version you want from: [https://sourceforge.net/projects/wine/files/Source/](https://sourceforge.net/projects/wine/files/Source/)

Then read this:
[http://www.winehq.org/docs/wineusr-guide/installing-wine-source](http://www.winehq.org/docs/wineusr-guide/installing-wine-source)

just know that instead of:
make install

You will need sudo make install

Although:
sudo checkinstall

Is probably better as it will allow you to uninstall.

---

### Post by jan123 on 2012-09-22
Thanks.
Long ago, I had some problems in wine-1.2 compiling.
The current base compiles well.
I do not need all documentation, so I needed to cherry-pick installation of -dev packages for my system.
Now, the current wine runs well.

---

