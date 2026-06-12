---
title: "Sources list for 64 distro different than 32 ?"
date: 2005-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by NoTiG on 2005-05-16
Hey .. just wondering. when you run the [automated script for beginners](http://www.ubuntuforums.org/showthread.php?t=22646) the sources list it uses is [here](http://download.ubuntuforums.org/ubuntusetup/sources.list) . THe problem is.. it works for the 32 bit distro but not for the 64 distro. More specifically the lines:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

will not work for 64, but will for 32. does anyone know the 64 bit version???

edit: actually the middle one... unstable works. the rest don't.

---

### Post by FluffyElmo on 2005-05-16
The 64bit version of the marillat repositories is here:
```
deb http://cyberspace.ucla.edu/marillat/ unstable main
```

You will may have problems with some packages though as this repository is built against debian-unstable which has updated a number of packages since the release of Hoary. Most will work though.

Also note that the script you are using tries to install both the w32codecs and flash which aren't available on 64bit. Java may be a problem as well since you'll need the amd64 version.

Hope this helps...

---

### Post by NoTiG on 2005-05-16
[QUOTE=FluffyElmo]The 64bit version of the marillat repositories is here:
```
deb http://cyberspace.ucla.edu/marillat/ unstable main
```

You will may have problems with some packages though as this repository is built against debian-unstable which has updated a number of packages since the release of Hoary. Most will work though.

Also note that the script you are using tries to install both the w32codecs and flash which aren't available on 64bit. Java may be a problem as well since you'll need the amd64 version.

Hope this helps...[/QUOTE]

tx :P those repositories are where the w32 codecs are... so i guess it doesnt make much difference if they are inaccessible.

---

