---
title: "suitable Wine for Xubuntu"
date: 2017-05-29
forum: Wine
---

### Post by xpeaceservant on 2017-05-29
Did a Google search and found some confusing information on installing Wine under Xubuntu.  Found wiki.winehq.org and that wasn't helpful. Tried finding it from the terminal prompt and get warnings about this and that.

So is there a good, stable download for Wine on Xubuntu?:confused:

---

### Post by The Cog on 2017-05-29
Is there any reason you don't want to use the one in the Ubuntu repository? 
If not then I would think that
```
sudo apt-get install wine
```
would be easiest.

---

### Post by ian-weisser on 2017-05-29
> **xpeaceservant said:**
> Tried finding it from the terminal prompt and get warnings about this and that.

Unable to duplicate: I can install wine without any warnings at all.
What warnings exactly?
What did you do to your system to cause the warnings?

---

### Post by howefield on 2017-05-30
If I need Wine I usually take it from the winehq repository, never failed.


```
wget -nc https://dl.winehq.org/wine-builds/Release.key
--2017-05-30 08:37:34--  https://dl.winehq.org/wine-builds/Release.key
Resolving dl.winehq.org (dl.winehq.org)... 151.101.60.69
Connecting to dl.winehq.org (dl.winehq.org)|151.101.60.69|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3122 (3.0K) [application/pgp-keys]
Saving to: &#8216;Release.key&#8217;

Release.key                        100%[================================================================>]   3.05K  --.-KB/s    in 0s      

2017-05-30 08:37:35 (29.8 MB/s) - &#8216;Release.key&#8217; saved [3122/3122]
```

```
sudo apt-key add Release.key
[sudo] password for hugh: 
OK
```

```
sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/
```

```
sudo dpkg --add-architecture i386 
```

```
sudo apt update
Hit:1 http://gb.archive.ubuntu.com/ubuntu zesty InRelease
Get:2 http://security.ubuntu.com/ubuntu zesty-security InRelease [89.2 kB]
Hit:3 http://ppa.launchpad.net/nextcloud-devs/client/ubuntu zesty InRelease
Get:4 http://gb.archive.ubuntu.com/ubuntu zesty-updates InRelease [89.2 kB]         
Get:5 http://gb.archive.ubuntu.com/ubuntu zesty-backports InRelease [89.2 kB]                  
Get:6 https://dl.winehq.org/wine-builds/ubuntu zesty InRelease [4,681 B]
Get:7 https://dl.winehq.org/wine-builds/ubuntu zesty/main i386 Packages [8,980 B]
Get:8 https://dl.winehq.org/wine-builds/ubuntu zesty/main amd64 Packages [9,048 B]
Fetched 290 kB in 0s (323 kB/s)     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
69 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

```
sudo apt-get install -s --install-recommends winehq-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gcc-6-base:i386 gstreamer1.0-plugins-base:i386 libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libblkid1:i386 libbsd0:i386 libc6:i386 libcairo2:i386 libcap2:i386
  libcapi20-3 libcapi20-3:i386 libcdparanoia0:i386 libcomerr2:i386 libcups2:i386 libdb5.3:i386 libdbus-1-3:i386 libdrm-amdgpu1:i386
  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexif12:i386 libexpat1:i386
  libffi6:i386 libflac8:i386 libfontconfig1:i386 libfreetype6 libfreetype6:i386 libgcc1:i386 libgcrypt20:i386 libgd3:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386 libgmp10:i386 libgnutls30:i386
  libgpg-error0:i386 libgphoto2-6:i386 libgphoto2-port12:i386 libgpm2:i386 libgsm1:i386 libgssapi-krb5-2 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libgstreamer-plugins-base1.0-0:i386 libgstreamer1.0-0:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhogweed4:i386 libhx509-5-heimdal:i386 libicu57 libicu57:i386 libidn11:i386 libieee1284-3:i386
  libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-26-heimdal:i386 libkrb5-3 libkrb5-3:i386 libkrb5support0 libkrb5support0:i386 liblcms2-2:i386 libldap-2.4-2:i386 libllvm4.0:i386
  libltdl7:i386 liblz4-1:i386 liblzma5:i386 libmount1:i386 libmpg123-0:i386 libncurses5:i386 libnettle6:i386 libnss-resolve libodbc1
  libodbc1:i386 libogg0:i386 libopenal-data libopenal1 libopenal1:i386 libopus0:i386 liborc-0.4-0:i386 libosmesa6 libosmesa6:i386
  libp11-kit0:i386 libpam-systemd libpcap0.8:i386 libpciaccess0:i386 libpcre3:i386 libpixman-1-0:i386 libpng16-16:i386 libpulse0:i386
  libroken18-heimdal:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386 libsasl2-modules-db:i386 libselinux1:i386
  libsensors4:i386 libsndfile1:i386 libsndio6.1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libsystemd0
  libsystemd0:i386 libtasn1-6:i386 libtheora0:i386 libtiff5:i386 libtinfo5:i386 libtxc-dxtn-s2tc:i386 libudev1 libudev1:i386
  libusb-1.0-0:i386 libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvorbis0a:i386 libvorbisenc2:i386 libwebp6:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb1:i386 libxcomposite1:i386 libxcursor1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386
  libxrender1:i386 libxshmfence1:i386 libxslt1.1 libxslt1.1:i386 libxxf86vm1:i386 systemd udev wine-stable wine-stable-amd64
  wine-stable-i386:i386 zlib1g:i386
Suggested packages:
  gvfs:i386 glibc-doc:i386 locales:i386 rng-tools:i386 libgd-tools:i386 gnutls-bin:i386 gphoto2:i386 gpm:i386 krb5-doc krb5-user
  krb5-doc:i386 krb5-user:i386 libvisual-0.4-plugins:i386 gstreamer1.0-tools:i386 jackd2:i386 libmyodbc odbc-postgresql tdsodbc
  unixodbc-bin libmyodbc:i386 odbc-postgresql:i386 tdsodbc:i386 unixodbc-bin:i386 libportaudio2:i386 opus-tools:i386 hplip:i386
  libsane-extras:i386 libsasl2-modules-gssapi-mit:i386 | libsasl2-modules-gssapi-heimdal:i386 libsasl2-modules-ldap:i386
  libsasl2-modules-otp:i386 libsasl2-modules-sql:i386 lm-sensors:i386 sndiod:i386 systemd-ui systemd-container
The following NEW packages will be installed
  gcc-6-base:i386 gstreamer1.0-plugins-base:i386 libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libblkid1:i386 libbsd0:i386 libc6:i386 libcairo2:i386 libcap2:i386
  libcapi20-3 libcapi20-3:i386 libcdparanoia0:i386 libcomerr2:i386 libcups2:i386 libdb5.3:i386 libdbus-1-3:i386 libdrm-amdgpu1:i386
  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexif12:i386 libexpat1:i386
  libffi6:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libgcc1:i386 libgcrypt20:i386 libgd3:i386 libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386 libgmp10:i386 libgnutls30:i386 libgpg-error0:i386
  libgphoto2-6:i386 libgphoto2-port12:i386 libgpm2:i386 libgsm1:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer1.0-0:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhogweed4:i386 libhx509-5-heimdal:i386 libicu57:i386 libidn11:i386 libieee1284-3:i386 libjack-jackd2-0:i386 libjbig0:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386
  liblcms2-2:i386 libldap-2.4-2:i386 libllvm4.0:i386 libltdl7:i386 liblz4-1:i386 liblzma5:i386 libmount1:i386 libmpg123-0:i386
  libncurses5:i386 libnettle6:i386 libodbc1 libodbc1:i386 libogg0:i386 libopenal-data libopenal1 libopenal1:i386 libopus0:i386
  liborc-0.4-0:i386 libosmesa6 libosmesa6:i386 libp11-kit0:i386 libpcap0.8:i386 libpciaccess0:i386 libpcre3:i386 libpixman-1-0:i386
  libpng16-16:i386 libpulse0:i386 libroken18-heimdal:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libselinux1:i386 libsensors4:i386 libsndfile1:i386 libsndio6.1:i386 libspeexdsp1:i386 libsqlite3-0:i386
  libssl1.0.0:i386 libstdc++6:i386 libsystemd0:i386 libtasn1-6:i386 libtheora0:i386 libtiff5:i386 libtinfo5:i386 libtxc-dxtn-s2tc:i386
  libudev1:i386 libusb-1.0-0:i386 libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvorbis0a:i386 libvorbisenc2:i386
  libwebp6:i386 libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb1:i386 libxcomposite1:i386
  libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxpm4:i386
  libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386 libxxf86vm1:i386 wine-stable wine-stable-amd64 wine-stable-i386:i386
  winehq-stable zlib1g:i386
The following packages will be upgraded:
  libfreetype6 libgssapi-krb5-2 libicu57 libk5crypto3 libkrb5-3 libkrb5support0 libnss-resolve libpam-systemd libsystemd0 libudev1
  libxslt1.1 systemd udev
13 to upgrade, 159 to newly install, 0 to remove and 56 not to upgrade.
Inst libsystemd0 [232-21ubuntu2] (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64]) [systemd:amd64 ]
Inst libc6:i386 (2.24-9ubuntu2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Inst libgcc1:i386 (1:6.3.0-12ubuntu2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Inst gcc-6-base:i386 (6.3.0-12ubuntu2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Conf gcc-6-base:i386 (6.3.0-12ubuntu2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Conf libgcc1:i386 (1:6.3.0-12ubuntu2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Conf libc6:i386 (2.24-9ubuntu2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Inst libgcrypt20:i386 (1.7.6-1 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Inst libgpg-error0:i386 (1.26-2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Conf libgpg-error0:i386 (1.26-2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Conf libgcrypt20:i386 (1.7.6-1 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Inst liblz4-1:i386 (0.0~r131-2ubuntu2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Conf liblz4-1:i386 (0.0~r131-2ubuntu2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Inst liblzma5:i386 (5.2.2-1.2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Conf liblzma5:i386 (5.2.2-1.2 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Inst libselinux1:i386 (2.6-3 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Inst libpcre3:i386 (2:8.39-3 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Conf libpcre3:i386 (2:8.39-3 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Conf libselinux1:i386 (2.6-3 Ubuntu:17.04/zesty [i386]) [systemd:amd64 ]
Inst libsystemd0:i386 (232-21ubuntu3 Ubuntu:17.04/zesty-updates [i386]) [systemd:amd64 ]
Conf libsystemd0 (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64]) [systemd:amd64 ]
Conf libsystemd0:i386 (232-21ubuntu3 Ubuntu:17.04/zesty-updates [i386]) [systemd:amd64 ]
Inst libnss-resolve [232-21ubuntu2] (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64]) [systemd:amd64 ]
Inst libpam-systemd [232-21ubuntu2] (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64]) [systemd:amd64 ]
Inst systemd [232-21ubuntu2] (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64])
Inst udev [232-21ubuntu2] (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64]) []
Inst libudev1 [232-21ubuntu2] (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64])
Inst libudev1:i386 (232-21ubuntu3 Ubuntu:17.04/zesty-updates [i386])
Conf libudev1 (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64])
Conf libudev1:i386 (232-21ubuntu3 Ubuntu:17.04/zesty-updates [i386])
Inst libxau6:i386 (1:1.0.8-1 Ubuntu:17.04/zesty [i386])
Inst libxdmcp6:i386 (1:1.1.2-1.1 Ubuntu:17.04/zesty [i386])
Inst libxcb1:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libx11-6:i386 (2:1.6.4-3 Ubuntu:17.04/zesty [i386])
Inst libxext6:i386 (2:1.3.3-1 Ubuntu:17.04/zesty [i386])
Inst libcdparanoia0:i386 (3.10.2+debian-11 Ubuntu:17.04/zesty [i386])
Inst libexif12:i386 (0.6.21-2 Ubuntu:17.04/zesty [i386])
Inst libgsm1:i386 (1.0.13-4 Ubuntu:17.04/zesty [i386])
Inst libjpeg-turbo8:i386 (1.5.1-0ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libogg0:i386 (1.3.2-1 Ubuntu:17.04/zesty [i386])
Inst libsamplerate0:i386 (0.1.8-8 Ubuntu:17.04/zesty [i386])
Inst libxfixes3:i386 (1:5.0.3-1 Ubuntu:17.04/zesty [i386])
Inst libxrender1:i386 (1:0.9.10-1 Ubuntu:17.04/zesty [i386])
Inst libxcursor1:i386 (1:1.1.14-1 Ubuntu:17.04/zesty [i386])
Inst libxdamage1:i386 (1:1.1.4-2 Ubuntu:17.04/zesty [i386])
Inst libxinerama1:i386 (2:1.1.3-1 Ubuntu:17.04/zesty [i386])
Inst libxshmfence1:i386 (1.2-1 Ubuntu:17.04/zesty [i386])
Inst libxxf86vm1:i386 (1:1.1.4-1 Ubuntu:17.04/zesty [i386])
Inst libopenal-data (1:1.17.2-4 Ubuntu:17.04/zesty [all])
Inst libopenal1 (1:1.17.2-4 Ubuntu:17.04/zesty [amd64])
Inst wine-stable-amd64 (2.0.1~zesty winehq:17.04/zesty [amd64])
Inst libasound2:i386 (1.1.3-5 Ubuntu:17.04/zesty [i386])
Inst libffi6:i386 (3.2.1-6 Ubuntu:17.04/zesty [i386])
Inst libuuid1:i386 (2.29-1ubuntu2 Ubuntu:17.04/zesty [i386])
Inst libblkid1:i386 (2.29-1ubuntu2 Ubuntu:17.04/zesty [i386])
Inst libmount1:i386 (2.29-1ubuntu2 Ubuntu:17.04/zesty [i386])
Inst zlib1g:i386 (1:1.2.11.dfsg-0ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libglib2.0-0:i386 (2.52.0-1 Ubuntu:17.04/zesty [i386])
Inst libdrm2:i386 (2.4.76-1 Ubuntu:17.04/zesty [i386])
Inst libexpat1:i386 (2.2.0-2 Ubuntu:17.04/zesty [i386])
Inst libglapi-mesa:i386 (17.0.3-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libx11-xcb1:i386 (2:1.6.4-3 Ubuntu:17.04/zesty [i386])
Inst libxcb-dri2-0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libxcb-dri3-0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libxcb-glx0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libxcb-present0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libxcb-sync1:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libdrm-amdgpu1:i386 (2.4.76-1 Ubuntu:17.04/zesty [i386])
Inst libpciaccess0:i386 (0.13.4-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libdrm-intel1:i386 (2.4.76-1 Ubuntu:17.04/zesty [i386])
Inst libdrm-nouveau2:i386 (2.4.76-1 Ubuntu:17.04/zesty [i386])
Inst libdrm-radeon1:i386 (2.4.76-1 Ubuntu:17.04/zesty [i386])
Inst libelf1:i386 (0.166-2ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libtinfo5:i386 (6.0+20160625-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libedit2:i386 (3.1-20160903-3 Ubuntu:17.04/zesty [i386])
Inst libstdc++6:i386 (6.3.0-12ubuntu2 Ubuntu:17.04/zesty [i386])
Inst libllvm4.0:i386 (1:4.0-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libsensors4:i386 (1:3.4.0-4 Ubuntu:17.04/zesty [i386])
Inst libgl1-mesa-dri:i386 (17.0.3-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libgl1-mesa-glx:i386 (17.0.3-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libglu1-mesa:i386 (9.0.0-2.1build1 Ubuntu:17.04/zesty [i386])
Inst libfreetype6 [2.6.3-3ubuntu2] (2.6.3-3ubuntu2.2 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [amd64])
Inst libpng16-16:i386 (1.6.28-1 Ubuntu:17.04/zesty [i386])
Inst libfreetype6:i386 (2.6.3-3ubuntu2.2 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [i386])
Inst libfontconfig1:i386 (2.11.94-0ubuntu2 Ubuntu:17.04/zesty [i386])
Inst libjpeg8:i386 (8c-2ubuntu8 Ubuntu:17.04/zesty [i386])
Inst libjbig0:i386 (2.1-3.1 Ubuntu:17.04/zesty [i386])
Inst libtiff5:i386 (4.0.7-5 Ubuntu:17.04/zesty [i386])
Inst libwebp6:i386 (0.5.2-1 Ubuntu:17.04/zesty [i386])
Inst libxpm4:i386 (1:3.5.12-1 Ubuntu:17.04/zesty [i386])
Inst libgd3:i386 (2.2.4-2 Ubuntu:17.04/zesty [i386])
Inst libltdl7:i386 (2.4.6-2 Ubuntu:17.04/zesty [i386])
Inst libusb-1.0-0:i386 (2:1.0.21-1 Ubuntu:17.04/zesty [i386])
Inst libgphoto2-port12:i386 (2.5.12-1 Ubuntu:17.04/zesty [i386])
Inst libicu57 [57.1-5] (57.1-5ubuntu0.1 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [amd64])
Inst libicu57:i386 (57.1-5ubuntu0.1 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [i386])
Inst libxml2:i386 (2.9.4+dfsg1-2.2 Ubuntu:17.04/zesty [i386])
Inst libgphoto2-6:i386 (2.5.12-1 Ubuntu:17.04/zesty [i386])
Inst libcap2:i386 (1:2.25-1 Ubuntu:17.04/zesty [i386])
Inst libgstreamer1.0-0:i386 (1.10.4-1 Ubuntu:17.04/zesty [i386])
Inst liborc-0.4-0:i386 (1:0.4.26-2 Ubuntu:17.04/zesty [i386])
Inst libgstreamer-plugins-base1.0-0:i386 (1.10.4-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst liblcms2-2:i386 (2.7-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libgmp10:i386 (2:6.1.2+dfsg-1 Ubuntu:17.04/zesty [i386])
Inst libnettle6:i386 (3.3-1 Ubuntu:17.04/zesty [i386])
Inst libhogweed4:i386 (3.3-1 Ubuntu:17.04/zesty [i386])
Inst libidn11:i386 (1.33-1 Ubuntu:17.04/zesty [i386])
Inst libp11-kit0:i386 (0.23.3-5 Ubuntu:17.04/zesty [i386])
Inst libtasn1-6:i386 (4.10-1 Ubuntu:17.04/zesty [i386])
Inst libgnutls30:i386 (3.5.6-4ubuntu4 Ubuntu:17.04/zesty [i386])
Inst libcomerr2:i386 (1.43.4-2 Ubuntu:17.04/zesty [i386])
Inst libroken18-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libasn1-8-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libheimbase1-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libhcrypto4-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libwind0-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libhx509-5-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libsqlite3-0:i386 (3.16.2-3 Ubuntu:17.04/zesty [i386])
Inst libkrb5-26-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libheimntlm0-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libgssapi3-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libdb5.3:i386 (5.3.28-12 Ubuntu:17.04/zesty [i386])
Inst libsasl2-modules-db:i386 (2.1.27~101-g0780600+dfsg-2ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libsasl2-2:i386 (2.1.27~101-g0780600+dfsg-2ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libldap-2.4-2:i386 (2.4.44+dfsg-3ubuntu2 Ubuntu:17.04/zesty [i386])
Inst libmpg123-0:i386 (1.23.8-1 Ubuntu:17.04/zesty [i386])
Inst libbsd0:i386 (0.8.3-1 Ubuntu:17.04/zesty [i386])
Inst libsndio6.1:i386 (1.1.0-3 Ubuntu:17.04/zesty [i386])
Inst libopenal1:i386 (1:1.17.2-4 Ubuntu:17.04/zesty [i386])
Inst libpcap0.8:i386 (1.8.1-3ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libasyncns0:i386 (0.8-6 Ubuntu:17.04/zesty [i386])
Inst libdbus-1-3:i386 (1.10.10-1ubuntu2 Ubuntu:17.04/zesty [i386])
Inst libflac8:i386 (1.3.2-1 Ubuntu:17.04/zesty [i386])
Inst libvorbis0a:i386 (1.3.5-4 Ubuntu:17.04/zesty [i386])
Inst libvorbisenc2:i386 (1.3.5-4 Ubuntu:17.04/zesty [i386])
Inst libsndfile1:i386 (1.0.27-1 Ubuntu:17.04/zesty [i386])
Inst libwrap0:i386 (7.6.q-26 Ubuntu:17.04/zesty [i386])
Inst libpulse0:i386 (1:10.0-1ubuntu2 Ubuntu:17.04/zesty [i386])
Inst libjack-jackd2-0:i386 (1.9.10+20150825git1ed50c92~dfsg-2ubuntu2 Ubuntu:17.04/zesty [i386])
Inst libspeexdsp1:i386 (1.2~rc1.2-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libasound2-plugins:i386 (1.1.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libncurses5:i386 (6.0+20160625-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst wine-stable-i386:i386 (2.0.1~zesty winehq:17.04/zesty [i386])
Inst wine-stable (2.0.1~zesty winehq:17.04/zesty [amd64])
Inst libssl1.0.0:i386 (1.0.2g-1ubuntu11 Ubuntu:17.04/zesty [i386])
Inst libsasl2-modules:i386 (2.1.27~101-g0780600+dfsg-2ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libgssapi-krb5-2 [1.15-1] (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [amd64]) []
Inst libkrb5-3 [1.15-1] (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [amd64]) []
Inst libkrb5support0 [1.15-1] (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [amd64])
Inst libk5crypto3 [1.15-1] (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [amd64])
Inst libkrb5support0:i386 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [i386])
Inst libk5crypto3:i386 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [i386])
Inst libkeyutils1:i386 (1.5.9-9ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libkrb5-3:i386 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [i386])
Inst libgssapi-krb5-2:i386 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [i386])
Inst libopus0:i386 (1.1.2-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libpixman-1-0:i386 (0.34.0-1 Ubuntu:17.04/zesty [i386])
Inst libxcb-render0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libxcb-shm0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libcairo2:i386 (1.14.8-1 Ubuntu:17.04/zesty [i386])
Inst libtheora0:i386 (1.1.1+dfsg.1-14 Ubuntu:17.04/zesty [i386])
Inst libvisual-0.4-0:i386 (0.4.0-10 Ubuntu:17.04/zesty [i386])
Inst gstreamer1.0-plugins-base:i386 (1.10.4-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libavahi-common-data:i386 (0.6.32-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libavahi-common3:i386 (0.6.32-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libavahi-client3:i386 (0.6.32-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libcups2:i386 (2.2.2-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libgpm2:i386 (1.20.4-6.2 Ubuntu:17.04/zesty [i386])
Inst libieee1284-3:i386 (0.2.11-13 Ubuntu:17.04/zesty [i386])
Inst libodbc1 (2.3.4-1 Ubuntu:17.04/zesty [amd64])
Inst libodbc1:i386 (2.3.4-1 Ubuntu:17.04/zesty [i386])
Inst libsane:i386 (1.0.25+git20150528-1ubuntu4 Ubuntu:17.04/zesty [i386])
Inst libv4lconvert0:i386 (1.12.3-1 Ubuntu:17.04/zesty [i386])
Inst libv4l-0:i386 (1.12.3-1 Ubuntu:17.04/zesty [i386])
Inst libxcomposite1:i386 (1:0.4.4-2 Ubuntu:17.04/zesty [i386])
Inst libxi6:i386 (2:1.7.9-1 Ubuntu:17.04/zesty [i386])
Inst libxrandr2:i386 (2:1.5.1-1 Ubuntu:17.04/zesty [i386])
Inst libxslt1.1 [1.1.29-2] (1.1.29-2ubuntu0.1 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [amd64])
Inst libxslt1.1:i386 (1.1.29-2ubuntu0.1 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [i386])
Inst winehq-stable (2.0.1~zesty winehq:17.04/zesty [amd64])
Inst libcapi20-3 (1:3.27-2 Ubuntu:17.04/zesty [amd64])
Inst libcapi20-3:i386 (1:3.27-2 Ubuntu:17.04/zesty [i386])
Inst libosmesa6:i386 (17.0.3-1ubuntu1 Ubuntu:17.04/zesty [i386])
Inst libosmesa6 (17.0.3-1ubuntu1 Ubuntu:17.04/zesty [amd64])
Inst libtxc-dxtn-s2tc:i386 (1.0+git20151227-2 Ubuntu:17.04/zesty [i386])
Conf libnss-resolve (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64])
Conf libpam-systemd (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64])
Conf systemd (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64])
Conf udev (232-21ubuntu3 Ubuntu:17.04/zesty-updates [amd64])
Conf libxau6:i386 (1:1.0.8-1 Ubuntu:17.04/zesty [i386])
Conf libxdmcp6:i386 (1:1.1.2-1.1 Ubuntu:17.04/zesty [i386])
Conf libxcb1:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libx11-6:i386 (2:1.6.4-3 Ubuntu:17.04/zesty [i386])
Conf libxext6:i386 (2:1.3.3-1 Ubuntu:17.04/zesty [i386])
Conf libcdparanoia0:i386 (3.10.2+debian-11 Ubuntu:17.04/zesty [i386])
Conf libexif12:i386 (0.6.21-2 Ubuntu:17.04/zesty [i386])
Conf libgsm1:i386 (1.0.13-4 Ubuntu:17.04/zesty [i386])
Conf libjpeg-turbo8:i386 (1.5.1-0ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libogg0:i386 (1.3.2-1 Ubuntu:17.04/zesty [i386])
Conf libsamplerate0:i386 (0.1.8-8 Ubuntu:17.04/zesty [i386])
Conf libxfixes3:i386 (1:5.0.3-1 Ubuntu:17.04/zesty [i386])
Conf libxrender1:i386 (1:0.9.10-1 Ubuntu:17.04/zesty [i386])
Conf libxcursor1:i386 (1:1.1.14-1 Ubuntu:17.04/zesty [i386])
Conf libxdamage1:i386 (1:1.1.4-2 Ubuntu:17.04/zesty [i386])
Conf libxinerama1:i386 (2:1.1.3-1 Ubuntu:17.04/zesty [i386])
Conf libxshmfence1:i386 (1.2-1 Ubuntu:17.04/zesty [i386])
Conf libxxf86vm1:i386 (1:1.1.4-1 Ubuntu:17.04/zesty [i386])
Conf libopenal-data (1:1.17.2-4 Ubuntu:17.04/zesty [all])
Conf libopenal1 (1:1.17.2-4 Ubuntu:17.04/zesty [amd64])
Conf wine-stable-amd64 (2.0.1~zesty winehq:17.04/zesty [amd64])
Conf libasound2:i386 (1.1.3-5 Ubuntu:17.04/zesty [i386])
Conf libffi6:i386 (3.2.1-6 Ubuntu:17.04/zesty [i386])
Conf libuuid1:i386 (2.29-1ubuntu2 Ubuntu:17.04/zesty [i386])
Conf libblkid1:i386 (2.29-1ubuntu2 Ubuntu:17.04/zesty [i386])
Conf libmount1:i386 (2.29-1ubuntu2 Ubuntu:17.04/zesty [i386])
Conf zlib1g:i386 (1:1.2.11.dfsg-0ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libglib2.0-0:i386 (2.52.0-1 Ubuntu:17.04/zesty [i386])
Conf libdrm2:i386 (2.4.76-1 Ubuntu:17.04/zesty [i386])
Conf libexpat1:i386 (2.2.0-2 Ubuntu:17.04/zesty [i386])
Conf libglapi-mesa:i386 (17.0.3-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libx11-xcb1:i386 (2:1.6.4-3 Ubuntu:17.04/zesty [i386])
Conf libxcb-dri2-0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libxcb-dri3-0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libxcb-glx0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libxcb-present0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libxcb-sync1:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libdrm-amdgpu1:i386 (2.4.76-1 Ubuntu:17.04/zesty [i386])
Conf libpciaccess0:i386 (0.13.4-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libdrm-intel1:i386 (2.4.76-1 Ubuntu:17.04/zesty [i386])
Conf libdrm-nouveau2:i386 (2.4.76-1 Ubuntu:17.04/zesty [i386])
Conf libdrm-radeon1:i386 (2.4.76-1 Ubuntu:17.04/zesty [i386])
Conf libelf1:i386 (0.166-2ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libtinfo5:i386 (6.0+20160625-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libedit2:i386 (3.1-20160903-3 Ubuntu:17.04/zesty [i386])
Conf libstdc++6:i386 (6.3.0-12ubuntu2 Ubuntu:17.04/zesty [i386])
Conf libllvm4.0:i386 (1:4.0-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libsensors4:i386 (1:3.4.0-4 Ubuntu:17.04/zesty [i386])
Conf libgl1-mesa-dri:i386 (17.0.3-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libgl1-mesa-glx:i386 (17.0.3-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libglu1-mesa:i386 (9.0.0-2.1build1 Ubuntu:17.04/zesty [i386])
Conf libfreetype6 (2.6.3-3ubuntu2.2 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [amd64])
Conf libpng16-16:i386 (1.6.28-1 Ubuntu:17.04/zesty [i386])
Conf libfreetype6:i386 (2.6.3-3ubuntu2.2 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [i386])
Conf libfontconfig1:i386 (2.11.94-0ubuntu2 Ubuntu:17.04/zesty [i386])
Conf libjpeg8:i386 (8c-2ubuntu8 Ubuntu:17.04/zesty [i386])
Conf libjbig0:i386 (2.1-3.1 Ubuntu:17.04/zesty [i386])
Conf libtiff5:i386 (4.0.7-5 Ubuntu:17.04/zesty [i386])
Conf libwebp6:i386 (0.5.2-1 Ubuntu:17.04/zesty [i386])
Conf libxpm4:i386 (1:3.5.12-1 Ubuntu:17.04/zesty [i386])
Conf libgd3:i386 (2.2.4-2 Ubuntu:17.04/zesty [i386])
Conf libltdl7:i386 (2.4.6-2 Ubuntu:17.04/zesty [i386])
Conf libusb-1.0-0:i386 (2:1.0.21-1 Ubuntu:17.04/zesty [i386])
Conf libgphoto2-port12:i386 (2.5.12-1 Ubuntu:17.04/zesty [i386])
Conf libicu57 (57.1-5ubuntu0.1 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [amd64])
Conf libicu57:i386 (57.1-5ubuntu0.1 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [i386])
Conf libxml2:i386 (2.9.4+dfsg1-2.2 Ubuntu:17.04/zesty [i386])
Conf libgphoto2-6:i386 (2.5.12-1 Ubuntu:17.04/zesty [i386])
Conf libcap2:i386 (1:2.25-1 Ubuntu:17.04/zesty [i386])
Conf libgstreamer1.0-0:i386 (1.10.4-1 Ubuntu:17.04/zesty [i386])
Conf liborc-0.4-0:i386 (1:0.4.26-2 Ubuntu:17.04/zesty [i386])
Conf libgstreamer-plugins-base1.0-0:i386 (1.10.4-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf liblcms2-2:i386 (2.7-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libgmp10:i386 (2:6.1.2+dfsg-1 Ubuntu:17.04/zesty [i386])
Conf libnettle6:i386 (3.3-1 Ubuntu:17.04/zesty [i386])
Conf libhogweed4:i386 (3.3-1 Ubuntu:17.04/zesty [i386])
Conf libidn11:i386 (1.33-1 Ubuntu:17.04/zesty [i386])
Conf libp11-kit0:i386 (0.23.3-5 Ubuntu:17.04/zesty [i386])
Conf libtasn1-6:i386 (4.10-1 Ubuntu:17.04/zesty [i386])
Conf libgnutls30:i386 (3.5.6-4ubuntu4 Ubuntu:17.04/zesty [i386])
Conf libcomerr2:i386 (1.43.4-2 Ubuntu:17.04/zesty [i386])
Conf libroken18-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libasn1-8-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libheimbase1-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libhcrypto4-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libwind0-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libhx509-5-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libsqlite3-0:i386 (3.16.2-3 Ubuntu:17.04/zesty [i386])
Conf libkrb5-26-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libheimntlm0-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libgssapi3-heimdal:i386 (7.1.0+dfsg-9ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libdb5.3:i386 (5.3.28-12 Ubuntu:17.04/zesty [i386])
Conf libsasl2-modules-db:i386 (2.1.27~101-g0780600+dfsg-2ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libsasl2-2:i386 (2.1.27~101-g0780600+dfsg-2ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libldap-2.4-2:i386 (2.4.44+dfsg-3ubuntu2 Ubuntu:17.04/zesty [i386])
Conf libmpg123-0:i386 (1.23.8-1 Ubuntu:17.04/zesty [i386])
Conf libbsd0:i386 (0.8.3-1 Ubuntu:17.04/zesty [i386])
Conf libsndio6.1:i386 (1.1.0-3 Ubuntu:17.04/zesty [i386])
Conf libopenal1:i386 (1:1.17.2-4 Ubuntu:17.04/zesty [i386])
Conf libpcap0.8:i386 (1.8.1-3ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libasyncns0:i386 (0.8-6 Ubuntu:17.04/zesty [i386])
Conf libdbus-1-3:i386 (1.10.10-1ubuntu2 Ubuntu:17.04/zesty [i386])
Conf libflac8:i386 (1.3.2-1 Ubuntu:17.04/zesty [i386])
Conf libvorbis0a:i386 (1.3.5-4 Ubuntu:17.04/zesty [i386])
Conf libvorbisenc2:i386 (1.3.5-4 Ubuntu:17.04/zesty [i386])
Conf libsndfile1:i386 (1.0.27-1 Ubuntu:17.04/zesty [i386])
Conf libwrap0:i386 (7.6.q-26 Ubuntu:17.04/zesty [i386])
Conf libpulse0:i386 (1:10.0-1ubuntu2 Ubuntu:17.04/zesty [i386])
Conf libjack-jackd2-0:i386 (1.9.10+20150825git1ed50c92~dfsg-2ubuntu2 Ubuntu:17.04/zesty [i386])
Conf libspeexdsp1:i386 (1.2~rc1.2-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libasound2-plugins:i386 (1.1.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libncurses5:i386 (6.0+20160625-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf wine-stable-i386:i386 (2.0.1~zesty winehq:17.04/zesty [i386])
Conf wine-stable (2.0.1~zesty winehq:17.04/zesty [amd64])
Conf libssl1.0.0:i386 (1.0.2g-1ubuntu11 Ubuntu:17.04/zesty [i386])
Conf libsasl2-modules:i386 (2.1.27~101-g0780600+dfsg-2ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libgssapi-krb5-2 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [amd64])
Conf libkrb5-3 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [amd64])
Conf libkrb5support0 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [amd64])
Conf libk5crypto3 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [amd64])
Conf libkrb5support0:i386 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [i386])
Conf libk5crypto3:i386 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [i386])
Conf libkeyutils1:i386 (1.5.9-9ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libkrb5-3:i386 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [i386])
Conf libgssapi-krb5-2:i386 (1.15-1ubuntu0.1 Ubuntu:17.04/zesty-updates [i386])
Conf libopus0:i386 (1.1.2-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libpixman-1-0:i386 (0.34.0-1 Ubuntu:17.04/zesty [i386])
Conf libxcb-render0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libxcb-shm0:i386 (1.11.1-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libcairo2:i386 (1.14.8-1 Ubuntu:17.04/zesty [i386])
Conf libtheora0:i386 (1.1.1+dfsg.1-14 Ubuntu:17.04/zesty [i386])
Conf libvisual-0.4-0:i386 (0.4.0-10 Ubuntu:17.04/zesty [i386])
Conf gstreamer1.0-plugins-base:i386 (1.10.4-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libavahi-common-data:i386 (0.6.32-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libavahi-common3:i386 (0.6.32-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libavahi-client3:i386 (0.6.32-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libcups2:i386 (2.2.2-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libgpm2:i386 (1.20.4-6.2 Ubuntu:17.04/zesty [i386])
Conf libieee1284-3:i386 (0.2.11-13 Ubuntu:17.04/zesty [i386])
Conf libodbc1 (2.3.4-1 Ubuntu:17.04/zesty [amd64])
Conf libodbc1:i386 (2.3.4-1 Ubuntu:17.04/zesty [i386])
Conf libsane:i386 (1.0.25+git20150528-1ubuntu4 Ubuntu:17.04/zesty [i386])
Conf libv4lconvert0:i386 (1.12.3-1 Ubuntu:17.04/zesty [i386])
Conf libv4l-0:i386 (1.12.3-1 Ubuntu:17.04/zesty [i386])
Conf libxcomposite1:i386 (1:0.4.4-2 Ubuntu:17.04/zesty [i386])
Conf libxi6:i386 (2:1.7.9-1 Ubuntu:17.04/zesty [i386])
Conf libxrandr2:i386 (2:1.5.1-1 Ubuntu:17.04/zesty [i386])
Conf libxslt1.1 (1.1.29-2ubuntu0.1 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [amd64])
Conf libxslt1.1:i386 (1.1.29-2ubuntu0.1 Ubuntu:17.04/zesty-updates, Ubuntu:17.04/zesty-security [i386])
Conf winehq-stable (2.0.1~zesty winehq:17.04/zesty [amd64])
Conf libcapi20-3 (1:3.27-2 Ubuntu:17.04/zesty [amd64])
Conf libcapi20-3:i386 (1:3.27-2 Ubuntu:17.04/zesty [i386])
Conf libosmesa6:i386 (17.0.3-1ubuntu1 Ubuntu:17.04/zesty [i386])
Conf libosmesa6 (17.0.3-1ubuntu1 Ubuntu:17.04/zesty [amd64])
Conf libtxc-dxtn-s2tc:i386 (1.0+git20151227-2 Ubuntu:17.04/zesty [i386])
```

---

### Post by kc1di on 2017-05-30
I like playonlinux because it allows me to install a different version of wine for each program I'm trying to run.  Once it is installed you manage the wine versions *(I think you can go to wine version 2.8 at the moment.) *with the tool tab in the menu.
install is simple```
sudo apt-get install playonlinux
```
it will then show up in the game section of the menu.
good luck. 
PS not all windows programs will run under wine or playonlinux.

---

