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

### Post by Joe_Linux on 2024-06-11
Sorry for the duplicate thread my error :(

---

### Post by Joe_Linux on 2024-06-13
bump

---

### Post by Joe_Linux on 2024-06-14
I tried this to correct the error 
```
joe@joe-X555LAB:~$ sudo dpkg --configure -a
[sudo] password for joe: 
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
 libboost-mpi-python1.74.0 depends on mpi-default-bin; however:
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
joe@joe-X555LAB:~$ sudo apt-get remove wine
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'wine' is not installed, so not removed
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
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
11 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
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
joe@joe-X555LAB:~$ sudo apt install -f
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
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
11 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up openmpi-bin (4.1.2-2ubuntu1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/mpi corrupt: slave link s
ame as main link /usr/bin/mpicc
dpkg: error processing package openmpi-bin (--configure):
 installed openmpi-bin package post-installation script subprocess returned erro
r exit status 2
dpkg: dependency problems prevent configuration of mpi-default-bin:
 mpi-default-bin depends on openmpi-bin; however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package mpi-default-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcoarrays-openmpi-dev:amd64
:
 libcoarrays-openmpi-dev:amd64 depends on openmpi-bin; however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package libcoarrays-openmpi-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopenmpi-dev:amd64:
 libopenmpi-dev:amd64 depends on openmpi-bin (>= 3.0.0-1); however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package libopenmpi-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi-pythonNo apport 
report written because the error message indicates its a followup error from a p
revious failure.
                No apport report written because the error message indicates its
 a followup error from a previous failure.
                                          No apport report written because MaxRe
ports is reached already
                        No apport report written because MaxReports is reached a
lready
      No apport report written because MaxReports is reached already
                                                                    No apport re
port written because MaxReports is reached already
                                                  No apport report written becau
se MaxReports is reached already
                                No apport report written because MaxReports is r
eached already
              No apport report written because MaxReports is reached already
                                                                            No a
pport report written because MaxReports is reached already
                                                          1.74.0:
 libboost-mpi-python1.74.0 depends on mpi-default-bin; however:
  Package mpi-default-bin is not configured yet.

dpkg: error processing package libboost-mpi-python1.74.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi-python1.74-dev:
 libboost-mpi-python1.74-dev depends on libboost-mpi-python1.74.0 (= 1.74.0-14ub
untu3); however:
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
joe@joe-X555LAB:~$ sudo apt remove --purge libdvd-pkg
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
  libdvd-pkg* libdvdcss-dev* libdvdcss2*
0 upgraded, 0 newly installed, 3 to remove and 11 not upgraded.
11 not fully installed or removed.
After this operation, 170 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 306080 files and directories currently installed.)
Removing libdvdcss-dev:amd64 (1.4.2-1~local) ...
Removing libdvdcss2:amd64 (1.4.2-1~local) ...
Removing libdvd-pkg (1.4.3-1-1) ...
Setting up openmpi-bin (4.1.2-2ubuntu1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/mpi corrupt: slave link s
ame as main link /usr/bin/mpicc
dpkg: error processing package openmpi-bin (--configure):
 installed openmpi-bin package post-installation script subprocess returned erro
r exit status 2
dpkg: dependency problems prevent configuration of mpi-default-bin:
 mpi-default-bin depends on openmpi-bin; however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package mpi-default-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcoarrays-openmpi-dev:amd64
:
 libcoarrays-openmpi-dev:amd64 depends on openmpi-bin; however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package libcoarrays-openmpi-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopenmpi-dev:amd64:
 libopenmpi-dev:amd64 depends on openmpi-bin (>= 3.0.0-1); however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package libopenmpi-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi-pythonNo apport 
report written because the error message indicates its a followup error from a p
revious failure.
                No apport report written because the error message indicates its
 a followup error from a previous failure.
                                          No apport report written because MaxRe
ports is reached already
                        No apport report written because MaxReports is reached a
lready
      No apport report written because MaxReports is reached already
                                                                    No apport re
port written because MaxReports is reached already
                                                  No apport report written becau
se MaxReports is reached already
                                No apport report written because MaxReports is r
eached already
              No apport report written because MaxReports is reached already
                                                                            No a
pport report written because MaxReports is reached already
                                                          1.74.0:
 libboost-mpi-python1.74.0 depends on mpi-default-bin; however:
  Package mpi-default-bin is not configured yet.

dpkg: error processing package libboost-mpi-python1.74.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi-python1.74-dev:
 libboost-mpi-python1.74-dev depends on libboost-mpi-python1.74.0 (= 1.74.0-14ub
untu3); however:
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
Processing triggers for libc-bin (2.35-0ubuntu3.8) ...
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
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe@joe-X555LAB:~$
```
I used the information from this website ```
 https://phoenixnap.com/kb/fix-sub-process-usr-bin-dpkg-returned-error-code-1
```

I also tried
```
oe@joe-X555LAB:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
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
0 upgraded, 0 newly installed, 483 to remove and 2 not upgraded.
11 not fully installed or removed.
After this operation, 2,505 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 306102 files and directories currently installed.)
Removing accountsservice-ubuntu-schemas (0.0.7+21.10.20210712-0ubuntu2) ...
Removing bsdmainutils (12.1.7+nmu3ubuntu2) ...
Removing fonts-wine (6.0.3~repack-1) ...
Removing g++-9 (9.5.0-1ubuntu1~22.04) ...
Removing gir1.2-appindicator3-0.1 (12.10.1+20.10.20200706.1-0ubuntu1) ...
Removing gir1.2-clutter-gst-3.0:amd64 (3.0.27-2ubuntu1) ...
Removing gir1.2-gtkclutter-1.0:amd64 (1.8.4-4build2) ...
Removing gir1.2-clutter-1.0:amd64 (1.26.4+dfsg-4build1) ...
Removing gir1.2-coglpango-1.0:amd64 (1.22.8-3build1) ...
Removing gir1.2-cogl-1.0:amd64 (1.22.8-3build1) ...
Removing gir1.2-gnomebluetooth-1.0:amd64 (3.34.3-0ubuntu1) ...
Removing gstreamer1.0-plugins-good:i386 (1.20.3-0ubuntu1.1) ...
Removing libsoup2.4-1:i386 (2.74.2-3) ...
Removing glib-networking:i386 (2.72.0-1) ...
Removing gstreamer1.0-plugins-base:i386 (1.20.1-1ubuntu0.2) ...
Removing gstreamer1.0-x:i386 (1.20.1-1ubuntu0.2) ...
Removing hddtemp (0.3-beta15-53) ...
Removing va-driver-all:i386 (2.14.0-1) ...
Removing i965-va-driver:i386 (2.4.1+dfsg1-1) ...
Removing intel-media-va-driver:i386 (22.3.1+dfsg1-1ubuntu2) ...
Removing ippusbxd (1.34-2ubuntu1) ...
Removing kde-cli-tools (4:5.24.4-0ubuntu1) ...
Removing kde-cli-tools-data (4:5.24.4-0ubuntu1) ...
Removing libaa1:i386 (1.4p5-50build1) ...
Removing libtepl-4-0:amd64 (4.4.0-1) ...
Removing libamtk-5-0:amd64 (5.2.0-1) ...
Removing libamtk-5-common (5.2.0-1) ...
Removing libaom0:amd64 (1.0.0.errata1-3+deb11u1build0.20.04.1) ...
Removing libaom0:i386 (1.0.0.errata1-3+deb11u1build0.20.04.1) ...
Removing libavcodec-extra58:i386 (7:4.4.2-0ubuntu0.22.04.1) ...
Removing libaom3:i386 (3.3.0-1) ...
Removing wine32:i386 (6.0.3~repack-1) ...
Removing libwine:i386 (6.0.3~repack-1) ...
Removing libfaudio0:i386 (22.02-1) ...
Removing libsdl2-2.0-0:i386 (2.0.20+dfsg-2ubuntu1.22.04.1) ...
Removing libasound2-plugins:i386 (1.2.6-1) ...
Removing libpulse0:i386 (1:15.99.1+dfsg1-1ubuntu2.2) ...
Removing libapparmor1:i386 (3.0.4-2ubuntu2.3) ...
Removing libaribb24-0:i386 (1.0.3-2) ...
Removing libopencv-calib3d4.2:amd64 (4.2.0+dfsg-5) ...
Removing libopencv-features2d4.2:amd64 (4.2.0+dfsg-5) ...
Removing libopencv-highgui4.2:amd64 (4.2.0+dfsg-5) ...
Removing libopenimageio2.1:amd64 (2.1.12.0~dfsg0-1) ...
Removing libopencv-videoio4.2:amd64 (4.2.0+dfsg-5) ...
Removing libopencv-imgcodecs4.2:amd64 (4.2.0+dfsg-5) ...
Removing libgdal26 (3.0.4+dfsg-1build3) ...
Removing libarmadillo9 (1:9.800.4+dfsg-1build1) ...
Removing libldap-2.4-2:i386 (2.4.49+dfsg-2ubuntu1.10) ...
Removing libgssapi3-heimdal:i386 (7.7.0+dfsg-3ubuntu1) ...
Removing libheimntlm0-heimdal:i386 (7.7.0+dfsg-3ubuntu1) ...
Removing libkrb5-26-heimdal:i386 (7.7.0+dfsg-3ubuntu1) ...
Removing libhx509-5-heimdal:i386 (7.7.0+dfsg-3ubuntu1) ...
Removing libldap-2.4-2:amd64 (2.4.49+dfsg-2ubuntu1.10) ...
Removing libgssapi3-heimdal:amd64 (7.7.0+dfsg-3ubuntu1) ...
Removing libheimntlm0-heimdal:amd64 (7.7.0+dfsg-3ubuntu1) ...
Removing libkrb5-26-heimdal:amd64 (7.7.0+dfsg-3ubuntu1) ...
Removing libhx509-5-heimdal:amd64 (7.7.0+dfsg-3ubuntu1) ...
Removing libopenal1:i386 (1:1.19.1-2build3) ...
Removing libsndio7.0:i386 (1.8.1-1.1) ...
Removing libasound2:i386 (1.2.6.1-1ubuntu1) ...
Removing libasyncns0:i386 (0.8-6build2) ...
Removing mesa-va-drivers:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Removing mesa-vulkan-drivers:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Removing libllvm12:i386 (1:12.0.1-19ubuntu3) ...
Removing libcups2:i386 (2.4.1op1-1ubuntu4.8) ...
Removing libsane:i386 (1.1.1-5) ...
Removing libsane1:i386 (1.1.1-5) ...
Removing libavahi-client3:i386 (0.8-5ubuntu5.2) ...
Removing libavahi-common3:i386 (0.8-5ubuntu5.2) ...
Removing libavahi-common-data:i386 (0.8-5ubuntu5.2) ...
Removing libavc1394-0:i386 (0.5.4-5build2) ...
Removing libswresample3:i386 (7:4.4.2-0ubuntu0.22.04.1) ...
Removing libavutil56:i386 (7:4.4.2-0ubuntu0.22.04.1) ...
Removing liblivemedia77:amd64 (2020.01.19-1build1) ...
Removing libgroupsock8:amd64 (2020.01.19-1build1) ...
Removing libbasicusageenvironment1:amd64 (2020.01.19-1build1) ...
Removing libboost-atomic1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-timer1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-chrono1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-container1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-coroutine1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-fiber1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-context1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-date-time1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-log1.71.0 (1.71.0-6ubuntu6) ...
Removing liborcus-0.15-0:amd64 (0.15.3-3build2) ...
Removing libboost-filesystem1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-graph-parallel1.71.0 (1.71.0-6ubuntu6) ...
Removing libboost-graph1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libopenvdb6.2 (6.2.1-8ubuntu1.1) ...
Removing libboost-iostreams1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-locale1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-math1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-mpi1.71.0 (1.71.0-6ubuntu6) ...
Removing libboost-numpy1.71.0 (1.71.0-6ubuntu6) ...
Removing libboost-program-options1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-python1.71.0 (1.71.0-6ubuntu6) ...
Removing libboost-random1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-regex1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-serialization1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-stacktrace1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-system1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-test1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libphonenumber7:amd64 (7.1.0-5ubuntu11) ...
Removing libboost-wave1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libboost-type-erasure1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libbrlapi0.7:amd64 (6.0+dfsg-4ubuntu6) ...
Removing libpoppler-glib8:i386 (22.02.0-2ubuntu0.4) ...
Removing libpoppler118:i386 (22.02.0-2ubuntu0.4) ...
Removing librsvg2-common:i386 (2.52.5+dfsg-3ubuntu0.2) ...
Removing librsvg2-2:i386 (2.52.5+dfsg-3ubuntu0.2) ...
Removing libgphoto2-6:i386 (2.5.27-1build2) ...
Removing libcurl4:i386 (7.81.0-1ubuntu1.16) ...
Removing vdpau-driver-all:i386 (1.4-3build2) ...
Removing mesa-vdpau-drivers:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Removing libcaca0:i386 (0.99.beta19-2.2ubuntu4) ...
Removing libcairo-gobject2:i386 (1.16.0-5ubuntu2) ...
Removing libdecor-0-plugin-1-cairo:i386 (0.1.0-3build1) ...
Removing libshout3:i386 (2.4.5-1build3) ...
Removing libtheora0:i386 (1.1.1+dfsg.1-15ubuntu4) ...
Removing libedataserverui-1.2-2:amd64 (3.36.5-0ubuntu1) ...
Removing libedataserver-1.2-24:amd64 (3.36.5-0ubuntu1) ...
Removing libcamel-1.2-62:amd64 (3.36.5-0ubuntu1) ...
Removing libcapi20-3:i386 (1:3.27-3) ...
Removing libcapi20-3:amd64 (1:3.27-3) ...
Removing libcbor0.6:amd64 (0.6.0-0ubuntu1) ...
Removing libcdparanoia0:i386 (3.10.2+debian-14build2) ...
Removing libcfitsio8:amd64 (3.470-3) ...
Removing libcmis-0.5-5v5 (0.5.2-3build1) ...
Removing libcodec2-0.9:amd64 (0.9.2-2) ...
Removing libcodec2-0.9:i386 (0.9.2-2) ...
Removing libcodec2-1.0:i386 (1.0.1-3) ...
Removing libjson-xs-perl (4.030-1build3) ...
Removing libtypes-serialiser-perl (1.01-1) ...
Removing libcommon-sense-perl:amd64 (3.75-2build1) ...
Removing libcroco3:amd64 (0.6.13-1) ...
Removing libcurl3-gnutls:i386 (7.81.0-1ubuntu1.16) ...
Removing libdap25:amd64 (3.20.5-1) ...
Removing libdapclient6v5:amd64 (3.20.9-1) ...
Removing libdap27:amd64 (3.20.9-1) ...
Removing libdav1d5:i386 (0.9.2-1) ...
Removing libdc1394-22:amd64 (2.2.5-2.1) ...
Removing libdcmtk14 (3.6.4-2.1build2) ...
Removing libdecor-0-0:i386 (0.1.0-3build1) ...
Removing libgdk-pixbuf2.0-0:i386 (2.40.2-2build4) ...
Removing libgdk-pixbuf-xlib-2.0-0:i386 (2.40.2-2build4) ...
Removing libgdk-pixbuf-2.0-0:i386 (2.42.8+dfsg-1ubuntu0.3) ...
Removing libgd3:i386 (2.3.0-2ubuntu2) ...
Removing libtiff5:i386 (4.3.0-6ubuntu0.9) ...
Removing libdeflate0:i386 (1.10-2) ...
Removing libdirectfb-1.7-7:amd64 (1.7.7-9build1) ...
Removing libdns-export1109 (1:9.11.16+dfsg-3~ubuntu1) ...
Removing libgl1:i386 (1.4.0-1) ...
Removing libglx0:i386 (1.4.0-1) ...
Removing libglx-mesa0:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Removing libgl1-mesa-dri:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Removing libdrm-amdgpu1:i386 (2.4.113-2~ubuntu0.22.04.1) ...
Removing libdrm-intel1:i386 (2.4.113-2~ubuntu0.22.04.1) ...
Removing libdrm-nouveau2:i386 (2.4.113-2~ubuntu0.22.04.1) ...
Removing libdrm-radeon1:i386 (2.4.113-2~ubuntu0.22.04.1) ...
Removing libosmesa6:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Removing libgbm1:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Removing libdv4:i386 (1.0.0-14build1) ...
Removing libgstreamer-plugins-good1.0-0:i386 (1.20.3-0ubuntu1.1) ...
Removing libgstreamer-plugins-base1.0-0:i386 (1.20.1-1ubuntu0.2) ...
Removing libgstreamer1.0-0:i386 (1.20.3-0ubuntu1) ...
Removing libdw1:i386 (0.186-1build1) ...
Removing libmatroska6v5:amd64 (1.5.2-3build1) ...
Removing libebml4v5:amd64 (1.3.10-1build1) ...
Removing libelf1:i386 (0.186-1build1) ...
Removing libepsilon1:amd64 (0.9.2+dfsg-4) ...
Removing libexif12:i386 (0.6.24-1build1) ...
Removing libextutils-pkgconfig-perl (1.16-1.1) ...
Removing wine64 (6.0.3~repack-1) ...
Removing libwine:amd64 (6.0.3~repack-1) ...
Removing libfaudio0:amd64 (22.02-1) ...
Removing libffi7:i386 (3.3-5ubuntu1) ...
Removing libwayland-server0:i386 (1.20.0-1ubuntu0.1) ...
Removing libwayland-cursor0:i386 (1.20.0-1ubuntu0.1) ...
Removing libwayland-client0:i386 (1.20.0-1ubuntu0.1) ...
Removing libsndfile1:i386 (1.0.31-2ubuntu0.1) ...
Removing libflac8:i386 (1.3.3-2ubuntu0.2) ...
Removing libfreenect0.5:amd64 (1:0.5.3-2) ...
Removing libsnmp35:i386 (5.8+dfsg-2ubuntu2.9) ...
Removing libperl5.30:i386 (5.30.0-9ubuntu0.5) ...
Removing libsnmp40:i386 (5.9.1+dfsg-1ubuntu2.6) ...
Removing libperl5.34:i386 (5.34.0-3ubuntu1.3) ...
Removing libgdbm-compat4:i386 (1.23-1) ...
Removing libgdbm6:i386 (1.23-1) ...
Removing libgdk-pixbuf2.0-0:amd64 (2.40.2-2build4) ...
Removing libgeos-3.8.0:amd64 (3.8.0-1build1) ...
Removing libglapi-mesa:i386 (23.2.1-1ubuntu3.1~22.04.2) ...
Removing libglew2.1:amd64 (2.1.0-4) ...
Removing libgudev-1.0-0:i386 (1:237-2build1) ...
Removing libglu1-mesa:i386 (9.0.2-1) ...
Removing libopengl0:i386 (1.4.0-1) ...
Removing libglvnd0:i386 (1.4.0-1) ...
Removing libldap-2.5-0:i386 (2.5.17+dfsg-0ubuntu0.22.04.1) ...
Removing librtmp1:i386 (2.4+20151223.gitfa8646d.1-2build4) ...
Removing libgnutls30:i386 (3.7.3-4ubuntu1.5) ...
Removing libsoxr0:i386 (0.1.3-4build2) ...
Removing libgomp1:i386 (12.3.0-1ubuntu1~22.04) ...
Removing libgpac4:amd64 (0.5.2-426-gc5ad4e4+dfsg5-5) ...
Removing libgphoto2-port12:i386 (2.5.27-1build2) ...
Removing libgsm1:i386 (1.0.19-1) ...
Removing libgtkspell0:amd64 (2.0.16-1.3) ...
Removing libgupnp-1.2-0:amd64 (1.2.4-0ubuntu1) ...
Removing libhandy-0.0-0:amd64 (0.0.13-3) ...
Removing libhcrypto4-heimdal:amd64 (7.7.0+dfsg-3ubuntu1) ...
Removing libhcrypto4-heimdal:i386 (7.7.0+dfsg-3ubuntu1) ...
Removing libnetcdf15:amd64 (1:4.7.3-1) ...
Removing libhdf5-103:amd64 (1.10.7+repack-4ubuntu2) ...
Removing libhdf5-hl-fortran-100:amd64 (1.10.7+repack-4ubuntu2) ...
Removing libhdf5-fortran-102:amd64 (1.10.7+repack-4ubuntu2) ...
Removing libheimbase1-heimdal:i386 (7.7.0+dfsg-3ubuntu1) ...
Removing libheimbase1-heimdal:amd64 (7.7.0+dfsg-3ubuntu1) ...
Removing libhogweed5:amd64 (3.5.1+really3.5.1-2ubuntu0.2) ...
Removing libhogweed5:i386 (3.5.1+really3.5.1-2ubuntu0.2) ...
Removing libhogweed6:i386 (3.7.3-1build2) ...
Removing libicu66:i386 (66.1-2ubuntu2.1) ...
Removing libxslt1.1:i386 (1.1.34-4ubuntu0.22.04.1) ...
Removing libtag1v5:i386 (1.11.1+dfsg.1-3ubuntu3) ...
Removing libtag1v5-vanilla:i386 (1.11.1+dfsg.1-3ubuntu3) ...
Removing libiec61883-0:i386 (1.2.0-4build3) ...
Removing libieee1284-3:i386 (0.2.11-14build2) ...
Removing libigdgmm11:i386 (20.1.1+ds1-1) ...
Removing libigdgmm11:amd64 (20.1.1+ds1-1) ...
Removing libigdgmm12:i386 (22.1.2+ds1-1) ...
Removing libopenexr24:amd64 (2.3.0-6ubuntu0.5) ...
Removing libilmbase24:amd64 (2.3.0-6build1) ...
Removing libjack-jackd2-0:i386 (1.9.20~dfsg-1) ...
Removing libjbig0:i386 (2.1-3.1ubuntu0.22.04.1) ...
Removing libv4l-0:i386 (1.22.1-2build1) ...
Removing libv4lconvert0:i386 (1.22.1-2build1) ...
Removing libjpeg8:i386 (8c-2ubuntu10) ...
Removing libjpeg-turbo8:i386 (2.1.2-0ubuntu1) ...
Removing libjs-scriptaculous (1.9.0-2.1) ...
Removing libjs-prototype (1.7.1-3.1) ...
Removing libjson-c4:amd64 (0.13.1+dfsg-7ubuntu0.3) ...
Removing libopenshot16:amd64 (0.2.2+dfsg1-1ubuntu3) ...
Removing libjsoncpp1:amd64 (1.7.4-3.1ubuntu2) ...
Removing libjuh-java (1:7.3.7-0ubuntu0.22.04.5) ...
Removing libjurt-java (1:7.3.7-0ubuntu0.22.04.5) ...
Removing libkf5su-bin (5.92.0-0ubuntu1.1) ...
Removing libkf5su5:amd64 (5.92.0-0ubuntu1.1) ...
Removing libkf5pty5:amd64 (5.92.0-0ubuntu1) ...
Removing libkf5pty-data (5.92.0-0ubuntu1) ...
Removing libkf5pulseaudioqt2:amd64 (1.2-2build1) ...
Removing libkf5su-data (5.92.0-0ubuntu1.1) ...
Removing libkworkspace5-5 (4:5.24.7-0ubuntu0.1) ...
Removing liblcms2-2:i386 (2.12~rc1-2build2) ...
Removing libridl-java (1:7.3.7-0ubuntu0.22.04.5) ...
Removing liblibreoffice-java (1:7.3.7-0ubuntu0.22.04.5) ...
Removing libllvm12:amd64 (1:12.0.1-19ubuntu3) ...
Removing libodbc1:i386 (2.3.9-5ubuntu0.1) ...
Removing libodbccr2:i386 (2.3.9-5ubuntu0.1) ...
Removing libodbc2:i386 (2.3.9-5ubuntu0.1) ...
Removing libltdl7:i386 (2.4.6-15build2) ...
Removing libmozjs-68-0:amd64 (68.6.0-1ubuntu1) ...
Removing libmp3lame0:i386 (3.100-3build2) ...
Removing libmpg123-0:i386 (1.29.3-1build1) ...
Removing libmysqlclient21:i386 (8.0.37-0ubuntu0.22.04.3) ...
Removing libnettle7:i386 (3.5.1+really3.5.1-2ubuntu0.2) ...
Removing libnettle7:amd64 (3.5.1+really3.5.1-2ubuntu0.2) ...
Removing libnettle8:i386 (3.7.3-1build2) ...
Removing libnghttp2-14:i386 (1.43.0-1ubuntu0.2) ...
Removing libnss3:i386 (2:3.98-0ubuntu0.22.04.2) ...
Removing libnspr4:i386 (2:4.35-0ubuntu0.22.04.1) ...
Removing libntfs-3g883 (1:2017.3.23AR.3-3ubuntu1.3) ...
Removing libx265-179:i386 (3.2.1-1build1) ...
Removing libx265-199:i386 (3.5-2) ...
Removing libnuma1:i386 (2.0.14-3ubuntu2) ...
Removing libodbc1:amd64 (2.3.9-5ubuntu0.1) ...
Removing libodbccr2:amd64 (2.3.9-5ubuntu0.1) ...
Removing libvorbisenc2:i386 (1.3.7-1build2) ...
Removing libvorbis0a:i386 (1.3.7-1build2) ...
Removing libogg0:i386 (1.3.5-0ubuntu3) ...
Removing libopencore-amrnb0:i386 (0.1.5-1) ...
Removing libopencore-amrwb0:i386 (0.1.5-1) ...
Removing libopencv-ml4.2:amd64 (4.2.0+dfsg-5) ...
Removing libopencv-imgproc4.2:amd64 (4.2.0+dfsg-5) ...
Removing libopencv-flann4.2:amd64 (4.2.0+dfsg-5) ...
Removing libopenjp2-7:i386 (2.4.0-6) ...
Removing libopenshot-audio6:amd64 (0.1.7+dfsg1-1) ...
Removing libopus0:i386 (1.3.1-0.1build2) ...
Removing liborc-0.4-0:i386 (1:0.4.32-2) ...
Removing libosmesa6:amd64 (23.2.1-1ubuntu3.1~22.04.2) ...
Removing libp11-kit0:i386 (0.24.0-6build1) ...
Removing libpcap0.8:i386 (1.10.1-4build1) ...
Removing libpci3:i386 (1:3.7.0-6) ...
Removing libpciaccess0:i386 (0.16-3) ...
Removing libpcre2-posix2:amd64 (10.34-7ubuntu0.1) ...
Removing libsnmp35:amd64 (5.8+dfsg-2ubuntu2.9) ...
Removing libperl5.30:amd64 (5.30.0-9ubuntu0.5) ...
Removing libpgm-5.2-0:amd64 (5.2.122~dfsg-3ubuntu1) ...
Removing phonon4qt5:amd64 (4:4.11.1-4) ...
Removing phonon4qt5-backend-vlc:amd64 (0.11.3-1) ...
Removing libphonon4qt5-4:amd64 (4:4.11.1-4) ...
Removing libphonon4qt5-data (4:4.11.1-4) ...
Removing libplacebo7:amd64 (1.7.0-2) ...
Removing libzvbi0:i386 (0.2.35-19) ...
Removing libpoppler97:amd64 (0.86.1-0ubuntu1.4) ...
Removing libproj15:amd64 (6.3.1-1) ...
Removing libprotobuf-lite17:amd64 (3.6.1.3-2ubuntu5.2) ...
Removing libprotobuf17:amd64 (3.6.1.3-2ubuntu5.2) ...
Removing libproxy1v5:i386 (0.4.17-2) ...
Removing libpsl5:i386 (0.21.0-1.2build2) ...
Removing python2-dev (2.7.18-3) ...
Removing libpython2-dev:amd64 (2.7.18-3) ...
Removing python2.7-dev (2.7.18-13ubuntu1.2) ...
Removing libpython2.7-dev:amd64 (2.7.18-13ubuntu1.2) ...
Removing libpython2.7:amd64 (2.7.18-13ubuntu1.2) ...
Removing python3.8-dev (3.8.10-0ubuntu1~20.04.9) ...
Removing libpython3.8-dev:amd64 (3.8.10-0ubuntu1~20.04.9) ...
Removing libpython3.8:amd64 (3.8.10-0ubuntu1~20.04.9) ...
Removing python3.8 (3.8.10-0ubuntu1~20.04.9) ...
Removing libpython3.8-stdlib:amd64 (3.8.10-0ubuntu1~20.04.9) ...
Removing python3.8-minimal (3.8.10-0ubuntu1~20.04.9) ...
Unlinking and removing bytecode for runtime python3.8
Removing libpython3.8-minimal:amd64 (3.8.10-0ubuntu1~20.04.9) ...
Removing libqhull7:amd64 (2015.2-4) ...
Removing libqpdf26:amd64 (9.1.1-1ubuntu0.1) ...
Removing libqt5opengl5:amd64 (5.15.3+dfsg-2ubuntu0.2) ...
Removing libqt5webenginewidgets5:amd64 (5.15.9+dfsg-1) ...
Removing libqt5webenginecore5:amd64 (5.15.9+dfsg-1) ...
Removing libqt5webengine-data (5.15.9+dfsg-1) ...
Removing rarian-compat (0.8.1-6build1) ...
Removing librarian0 (0.8.1-6build1) ...
Removing libraw1394-11:i386 (2.1.2-2build2) ...
Removing libraw19:amd64 (0.19.5-1ubuntu1.3) ...
Removing libre2-5:amd64 (20200101+dfsg-1build1) ...
Removing libre2-9:amd64 (20220201+dfsg-1) ...
Removing libreoffice-style-tango (1:7.3.7-0ubuntu0.22.04.5) ...
Removing libwind0-heimdal:amd64 (7.7.0+dfsg-3ubuntu1) ...
Removing libwind0-heimdal:i386 (7.7.0+dfsg-3ubuntu1) ...
Removing libsamplerate0:i386 (0.2.2-1build1) ...
Removing libsane:amd64 (1.1.1-5) ...
Removing libsasl2-2:i386 (2.1.27+dfsg2-3ubuntu1.2) ...
Removing libsasl2-modules:i386 (2.1.27+dfsg2-3ubuntu1.2) ...
Removing libsasl2-modules-db:i386 (2.1.27+dfsg2-3ubuntu1.2) ...
Removing libsensors5:i386 (1:3.6.0-7ubuntu1) ...
Removing libshine3:i386 (3.1.1-2) ...
Removing libslang2:i386 (2.3.2-5build4) ...
Removing libsnappy1v5:i386 (1.1.8-1build3) ...
Removing libspeex1:i386 (1.2~rc1.2-1.1ubuntu3) ...
Removing libsqlite3-0:i386 (3.37.2-2ubuntu0.3) ...
Removing libsrt1:amd64 (1.4.0-1build1) ...
Removing libssh-4:i386 (0.9.6-2ubuntu0.22.04.3) ...
Removing libssl1.1:i386 (1.1.1f-1ubuntu2.22) ...
Removing libstb0:amd64 (0.0~git20210910.af1a5bc+ds-1) ...
Removing libstb0:i386 (0.0~git20210910.af1a5bc+ds-1) ...
Removing libstdc++-7-dev:amd64 (7.5.0-6ubuntu2) ...
Removing libstdc++-9-dev:amd64 (9.5.0-1ubuntu1~22.04) ...
Removing libtasn1-6:i386 (4.18.0-4build1) ...
Removing libtracker-control-2.0-0:amd64 (2.3.6-0ubuntu1) ...
Removing libtracker-miner-2.0-0:amd64 (2.3.6-0ubuntu1) ...
Removing libtracker-sparql-2.0-0:amd64 (2.3.6-0ubuntu1) ...
Removing libtwolame0:i386 (0.4.0-2build2) ...
Removing ure-java (1:7.3.7-0ubuntu0.22.04.5) ...
Removing libunoloader-java (1:7.3.7-0ubuntu0.22.04.5) ...
Removing libunwind8:i386 (1.3.2-2build2.1) ...
Removing liburl-dispatcher1:amd64 (0.1+17.04.20170328-0ubuntu4) ...
Removing libusageenvironment3:amd64 (2020.01.19-1build1) ...
Removing libusb-1.0-0:i386 (2:1.0.25-1ubuntu2) ...
Removing libva-drm2:i386 (2.14.0-1) ...
Removing libva-x11-2:i386 (2.14.0-1) ...
Removing libva2:i386 (2.14.0-1) ...
Removing libvdpau1:i386 (1.4-3build2) ...
Removing libvisual-0.4-0:i386 (0.4.0-17build2) ...
Removing libvkd3d1:i386 (1.1-5) ...
Removing libvkd3d1:amd64 (1.1-5) ...
Removing libvo-amrwbenc0:i386 (0.1.3-2) ...
Removing libvpx6:i386 (1.8.2-1ubuntu0.3) ...
Removing libvpx6:amd64 (1.8.2-1ubuntu0.3) ...
Removing libvpx7:i386 (1.11.0-2ubuntu2.3) ...
Removing libvulkan1:i386 (1.3.204.1-2) ...
Removing libwavpack1:i386 (5.4.0-1build2) ...
Removing libwayland-egl1:i386 (1.20.0-1ubuntu0.1) ...
Removing libwcs7:amd64 (7.7+ds-1) ...
Removing libwebp6:amd64 (0.6.1-2ubuntu0.20.04.3) ...
Removing libwebp6:i386 (0.6.1-2ubuntu0.20.04.3) ...
Removing libwebpmux3:i386 (1.2.2-2ubuntu0.22.04.2) ...
Removing libwebp7:i386 (1.2.2-2ubuntu0.22.04.2) ...
Removing libwmf0.2-7:amd64 (0.2.12-5ubuntu1) ...
Removing libwrap0:i386 (7.6.q-31build2) ...
Removing libxpm4:i386 (1:3.5.12-1ubuntu0.22.04.2) ...
Removing libx11-xcb1:i386 (2:1.7.5-1ubuntu0.3) ...
Removing libx264-155:amd64 (2:0.155.2917+git0a84d98-2) ...
Removing libx264-155:i386 (2:0.155.2917+git0a84d98-2) ...
Removing libx264-163:i386 (2:0.163.3060+git5db6aa6-2build1) ...
Removing libx265-179:amd64 (3.2.1-1build1) ...
Removing libxcb-dri2-0:i386 (1.14-3ubuntu3) ...
Removing libxcb-dri3-0:i386 (1.14-3ubuntu3) ...
Removing libxcb-glx0:i386 (1.14-3ubuntu3) ...
Removing libxcb-present0:i386 (1.14-3ubuntu3) ...
Removing libxcb-randr0:i386 (1.14-3ubuntu3) ...
Removing libxcb-sync1:i386 (1.14-3ubuntu3) ...
Removing libxcb-xfixes0:i386 (1.14-3ubuntu3) ...
Removing libxcomposite1:i386 (1:0.4.5-1build2) ...
Removing libxcursor1:i386 (1:1.2.0-2build4) ...
Removing libxdamage1:i386 (1:1.1.5-2build2) ...
Removing libxxf86vm1:i386 (1:1.1.4-1build3) ...
Removing libxv1:i386 (2:1.0.11-1build2) ...
Removing libxfixes3:i386 (1:6.0.0-1) ...
Removing libxi6:i386 (2:1.8-1build1) ...
Removing libxinerama1:i386 (2:1.1.4-3) ...
Removing libxkbcommon0:i386 (1.4.0-1) ...
Removing libxrandr2:i386 (2:1.5.2-1build1) ...
Removing libxshmfence1:i386 (1.3-1build4) ...
Removing libxss1:i386 (1:1.2.3-1build2) ...
Removing libxvidcore4:i386 (2:1.3.7-1) ...
Removing libyaml-cpp0.6:amd64 (0.6.2-4ubuntu1) ...
Removing libz-mingw-w64 (1.2.11+dfsg-4) ...
Removing libzip5:amd64 (1.5.1-0ubuntu1) ...
Removing ltrace (0.7.3-6.1ubuntu6.22.04.1) ...
Removing lz4 (1.9.3-2build2) ...
Removing ncal (12.1.7+nmu3ubuntu2) ...
Removing ocl-icd-libopencl1:i386 (2.2.14-3) ...
Removing odbcinst1debian2:amd64 (2.3.9-5ubuntu0.1) ...
Removing odbcinst (2.3.9-5ubuntu0.1) ...
Removing perl-modules-5.30 (5.30.0-9ubuntu0.5) ...
Removing popularity-contest (1.71ubuntu3) ...
Removing python-bs4 (4.8.2-1) ...
Removing python-soupsieve (1.9.5+dfsg-1) ...
Removing python-backports.functools-lru-cache (1.5-3build1) ...
Removing python-html5lib (1.0.1-2) ...
Removing python-lxml:amd64 (4.5.0-1ubuntu0.5) ...
Removing python-numpy (1:1.16.5-2ubuntu7) ...
Removing python-pkg-resources (44.1.1-1.2ubuntu0.22.04.1) ...
Removing python-six (1.16.0-3ubuntu1) ...
Removing python-webencodings (0.5.1-1ubuntu1) ...
Removing python3-entrypoints (0.4-1) ...
Removing python3-requests-unixsocket (0.2.0-2) ...
Removing python3-simplejson (3.17.6-1build1) ...
Removing python3-sip (4.19.25+dfsg-3build1) ...
Removing ruby2.7 (2.7.0-5ubuntu1.12) ...
Removing siril-common (1.2.1-0ubuntu0~focalppa2) ...
Removing syslinux (3:6.04~git20190206.bf6db5b4+dfsg1-3ubuntu1) ...
Removing syslinux-common (3:6.04~git20190206.bf6db5b4+dfsg1-3ubuntu1) ...
Removing syslinux-legacy (2:3.63+dfsg-2ubuntu9) ...
Removing x11proto-input-dev (2021.5-1) ...
Removing x11proto-randr-dev (2021.5-1) ...
Removing x11proto-xext-dev (2021.5-1) ...
Removing x11proto-xinerama-dev (2021.5-1) ...
Removing libasn1-8-heimdal:i386 (7.7.0+dfsg-3ubuntu1) ...
Removing libasn1-8-heimdal:amd64 (7.7.0+dfsg-3ubuntu1) ...
Removing libllvm15:i386 (1:15.0.7-0ubuntu0.22.04.3) ...
Removing libatomic1:i386 (12.3.0-1ubuntu1~22.04) ...
Removing libboost-thread1.71.0:amd64 (1.71.0-6ubuntu6) ...
Removing libpangocairo-1.0-0:i386 (1.50.6+ds-2ubuntu1) ...
Removing libpangoft2-1.0-0:i386 (1.50.6+ds-2ubuntu1) ...
Removing libedit2:i386 (3.1-20210910-1build1) ...
Removing libcairo2:i386 (1.16.0-5ubuntu2) ...
Removing libpango-1.0-0:i386 (1.50.6+ds-2ubuntu1) ...
Removing libthai0:i386 (0.1.29-1build1) ...
Removing libdatrie1:i386 (0.2.13-2) ...
Removing libdrm2:i386 (2.4.113-2~ubuntu0.22.04.1) ...
Removing libfontconfig1:i386 (2.13.1-4.2ubuntu5) ...
Removing libexpat1:i386 (2.4.7-1ubuntu0.3) ...
Removing libfribidi0:i386 (1.0.8-2ubuntu3.1) ...
Removing libharfbuzz0b:i386 (2.7.4-1ubuntu3.1) ...
Removing libglib2.0-0:i386 (2.72.4-0ubuntu2.3) ...
Removing libgraphite2-3:i386 (1.3.14-1build2) ...
Removing libxml2:i386 (2.9.13+dfsg-1ubuntu0.4) ...
Removing libicu70:i386 (70.1-2) ...
Removing libopencv-core4.2:amd64 (4.2.0+dfsg-5) ...
Removing libpixman-1-0:i386 (0.40.0-1ubuntu0.22.04.1) ...
Removing libroken18-heimdal:amd64 (7.7.0+dfsg-3ubuntu1) ...
Removing libroken18-heimdal:i386 (7.7.0+dfsg-3ubuntu1) ...
Removing libstdc++6:i386 (12.3.0-1ubuntu1~22.04) ...
Removing libxcb-render0:i386 (1.14-3ubuntu3) ...
Removing libxcb-shm0:i386 (1.14-3ubuntu3) ...
Removing libxext6:i386 (2:1.3.4-1build1) ...
Removing libxrender1:i386 (1:0.9.10-1build4) ...
Removing libfreetype6:i386 (2.11.1+dfsg-1ubuntu0.2) ...
Removing libbrotli1:i386 (1.0.9-2build6) ...
Removing libffi8:i386 (3.4.2-4) ...
Removing libpng16-16:i386 (1.6.37-3build5) ...
Removing libx11-6:i386 (2:1.7.5-1ubuntu0.3) ...
Removing libxcb1:i386 (1.14-3ubuntu3) ...
Removing libxdmcp6:i386 (1:1.1.3-0ubuntu5) ...
Removing libbsd0:i386 (0.11.5-1) ...
Removing libmd0:i386 (1.0.4-1build1) ...
Removing libxau6:i386 (1:1.0.9-1build5) ...
Setting up openmpi-bin (4.1.2-2ubuntu1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/mpi corrupt: slave link s
ame as main link /usr/bin/mpicc
dpkg: error processing package openmpi-bin (--configure):
 installed openmpi-bin package post-installation script subprocess returned erro
r exit status 2
dpkg: dependency problems prevent configuration of mpi-default-bin:
 mpi-default-bin depends on openmpi-bin; however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package mpi-default-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcoarrays-openmpi-dev:amd64
:
 libcoarrays-openmpi-dev:amd64 depends on openmpi-bin; however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package libcoarrays-openmpi-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopenmpi-dev:amd64:
 libopenmpi-dev:amd64 depends on openmpi-bin (>= 3.0.0-1); however:
  Package openmpi-bin is not configured yet.

dpkg: error processing package libopenmpi-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi-pythonNo apport 
report written because the error message indicates its a followup error from a p
revious failure.
                No apport report written because the error message indicates its
 a followup error from a previous failure.
                                          No apport report written because MaxRe
ports is reached already
                        No apport report written because MaxReports is reached a
lready
      No apport report written because MaxReports is reached already
                                                                    No apport re
port written because MaxReports is reached already
                                                  No apport report written becau
se MaxReports is reached already
                                No apport report written because MaxReports is r
eached already
              No apport report written because MaxReports is reached already
                                                                            No a
pport report written because MaxReports is reached already
                                                          1.74.0:
 libboost-mpi-python1.74.0 depends on mpi-default-bin; however:
  Package mpi-default-bin is not configured yet.

dpkg: error processing package libboost-mpi-python1.74.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi-python1.74-dev:
 libboost-mpi-python1.74-dev depends on libboost-mpi-python1.74.0 (= 1.74.0-14ub
untu3); however:
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
Processing triggers for shared-mime-info (2.1-2) ...
Processing triggers for sgml-base (1.30) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.6+22.04.20220217-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libc-bin (2.35-0ubuntu3.8) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libreoffice-common (1:7.3.7-0ubuntu0.22.04.5) ...
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
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe@joe-X555LAB:~$ sudo apt clean
joe@joe-X555LAB:~$
```

---

### Post by Joe_Linux on 2024-06-15
bump please help this error appears when I use apt

---

### Post by Joe_Linux on 2024-06-15
I also tried 
```
joe@joe-X555LAB:~$ sudo apt --fix-broken install
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
11 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
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
dpkg: dependency problems prevent configuration of libboost-mpi-pythonNo apport 
report written because the error message indicates its a followup error from a p
revious failure.
                No apport report written because the error message indicates its
 a followup error from a previous failure.
                                          No apport report written because MaxRe
ports is reached already
                        No apport report written because MaxReports is reached a
lready
      No apport report written because MaxReports is reached already
                                                                    No apport re
port written because MaxReports is reached already
                                                  No apport report written becau
se MaxReports is reached already
                                No apport report written because MaxReports is r
eached already
              No apport report written because MaxReports is reached already
                                                                            No a
pport report written because MaxReports is reached already
                                                          1.74.0:
 libboost-mpi-python1.74.0 depends on mpi-default-bin; however:
  Package mpi-default-bin is not configured yet.

dpkg: error processing package libboost-mpi-python1.74.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-mpi-python1.74-dev:
 libboost-mpi-python1.74-dev depends on libboost-mpi-python1.74.0 (= 1.74.0-14ub
untu3); however:
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
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe@joe-X555LAB:~$ sudo apt-get clean
joe@joe-X555LAB:~$ sudo package libboost-mpi1.74-dev (--configure)
bash: syntax error near unexpected token `('
joe@joe-X555LAB:~$ sudo configure libboost-mpi1.74-dev
sudo: configure: command not found
joe@joe-X555LAB:~$ cat libboost-mpi1.74-dev
cat: libboost-mpi1.74-dev: No such file or directory
joe@joe-X555LAB:~$ cat libboost-mpi-dev
cat: libboost-mpi-dev: No such file or directory
joe@joe-X555LAB:~$

```

---

### Post by Joe_Linux on 2024-06-15
I realize that everyone here is a volunteer
but if any one can help please do so. With my limited knowledge these lines of code seem to be the problem
```
 dpkg: error processing package libboost-mpi-dev (--configure):
 dependency problems - leaving unconfigured
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
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by #&amp;thj^% on 2024-06-15
Just to help get things rolling, first do you not have a back-up in place....just saying a OS Version Upgrade has always been a hit or miss so backus should have taken place before the upgrade.

1st Good suggestion, copy off your install you have now to a back-up media disk or drive then do a clean install. (And you would have been up and running now)

2nd suggestion is please show us this:
```
sudo apt clean
sudo apt update
sudo apt -s upgrade
```

---

