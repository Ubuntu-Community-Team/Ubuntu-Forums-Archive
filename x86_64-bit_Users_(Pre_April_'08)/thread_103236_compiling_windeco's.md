---
title: "compiling windeco's"
date: 2005-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Terracotta on 2005-12-13
Hye,
I've been trying to compile the windeco's from source from KDE-look.org, but it always gives the same error:
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

It does this during ./configure, I'm new to compiling (a guy helped me to compile xinelib from source, and it works now but whenever I try to compile something myself it doesn't work), I get this mistake with ever windeco I tried, can anyone help me with this?
tx

Edit: I don't know where to put this but: would it be possible in dapper to have a lot more windeco's installed? in xubuntu-desktop it's been done, and it really nice to be able to just choose another deco, instead of compiling :s.

---

### Post by daller on 2005-12-14
What windeco?

...This one comes with an ubuntu .deb:

[http://kde-look.org/content/show.php?content=23579](http://kde-look.org/content/show.php?content=23579)

---

### Post by Terracotta on 2005-12-14
indeed it does, but it's a i386 deb package, I just thought I'd make a 64bit .deb from source, but well, :s no deco I try to compile really compiles.

---

### Post by Navyblue on 2005-12-20
I used to have problem as well compiling window decoration.

This thread might help you:

[http://ubuntuforums.org/showthread.php?t=88396](http://ubuntuforums.org/showthread.php?t=88396)

---

### Post by freedom on 2005-12-20
I like to have many styles and decorations in my KDE.
I'm also amd64 user and I compile many windeccos and themes from kde-look.org. Here is the thing...
You need kdelibs4-dev, libqt3-mt-dev and xlibs-dev for styles
and for window decorations also kdebase-dev
and build-essentials of course. :smile: 
and all works with
```
./configure --prefix `kdeconfig -prefix`
make
sudo make install
```

but I like to use checkinstall to make a .deb package so the uninstall is much easier
```
sudo checkinstall -D make install
```

hope that help

---

### Post by Terracotta on 2006-01-07
[QUOTE=freedom]
```
./configure --prefix `kdeconfig -prefix`
make
sudo make install
```

but I like to use checkinstall to make a .deb package so the uninstall is much easier
```
sudo checkinstall -D make install
```

hope that help[/QUOTE]

before anyone else tries this: it should be:
```
./configure --prefix='kdeconfig -prefix'
```
well I still have a problem:
```

grep: /lib/libacl.la: No such file or directory
/bin/sed: can't read /lib/libacl.la: No such file or directory
libtool: link: `/lib/libacl.la' is not a valid libtool archive
make[3]: *** [kwin_deKorator_config.la] Fout 1
make[3]: Leaving directory `/home/terracotta/Installs/deKorator-0.2-fix1/client/config'
make[2]: *** [all-recursive] Fout 1
make[2]: Leaving directory `/home/terracotta/Installs/deKorator-0.2-fix1/client'
make[1]: *** [all-recursive] Fout 1
make[1]: Leaving directory `/home/terracotta/Installs/deKorator-0.2-fix1'
make: *** [all] Fout 2

```
Can anyone help me with this?

---

