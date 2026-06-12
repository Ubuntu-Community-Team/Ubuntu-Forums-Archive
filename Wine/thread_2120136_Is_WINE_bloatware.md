---
title: "Is WINE bloatware?"
date: 2013-02-25
forum: Wine
---

### Post by zph on 2013-02-25
Did a fresh install of Ubuntu 12.04.2 x64 and then tried to install WINE. Since when it pulls another 500Mb of dependences?

```

# apt-get install wine
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  binfmt-support cabextract fonts-droid fonts-horai-umefont fonts-unfonts-core
  gcc-4.6-base:i386 gnome-exe-thumbnailer icoutils imagemagick
  imagemagick-common libasn1-8-heimdal:i386 libasound2:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libc6:i386 libcapi20-3 libcapi20-3:i386 libcdt4 libcomerr2:i386
  libcups2:i386 libdb5.1:i386 libdbus-1-3:i386 libdrm2:i386
  libencode-locale-perl libexif12:i386 libexpat1:i386 libffi6:i386
  libfile-listing-perl libfont-afm-perl libfontconfig1:i386 libfreetype6:i386
  libgcc1:i386 libgcrypt11:i386 libgd2-xpm:i386 libgettextpo0 libgif4
  libgif4:i386 libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-glx:i386
  libglapi-mesa libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386
  libgnutls26:i386 libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libgpm2:i386 libgraph4 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgvc5
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhx509-5-heimdal:i386 libice6:i386
  libieee1284-3:i386 libilmbase6 libio-socket-inet6-perl libio-socket-ssl-perl
  libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms1:i386
  libldap-2.4-2:i386 libllvm3.0 liblqr-1-0 libltdl7:i386
  liblwp-mediatypes-perl liblwp-protocol-https-perl libmagickcore4
  libmagickcore4-extra libmagickwand4 libmailtools-perl libmpg123-0
  libmpg123-0:i386 libncurses5:i386 libnet-http-perl libnet-ssleay-perl
  libnetpbm10 libodbc1 libopenal-data libopenal1 libopenal1:i386 libopenexr6
  liborc-0.4-0:i386 libp11-kit0:i386 libpam-winbind libpathplan4 libpcre3:i386
  libpng12-0:i386 libroken18-heimdal:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libselinux1:i386 libsm6:i386 libsocket6-perl
  libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-3:i386
  libtiff4:i386 libtinfo5:i386 libunistring0 liburi-perl libusb-0.1-4:i386
  libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libwind0-heimdal:i386
  libwww-perl libwww-robotrules-perl libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-glx0:i386 libxcb1:i386 libxcomposite1:i386
  libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxpm4:i386
  libxrandr2:i386 libxrender1:i386 libxslt1.1:i386 libxt6:i386
  libxxf86vm1:i386 netpbm odbcinst odbcinst1debian2 ttf-droid
  ttf-mscorefonts-installer ttf-umefont ttf-unfonts-core unixodbc unrar
  winbind wine-gecko1.4 wine-gecko1.4:i386 wine1.4 wine1.4-amd64
  wine1.4-common wine1.4-i386:i386 winetricks xserver-xorg-core
  xserver-xorg-input-evdev zlib1g:i386
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl imagemagick-doc
  autotrace curl enscript ffmpeg gimp gnuplot grads hp2xx html2ps libwmf-bin
  mplayer povray radiance texlive-base-bin transfig ufraw-batch
  libasound2-plugins:i386 libasound2-python:i386 glibc-doc:i386 locales:i386
  cups-common:i386 rng-tools:i386 libgd-tools:i386 libglide3 gnutls-bin:i386
  gphoto2:i386 gtkam:i386 gpm:i386 krb5-doc:i386 krb5-user:i386
  libvisual-0.4-plugins:i386 gstreamer-codec-install:i386
  gnome-codec-install:i386 gstreamer0.10-tools:i386
  gstreamer0.10-plugins-base:i386 libdata-dump-perl liblcms-utils:i386
  libcrypt-ssleay-perl libmyodbc odbc-postgresql tdsodbc unixodbc-bin
  hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
  libsasl2-modules-otp:i386 libsasl2-modules-ldap:i386
  libsasl2-modules-sql:i386 libsasl2-modules-gssapi-mit:i386
  libsasl2-modules-gssapi-heimdal:i386 libauthen-ntlm-perl dosbox
  xfonts-100dpi xfonts-75dpi
Recommended packages:
  libgl1-mesa-dri:i386 xml-core:i386 gettext gettext:i386 unixodbc:i386
The following packages will be REMOVED:
  libgl1-mesa-dri-lts-quantal libgl1-mesa-glx-lts-quantal
  libglapi-mesa-lts-quantal libxatracker1-lts-quantal
  x11-xserver-utils-lts-quantal xorg xserver-common-lts-quantal
  xserver-xorg-core-lts-quantal xserver-xorg-input-all-lts-quantal
  xserver-xorg-input-evdev-lts-quantal xserver-xorg-input-mouse-lts-quantal
  xserver-xorg-input-synaptics-lts-quantal
  xserver-xorg-input-vmmouse-lts-quantal xserver-xorg-input-wacom-lts-quantal
  xserver-xorg-lts-quantal xserver-xorg-video-all-lts-quantal
  xserver-xorg-video-ati-lts-quantal xserver-xorg-video-cirrus-lts-quantal
  xserver-xorg-video-fbdev-lts-quantal xserver-xorg-video-intel-lts-quantal
  xserver-xorg-video-mach64-lts-quantal xserver-xorg-video-mga-lts-quantal
  xserver-xorg-video-modesetting-lts-quantal
  xserver-xorg-video-neomagic-lts-quantal
  xserver-xorg-video-nouveau-lts-quantal
  xserver-xorg-video-openchrome-lts-quantal
  xserver-xorg-video-r128-lts-quantal xserver-xorg-video-radeon-lts-quantal
  xserver-xorg-video-s3-lts-quantal xserver-xorg-video-savage-lts-quantal
  xserver-xorg-video-siliconmotion-lts-quantal
  xserver-xorg-video-sis-lts-quantal xserver-xorg-video-sisusb-lts-quantal
  xserver-xorg-video-tdfx-lts-quantal xserver-xorg-video-trident-lts-quantal
  xserver-xorg-video-vesa-lts-quantal xserver-xorg-video-vmware-lts-quantal
The following NEW packages will be installed:
  binfmt-support cabextract fonts-droid fonts-horai-umefont fonts-unfonts-core
  gcc-4.6-base:i386 gnome-exe-thumbnailer icoutils imagemagick
  imagemagick-common libasn1-8-heimdal:i386 libasound2:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libc6:i386 libcapi20-3 libcapi20-3:i386 libcdt4 libcomerr2:i386
  libcups2:i386 libdb5.1:i386 libdbus-1-3:i386 libdrm2:i386
  libencode-locale-perl libexif12:i386 libexpat1:i386 libffi6:i386
  libfile-listing-perl libfont-afm-perl libfontconfig1:i386 libfreetype6:i386
  libgcc1:i386 libgcrypt11:i386 libgd2-xpm:i386 libgettextpo0 libgif4
  libgif4:i386 libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-glx:i386
  libglapi-mesa libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386
  libgnutls26:i386 libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libgpm2:i386 libgraph4 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgvc5
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhx509-5-heimdal:i386 libice6:i386
  libieee1284-3:i386 libilmbase6 libio-socket-inet6-perl libio-socket-ssl-perl
  libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms1:i386
  libldap-2.4-2:i386 libllvm3.0 liblqr-1-0 libltdl7:i386
  liblwp-mediatypes-perl liblwp-protocol-https-perl libmagickcore4
  libmagickcore4-extra libmagickwand4 libmailtools-perl libmpg123-0
  libmpg123-0:i386 libncurses5:i386 libnet-http-perl libnet-ssleay-perl
  libnetpbm10 libodbc1 libopenal-data libopenal1 libopenal1:i386 libopenexr6
  liborc-0.4-0:i386 libp11-kit0:i386 libpam-winbind libpathplan4 libpcre3:i386
  libpng12-0:i386 libroken18-heimdal:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libselinux1:i386 libsm6:i386 libsocket6-perl
  libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-3:i386
  libtiff4:i386 libtinfo5:i386 libunistring0 liburi-perl libusb-0.1-4:i386
  libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libwind0-heimdal:i386
  libwww-perl libwww-robotrules-perl libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-glx0:i386 libxcb1:i386 libxcomposite1:i386
  libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxpm4:i386
  libxrandr2:i386 libxrender1:i386 libxslt1.1:i386 libxt6:i386
  libxxf86vm1:i386 netpbm odbcinst odbcinst1debian2 ttf-droid
  ttf-mscorefonts-installer ttf-umefont ttf-unfonts-core unixodbc unrar
  winbind wine wine-gecko1.4 wine-gecko1.4:i386 wine1.4 wine1.4-amd64
  wine1.4-common wine1.4-i386:i386 winetricks xserver-xorg-core
  xserver-xorg-input-evdev zlib1g:i386
0 upgraded, 173 newly installed, 37 to remove and 0 not upgraded.
Need to get 188 MB of archives.
After this operation, 495 MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

How can this be possible?

---

### Post by JiuJitsu500 on 2013-02-25
WINE is a translator, not an emulator.

The programs for Windows ask the WINDOWS kernel (or any DOS, etc. variant or part) what to allocate to what process. This doesn't work on linux since the kernel, hierarchy, everything is different. A lot of those packages are fonts, too, which are a lot of that space (microsoft's fonts are standard everywhere, even in Macs and Linux - so they for the most part are necessary in a way though you may be able to remove them without issue... I'm not really sure on that).

So, WINE uses most of those libraries and packages to read what the windows program is asking for - then those libraries translate that into something the linux kernel can understand, then the linux kernel gives up the resources, then it gets back to the program, which then it brought to what you can see and interface with.

WINE really doesn't need all of those - some are graphics-related, some are very specific - some are completely unnecessary for most apps. But, in the end, it's no easy task - especially for something like a game or production software (Newer Photoshops, Fruity Loops, Modern Warfare) that require big resources fast.

500MB is actually not that much when you think about what has to happen. Winetricks and some of the other crap you can get rid of and you'll never need. But the libraries and such I wouldn't touch unless you 100% knew exactly what libs you needed, and even then you might be left with an unresolved dependency or 38 and be screwed until it's resolved.

It's like meeting someone who speaks another language - it'd be perfect if you knew it, but you're fine with a translator so long as he can keep up - but any translator/interpretor you find has that native tounge as his/her second language. WINE and Parallels and such try, but it's not an easy task. Hence, all those packages and the need for a pretty boss computer to handle newer or resource-intensive things. Even then it might just be best to say "good luck" to yourself.

Or just dual boot or VM windows. It's only Apple that doesn't want that.

---

### Post by Bucky Ball on 2013-02-25
> **JiuJitsu500 said:**
> 

Or just dual boot or VM windows.

+1. The Windows app(s) you want to use may not work or will run poorly anyway. If you intend using a lot of Win apps, the above recommendation is definitely the way to go (or stick with Win as if you are looking for a drop in replacement for Win Ubuntu, even with Wine, is not it). ;)

---

### Post by offgridguy on 2013-02-25
> **Bucky Ball said:**
> +1. The Windows app(s) you want to use may not work or will run poorly anyway. If you intend using a lot of Win apps, the above recommendation is definitely the way to go (or stick with Win as if you are looking for a drop in replacement for Win Ubuntu, even with Wine, is not it). ;)
+1 here.

@JuiJitsu500,  Thanks for the great explanation.:D

---

### Post by Mark Phelps on 2013-02-27
> **zph said:**
> Did a fresh install of Ubuntu 12.04.2 x64 and then tried to install WINE...

BEFORE you get very far down this path, you could save yourself a lot of work and frustration if you go to the WineHQ site and browse the Application Compatibility database, looking for the Windows app and version you want to use.

You will see ratings there, from GARBAGE to Platinum.  Anything not listed, or rated less than Gold is going to be a waste of your time to install.

In such cases, you would better coming back and asking about Linux alternative apps, as those will work properly.

---

