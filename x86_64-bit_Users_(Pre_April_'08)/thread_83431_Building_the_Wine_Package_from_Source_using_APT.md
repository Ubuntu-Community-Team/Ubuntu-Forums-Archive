---
title: "Building the Wine Package from Source using APT"
date: 2005-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by toujours on 2005-10-28
Well, I wanted to see how the new version of Wine was doing, so I went to winehq and followed the instructions for rebuilding it for a non 386 platform. The instructions are [here]("http://www.winehq.org/site/download-deb").

This is what I get once I've added the repositories and lauch the first command :

```
sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
Note, selecting libfontconfig1-dev instead of libfontconfig-dev
Package mesa-common-dev is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  mesa-doc libgl1-mesa-dev
The following packages will be REMOVED:
  fglrx-control xorg-driver-fglrx
The following NEW packages will be installed:
  binutils bison build-essential debconf-utils debhelper docbook docbook-dsssl
  docbook-to-man docbook-utils docbook-xsl dpkg-dev flex fontforge g++ g++-4.0
  gcc gcc-4.0 gettext html2text intltool-debian jackd jadetex libarts1-dev
  libarts1c2 libartsc0-dev libasound2-dev libaudio-dev libaudiofile-dev
  libc6-dev libcapi20-3 libcapi20-dev libcupsys2-dev libesd0-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev
  libglib1.2-dev libglib2.0-dev libglu1-mesa-dev libgnutls11-dev
  libgpg-error-dev libice-dev libicu28-dev libicu28c2 libjack0.80.0-0
  libjack0.80.0-dev libjpeg62-dev liblcms1-dev libmng-dev libncurses5-dev
  libogg-dev libopencdk8-dev libosp4 libostyle1c2 libpng12-dev libqt3-headers
  libqt3-mt-dev libsgmls-perl libsm-dev libsndfile1 libsp1c2 libssl-dev
  libstdc++6-4.0-dev libt1-5 libtasn1-2-dev libungif4-dev libungif4g
  libvorbis-dev libwww-ssl0 libx11-dev libxau-dev libxcursor-dev libxext-dev
  libxft-dev libxi-dev libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev
  libxrender-dev libxt-dev linux-kernel-headers m4 make nvidia-glx
  nvidia-glx-dev openjade po-debconf qt3-dev-tools sgmlspl sp tetex-base
  tetex-bin tetex-extra texinfo x-dev x11proto-core-dev x11proto-gl-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev xlibs-static-dev zlib1g-dev
0 upgraded, 108 newly installed, 2 to remove and 0 not upgraded.
E: Package mesa-common-dev has no installation candidate
E: Failed to process build dependencies

```

It looks like my ATI driver is upsetting it somewhat !! What can I do ? Also, I can't find the mesa-common-dev in my existing standard repositories..

Anyway, not to be deterred by an error message, I enter the next magic command :

```

 sudo apt-get --build source wine
Reading package lists... Done
Building dependency tree... Done
Need to get 12.8MB of source archives.
Get:1 http://wine.sourceforge.net source/ wine 0.9.0-winehq-1 (dsc) [1010B]
Get:2 http://wine.sourceforge.net source/ wine 0.9.0-winehq-1 (tar) [12.7MB]
Get:3 http://wine.sourceforge.net source/ wine 0.9.0-winehq-1 (diff) [45.5kB]
Fetched 12.8MB in 59s (215kB/s)
sh: dpkg-source: command not found
Unpack command 'dpkg-source -x wine_0.9.0-winehq-1.dsc' failed.
E: Child process failed

```

OK, I'm beginning to see a pattern emerging here - like something's wrong...

Any help - please ?

---

### Post by RAOF on 2005-10-30
I don't think you can actually get wine to build on a 64bit breezy install at the moment.  You can actually download the (32bit) binary .deb and install that.  See [here]("http://www.ubuntuforums.org/showthread.php?t=82676").

---

