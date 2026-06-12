---
title: "How can I run Pando downloader with x64 Ubuntu?"
date: 2007-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by doragasu on 2007-11-30
I'm trying to get Pando Downloader to run with Ubuntu 7.10 amd64, but I'm out of luck. The program and the following installation instructions can be found [here](http://www.pando.com/phpbb/viewtopic.php?t=4046).

INSTALLATION INSTRUCTIONS (from pando forums)

> Hello,

Please see below for the link to download the Pando Linux Downloader (v0.9.2 Beta), please read the following instructions before installing/running this software.

We are very interested in hearing about your experiences with this software so please create posts sharing your feedback, don't forget to include the distribution you are running and it's version!

Thanks.

[http://www.pando.com/dl/download/pandodl-0.9.2.0.tar.bz2](http://www.pando.com/dl/download/pandodl-0.9.2.0.tar.bz2)

Fixes: 1.8.5+ File Compatiblility
Numerous Connection fixes present in the 1.8.5.1 Win/Mac Client

Prerequisites
===========

Debian/Ubuntu
------------------

The packages listed below can be installed by becoming root and typing,
'apt-get install <package>'

libgtk2.0-0
libuuid1
libexpat1
zlib1g
libstdc++5

Fedora
---------

The packages listed below can be installed by becoming root and typing,
'yum install <package>'

gtk2
e2fsprogs-libs
expat
zlib
compat-libstdc++-33

Note: If installing on Fedora, after following the installation steps below
the following additional step has to be taken.

Go to the pandodl directory and run 'ln -s /lib/libexpat.so.0 lib/libexpat.so.1'

Installation
=========

After the prerequisites are installed the Pando Downloader Beta can be
installed by following the steps below.

1. If a systemwide install is desired become root and run the command below
from the /usr/local/bin directory, for a user install run it in the user's home dir.

tar xvfj pandodl-xx.tar.bz2

2. Run 'export PANDO_HOME=/PATH/TO/PANDODL_DIR'

3. $PANDO_HOME/pandodl may be run to launch the Pando Downloader.

Configuration
===========

After first run a file named .pandoDownloader will be created, the following
values can be added to it.

Listen_Port - is the listening port for other peers to connect to.
Limit_Upload_Rate - is the upload rate in KB/s.
Proxy_Host - Hostname or IP of the Proxy server.
Proxy_Port - Port the proxy server is listening on.
Proxy_User - Username for the proxy server.
Proxy_Pass - Password for the proxy server.

I have installed the required libraries, but when I run the program, it crashes with this message:

> ./pandoDownloader: error while loading shared libraries: libwx_gtk2_aui-2.8.so.0: cannot open shared object file: No such file or directory

Under /user/lib I have the following libraries:

```
doragasu@doragasu-64:/usr/lib$ ls libwx_gtk2*
libwx_gtk2u_adv-2.6.so.0             libwx_gtk2u_html-2.6.so.0.3.1
libwx_gtk2u_adv-2.6.so.0.3.1         libwx_gtk2u_media-2.6.so.0
libwx_gtk2u_animate-2.6.so.0         libwx_gtk2u_media-2.6.so.0.3.1
libwx_gtk2u_animate-2.6.so.0.3.1     libwx_gtk2u_mmedia-2.6.so.0
libwx_gtk2u_core-2.6.so.0            libwx_gtk2u_mmedia-2.6.so.0.3.1
libwx_gtk2u_core-2.6.so.0.3.1        libwx_gtk2u_ogl-2.6.so.0
libwx_gtk2u_deprecated-2.6.so.0      libwx_gtk2u_ogl-2.6.so.0.3.1
libwx_gtk2u_deprecated-2.6.so.0.3.1  libwx_gtk2u_plot-2.6.so.0
libwx_gtk2u_fl-2.6.so.0              libwx_gtk2u_plot-2.6.so.0.3.1
libwx_gtk2u_fl-2.6.so.0.3.1          libwx_gtk2u_qa-2.6.so.0
libwx_gtk2u_gizmos-2.6.so.0          libwx_gtk2u_qa-2.6.so.0.3.1
libwx_gtk2u_gizmos-2.6.so.0.3.1      libwx_gtk2u_stc-2.6.so.0
libwx_gtk2u_gizmos_xrc-2.6.so.0      libwx_gtk2u_stc-2.6.so.0.3.1
libwx_gtk2u_gizmos_xrc-2.6.so.0.3.1  libwx_gtk2u_svg-2.6.so.0
libwx_gtk2u_gl-2.6.so.0              libwx_gtk2u_svg-2.6.so.0.3.1
libwx_gtk2u_gl-2.6.so.0.3.1          libwx_gtk2u_xrc-2.6.so.0
libwx_gtk2u_html-2.6.so.0            libwx_gtk2u_xrc-2.6.so.0.3.1
```

As you can see, there's no libwx_gtk2_aui library, How can I fix this problem?

---

### Post by Kilz on 2007-11-30
I did a search on the [Ubuntu package site]("http://packages.ubuntu.com/") for that file in any package. It doesnt exist. You may want to contact the developer of the application.

---

