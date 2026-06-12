---
title: "[SOLVED] sauerbraten 64bit debs"
date: 2008-06-29
forum: x86 64-bit Users
---

### Post by Zopiac on 2008-06-29
does anyone know of any?

---

### Post by harvey186 on 2008-06-29
search here [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by Zopiac on 2008-06-29
> **harvey186 said:**
> search here [http://www.getdeb.net/](http://www.getdeb.net/)

it only has the older version...

---

### Post by Rhubarb on 2008-06-29
It may be easier to compile it yourself (that's what I do).
[http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten](http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten)

Once you've extracted sauerbraten_2008_06_20_ctf_edition_linux.tar.bz2, download and extract patch_2008_06_20_linux.tar.bz2 over the top (so it just updates your sauerbraten directory), then you may proceed to compiling it yourself.

---

### Post by Zopiac on 2008-06-29
> **Rhubarb said:**
> It may be easier to compile it yourself (that's what I do).
[http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten](http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten)

Once you've extracted sauerbraten_2008_06_20_ctf_edition_linux.tar.bz2, download and extract patch_2008_06_20_linux.tar.bz2 over the top (so it just updates your sauerbraten directory), then you may proceed to compiling it yourself.

how do i compile? lol im new at that. is there a script, or a terminal command, or what?

---

### Post by soxs on 2008-06-30
to compile, change into the directory in thhe extracted folder named < src >
open a console and type:
```
sudo make install
```
afterwards you can run the 2 scripts in the download folder by doubleclick.

To make it possible to run it via typing sauerbraten in a terminal do the following steps:
```
sudo nano /usr/bin/sauerbraten
```

Add these lines (the file should be empty, if you removed the deb, if not purge the debs first)

```
#!/bin/bash
cd /the/persistant/sauerbraten/folder
sh ./sauerbraten_unix
```

make it executableand accessable by your user
```
sudo chmod 755 -vf /usr/bin/sauerbraten

```

You can now aswell add a shortcut to your panel , select "add to panel" -> "userdefined application starter" and type sauerbraten (this will now run sauerbraten)

---

