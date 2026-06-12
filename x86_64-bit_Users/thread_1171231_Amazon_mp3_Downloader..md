---
title: "Amazon mp3 Downloader."
date: 2009-05-27
forum: x86 64-bit Users
---

### Post by Mind Stab on 2009-05-27
I recently downloaded the new Amazonmp3 downloder, which I found was for 32 bit linux, therefore "wrong architecture i386."  I followed instructions from _[ here]("http://ubuntuforums.org/showthread.php?t=692590")_ but I got this when running

```
sudo dpkg --install --force-architecture amazonmp3.deb
``````
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 231488 files and directories currently installed.)
Preparing to replace amazonmp3 1.0.3-1 (using amazonmp3.deb) ...
Unpacking replacement amazonmp3 ...
dpkg: dependency problems prevent configuration of amazonmp3:
 amazonmp3 depends on libboost-thread1.34.1; however:
  Package libboost-thread1.34.1 is not installed.
 amazonmp3 depends on libboost-iostreams1.34.1; however:
  Package libboost-iostreams1.34.1 is not installed.
 amazonmp3 depends on libboost-signals1.34.1; however:
  Package libboost-signals1.34.1 is not installed.
 amazonmp3 depends on libboost-date-time1.34.1; however:
  Package libboost-date-time1.34.1 is not installed.
dpkg: error processing amazonmp3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Errors were encountered while processing:
 amazonmp3

```And when running ```
getlibs -l /usr/bin/amazonmp3
```I kept getting ```
No match for amazonmp3
No packages to install

```

What should I do?

---

### Post by oldos2er on 2009-05-27
Use [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by pixel :-) on 2009-05-27
what oldos2er said

for your problem

getlibs /usr/bin/amazonmp3

the -l flag treats "/usr/bin/amazonmp3" as a library file, and searches for the corresponding package

---

