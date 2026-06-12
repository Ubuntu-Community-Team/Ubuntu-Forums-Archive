---
title: "Can't install wine on my machine due to libldap version"
date: 2015-10-15
forum: Wine
---

### Post by clemensius on 2015-10-15
Hello,
this is my first post on this forum.

As the title indicates I've troubles installing wine on my machine. I'm running Ubuntu Mint 17.2 (and I'm native German speaker, thats why some of my outputs are in German).

```

cat /proc/version 
Linux version 3.16.0-38-generic (buildd@allspice) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015

lsb_release -a
No LSB modules are available.
Distributor ID: LinuxMint
Description:    Linux Mint 17.2 Rafaela
Release:        17.2
Codename:       rafaela

```

when running apt-get install wine I get this output:
```
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Einige Pakete konnten nicht installiert werden. Das kann bedeuten, dass
Sie eine unmögliche Situation angefordert haben oder, wenn Sie die
Unstable-Distribution verwenden, dass einige erforderliche Pakete noch
nicht erstellt wurden oder Incoming noch nicht verlassen haben.
Die folgenden Informationen helfen Ihnen vielleicht, die Situation zu lösen:

Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 wine : Hängt ab von: wine1.6 soll aber nicht installiert werden oder
                       wine1.7 soll aber nicht installiert werden
E: Probleme können nicht korrigiert werden, Sie haben zurückgehaltene defekte Pakete.

```

aptitude gives me more output:
```
 Die folgenden NEUEN Pakete werden zusätzlich installiert:   libasn1-8-heimdal:i386{a} libdb5.3:i386{a} libgssapi3-heimdal:i386{a} libhcrypto4-heimdal:i386{a} libheimbase1-heimdal:i386{a} libheimntlm0-heimdal:i386{a}   libhx509-5-heimdal:i386{a} libkrb5-26-heimdal:i386{a} liblcms2-2:i386{a} libldap-2.4-2:i386{ab} libroken18-heimdal:i386{a} libsasl2-2:i386{a} libsasl2-modules-db:i386{a}   libwind0-heimdal:i386{a} ocl-icd-libopencl1:i386{a} wine wine1.6 wine1.6-amd64{a} wine1.6-i386:i386{a} Die folgenden Pakete werden EMPFOHLEN, aber NICHT installiert:   fonts-horai-umefont fonts-unfonts-core libcapi20-3 libgif4:i386 libosmesa6 libosmesa6:i386 libp11-kit-gnome-keyring:i386 p11-kit-modules:i386 unixodbc unixodbc:i386   winbind wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8 winetricks 0 Pakete aktualisiert, 19 zusätzlich installiert, 0 werden entfernt und 26 nicht aktualisiert. 
34,3 MB an Archiven müssen heruntergeladen werden. Nach dem Entpacken werden 251 MB zusätzlich belegt sein. 
Die folgenden Pakete haben verletzte Abhängigkeiten:  
libldap-2.4-2 : Beschädigt: libldap-2.4-2:i386 (!= 2.4.40+dfsg-1) aber 2.4.31-1+nmu2ubuntu8.2 soll installiert werden.  
libldap-2.4-2:i386 : Beschädigt: libldap-2.4-2 (!= 2.4.31-1+nmu2ubuntu8.2) aber 2.4.40+dfsg-1 ist installiert. 

Die folgenden Aktionen werden diese Abhängigkeiten auflösen:       Beibehalten der folgenden Pakete in ihrer aktuellen Version: 1)     libldap-2.4-2:i386 [Nicht installiert] 2)     wine [Nicht installiert] 3)     wine1.6 [Nicht installiert] 4)     wine1.6-amd64 [Nicht installiert] 5)     wine1.6-i386:i386 [Nicht installiert]    Diese Lösung akzeptieren? [Y/n/q/?]
```

In my interpretation of this output aptitude tries to tell me that my libldap is to recent for wine. thats why i added the ppa:ubuntu-wine/ppa but after an apt-get update the output doesn't change...

is there a possibility do downgrade my libldap?

if t try to uninstall it aptitdue list the dependencies:
```

 postgresql-9.4 : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
 gconf-service-backend : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
 libreoffice-core : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
 libhdb9-heimdal : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
 samba-common-bin : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
 libldb1 : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
 samba-libs : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
 libcurl3 : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
 evolution-data-server : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
 seahorse : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
 libpq5 : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
 libcurl3-gnutls : Hängt ab von: libldap-2.4-2 (>= 2.4.7) aber es soll nicht installiert werden.
```

as you can see no application requires this high version of libldap...

maybe this helps:
```
/etc/apt/sources.list
# deb cdrom:[Linux Mint 17.2 _Rafaela_ - Release amd64 20150627]/ trusty contrib main non-free
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib

```


I hope you can help me,
Your Clemens

---

### Post by clemensius on 2015-10-15
thank you. In the meantime i fixed it on my own via downgrading the package...

```
sudo apt-get install libldap-2.4=2.4.31-1+nmu2ubuntu8.2 

```

*please close*

---

