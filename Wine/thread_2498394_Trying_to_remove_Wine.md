---
title: "Trying to remove Wine"
date: 2024-06-11
forum: Wine
---

### Post by Joe_Linux on 2024-06-11
Trying to remove Wine 
```
joe@joe-X555LAB:~$ sudo apt-get remove wine
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  accountsservice-ubuntu-schemas bsdmainutils fonts-wine g++-9
  gir1.2-appindicator3-0.1 gir1.2-clutter-1.0 gir1.2-clutter-gst-3.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gnomebluetooth-1.0
  gir1.2-gtkclutter-1.0 glib-networking:i386 gstreamer1.0-plugins-base:i386
  gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386 hddtemp
  i965-va-driver:i386 intel-media-va-driver:i386 ippusbxd kde-cli-tools
  kde-cli-tools-data libaa1:i386 libamtk-5-0 libamtk-5-common libaom0
  libaom0:i386 libaom3:i386 libapparmor1:i386 libaribb24-0:i386 libarmadillo9
  libasn1-8-heimdal libasn1-8-heimdal:i386 libasound2:i386
  libasound2-plugins:i386 libasyncns0:i386 libatomic1:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libavc1394-0:i386 libavcodec-extra58:i386 libavutil56:i386
  libbasicusageenvironment1 libboost-atomic1.71.0 libboost-chrono1.71.0
  libboost-container1.71.0 libboost-context1.71.0 libboost-coroutine1.71.0
  libboost-date-time1.71.0 libboost-fiber1.71.0 libboost-filesystem1.71.0
  libboost-graph-parallel1.71.0 libboost-graph1.71.0 libboost-iostreams1.71.0
  libboost-locale1.71.0 libboost-log1.71.0 libboost-math1.71.0
  libboost-mpi1.71.0 libboost-numpy1.71.0 libboost-program-options1.71.0
  libboost-python1.71.0 libboost-random1.71.0 libboost-regex1.71.0
  libboost-serialization1.71.0 libboost-stacktrace1.71.0 libboost-system1.71.0
  libboost-test1.71.0 libboost-thread1.71.0 libboost-timer1.71.0
  libboost-type-erasure1.71.0 libboost-wave1.71.0 libbrlapi0.7 libbrotli1:i386
  libbsd0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386
  libcamel-1.2-62 libcapi20-3 libcapi20-3:i386 libcbor0.6 libcdparanoia0:i386
  libcfitsio8 libcmis-0.5-5v5 libcodec2-0.9 libcodec2-0.9:i386
  libcodec2-1.0:i386 libcommon-sense-perl libcroco3 libcups2:i386
  libcurl3-gnutls:i386 libcurl4:i386 libdap25 libdap27 libdapclient6v5
  libdatrie1:i386 libdav1d5:i386 libdc1394-22 libdcmtk14 libdecor-0-0:i386
  libdecor-0-plugin-1-cairo:i386 libdeflate0:i386 libdirectfb-1.7-7
  libdns-export1109 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libdv4:i386
  libdw1:i386 libebml4v5 libedataserver-1.2-24 libedataserverui-1.2-2
  libedit2:i386 libelf1:i386 libepsilon1 libexif12:i386 libexpat1:i386
  libextutils-pkgconfig-perl libfaudio0 libfaudio0:i386 libffi7:i386
  libffi8:i386 libflac8:i386 libfontconfig1:i386 libfreenect0.5
  libfreetype6:i386 libfribidi0:i386 libgbm1:i386 libgd3:i386 libgdal26
  libgdbm-compat4:i386 libgdbm6:i386 libgdk-pixbuf-2.0-0:i386
  libgdk-pixbuf-xlib-2.0-0:i386 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-0:i386
  libgeos-3.8.0 libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglew2.1
  libglib2.0-0:i386 libglu1-mesa:i386 libglvnd0:i386 libglx-mesa0:i386
  libglx0:i386 libgnutls30:i386 libgomp1:i386 libgpac4 libgphoto2-6:i386
  libgphoto2-port12:i386 libgraphite2-3:i386 libgroupsock8 libgsm1:i386
  libgssapi3-heimdal libgssapi3-heimdal:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer-plugins-good1.0-0:i386
  libgstreamer1.0-0:i386 libgtkspell0 libgudev-1.0-0:i386 libgupnp-1.2-0
  libhandy-0.0-0 libharfbuzz0b:i386 libhcrypto4-heimdal
  libhcrypto4-heimdal:i386 libhdf5-103 libhdf5-fortran-102
  libhdf5-hl-fortran-100 libheimbase1-heimdal libheimbase1-heimdal:i386
  libheimntlm0-heimdal libheimntlm0-heimdal:i386 libhogweed5 libhogweed5:i386
  libhogweed6:i386 libhx509-5-heimdal libhx509-5-heimdal:i386 libicu66:i386
  libicu70:i386 libiec61883-0:i386 libieee1284-3:i386 libigdgmm11
  libigdgmm11:i386 libigdgmm12:i386 libilmbase24 libjack-jackd2-0:i386
  libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjs-prototype
  libjs-scriptaculous libjson-c4 libjson-xs-perl libjsoncpp1 libjuh-java
  libjurt-java libkf5pty-data libkf5pty5 libkf5pulseaudioqt2 libkf5su-bin
  libkf5su-data libkf5su5 libkrb5-26-heimdal libkrb5-26-heimdal:i386
  libkworkspace5-5 liblcms2-2:i386 libldap-2.4-2 libldap-2.4-2:i386
  libldap-2.5-0:i386 liblibreoffice-java liblivemedia77 libllvm12
  libllvm12:i386 libllvm15:i386 libltdl7:i386 libmatroska6v5 libmd0:i386
  libmozjs-68-0 libmp3lame0:i386 libmpg123-0:i386 libmysqlclient21:i386
  libnetcdf15 libnettle7 libnettle7:i386 libnettle8:i386 libnghttp2-14:i386
  libnspr4:i386 libnss3:i386 libntfs-3g883 libnuma1:i386 libodbc1
  libodbc1:i386 libodbc2:i386 libodbccr2 libodbccr2:i386 libogg0:i386
  libopenal1:i386 libopencore-amrnb0:i386 libopencore-amrwb0:i386
  libopencv-calib3d4.2 libopencv-core4.2 libopencv-features2d4.2
  libopencv-flann4.2 libopencv-highgui4.2 libopencv-imgcodecs4.2
  libopencv-imgproc4.2 libopencv-ml4.2 libopencv-videoio4.2 libopenexr24
  libopengl0:i386 libopenimageio2.1 libopenjp2-7:i386 libopenshot-audio6
  libopenshot16 libopenvdb6.2 libopus0:i386 liborc-0.4-0:i386 liborcus-0.15-0
  libosmesa6 libosmesa6:i386 libp11-kit0:i386 libpango-1.0-0:i386
  libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpcap0.8:i386 libpci3:i386
  libpciaccess0:i386 libpcre2-posix2 libperl5.30 libperl5.30:i386
  libperl5.34:i386 libpgm-5.2-0 libphonenumber7 libphonon4qt5-4
  libphonon4qt5-data libpixman-1-0:i386 libplacebo7 libpng16-16:i386
  libpoppler-glib8:i386 libpoppler118:i386 libpoppler97 libproj15
  libprotobuf-lite17 libprotobuf17 libproxy1v5:i386 libpsl5:i386
  libpulse0:i386 libpython2-dev libpython2.7 libpython2.7-dev libpython3.8
  libpython3.8-dev libpython3.8-minimal libpython3.8-stdlib libqhull7
  libqpdf26 libqt5opengl5 libqt5webengine-data libqt5webenginecore5
  libqt5webenginewidgets5 librarian0 libraw1394-11:i386 libraw19 libre2-5
  libre2-9 libreoffice-style-tango libridl-java libroken18-heimdal
  libroken18-heimdal:i386 librsvg2-2:i386 librsvg2-common:i386 librtmp1:i386
  libsamplerate0:i386 libsane libsane:i386 libsane1:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsdl2-2.0-0:i386
  libsensors5:i386 libshine3:i386 libshout3:i386 libslang2:i386
  libsnappy1v5:i386 libsndfile1:i386 libsndio7.0:i386 libsnmp35 libsnmp35:i386
  libsnmp40:i386 libsoup2.4-1:i386 libsoxr0:i386 libspeex1:i386
  libsqlite3-0:i386 libsrt1 libssh-4:i386 libssl1.1:i386 libstb0 libstb0:i386
  libstdc++-7-dev libstdc++-9-dev libstdc++6:i386 libswresample3:i386
  libtag1v5:i386 libtag1v5-vanilla:i386 libtasn1-6:i386 libtepl-4-0
  libthai0:i386 libtheora0:i386 libtiff5:i386 libtracker-control-2.0-0
  libtracker-miner-2.0-0 libtracker-sparql-2.0-0 libtwolame0:i386
  libtypes-serialiser-perl libunoloader-java libunwind8:i386
  liburl-dispatcher1 libusageenvironment3 libusb-1.0-0:i386 libv4l-0:i386
  libv4lconvert0:i386 libva-drm2:i386 libva-x11-2:i386 libva2:i386
  libvdpau1:i386 libvisual-0.4-0:i386 libvkd3d1 libvkd3d1:i386
  libvo-amrwbenc0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx6
  libvpx6:i386 libvpx7:i386 libvulkan1:i386 libwavpack1:i386
  libwayland-client0:i386 libwayland-cursor0:i386 libwayland-egl1:i386
  libwayland-server0:i386 libwcs7 libwebp6 libwebp6:i386 libwebp7:i386
  libwebpmux3:i386 libwind0-heimdal libwind0-heimdal:i386 libwine libwine:i386
  libwmf0.2-7 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386 libx264-155
  libx264-155:i386 libx264-163:i386 libx265-179 libx265-179:i386
  libx265-199:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-render0:i386
  libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386
  libxkbcommon0:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386
  libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386 libxss1:i386 libxv1:i386
  libxvidcore4:i386 libxxf86vm1:i386 libyaml-cpp0.6 libz-mingw-w64 libzip5
  libzvbi0:i386 ltrace lz4 mesa-va-drivers:i386 mesa-vdpau-drivers:i386
  mesa-vulkan-drivers:i386 ncal ocl-icd-libopencl1:i386 odbcinst
  odbcinst1debian2 perl-modules-5.30 phonon4qt5 phonon4qt5-backend-vlc
  popularity-contest python-backports.functools-lru-cache python-bs4
  python-html5lib python-lxml python-numpy python-pkg-resources python-six
  python-soupsieve python-webencodings python2-dev python2.7-dev
  python3-entrypoints python3-requests-unixsocket python3-simplejson
  python3-sip python3.8 python3.8-dev python3.8-minimal rarian-compat ruby2.7
  siril-common syslinux syslinux-common syslinux-legacy ure-java
  va-driver-all:i386 vdpau-driver-all:i386 wine32:i386 wine64
  x11proto-input-dev x11proto-randr-dev x11proto-xext-dev
  x11proto-xinerama-dev
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  wine
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
11 not fully installed or removed.
After this operation, 200 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 306124 files and directories currently installed.)
Removing wine (6.0.3~repack-1) ...
Setting up openmpi-bin (4.1.2-2ubuntu1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/mpi corrupt: slave link same as main link /usr/bin/mpicc
dpkg: error processing package openmpi-bin (--configure):
 installed openmpi-bin package post-installation script subprocess returned error exit status 2
dpkg: dependency problems prevent configuration of mpi-default-bin:
 mpi-default-bin depends on openmpi-bin; however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package mpi-default-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcoarrays-openmpi-dev:amd64:
 libcoarrays-openmpi-dev:amd64 depends on openmpi-bin; however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package libcoarrays-openmpi-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopenmpi-dev:amd64:
 libopenmpi-dev:amd64 depends on openmpi-bin (>= 3.0.0-1); however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package libopenmpi-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi-python1.74.0:
 libboost-mpi-python1.74.0 depends on mpi-defauNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                         No apport report written because the error message indicates its a followup error from a previous failure.
                   No apport report written because MaxReports is reached already
 No apport report written because MaxReports is reached already
                                                               No apport report written because MaxReports is reached already
                                             No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
         No apport report written because MaxReports is reached already
                                                                       No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                   lt-bin; however:
  Package mpi-default-bin is not configured yet.

dpkg: error processing package libboost-mpi-python1.74.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi-python1.74-dev:
 libboost-mpi-python1.74-dev depends on libboost-mpi-python1.74.0 (= 1.74.0-14ubuntu3); however:
  Package libboost-mpi-python1.74.0 is not configured yet.

dpkg: error processing package libboost-mpi-python1.74-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi-python-dev:
 libboost-mpi-python-dev depends on libboost-mpi-python1.74-dev; however:
  Package libboost-mpi-python1.74-dev is not configured yet.

dpkg: error processing package libboost-mpi-python-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-all-dev:
 libboost-all-dev depends on libboost-mpi-python-dev; however:
  Package libboost-mpi-python-dev is not configured yet.

dpkg: error processing package libboost-all-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mpi-default-dev:
 mpi-default-dev depends on libopenmpi-dev; however:
  Package libopenmpi-dev:amd64 is not configured yet.

dpkg: error processing package mpi-default-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi1.74-dev:
 libboost-mpi1.74-dev depends on mpi-default-dev; however:
  Package mpi-default-dev is not configured yet.

dpkg: error processing package libboost-mpi1.74-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi-dev:
 libboost-mpi-dev depends on libboost-mpi1.74-dev; however:
  Package libboost-mpi1.74-dev is not configured yet.

dpkg: error processing package libboost-mpi-dev (--configure):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Errors were encountered while processing:
 openmpi-bin
 mpi-default-bin
 libcoarrays-openmpi-dev:amd64
 libopenmpi-dev:amd64
 libboost-mpi-python1.74.0
 libboost-mpi-python1.74-dev
 libboost-mpi-python-dev
 libboost-all-dev
 mpi-default-dev
 libboost-mpi1.74-dev
 libboost-mpi-dev
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.3.orig.tar.bz2: OK
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe@joe-X555LAB:~$ 
```


I recently upgraded from Ubuntu 20.04 to 22.04
How do I correct the errors ?
Thank you

---

### Post by oldfred on 2024-06-11
Duplicate entry closed.
See
[https://ubuntuforums.org/showthread.php?t=2498394](https://ubuntuforums.org/showthread.php?t=2498394)

---

