---
title: "libXm.So.3"
date: 2009-03-02
forum: x86 64-bit Users
---

### Post by skeety on 2009-03-02
After installing netvault bakbone 8.21 & running nvgui to try & run the bakbone application I got the following error:-

***'error while loading shared librairies: libXm.So3: cannot open shared object file: No file or directory'***

Any help resolving the error much appreciated.

Regards
Skeety.

---

### Post by kyouens on 2009-03-03
Try this.  I had to do something similar to get my Citrix ICA client to work.

1. Download 32 bit package of libmotif3 from [http://packages.ubuntu.com/intrepid/i386/libmotif3/download](http://packages.ubuntu.com/intrepid/i386/libmotif3/download).

2. Extract files from the downloaded package:

```
dpkg -x libmotif3_2.2.3-2_i386.deb /tmp
```

3. Copy libmotif3 library to lib32:

```
sudo cp /tmp/usr/lib/libXm.so.3 /usr/lib32/
```

4. It should hopefully work now. Extracted files in /tmp can be deleted.

---

