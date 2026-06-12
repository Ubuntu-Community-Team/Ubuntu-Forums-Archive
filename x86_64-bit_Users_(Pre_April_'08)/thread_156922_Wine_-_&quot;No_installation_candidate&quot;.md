---
title: "Wine - &quot;No installation candidate&quot;"
date: 2006-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by BjornHaland on 2006-04-08
I did:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
sudo nano /etc/apt/sources.list
``` And added:
```
deb http://wine.sourceforge.net/apt/ binary/ 
deb-src http://wine.sourceforge.net/apt/ source/

``` Then
```
sudo apt-get update
``` Then
```
sudo apt-get install wine
``` Error:
```
Funnet http://wine.sourceforge.net binary/ Release
Funnet http://wine.sourceforge.net source/ Release
Ign http://wine.sourceforge.net binary/ Packages
Ign http://wine.sourceforge.net source/ Sources
Funnet http://wine.sourceforge.net binary/ Packages
Funnet http://wine.sourceforge.net source/ Sources
Hentet 5B på 5s (1B/s)
Leser pakkelister ... Ferdig
[COLOR=RoyalBlue]bjoern@shapeir:~$ sudo apt-get install wine
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold ... Ferdig
Pakken wine er ikke tilgjengelig, men en annen pakke henviser til den.
Dette kan bety at pakken mangler, er utgått, eller bare finnes
tilgjengelig fra en annen kilde.
E: Pakken wine har ingen installasjonskandidat[/COLOR]
``` Translation: (an attempt)
```

Found http://wine.sourceforge.net binary/ Release
Found http://wine.sourceforge.net source/ Release
Ign http://wine.sourceforge.net binary/ Packages
Ign http://wine.sourceforge.net source/ Sources
Found http://wine.sourceforge.net binary/ Packages
Found http://wine.sourceforge.net source/ Sources
Fetched 5B in 5s (1B/s)
Reading package lists ... Done
[COLOR=RoyalBlue]bjoern@shapeir:~$ sudo apt-get install wine
Reading package lists ... Done
Creating overview of dependency relations ... Done
Package wine is not available, but another package is pointing to it.
This could mean the package is missing, has expired or is only
available from another source.
E: Package wine has no installation candidate[/COLOR]

```

* Thanks Stormbringer.

---

### Post by Stormbringer on 2006-04-08
There is no native AMD64 version of WINE as it's a >> 32-Bit << Win32 Emulator.

If you need to run WINE on AMD64 Ubuntu you may want to consider installing a 32-Bit chroot to install WINE inside of it. Simply follow the [32-Bit Chroot on 64-Bit Installs]("http://ubuntuforums.org/showthread.php?t=24575") HOWTO to get it installed.

If you don't plan to runs games you may be better off by using VMware or QEMU instead.

---

