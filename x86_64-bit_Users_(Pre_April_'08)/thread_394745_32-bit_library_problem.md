---
title: "32-bit library problem?"
date: 2007-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mike Wilson on 2007-03-27
I have a 32-bit DTP application that runs under 32-bit Edgy but not 64-bit. Using ldd, the reply is "not a dynamic executable". Using file, I get:
/usr/share/PGS5-0-2-12/PageStream5: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped

So much for ldd. How else can I figure out which 32-bit libraries need to be added -- or is there a 32-bit-library compatibility package for 64-bit Edgy?

---

### Post by Kilz on 2007-03-27
> **Mike Wilson said:**
> I have a 32-bit DTP application that runs under 32-bit Edgy but not 64-bit. Using ldd, the reply is "not a dynamic executable". Using file, I get:
/usr/share/PGS5-0-2-12/PageStream5: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped

So much for ldd. How else can I figure out which 32-bit libraries need to be added -- or is there a 32-bit-library compatibility package for 64-bit Edgy?
[URL="http://tghc.org/32biton64bit.php"]
I have a page set up to answer this question. [/URL]

---

### Post by Mike Wilson on 2007-03-27
Thanks for that page reference. I have established that my problem app depends *only* on GLIBC_2.0; however, it is distributed as a tarball so your .deb procedure won't work, right?

---

### Post by Kilz on 2007-03-27
> **Mike Wilson said:**
> Thanks for that page reference. I have established that my problem app depends *only* on GLIBC_2.0; however, it is distributed as a tarball so your .deb procedure won't work, right?


Im not 100% sure. You might want to make sure that the linux32 package is installed, as well as all the packages listed on the page I linked to. As I understand it, GLIBC is so basic to a linux system we wouldnt be able to run any 32bit code without it installed.

---

