---
title: "Trouble compiling libvorbis-aotuv-b.4.51"
date: 2007-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Major_Kong on 2007-06-07
I'm having a little trouble creating the deb packages from the source. 

I downloaded the source from here - [http://xmixahlx.dyndns.org/debian/source/](http://xmixahlx.dyndns.org/debian/source/) - applied the patch and then when i try to create the packages using  
```
dpkg-buildpackage -rfakeroot
```

i get the following error: 

```
dpkg-buildpackage: source package is libvorbis-aotuv
dpkg-buildpackage: source version is 0.b4.51+20051117-0rarewares1
dpkg-buildpackage: source changed by mike gan <xmixahlx@yahoo.com>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 0.b4.51+20051117-0rarewares1
 debian/rules clean
/usr/bin/dpkg-buildpackage: 212: debian/rules: Permission denied

```

I can't seem to find what's the problem... :S

---

### Post by Major_Kong on 2007-06-07
/bump

---

### Post by Major_Kong on 2007-06-08
Ok... 

Is there a repo for Feisty Fawn (amd64) with these packages? A sort of ubuntu version of [http://www.rarewares.org/debian-info-misc.php#more-unofficial](http://www.rarewares.org/debian-info-misc.php#more-unofficial) ? 

Probably not...

---

### Post by gbesso on 2007-06-08
You need to make debian/rules executable.
```
chmod +x debian/rules
```

---

### Post by Major_Kong on 2007-06-08
Thx. :D

But know it get's stuck in this :( :

```
CFLAGS="-Wall -g -O2" ./configure --host=x86_64-linux-gnu  \
        --build=x86_64-linux-gnu --prefix=/usr \
        --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info \
        --libdir=/usr/lib/libvorbis-aotuv \
        --datadir=/usr/share/libvorbis-aotuv \
        --includedir=/usr/include/vorbis-aotuv
/bin/sh: ./configure: Permission denied
make: ** [config.status] Erro 126
```

---

### Post by gbesso on 2007-06-08
Same deal :)

```
chmod +x configure
```

On a side note, you might want to download the .tar.gz, .diff.gz, and .dsc files next time
and then use 
```
dpkg-source -x <dsc file>
```

It doesn't really make a difference but I find it easier.

---

### Post by Major_Kong on 2007-06-09
Thx. :D

---

### Post by Major_Kong on 2007-06-09
I'm trying to compile now the aotuv tweaked version of vorbis-tools, but again i get error messages:

speex_format.c:22:19: error: speex.h: Missing
speex_format.c:23:26: error: speex_header.h: Missing
speex_format.c:24:26: error: speex_stereo.h: Missing
speex_format.c:25:29: error: speex_callbacks.h: Missing

libspeex-dev is installed so i don't understand the problem. :S

---

### Post by Major_Kong on 2007-06-10
Found out on my own.

Aparently it's an old "bug" -> [https://trac.xiph.org/ticket/608](https://trac.xiph.org/ticket/608)

The solution is simple, just needed to make a change in speex_format.c 

Change 

#include <speex.h>
#include <speex_header.h>
#include <speex_stereo.h>
#include <speex_callbacks.h>

to 

#include <speex/speex.h>
#include <speex/speex_header.h>
#include <speex/speex_stereo.h>
#include <speex/speex_callbacks.h>

---------------------------

If anyone is interested in the "why?" :

> 
Aoyumi's later release of aoTuV beta 4 encoder as of November 2005** significantly improves Vorbis' quality** while increasing the compression ratio slightly.

Later on, Aoyumi released aoTuV beta 4.5 (later bugfixed with aoTuV beta 4.51) in December 2005, which improves low bit-rate quality even more. After extensive testing by Hydrogenaudio enthusiasts, aoTuV beta 4.51 is re-branded to aoTuV Release 1, and it became the recommended encoder of Hydrogenaudio.

Aoyumi keeps tuning aoTuV. The newest aoTuV encoder is aoTuV Beta 5. It is now undergoing peer-review at Hydrogenaudio.

Near the end of 2005, after aoTuV beta 4.51 was released, Xiph.org released Vorbis 1.1.2. Unfortunatly it only provides bugfixes to Vorbis 1.1.1. Although this is the 'official' version, it is not recommended by HA. 

---

