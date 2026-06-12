---
title: "Problems installing wine1.7 on 64 bit Trusty"
date: 2015-05-15
forum: Wine
---

### Post by Nutria on 2015-05-15
Hi,

xubuntu 14.04

After adding ppa:ubuntu-wine/ppa and updating, I tried running "apt-get install wine1.7".  This failed with a dependency error, which led back to another and another, etc all the way to libvpx1:i386, which wants to install what seem like some very important packages.

```
$ sudo apt-get install **libvpx1:i386**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  **colord** dvipng ffmpeg **gnome-control-center** graphviz gstreamer1.0-libav
  gstreamer1.0-plugins-bad gstreamer1.0-plugins-good **gvfs-backends**
  handbrake-gtk **hplip** libavcodec-dev libavcodec54 libavformat-dev
  libavformat54 libcheese-gtk23 libcheese7 libchromaprint0 **libgd3 libgphoto2-6**
  libgvc6 libopencv-contrib2.4 libopencv-highgui2.4 libopencv-legacy2.4
  libopencv-objdetect2.4 libsane libvpx-dev libvpx1
  **printer-driver-postscript-hp** python-pygraphviz sane-utils simple-scan
  **software-center** vlc vlc-nox vlc-plugin-notify vlc-plugin-samba xdot
```

Are there some "non-dependent" packages that need to be installed so that important 64 bit libs and programs don't get removed?

Thanks.

---

### Post by Nutria on 2015-05-16
bump

---

### Post by howefield on 2015-05-16
Thread moved to the "*Wine*" forum.

---

### Post by mc4man on 2015-05-16
Your issue is likely that the currently installed version of libvpx1 does not match the currently available version of libvpx1:i386
This could occur if you upgraded libvpx1 from a ppa then disabled or removed that ppa.
This is info you should know, ie. if you make use of ppa's then pay attention & be informed as to what you are doing/have done.

Post results of this if requiring further assist -  
```
apt-cache policy libvpx1:i386 libvpx1
```

---

### Post by Nutria on 2015-05-16
> **mc4man said:**
> Your issue is likely that the currently installed version of libvpx1 does not match the currently available version of libvpx1:i386
This could occur if you upgraded libvpx1 from a ppa then disabled or removed that ppa.
This is info you should know, ie. if you make use of ppa's then pay attention & be informed as to what you are doing/have done.

Post results of this if requiring further assist -  
```
apt-cache policy libvpx1:i386 libvpx1
```

I thought of that, so downgraded libvpx1, and it still didn't work.

(Are you related to m3man?)

```
$ apt-cache policy libvpx1:i386 libvpx1
libvpx1:i386:
  Installed: (none)
  Candidate: 1.3.0-3~trusty
  Version table:
     1.3.0-3~trusty 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main i386 Packages
     1.3.0-2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
libvpx1:
  Installed: 1.3.0-2           <<<<<<<<<<<<<
  Candidate: 1.3.0-3~trusty
  Version table:
     1.3.0-3~trusty 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
 *** 1.3.0-2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by mc4man on 2015-05-16
Yes & you shouldn't have had any issue if the ppa was still enabled, tested here with no problems regarding libvpx or wine1.7
So choices - 
Use ppa-purge on ppa & just use current 14.04 packages for all, instructions are on ppa page on how  to do that.

Otherwise - 
sudo apt-get update
Then simulate a dist-upgrade, if it looks ok then do for real (remove -s from command
```
sudo apt-get -s dist-upgrade
```
Then try to install libvpx1:i386 again

---

### Post by Nutria on 2015-05-16
> **mc4man said:**
> Yes & you shouldn't have had any issue if the ppa was still enabled, tested here with no problems regarding libvpx or wine1.7
So choices - 
Use ppa-purge on ppa & just use current 14.04 packages for all, instructions are on ppa page on how  to do that.

Otherwise - 
sudo apt-get update
Then simulate a dist-upgrade, if it looks ok then do for real (remove -s from command
```
sudo apt-get -s dist-upgrade
```
Then try to install libvpx1:i386 again

I just dist-upgraded this morning, and the first thing I tried after logging back in (it upgraded the kernel) was to try to install that package.  Still no joy.

Now I'm contemplating foregoing the program I wanted to run in Wine, or upgrading to 14.10.

Decisions, decisions...

---

### Post by mc4man on 2015-05-16
As I said both the 64 bit & 32 libvpx packages must match. Clearly you've done something(s) to make that not possible.
If 1.3.0-2 is installed then that :i386 version must be installed 
So as per your previous post  - 
libvpx1:
  Installed: 1.3.0-2 
You could disable the ppa, update your sources, then libvpx1:i386 (1.3.0-2)  would be available & installable.

Or as mentioned with the ppa enabled upgrade libvpx1 to 1.3.0-3~trusty & the i386  1.3.0-3~trusty will be installable

*If you are planning on doing a in place upgrade from 14.04 to 14.10 then you had better use ppa-purge first on that ppa, clearly & redundantly stated on ppa page.*

Ex.'s with stock 14.04.2 & ppa
 
> $ sudo apt-get -s install libvpx1:i386
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libvpx1:i386
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Inst libvpx1:i386 (1.3.0-3~trusty Ubuntu Multimedia for Trusty:14.04/trusty [i386])
Conf libvpx1:i386 (1.3.0-3~trusty Ubuntu Multimedia for Trusty:14.04/trusty [i386])


> $ sudo apt-get -s install wine1.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support cabextract fonts-horai-umefont fonts-unfonts-core
  fonts-wqy-microhei gnome-exe-thumbnailer icoutils imagemagick
  libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libcapi20-3 libcapi20-3:i386 libcomerr2:i386
  libcups2:i386 libdb5.3:i386 libencode-locale-perl libexif12:i386
  libfile-listing-perl libflac8:i386 libfont-afm-perl libgcrypt11:i386
  libgd3:i386 libgif4 libgif4:i386 libglu1-mesa:i386 libgnutls26:i386
  libgpg-error0:i386 libgphoto2-6:i386 libgphoto2-port10:i386 libgpm2:i386
  libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhx509-5-heimdal:i386 libieee1284-3:i386
  libio-html-perl libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386
  libjpeg8:i386 libjson-c2:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386
  libldap-2.4-2:i386 libltdl7:i386 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzma5:i386 libmagickcore5-extra libmagickwand5
  libmpg123-0:i386 libncurses5:i386 libnet-http-perl libnetpbm10 libodbc1
  libogg0:i386 libopenal1:i386 liborc-0.4-0:i386 libp11-kit0:i386
  libpcap0.8:i386 libpulse0:i386 libroken18-heimdal:i386 libsamplerate0:i386
  libsane:i386 libsasl2-2:i386 libsasl2-modules:i386 libsasl2-modules-db:i386
  libsndfile1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl1.0.0:i386
  libtasn1-6:i386 libtiff5:i386 libusb-1.0-0:i386 libv4l-0:i386
  libv4lconvert0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx1:i386
  libwind0-heimdal:i386 libwrap0:i386 libwww-perl libwww-robotrules-perl
  libxcomposite1:i386 libxcursor1:i386 libxi6:i386 libxinerama1:i386
  libxml2:i386 libxpm4:i386 libxrandr2:i386 libxslt1.1:i386 libxt6:i386 netpbm
  ocl-icd-libopencl1:i386 odbcinst odbcinst1debian2 p11-kit-modules:i386 p7zip
  ttf-mscorefonts-installer ttf-wqy-microhei unixodbc wine-gecko2.34
  wine-gecko2.34:i386 wine-mono4.5.4 wine1.7-amd64 wine1.7-i386:i386
  winetricks
........irrelevant
The following NEW packages will be installed:
  binfmt-support cabextract fonts-horai-umefont fonts-unfonts-core
  fonts-wqy-microhei gnome-exe-thumbnailer icoutils imagemagick
  libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libcapi20-3 libcapi20-3:i386 libcomerr2:i386
  libcups2:i386 libdb5.3:i386 libencode-locale-perl libexif12:i386
  libfile-listing-perl libflac8:i386 libfont-afm-perl libgcrypt11:i386
  libgd3:i386 libgif4 libgif4:i386 libglu1-mesa:i386 libgnutls26:i386
  libgpg-error0:i386 libgphoto2-6:i386 libgphoto2-port10:i386 libgpm2:i386
  libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhx509-5-heimdal:i386 libieee1284-3:i386
  libio-html-perl libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386
  libjpeg8:i386 libjson-c2:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386
  libldap-2.4-2:i386 libltdl7:i386 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzma5:i386 libmagickcore5-extra libmagickwand5
  libmpg123-0:i386 libncurses5:i386 libnet-http-perl libnetpbm10 libodbc1
  libogg0:i386 libopenal1:i386 liborc-0.4-0:i386 libp11-kit0:i386
  libpcap0.8:i386 libpulse0:i386 libroken18-heimdal:i386 libsamplerate0:i386
  libsane:i386 libsasl2-2:i386 libsasl2-modules:i386 libsasl2-modules-db:i386
  libsndfile1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl1.0.0:i386
  libtasn1-6:i386 libtiff5:i386 libusb-1.0-0:i386 libv4l-0:i386
  libv4lconvert0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx1:i386
  libwind0-heimdal:i386 libwrap0:i386 libwww-perl libwww-robotrules-perl
  libxcomposite1:i386 libxcursor1:i386 libxi6:i386 libxinerama1:i386
  libxml2:i386 libxpm4:i386 libxrandr2:i386 libxslt1.1:i386 libxt6:i386 netpbm
  ocl-icd-libopencl1:i386 odbcinst odbcinst1debian2 p11-kit-modules:i386 p7zip
  ttf-mscorefonts-installer ttf-wqy-microhei unixodbc wine-gecko2.34
  wine-gecko2.34:i386 wine-mono4.5.4 wine1.7 wine1.7-amd64 wine1.7-i386:i386
  winetricks
0 upgraded, 131 newly installed.
Inst libgpg-error0:i386 (1.12-0.2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libgcrypt11:i386 (1.5.3-2ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Inst libp11-kit0:i386 (0.20.2-2ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libtasn1-6:i386 (3.4-3ubuntu0.3 Ubuntu:14.04/trusty-updates [i386])
Inst libgnutls26:i386 (2.12.23-12ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Inst libsqlite3-0:i386 (3.8.2-1ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libssl1.0.0:i386 (1.0.1f-1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Inst libcomerr2:i386 (1.42.9-3ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst libdb5.3:i386 (5.3.28-3ubuntu3 Ubuntu:14.04/trusty [i386])
Inst libjson-c2:i386 (0.11-3ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Inst liblzma5:i386 (5.1.1alpha+20120614-2ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libncurses5:i386 (5.9+20140118-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libroken18-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libasn1-8-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libkrb5support0:i386 (1.12+dfsg-2ubuntu5.1 Ubuntu:14.04/trusty-updates [i386])
Inst libk5crypto3:i386 (1.12+dfsg-2ubuntu5.1 Ubuntu:14.04/trusty-updates [i386])
Inst libkeyutils1:i386 (1.5.6-1 Ubuntu:14.04/trusty [i386])
Inst libkrb5-3:i386 (1.12+dfsg-2ubuntu5.1 Ubuntu:14.04/trusty-updates [i386])
Inst libgssapi-krb5-2:i386 (1.12+dfsg-2ubuntu5.1 Ubuntu:14.04/trusty-updates [i386])
Inst libhcrypto4-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libheimbase1-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libwind0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libhx509-5-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libkrb5-26-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libheimntlm0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libgssapi3-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libsasl2-modules-db:i386 (2.1.25.dfsg1-17build1 Ubuntu:14.04/trusty [i386])
Inst libsasl2-2:i386 (2.1.25.dfsg1-17build1 Ubuntu:14.04/trusty [i386])
Inst libldap-2.4-2:i386 (2.4.31-1+nmu2ubuntu8 Ubuntu:14.04/trusty [i386])
Inst libpcap0.8:i386 (1.5.3-2 Ubuntu:14.04/trusty [i386])
Inst libusb-1.0-0:i386 (2:1.0.17-1ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libxml2:i386 (2.9.1+dfsg1-3ubuntu4.4 Ubuntu:14.04/trusty-updates [i386])
Inst fonts-horai-umefont (460-1 Ubuntu:14.04/trusty [all])
Inst fonts-unfonts-core (1.0.3.is.1.0.2-080608-10ubuntu1 Ubuntu:14.04/trusty [all])
Inst libasound2:i386 (1.0.27.2-3ubuntu7 Ubuntu:14.04/trusty [i386])
Inst libsamplerate0:i386 (0.1.8-7 Ubuntu:14.04/trusty [i386])
Inst libjack-jackd2-0:i386 (1.9.9.5+20130622git7de15e7a-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libasyncns0:i386 (0.8-4ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libogg0:i386 (1.3.1-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libflac8:i386 (1.3.0-2ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst libvorbis0a:i386 (1.3.4-1~trusty1 Ubuntu Multimedia for Trusty:14.04/trusty [i386])
Inst libvorbisenc2:i386 (1.3.4-1~trusty1 Ubuntu Multimedia for Trusty:14.04/trusty [i386])
Inst libsndfile1:i386 (1.0.25-7ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libwrap0:i386 (7.6.q-25 Ubuntu:14.04/trusty [i386])
Inst libpulse0:i386 (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [i386])
Inst libspeexdsp1:i386 (1.2~rc1.1-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libasound2-plugins:i386 (1.0.27-2ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libavahi-common-data:i386 (0.6.31-4ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libavahi-common3:i386 (0.6.31-4ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libavahi-client3:i386 (0.6.31-4ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libcups2:i386 (1.7.2-0ubuntu1.5 Ubuntu:14.04/trusty-updates [i386])
Inst libexif12:i386 (0.6.21-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libjpeg-turbo8:i386 (1.3.0-0ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libjpeg8:i386 (8c-2ubuntu8 Ubuntu:14.04/trusty [i386])
Inst libjbig0:i386 (2.0-2ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Inst libtiff5:i386 (4.0.3-7ubuntu0.3 Ubuntu:14.04/trusty-updates [i386])
Inst libvpx1:i386 (1.3.0-3~trusty Ubuntu Multimedia for Trusty:14.04/trusty [i386])
Inst libxpm4:i386 (1:3.5.10-1 Ubuntu:14.04/trusty [i386])
Inst libgd3:i386 (2.1.0-3 Ubuntu:14.04/trusty [i386])
Inst libgif4 (4.1.6-11 Ubuntu:14.04/trusty [amd64])
Inst libgif4:i386 (4.1.6-11 Ubuntu:14.04/trusty [i386])
Inst libltdl7:i386 (2.4.2-1.7ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Inst libgphoto2-6:i386 (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Inst libgpm2:i386 (1.20.4-6.1 Ubuntu:14.04/trusty [i386])
Inst libgstreamer0.10-0:i386 (0.10.36-1.2ubuntu3 Ubuntu:14.04/trusty [i386])
Inst liborc-0.4-0:i386 (1:0.4.18-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libieee1284-3:i386 (0.2.11-12 Ubuntu:14.04/trusty [i386])
Inst liblcms2-2:i386 (2.6-3ubuntu1~trusty Ubuntu Multimedia for Trusty:14.04/trusty [i386])
Inst libmagickwand5 (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [amd64])
Inst libmagickcore5-extra (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [amd64])
Inst libmpg123-0:i386 (1.16.0-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libodbc1 (2.2.14p2-5ubuntu5 Ubuntu:14.04/trusty [amd64])
Inst libv4lconvert0:i386 (1.0.1-1 Ubuntu:14.04/trusty [i386])
Inst libv4l-0:i386 (1.0.1-1 Ubuntu:14.04/trusty [i386])
Inst libsane:i386 (1.0.23-3ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Inst libxcomposite1:i386 (1:0.4.4-1 Ubuntu:14.04/trusty [i386])
Inst libxcursor1:i386 (1:1.1.14-1 Ubuntu:14.04/trusty [i386])
Inst libxi6:i386 (2:1.7.1.901-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libxinerama1:i386 (2:1.1.3-1 Ubuntu:14.04/trusty [i386])
Inst libxrandr2:i386 (2:1.4.2-1 Ubuntu:14.04/trusty [i386])
Inst libxslt1.1:i386 (1.1.28-2build1 Ubuntu:14.04/trusty [i386])
Inst libxt6:i386 (1:1.1.4-1 Ubuntu:14.04/trusty [i386])
Inst odbcinst (2.2.14p2-5ubuntu5 Ubuntu:14.04/trusty [amd64]) []
Inst odbcinst1debian2 (2.2.14p2-5ubuntu5 Ubuntu:14.04/trusty [amd64])
Inst cabextract (1.4-4 Ubuntu:14.04/trusty [amd64])
Inst ttf-mscorefonts-installer (3.4+nmu1ubuntu1 Ubuntu:14.04/trusty [all])
Inst wine-gecko2.34 (2.34-0ubuntu1~ppa1 Wine Team PPA:14.04/trusty [amd64])
Inst wine-gecko2.34:i386 (2.34-0ubuntu1~ppa1 Wine Team PPA:14.04/trusty [i386])
Inst wine-mono4.5.4 (4.5.4-0ubuntu1~ppa1 Wine Team PPA:14.04/trusty [all])
Inst wine1.7-amd64 (1:1.7.38-0ubuntu1 Wine Team PPA:14.04/trusty [amd64]) []
Inst binfmt-support (2.1.4-1 Ubuntu:14.04/trusty [amd64]) []
Inst libglu1-mesa:i386 (9.0.0-2 Ubuntu:14.04/trusty [i386]) []
Inst libopenal1:i386 (1:1.14-4ubuntu1 Ubuntu:14.04/trusty [i386]) []
Inst ocl-icd-libopencl1:i386 (2.1.3-4 Ubuntu:14.04/trusty [i386]) []
Inst wine1.7-i386:i386 (1:1.7.38-0ubuntu1 Wine Team PPA:14.04/trusty [i386]) []
Inst wine1.7 (1:1.7.38-0ubuntu1 Wine Team PPA:14.04/trusty [amd64])
Inst libcapi20-3 (1:3.25+dfsg1-3.3ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libcapi20-3:i386 (1:3.25+dfsg1-3.3ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libsasl2-modules:i386 (2.1.25.dfsg1-17build1 Ubuntu:14.04/trusty [i386])
Inst fonts-wqy-microhei (0.2.0-beta-2 Ubuntu:14.04/trusty [all])
Inst libencode-locale-perl (1.03-1 Ubuntu:14.04/trusty [all])
Inst libhttp-date-perl (6.02-1 Ubuntu:14.04/trusty [all])
Inst libfile-listing-perl (6.04-1 Ubuntu:14.04/trusty [all])
Inst libhtml-tagset-perl (3.20-2 Ubuntu:14.04/trusty [all])
Inst libhtml-parser-perl (3.71-1build1 Ubuntu:14.04/trusty [amd64])
Inst libhtml-tree-perl (5.03-1 Ubuntu:14.04/trusty [all])
Inst libio-html-perl (1.00-1 Ubuntu:14.04/trusty [all])
Inst liblwp-mediatypes-perl (6.02-1 Ubuntu:14.04/trusty [all])
Inst libhttp-message-perl (6.06-1 Ubuntu:14.04/trusty [all])
Inst libhttp-cookies-perl (6.00-2 Ubuntu:14.04/trusty [all])
Inst libhttp-negotiate-perl (6.00-2 Ubuntu:14.04/trusty [all])
Inst libnet-http-perl (6.06-1 Ubuntu:14.04/trusty [all])
Inst liblwp-protocol-https-perl (6.04-2ubuntu0.1 Ubuntu:14.04/trusty-updates [all]) []
Inst libwww-robotrules-perl (6.01-1 Ubuntu:14.04/trusty [all]) []
Inst libwww-perl (6.05-2 Ubuntu:14.04/trusty [all])
Inst icoutils (0.31.0-2 Ubuntu:14.04/trusty [amd64])
Inst imagemagick (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [amd64])
Inst libfont-afm-perl (1.20-1 Ubuntu:14.04/trusty [all])
Inst libhtml-form-perl (6.03-1 Ubuntu:14.04/trusty [all])
Inst libhtml-format-perl (2.11-1 Ubuntu:14.04/trusty [all])
Inst libhttp-daemon-perl (6.01-1 Ubuntu:14.04/trusty [all])
Inst libnetpbm10 (2:10.0-15ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst netpbm (2:10.0-15ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst p7zip (9.20.1~dfsg.1-4 Ubuntu:14.04/trusty [amd64])
Inst ttf-wqy-microhei (0.2.0-beta-2 Ubuntu:14.04/trusty [all])
Inst unixodbc (2.2.14p2-5ubuntu5 Ubuntu:14.04/trusty [amd64])
Inst winetricks (0.0+20140302-0ubuntu2 Ubuntu:14.04/trusty [all])
Inst gnome-exe-thumbnailer (0.9.3-0ubuntu1 Ubuntu:14.04/trusty [all])
Inst p11-kit-modules:i386 (0.20.2-2ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libgpg-error0:i386 (1.12-0.2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libgcrypt11:i386 (1.5.3-2ubuntu4.2 Ubuntu:14.04/trusty-updates [i386])
Conf libp11-kit0:i386 (0.20.2-2ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libtasn1-6:i386 (3.4-3ubuntu0.3 Ubuntu:14.04/trusty-updates [i386])
Conf libgnutls26:i386 (2.12.23-12ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Conf libsqlite3-0:i386 (3.8.2-1ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libssl1.0.0:i386 (1.0.1f-1ubuntu2.11 Ubuntu:14.04/trusty-updates [i386])
Conf libcomerr2:i386 (1.42.9-3ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf libdb5.3:i386 (5.3.28-3ubuntu3 Ubuntu:14.04/trusty [i386])
Conf libjson-c2:i386 (0.11-3ubuntu1.2 Ubuntu:14.04/trusty-updates [i386])
Conf liblzma5:i386 (5.1.1alpha+20120614-2ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libncurses5:i386 (5.9+20140118-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libroken18-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libasn1-8-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkrb5support0:i386 (1.12+dfsg-2ubuntu5.1 Ubuntu:14.04/trusty-updates [i386])
Conf libk5crypto3:i386 (1.12+dfsg-2ubuntu5.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkeyutils1:i386 (1.5.6-1 Ubuntu:14.04/trusty [i386])
Conf libkrb5-3:i386 (1.12+dfsg-2ubuntu5.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgssapi-krb5-2:i386 (1.12+dfsg-2ubuntu5.1 Ubuntu:14.04/trusty-updates [i386])
Conf libhcrypto4-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libheimbase1-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libwind0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libhx509-5-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libkrb5-26-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libheimntlm0-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libgssapi3-heimdal:i386 (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libsasl2-modules-db:i386 (2.1.25.dfsg1-17build1 Ubuntu:14.04/trusty [i386])
Conf libsasl2-2:i386 (2.1.25.dfsg1-17build1 Ubuntu:14.04/trusty [i386])
Conf libldap-2.4-2:i386 (2.4.31-1+nmu2ubuntu8 Ubuntu:14.04/trusty [i386])
Conf libpcap0.8:i386 (1.5.3-2 Ubuntu:14.04/trusty [i386])
Conf libusb-1.0-0:i386 (2:1.0.17-1ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libxml2:i386 (2.9.1+dfsg1-3ubuntu4.4 Ubuntu:14.04/trusty-updates [i386])
Conf fonts-horai-umefont (460-1 Ubuntu:14.04/trusty [all])
Conf fonts-unfonts-core (1.0.3.is.1.0.2-080608-10ubuntu1 Ubuntu:14.04/trusty [all])
Conf libasound2:i386 (1.0.27.2-3ubuntu7 Ubuntu:14.04/trusty [i386])
Conf libsamplerate0:i386 (0.1.8-7 Ubuntu:14.04/trusty [i386])
Conf libjack-jackd2-0:i386 (1.9.9.5+20130622git7de15e7a-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libasyncns0:i386 (0.8-4ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libogg0:i386 (1.3.1-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libflac8:i386 (1.3.0-2ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf libvorbis0a:i386 (1.3.4-1~trusty1 Ubuntu Multimedia for Trusty:14.04/trusty [i386])
Conf libvorbisenc2:i386 (1.3.4-1~trusty1 Ubuntu Multimedia for Trusty:14.04/trusty [i386])
Conf libsndfile1:i386 (1.0.25-7ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libwrap0:i386 (7.6.q-25 Ubuntu:14.04/trusty [i386])
Conf libpulse0:i386 (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [i386])
Conf libspeexdsp1:i386 (1.2~rc1.1-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libasound2-plugins:i386 (1.0.27-2ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libavahi-common-data:i386 (0.6.31-4ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libavahi-common3:i386 (0.6.31-4ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libavahi-client3:i386 (0.6.31-4ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libcups2:i386 (1.7.2-0ubuntu1.5 Ubuntu:14.04/trusty-updates [i386])
Conf libexif12:i386 (0.6.21-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libjpeg-turbo8:i386 (1.3.0-0ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libjpeg8:i386 (8c-2ubuntu8 Ubuntu:14.04/trusty [i386])
Conf libjbig0:i386 (2.0-2ubuntu4.1 Ubuntu:14.04/trusty-updates [i386])
Conf libtiff5:i386 (4.0.3-7ubuntu0.3 Ubuntu:14.04/trusty-updates [i386])
Conf libvpx1:i386 (1.3.0-3~trusty Ubuntu Multimedia for Trusty:14.04/trusty [i386])
Conf libxpm4:i386 (1:3.5.10-1 Ubuntu:14.04/trusty [i386])
Conf libgd3:i386 (2.1.0-3 Ubuntu:14.04/trusty [i386])
Conf libgif4 (4.1.6-11 Ubuntu:14.04/trusty [amd64])
Conf libgif4:i386 (4.1.6-11 Ubuntu:14.04/trusty [i386])
Conf libltdl7:i386 (2.4.2-1.7ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgphoto2-6:i386 (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [i386])
Conf libgpm2:i386 (1.20.4-6.1 Ubuntu:14.04/trusty [i386])
Conf libgstreamer0.10-0:i386 (0.10.36-1.2ubuntu3 Ubuntu:14.04/trusty [i386])
Conf liborc-0.4-0:i386 (1:0.4.18-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libieee1284-3:i386 (0.2.11-12 Ubuntu:14.04/trusty [i386])
Conf liblcms2-2:i386 (2.6-3ubuntu1~trusty Ubuntu Multimedia for Trusty:14.04/trusty [i386])
Conf libmagickwand5 (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [amd64])
Conf libmagickcore5-extra (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [amd64])
Conf libmpg123-0:i386 (1.16.0-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libodbc1 (2.2.14p2-5ubuntu5 Ubuntu:14.04/trusty [amd64])
Conf libv4lconvert0:i386 (1.0.1-1 Ubuntu:14.04/trusty [i386])
Conf libv4l-0:i386 (1.0.1-1 Ubuntu:14.04/trusty [i386])
Conf libsane:i386 (1.0.23-3ubuntu3.1 Ubuntu:14.04/trusty-updates [i386])
Conf libxcomposite1:i386 (1:0.4.4-1 Ubuntu:14.04/trusty [i386])
Conf libxcursor1:i386 (1:1.1.14-1 Ubuntu:14.04/trusty [i386])
Conf libxi6:i386 (2:1.7.1.901-1ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libxinerama1:i386 (2:1.1.3-1 Ubuntu:14.04/trusty [i386])
Conf libxrandr2:i386 (2:1.4.2-1 Ubuntu:14.04/trusty [i386])
Conf libxslt1.1:i386 (1.1.28-2build1 Ubuntu:14.04/trusty [i386])
Conf libxt6:i386 (1:1.1.4-1 Ubuntu:14.04/trusty [i386])
Conf odbcinst (2.2.14p2-5ubuntu5 Ubuntu:14.04/trusty [amd64])
Conf odbcinst1debian2 (2.2.14p2-5ubuntu5 Ubuntu:14.04/trusty [amd64])
Conf cabextract (1.4-4 Ubuntu:14.04/trusty [amd64])
Conf ttf-mscorefonts-installer (3.4+nmu1ubuntu1 Ubuntu:14.04/trusty [all])
Conf wine-gecko2.34 (2.34-0ubuntu1~ppa1 Wine Team PPA:14.04/trusty [amd64])
Conf wine-gecko2.34:i386 (2.34-0ubuntu1~ppa1 Wine Team PPA:14.04/trusty [i386])
Conf wine-mono4.5.4 (4.5.4-0ubuntu1~ppa1 Wine Team PPA:14.04/trusty [all])
Conf binfmt-support (2.1.4-1 Ubuntu:14.04/trusty [amd64])
Conf libglu1-mesa:i386 (9.0.0-2 Ubuntu:14.04/trusty [i386])
Conf libopenal1:i386 (1:1.14-4ubuntu1 Ubuntu:14.04/trusty [i386])
Conf ocl-icd-libopencl1:i386 (2.1.3-4 Ubuntu:14.04/trusty [i386])
Conf wine1.7-amd64 (1:1.7.38-0ubuntu1 Wine Team PPA:14.04/trusty [amd64])
Conf wine1.7 (1:1.7.38-0ubuntu1 Wine Team PPA:14.04/trusty [amd64])
Conf wine1.7-i386:i386 (1:1.7.38-0ubuntu1 Wine Team PPA:14.04/trusty [i386])
Conf libcapi20-3 (1:3.25+dfsg1-3.3ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libcapi20-3:i386 (1:3.25+dfsg1-3.3ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libsasl2-modules:i386 (2.1.25.dfsg1-17build1 Ubuntu:14.04/trusty [i386])
Conf fonts-wqy-microhei (0.2.0-beta-2 Ubuntu:14.04/trusty [all])
Conf libencode-locale-perl (1.03-1 Ubuntu:14.04/trusty [all])
Conf libhttp-date-perl (6.02-1 Ubuntu:14.04/trusty [all])
Conf libfile-listing-perl (6.04-1 Ubuntu:14.04/trusty [all])
Conf libhtml-tagset-perl (3.20-2 Ubuntu:14.04/trusty [all])
Conf libhtml-parser-perl (3.71-1build1 Ubuntu:14.04/trusty [amd64])
Conf libhtml-tree-perl (5.03-1 Ubuntu:14.04/trusty [all])
Conf libio-html-perl (1.00-1 Ubuntu:14.04/trusty [all])
Conf liblwp-mediatypes-perl (6.02-1 Ubuntu:14.04/trusty [all])
Conf libhttp-message-perl (6.06-1 Ubuntu:14.04/trusty [all])
Conf libhttp-cookies-perl (6.00-2 Ubuntu:14.04/trusty [all])
Conf libhttp-negotiate-perl (6.00-2 Ubuntu:14.04/trusty [all])
Conf libnet-http-perl (6.06-1 Ubuntu:14.04/trusty [all])
Conf libwww-robotrules-perl (6.01-1 Ubuntu:14.04/trusty [all])
Conf liblwp-protocol-https-perl (6.04-2ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf libwww-perl (6.05-2 Ubuntu:14.04/trusty [all])
Conf icoutils (0.31.0-2 Ubuntu:14.04/trusty [amd64])
Conf imagemagick (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [amd64])
Conf libfont-afm-perl (1.20-1 Ubuntu:14.04/trusty [all])
Conf libhtml-form-perl (6.03-1 Ubuntu:14.04/trusty [all])
Conf libhtml-format-perl (2.11-1 Ubuntu:14.04/trusty [all])
Conf libhttp-daemon-perl (6.01-1 Ubuntu:14.04/trusty [all])
Conf libnetpbm10 (2:10.0-15ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf netpbm (2:10.0-15ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf p7zip (9.20.1~dfsg.1-4 Ubuntu:14.04/trusty [amd64])
Conf ttf-wqy-microhei (0.2.0-beta-2 Ubuntu:14.04/trusty [all])
Conf unixodbc (2.2.14p2-5ubuntu5 Ubuntu:14.04/trusty [amd64])
Conf winetricks (0.0+20140302-0ubuntu2 Ubuntu:14.04/trusty [all])
Conf gnome-exe-thumbnailer (0.9.3-0ubuntu1 Ubuntu:14.04/trusty [all])
Conf p11-kit-modules:i386 (0.20.2-2ubuntu2 Ubuntu:14.04/trusty [i386])


---

### Post by Nutria on 2015-05-16
This is what I can't understand.  What do these commands show on your system?

```

$ apt-cache policy libvpx1:i386
libvpx1:i386:
  Installed: (none)
  Candidate: 1.3.0-3~trusty
  Version table:
     1.3.0-3~trusty 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main i386 Packages
     1.3.0-2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages

$ apt-cache depends libvpx1:i386
libvpx1:i386
  Depends: libc6:i386
  PreDepends: multiarch-support:i386
    multiarch-support
  Replaces: libvpx1
  **[COLOR="#FF0000"]Breaks: libvpx1[/COLOR]**

$ apt-cache depends multiarch-support:i386
multiarch-support:i386
  Depends: libc6:i386
  [COLOR="#FF0000"]**Conflicts: multiarch-support**[/COLOR]

```

---

### Post by Nutria on 2015-05-16
Is there a "where's the conflict" tool in Debian/Ubuntu?

---

### Post by mc4man on 2015-05-16
> $ apt-cache policy libvpx1:i386
libvpx1:i386:
  Installed: (none)
  Candidate: 1.3.0-3~trusty
  Version table:
     1.3.0-3~trusty 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main i386 Packages
     1.3.0-2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages

doug@doug-Lenovo-IdeaPad-Y510P:~$ apt-cache depends libvpx1:i386
libvpx1:i386
  Depends: libc6:i386
  PreDepends: multiarch-support:i386
    multiarch-support
  Replaces: libvpx1
  Breaks: libvpx1

doug@doug-Lenovo-IdeaPad-Y510P:~$ apt-cache depends multiarch-support:i386
multiarch-support:i386
  Depends: libc6:i386
  Conflicts: multiarch-support
As previously shown I can install the i386 with no issue

? Is the ppa enabled? & what version of libvpx1 is Currently installed?

If desired install aptitude & retry installing - ex., actualling installing this time
> $ sudo aptitude install libvpx1:i386
[sudo] password for doug: 
The following NEW packages will be installed:
  libvpx1:i386 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/525 kB of archives. After unpacking 1,688 kB will be used.
Selecting previously unselected package libvpx1:i386.
(Reading database ... 270709 files and directories currently installed.)
Preparing to unpack .../libvpx1_1.3.0-3~trusty_i386.deb ...
Unpacking libvpx1:i386 (1.3.0-3~trusty) ...
Setting up libvpx1:i386 (1.3.0-3~trusty) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ... 



---

### Post by Nutria on 2015-05-16
Removed mc3man/trusty-media, did another dist-upgrade and even though "apt-get depends" still says that libvpx1:i386 breaks libvpx1:amd64, wine 1.6 installs.

---

