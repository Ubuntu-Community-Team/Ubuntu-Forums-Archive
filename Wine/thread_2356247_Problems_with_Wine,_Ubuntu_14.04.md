---
title: "Problems with Wine, Ubuntu 14.04"
date: 2017-03-21
forum: Wine
---

### Post by slyther11 on 2017-03-21
Iv tried for weeks now to install wine on this chromebook C201P Acer. I follow the instruction as said on the winehq page as posted below. but i always get this (E: Unable to locate package from winehq-devel) if anyone has a fix for this id really appreciate it. Id have posted this on the winehq forums but it seemed a bit more appropriate here.

sudo add-apt-repository ppa:wine/wine-builds

sudo apt-get update

sudo apt-get install --install-recommends winehq-devel

---

### Post by howefield on 2017-03-21
Thread moved to the "*Wine*" forum for a better fit.

Tried the above (albiet not in 14.04) and appears to work fine. Please post the actual terminal input/output.

```
sudo apt-get install --install-recommends winehq-devel
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
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
  libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386 libxxf86vm1:i386 wine-devel wine-devel-amd64 wine-devel-i386:i386
  zlib1g:i386
Suggested packages:
  gvfs:i386 glibc-doc:i386 locales:i386 rng-tools:i386 libgd-tools:i386 gnutls-bin:i386 gphoto2:i386 gpm:i386 krb5-doc:i386 krb5-user:i386
  libvisual-0.4-plugins:i386 gstreamer1.0-tools:i386 jackd2:i386 libmyodbc odbc-postgresql tdsodbc unixodbc-bin libmyodbc:i386
  odbc-postgresql:i386 tdsodbc:i386 unixodbc-bin:i386 libportaudio2:i386 opus-tools:i386 hplip:i386 libsane-extras:i386
  libsasl2-modules-gssapi-mit:i386 libsasl2-modules-ldap:i386 libsasl2-modules-otp:i386 libsasl2-modules-sql:i386 lm-sensors:i386
  sndiod:i386
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
  libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386 libxxf86vm1:i386 wine-devel wine-devel-amd64 wine-devel-i386:i386
  winehq-devel zlib1g:i386
0 to upgrade, 159 to newly install, 0 to remove and 57 not to upgrade.
Need to get 94.5 MB of archives.
After this operation, 688 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

---

### Post by slyther11 on 2017-03-21
(trusty)```
kuilox@localhost:~$ sudo add-apt-repository ppa:wine/wine-builds
[sudo] password for kuilox: 
 
 More info: [https://launchpad.net/~wine/+archive/ubuntu/wine-builds](https://launchpad.net/~wine/+archive/ubuntu/wine-builds)
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpkle6tcyt/secring.gpg' created
gpg: keyring `/tmp/tmpkle6tcyt/pubring.gpg' created
gpg: requesting key 77C899CB from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpkle6tcyt/trustdb.gpg: trustdb created
gpg: key 77C899CB: public key "Launchpad PPA for Wine" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
```
```
kuilox@localhost:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                        
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty InRelease                         
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main armhf Packages                 
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security InRelease                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                 
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty Release.gpg 
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/restricted Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/universe Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/multiverse Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/restricted armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/universe armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/multiverse armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates/universe Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/restricted Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/universe Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/multiverse Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/restricted armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/universe armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/multiverse armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-security/universe Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty Release          
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/restricted Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/universe Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/multiverse Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/main armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/restricted armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/universe armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/multiverse armhf Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/main Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/multiverse Translation-en                   
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/restricted Translation-en                   
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/universe Translation-en                     
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/main Translation-en_US                      
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/multiverse Translation-en_US                
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/restricted Translation-en_US                
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty/universe Translation-en_US                  
Reading package lists... Done
```                                               
```
kuilox@localhost:~$ sudo apt-get install --install-recommends winehq-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package winehq-devel
kuilox@localhost:~$
```


theres the entire terminal log from start to finish of the wine install process that i gave in the OP

---

### Post by howefield on 2017-03-21
armhf ?

I'd guess there is no winehq-devel package available for that architecture.

---

### Post by slyther11 on 2017-03-21
hmmm, im honestly just trying to run wow on this god awful chromebook. every guide says to install wine. iv tried everything possible it feels like. you know any other solutions as to how i could do this? im a bit new to the entire linux/ubuntu thing

do you know of any other way i could play world of warcraft on this chromebook?

---

### Post by howefield on 2017-03-21
Sorry, I neither play WOW nor own a Chromebook far less install Wine on one.

If someone has an answer I'm sure they'll post it, in the meantime feel free to bump your thread every day or so if no response.

---

### Post by slyther11 on 2017-03-21
Alright, thanks mate!

---

### Post by chellrose on 2017-03-22
I used to run 14.04 and IIRC, was able to install wine with no trouble.  (Not a Chromebook, though.)

Have you tried ```
sudo apt-get install wine
```?  I believe that installs an older version than what wine-hq-devel would install, but it may be sufficient for what you want to do.

---

### Post by howefield on 2017-03-22
> **chellrose said:**
> I used to run 14.04 and IIRC, was able to install wine with no trouble.  (Not a Chromebook, though.)

Nor on an armhf device, I'd guess ?

---

### Post by slyther11 on 2017-03-22
(trusty)kuilox@localhost:~$ sudo apt-get install wine
[sudo] password for kuilox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'wine' has no installation candidate
(trusty)kuilox@localhost:~$  

Thats what i got with sudo apt-get install wine

---

### Post by Perfect Storm on 2017-03-22
Try either
```
sudo apt-get install wine1.6
```

or

```
sudo apt-get install wine1.4
```

---

### Post by slyther11 on 2017-03-22
(trusty)kuilox@localhost:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wine1.4
E: Couldn't find any package by regex 'wine1.4'
(trusty)kuilox@localhost:~$ sudo apt-get install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wine1.6
E: Couldn't find any package by regex 'wine1.6'
(trusty)kuilox@localhost:~$ 


tried both, both failed. :\

---

### Post by slyther11 on 2017-03-22
i dont know if this is important or not but heres the exact model of chromebook im using. [https://www.amazon.ca/gp/product/B00VUV0MG0/ref=oh_aui_detailpage_o02_s00?ie=UTF8&psc=1](https://www.amazon.ca/gp/product/B00VUV0MG0/ref=oh_aui_detailpage_o02_s00?ie=UTF8&psc=1)

---

### Post by slyther11 on 2017-03-23
bump

---

### Post by Perfect Storm on 2017-03-23
Try this go to [https://launchpad.net/~wine/+archive/ubuntu/wine-builds/+packages](https://launchpad.net/~wine/+archive/ubuntu/wine-builds/+packages) and download and install the packages manually.

---

### Post by slyther11 on 2017-03-23
Mind giving instructions on how i do that? would appreciate it thanks. im new to all of this.

---

### Post by Perfect Storm on 2017-03-24
32-bit or 64-bit?

---

### Post by slyther11 on 2017-03-24
32bit ARM

---

### Post by Perfect Storm on 2017-03-24
I don't think it's available for ARM, though some have success compiling it from scratch with patches: [https://wiki.winehq.org/ARM](https://wiki.winehq.org/ARM)

---

### Post by slyther11 on 2017-03-25
lol, no way id be able to pull that off. im retarded when it comes to linux. thanks mate.

---

