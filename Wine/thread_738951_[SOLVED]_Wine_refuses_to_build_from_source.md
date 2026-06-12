---
title: "[SOLVED] Wine refuses to build from source"
date: 2008-03-29
forum: Wine
---

### Post by soxs on 2008-03-29
I own a Phenom 9500 and I am trying to compile wine with the regarding patch, which can be found at winehq.org.
But I always get an error when trying to build patched wine.
make: *** [dlls] error 2
this occures for wine 0.957 and 0.9.58
plx help!
Note: I am on 64 bit and I know what I have to do, usually iot worked on an AMD X2

---

### Post by FrozenFox on 2008-03-29
Please post the output prior to (and after?) the "error 2", as the error # is seldom helpful. Usually prior to that, there will be a message showing what's actually wrong. Most of the time, it's a simple missing dependency.

BTW, why are you compiling anyway? There are .debs for 0.9.58 already at winehq.

---

### Post by soxs on 2008-03-29
Well, but in order to work properly with phenom, wine has to recogize it properly, which the unpatched version does not. Thats why I have to compile it. And I know how to pactch wine properly (cd
wine-source-dir && patch -Np1 < /patch/filename && tools/make_requests)
and I have all required dependncies installed ([http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit))

---

### Post by soxs on 2008-03-29
Irrelevant, made a dumb mistake.

---

### Post by ajackson on 2008-03-29
> **soxs said:**
> this is the output of rerunning make over 0.47 source (this is the second run over source, so, only errors keep showing):
```
/bin/sh: cannot create version-stamp: Permission denied

```
Is there already a version-stamp file in there and if so do you have write permission to it? Or do you have write permission to the loader directory?

---

### Post by soxs on 2008-03-29
I retried and am currently at make stage and it ran through without any errors.
I will now try to build a package with checkinstall.
Btw. is there another way to build a deb package?

Edit: checkinstall failed:
the last errors were:
```
Installing with make install...

====================== Installations-Ergebnisse ==========================
make[1]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools'
make[1]: »makedep« ist bereits aktualisiert.
make[1]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools'
make[1]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/libs'
make[2]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/libs/port'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/libs/port'
make[2]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/libs/wine'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/libs/wine'
make[2]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/libs/wpp'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/libs/wpp'
make[1]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/libs'
make[1]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools'
make[2]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/widl'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/widl'
make[2]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/winebuild'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/winebuild'
make[2]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/winedump'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/winedump'
make[2]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/winegcc'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/winegcc'
make[2]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/wmc'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/wmc'
make[2]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/wrc'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools/wrc'
make[1]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/tools'
make[1]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/include'
make[1]: Für das Ziel »all« ist nichts zu tun.
make[1]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/include'
make[1]: Betrete Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/include'
../tools/mkinstalldirs -m 755 /usr/local/include/wine/windows/ddk
mkdir /usr/local/include/wine
chmod 755 /usr/local/include/wine
chmod: Beim Setzen der Zugriffsrechte für &#8222;/usr/local/include/wine&#8220;: No such file or directory
make[1]: *** [/usr/local/include/wine/windows/ddk] Fehler 1
make[1]: Verlasse Verzeichnis '/home/bernhard/Desktop/w/wine-0.9.57/include'
make: *** [include/__install__] Fehler 2

```

EDIT: For those non germans around:

 Beim Setzen der Zugriffsrechte für xxx == While setting permissions for directory xxx
Fehler = error
Für das Ziel »xxxl« ist nichts zu tun. == nothing to do for target xxx
Betrete Verzeichnis == Enter directory
Verlasse Verzeichnis == leaving driectory
Installations-Ergebnisse == InstallationResults

---

### Post by YokoZar on 2008-03-29
> **soxs said:**
> I retried and am currently at make stage and it ran through without any errors.
I will now try to build a package with checkinstall.
Btw. is there another way to build a deb package?
Yes, a much better way is to fork the official package.
apt-get source wine
change to the package directory, apply your patch there, and then dpkg-buildpackage -rfakeroot

You'll need the dpkg-dev package to do that.

---

### Post by soxs on 2008-03-30
I was able to build wine with  YokoZar's method. Thx a lot.

---

