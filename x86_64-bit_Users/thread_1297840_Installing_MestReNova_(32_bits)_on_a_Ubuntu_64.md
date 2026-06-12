---
title: "Installing MestReNova (32 bits) on a Ubuntu 64"
date: 2009-10-22
forum: x86 64-bit Users
---

### Post by acrocephalus on 2009-10-22
Hello!
I am trying to install a 32 package in a Ubuntu 9.04 64 using the getlibs. First, I run the sentence:

```
sudo dpkg -i --force-architecture mestrenova*deb
```

and I get this message

```
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 266467 files and directories currently installed.)
Preparing to replace mestrenova 6.0.2-5484 (using mestrenova_6.0.2-5484_i386.deb) ...
Unpacking replacement mestrenova ...
dpkg: dependency problems prevent configuration of mestrenova:
 mestrenova depends on libc6-i686 (>= 2.9); however:
  Package libc6-i686 is not installed.
dpkg: error processing mestrenova (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mestrenova
```

Then, I run

```
sudo getlibs /usr/local/bin/MestReNova
```

and I get this message

```
Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -l i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64l amd64librarytoinstall.so
```

I know I'm doing something wrong, but I have no idea on what can I do. Can anyone help?
Cheers!

Dani

---

### Post by macaholic on 2009-10-24
Have you tried installing libc6-i386? ```
sudo apt-get install libc6-i386
```
Not sure if that will fix the problem though...It's odd that it requires i686.

---

### Post by acrocephalus on 2009-10-26
I already have the libc6-i386 installed, so I don't know what to do. I really need this software, so any help will be really apreciated.

Dani

---

### Post by Yellow Pasque on 2009-10-26
A link to the software would help. Also, you're probably trying to run getlibs on a launcher script. Open the script in a text editor and see if you can figure out where the actual binary executable is.

---

### Post by acrocephalus on 2009-10-28
I'm quite a newby with Linux, so I paste the script here

```
#!/bin/bash
MESTRENOVADIR=/usr/local/share/MestReNova
MESTRENOVALIB=$MESTRENOVADIR/lib
LD_LIBRARY_PATH=$MESTRENOVALIB:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
export LC_NUMERIC=C
$MESTRENOVALIB/MestReNova $*
```

I also give you a link to the soft:

[http://mestrelab.com/]("http://mestrelab.com/")

---

### Post by acrocephalus on 2009-11-11
Anyone could help??
Cheers!

Dani

---

