---
title: "Library error:  wrong ELF class: ELFCLASS64"
date: 2007-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by dzimmerman on 2007-05-07
[FONT="Courier New"]error while loading shared libraries: libftdi.so.0: wrong ELF class: ELFCLASS64[/FONT]

libftdi.so.0 is a 32-bit library, and will be used exclusively by a 32-bit program.  I am running Feisty 7.04 (AMD64).  What is the correct way to resolve  this conflict between the 64-bit system and the 32-bit library?   Right now the library is located in /usr/local/lib/.

Thanks,

Dan

---

### Post by Kilz on 2007-05-07
> **dzimmerman said:**
> [FONT="Courier New"]error while loading shared libraries: libftdi.so.0: wrong ELF class: ELFCLASS64[/FONT]

libftdi.so.0 is a 32-bit library, and will be used exclusively by a 32-bit program.  I am running Feisty 7.04 (AMD64).  What is the correct way to resolve  this conflict between the 64-bit system and the 32-bit library?   Right now the library is located in /usr/local/lib/.

Thanks,

Dan

The reason for the error is it can only find a 64bit library. The correct way is [to go here]("http://packages.ubuntu.com/"), search for the package than contains the library. Download the i386 package. Use ```
sudo dpkg -x nameofpackage.deb
``` to extract the files in it. The extracted files will make a directory structure wherever they are extracted. Go into that structure to /usr/lib and copy those i386 files to /usr/lib32. Do not force architecture libraries in.

---

### Post by dzimmerman on 2007-05-07
Thanks, worked like a charm.

---

### Post by skidrash on 2007-10-09
rc: error while loading shared libraries: libreadline.so.4: wrong ELF class: ELFCLASS64

and libreadline version 4 does not seem to be available on Feisty,

Maybe I need to get the "rc" source and build and install it?

---

### Post by skidrash on 2007-10-09
UPDATE earlier in the path than the standard /usr/bin/rc, 

I had an install from a previous build -

I deleted that and it works fine now.

---

