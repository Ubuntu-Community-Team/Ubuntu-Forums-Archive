---
title: "DVD playback"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by v79 on 2006-01-25
Hi

Forgive me for asking such an old question, but I'm new to 64 bit... Where can I find the required repositories for libdvdcss2 and other related DVD playback software? I've found some i386 repositories but nothing for amd-64...

Many thanks

v79

---

### Post by JAwuku on 2006-01-25
try [www.videolan.org](www.videolan.org) and search there for [http://developers.videolan.org/libdvdcss/](http://developers.videolan.org/libdvdcss/)

The latest version is 1.2.9 ( you may have to compile the 64 bit version yourself)

---

### Post by v79 on 2006-01-28
Well, i downloaded, compiled and installed libdvdcss, which went fine. Unfortunately, totem doesn't believe me. I've installed totem-xine, but trying to play a DVD just pops up the following error:

"An error occurred
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

But...

$ ls /usr/local/lib

firmware      libdvdcss.so        libdvdread.a   libdvdread.so.3      site_ruby
libdvdcss.a   libdvdcss.so.2      libdvdread.la  libdvdread.so.3.1.0
libdvdcss.la  libdvdcss.so.2.0.8  libdvdread.so  python2.4

Is totem expecting to find it somewhere else?

v79

---

### Post by sbassett on 2006-01-29
[QUOTE=v79]Well, i downloaded, compiled and installed libdvdcss, which went fine. Unfortunately, totem doesn't believe me. I've installed totem-xine, but trying to play a DVD just pops up the following error:

"An error occurred
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

But...

$ ls /usr/local/lib

firmware      libdvdcss.so        libdvdread.a   libdvdread.so.3      site_ruby
libdvdcss.a   libdvdcss.so.2      libdvdread.la  libdvdread.so.3.1.0
libdvdcss.la  libdvdcss.so.2.0.8  libdvdread.so  python2.4

Is totem expecting to find it somewhere else?

v79[/QUOTE]

Good question, have you tried symlinking these to /usr/lib?

```
cd /usr/lib
```
```
sudo ln -s /usr/local/lib/* .
```
Please note the space between the * and the .
Then give it another go. Let us know if this helps.

---

### Post by v79 on 2006-01-29
Hi

sudo ln -s /usr/local/lib/* .
Password:
ln: `./libdvdcss.so': File exists
ln: `./libdvdread.a': File exists
ln: `./libdvdread.la': File exists
ln: `./libdvdread.so': File exists
ln: `./libdvdread.so.3': File exists
ln: `./python2.4': cannot overwrite directory

So there were a few files aready there, but not all of them. However, totem now plays DVDs, so thanks!

v79

---

### Post by sbassett on 2006-01-29
[QUOTE=v79]Hi

sudo ln -s /usr/local/lib/* .
Password:
ln: `./libdvdcss.so': File exists
ln: `./libdvdread.a': File exists
ln: `./libdvdread.la': File exists
ln: `./libdvdread.so': File exists
ln: `./libdvdread.so.3': File exists
ln: `./python2.4': cannot overwrite directory

So there were a few files aready there, but not all of them. However, totem now plays DVDs, so thanks!

v79[/QUOTE]
Super cool beans. Just prepping my own self. Building an AMD64 system this week, and hoping for the best.

---

### Post by RAOF on 2006-01-29
You can also run an automated "install-css" script.  You'll find it in
/usr/share/doc/libdvdread3/examples/install-css.sh
This downloads, compiles & installs libdvdcss.

---

### Post by Terracotta on 2006-02-07
[QUOTE=RAOF]You can also run an automated "install-css" script.  You'll find it in
/usr/share/doc/libdvdread3/examples/install-css.sh
This downloads, compiles & installs libdvdcss.[/QUOTE]

Hye, I've tried this several times, in i386 it works, but every time I try it in the 64 bit version it just says:
/usr/share/doc/libdvdread3/examples/install-css.sh: line 39: dpkg-source: command not found

Can anyone help me with this?

---

### Post by RAOF on 2006-02-07
[QUOTE=Terracotta]Hye, I've tried this several times, in i386 it works, but every time I try it in the 64 bit version it just says:
/usr/share/doc/libdvdread3/examples/install-css.sh: line 39: dpkg-source: command not found

Can anyone help me with this?[/QUOTE]
You need to apt-get some of the deb developer stuff.  I'll just see if I can find the exact packages...

---

### Post by davidcrickett on 2006-02-08
I have just succeeded in installing libdvdcss2 for AMD64. Now I can watch movies on my Ubuntu yeah!
I followed this:
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
and compiled like it said in the section for AMD64 users. :mrgreen:

---

### Post by hasek on 2006-02-08
i do not know how you manage to install libdvdcss2

i followed your link it does not work on amd64

root@satan:~# sudo apt-get build-dep libdvdcss2
Lecture des listes de paquets... Fait
Construction de l'arbre des dÃ©pendances... Fait
Les NOUVEAUX paquets suivants seront installÃ©sÂ :
  libt1-5 libwww-ssl0 tetex-base tetex-bin tetex-extra texinfo
0 mis Ã  jour, 6 nouvellement installÃ©s, 0 Ã  enlever et 0 non mis Ã  jour.
Il est nÃ©cessaire de prendre 30,5Mo dans les archives.
AprÃ¨s dÃ©paquetage, 109Mo d'espace disque supplÃ©mentaires seront utilisÃ©s.
Souhaitez-vous continuer [O/n] ? O
RÃ©ception deÂ : 1 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) breezy/main tetex-base 2.0.2c-8 [14,4MB]
RÃ©ception deÂ : 2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main texinfo 4.7-2.2ubuntu2.1 [494kB]
RÃ©ception deÂ : 3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libwww-ssl0 5.4.0-9ubuntu0.5.10 [520kB]
RÃ©ception deÂ : 4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main tetex-bin 2.0.2-30ubuntu3.4 [4483kB]
RÃ©ception deÂ : 5 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) breezy/main libt1-5 5.0.2-3 [155kB]
RÃ©ception deÂ : 6 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) breezy/main tetex-extra 2.0.2c-8 [10,5MB]
30,5Mo rÃ©ceptionnÃ©s en 8m1s (63,3ko/s)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)

PrÃ©configuration des paquetsÂ ...
SÃ©lection du paquet texinfo prÃ©cÃ©demment dÃ©sÃ©lectionnÃ©.
(Lecture de la base de donnÃ©es... 79397 fichiers et rÃ©pertoires dÃ©jÃ  installÃ©s.)
DÃ©paquetage de texinfo (Ã  partir de .../texinfo_4.7-2.2ubuntu2.1_amd64.deb) ...
SÃ©lection du paquet tetex-base prÃ©cÃ©demment dÃ©sÃ©lectionnÃ©.
DÃ©paquetage de tetex-base (Ã  partir de .../tetex-base_2.0.2c-8_all.deb) ...
SÃ©lection du paquet libt1-5 prÃ©cÃ©demment dÃ©sÃ©lectionnÃ©.
DÃ©paquetage de libt1-5 (Ã  partir de .../libt1-5_5.0.2-3_amd64.deb) ...
SÃ©lection du paquet libwww-ssl0 prÃ©cÃ©demment dÃ©sÃ©lectionnÃ©.
DÃ©paquetage de libwww-ssl0 (Ã  partir de .../libwww-ssl0_5.4.0-9ubuntu0.5.10_amd64.deb) ...
SÃ©lection du paquet tetex-bin prÃ©cÃ©demment dÃ©sÃ©lectionnÃ©.
DÃ©paquetage de tetex-bin (Ã  partir de .../tetex-bin_2.0.2-30ubuntu3.4_amd64.deb) ...
SÃ©lection du paquet tetex-extra prÃ©cÃ©demment dÃ©sÃ©lectionnÃ©.
DÃ©paquetage de tetex-extra (Ã  partir de .../tetex-extra_2.0.2c-8_all.deb) ...
ParamÃ©trage de texinfo (4.7-2.2ubuntu2.1) ...

ParamÃ©trage de tetex-base (2.0.2c-8) ...

Creating config file /etc/texmf/mktex.cnf with new version

Creating config file /etc/texmf/dvips/config.builtin35 with new version

Creating config file /etc/texmf/updmap.d/00updmap.cfg with new version

Creating config file /etc/texmf/dvipdfm/config with new version

Creating config file /etc/texdoctk/texdocrc with new version

ParamÃ©trage de libt1-5 (5.0.2-3) ...

ParamÃ©trage de libwww-ssl0 (5.4.0-9ubuntu0.5.10) ...

ParamÃ©trage de tetex-bin (2.0.2-30ubuntu3.4) ...

Creating config file /etc/texmf/texmf.d/05TeXMF.cnf with new version

Creating config file /etc/texmf/texmf.d/15Plain.cnf with new version

Creating config file /etc/texmf/texmf.d/45TeXinputs.cnf with new version

Creating config file /etc/texmf/texmf.d/55Fonts.cnf with new version

Creating config file /etc/texmf/texmf.d/65BibTeX.cnf with new version

Creating config file /etc/texmf/texmf.d/75DviPS.cnf with new version

Creating config file /etc/texmf/texmf.d/85Misc.cnf with new version

Creating config file /etc/texmf/texmf.d/90TeXDoc.cnf with new version

Creating config file /etc/texmf/texmf.d/95NonPath.cnf with new version
Generating /etc/texmf/texmf.cnf ...
Creating config file /etc/texmf/texmf.cnf with new version
done
Generating /var/lib/texmf/web2c/fmtutil.cnf ... done
Regenerating /var/lib/texmf/web2c/updmap.cfg ... done
Running initex. This may take some time. ...
fmtutil: /var/lib/texmf/web2c/lambda.oft installed.
fmtutil: /var/lib/texmf/web2c/omega.oft installed.
fmtutil: /var/lib/texmf/web2c/amstex.fmt installed.
fmtutil: /var/lib/texmf/web2c/latex.fmt installed.
fmtutil: /var/lib/texmf/web2c/pdflatex.fmt installed.
fmtutil: /var/lib/texmf/web2c/pdftex.fmt installed.
fmtutil: /var/lib/texmf/web2c/tex.fmt installed.
fmtutil: /var/lib/texmf/web2c/cont-en.efmt installed.
fmtutil: /var/lib/texmf/web2c/elatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/etex.efmt installed.
fmtutil: /var/lib/texmf/web2c/latex.efmt installed.
fmtutil: /var/lib/texmf/web2c/mptopdf.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdfelatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdfetex.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdflatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/metafun.mem installed.
fmtutil: /var/lib/texmf/web2c/mpost.mem installed.
fmtutil: /var/lib/texmf/web2c/mf.base installed.
Running updmap. This may take some time. ...


If you want to change the default settings,
use /usr/bin/texconfig to configure teTeX.

Fixing permissions and group of ls-R as specified by debconf ...

ParamÃ©trage de tetex-extra (2.0.2c-8) ...

Creating config file /etc/texmf/dvips/config.ams with new version

Creating config file /etc/texmf/dvips/config.cm with new version

Creating config file /etc/texmf/dvips/config.amz with new version

Creating config file /etc/texmf/dvips/config.cmz with new version
Running initex. This may take some time. ...
Running updmap. This may take some time. ...


W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Impossible de localiser la liste des paquets sources [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 Aucun fichier ou rÃ©pertoire de ce type)
W: Vous pouvez lancer Â«Â apt-get updateÂ Â» pour corriger ces problÃ¨mes.
root@satan:~#

---

### Post by seannyob on 2006-03-04
I tried the instructions at [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf), too, and I get:

```

sean@beagle:~$ sudo apt-get build-dep libdvdcss2
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for libdvdcss2

```

WTF?!?!  :(

---

### Post by equilibrium on 2006-03-04
I just got mine working by downloading a deb package. Seems really jerky atm tho, not sure if its just where my ati drivers aren't setup on my laptop right tho.

```
wget http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_amd64.deb
sudo dpkg -i libdvdcss2_1.2.5-1_amd64.deb
```

I thought I'd add that I am using xine, still getting errors on totem :(

---

### Post by equilibrium on 2006-03-05
sorted out the dvdplayback being jerky :) was just where I hadn't setup hdparm, just enabled dma mode on dvd drive and it is perfect :D

---

### Post by Remmelas on 2006-04-27
[QUOTE=RAOF]You need to apt-get some of the deb developer stuff.  I'll just see if I can find the exact packages...[/QUOTE]
The packages I needed (based on Dapper beta install)
debhelper
build-essential
fakeroot

ran the build script successfully, however, still get errors trying to play via totem or xine

---

