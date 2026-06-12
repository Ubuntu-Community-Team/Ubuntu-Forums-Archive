---
title: "nspluginwrapper packages for Gutsy"
date: 2007-07-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by j_dog on 2007-07-05
I know I saw these somewhere, I can't seem to find them !

---

### Post by sj3fk3 on 2007-07-05
> **j_dog said:**
> I know I saw these somewhere, I can't seem to find them !

apt-get update ; apt-get install nspluginwrapper

---

### Post by j_dog on 2007-07-05
Thank you for your help !!

I gave it a try.    I get this upon install.       "dpkg: error processing /var/cache/apt/archives/nspluginwrapper_0.9.91.4-2ubuntu2_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386
Errors were encountered while processing:
 /var/cache/apt/archives/nspluginwrapper_0.9.91.4-2ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


What now ?#-o

---

### Post by sj3fk3 on 2007-07-05
> **j_dog said:**
> Thank you for your help !!

I gave it a try.    I get this upon install.       "dpkg: error processing /var/cache/apt/archives/nspluginwrapper_0.9.91.4-2ubuntu2_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/nspluginwrapper/i386/linux/npviewer.bin', which is also in package nspluginwrapper-i386
Errors were encountered while processing:
 /var/cache/apt/archives/nspluginwrapper_0.9.91.4-2ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


What now ?#-o

apt-get remove nspluginwrapper-i386 first? Looks like you already have a other version there.

---

### Post by j_dog on 2007-07-05
Awesome !   I think that worked !             "The following NEW packages will be installed:
  nspluginwrapper
0 upgraded, 1 newly installed, 0 to remove and 15 not upgraded.
Need to get 0B/103kB of archives.
After unpacking 365kB of additional disk space will be used.
(Reading database ... 125243 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_0.9.91.4-2ubuntu2_amd64.deb) ...
Setting up nspluginwrapper (0.9.91.4-2ubuntu2) ..."


Thanks Again !\\:D/

---

### Post by Sockerdrickan on 2007-07-05
Need to get 0B/103kB of archives.

Might be the version you had :P

---

### Post by j_dog on 2007-07-05
NO.....wait a minute here. I spoke to soon !   Still no Flash !](*,)

---

### Post by sj3fk3 on 2007-07-05
> **j_dog said:**
> NO.....wait a minute here. I spoke to soon !   Still no Flash !](*,)

Ah, but getting nspluginwrapper is only the first step, then you need to download install_flash_player_9_linux.tar.gz from the adobe site, unpack it and move libflashplayer.so to /usr/lib/mozilla/plugins/ and then type nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by j_dog on 2007-07-05
That worked !!  I thank you for your kind help !!   =D>

---

### Post by sj3fk3 on 2007-07-06
> **j_dog said:**
> That worked !!  I thank you for your kind help !!   =D>

dmi

---

