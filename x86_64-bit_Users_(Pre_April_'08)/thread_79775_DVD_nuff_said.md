---
title: "DVD nuff said"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by jhbumby on 2005-10-20
I tried to follow the unofficial guide, but ended up not reading correctly:  I changed my repositories.  I may or may not have screwed them up.  Can you say newbie.
Here is what I did:

Before reading, how do I get it back and then how can I get my DVD player working?  (Breezy Badger 5.10)

Q: How to add extra repositories?

   1. Read General Notes
   2.

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

   3. Find this section

...
## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

   4. Replace with the following lines

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

   5. Save the edited file (sample)
   6. sudo apt-get update

---

### Post by jhbumby on 2005-10-20
PS:  Website info:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by Aravinth on 2005-10-20
Just change hoary to breezy in your /etc/apt/sources.list

For the DVD, install "fakeroot" and execute
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

Make sure to install "totem-xine" if you want DVD playback in totem.

**Aravinth**

---

### Post by jhbumby on 2005-10-21
I installed that and the other two required apps, but got this string:
jhbumby@ubuntu:~$ sudo /usr/share/doc/libdvdread3/examples/install-css.sh
Password:
No binary deb available.  Will try to build and install it.
You need to have debhelper, dpkg-dev and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

--17:17:22--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz)
           => `libdvdcss_1.2.5.orig.tar.gz'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 267,699 (261K) [application/x-tar]

100%[====================================>] 267,699      211.03K/s

17:17:24 (210.56 KB/s) - `libdvdcss_1.2.5.orig.tar.gz' saved [267699/267699]

--17:17:24--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.diff.gz](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.diff.gz)
           => `libdvdcss_1.2.5-1.diff.gz'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20 [text/plain]

100%[====================================>] 20            --.--K/s

17:17:24 (1.59 MB/s) - `libdvdcss_1.2.5-1.diff.gz' saved [20/20]

--17:17:24--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.dsc](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.dsc)
           => `libdvdcss_1.2.5-1.dsc'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 341 [text/plain]

100%[====================================>] 341           --.--K/s

17:17:25 (27.10 MB/s) - `libdvdcss_1.2.5-1.dsc' saved [341/341]

dpkg-source: extracting libdvdcss in libdvdcss-1.2.5
dpkg-source: unpacking libdvdcss_1.2.5.orig.tar.gz
dpkg-source: applying ./libdvdcss_1.2.5-1.diff.gz
dh_testdir
./configure --prefix=/usr --mandir=${prefix}/share/man \
        --infodir=${prefix}/share/info
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
make: *** [build-stamp] Error 1

---

### Post by jhbumby on 2005-10-21
Got it, had to add the programs where it said no (cc, cl etc).  Figured out how to mount my cdroms and such, and am now trying to figure out how to get sound....

The computer reads it, but when I hook up my speakers, no sound.  Any auggestions?
Thx thus far - John

---

### Post by AngryPanda on 2005-12-26
I had to install the dh_make package in Synaptic before the install-css.sh script would run successfully. Also make sure Synaptic is not running while the script is. Even then, I needed to reboot my machine before the DVDs would start playing, but now they're going.

---

