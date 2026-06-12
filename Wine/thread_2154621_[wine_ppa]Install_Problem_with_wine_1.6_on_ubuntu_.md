---
title: "[wine ppa]Install Problem with wine 1.6 on ubuntu 12.04 64 bit"
date: 2013-06-15
forum: Wine
---

### Post by www2 on 2013-06-15
Hi i have a when i update wine 1.6 on my system i get this error:
```

    De volgende NIEUWE pakketten zullen geïnstalleerd worden:
      wine1.6 wine1.6-amd64 wine1.6-i386:i386
    0 pakketten opgewaardeerd, 3 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
    Er moeten 0 B/50,2 MB aan archieven opgehaald worden.
    Door deze operatie zal er 246 MB extra schijfruimte gebruikt worden.
    Wilt u doorgaan [J/n]?
    Selecting previously unselected package wine1.6-amd64.
    (Database inlezen ... 469301 files and directories currently installed.)
    Uitpakken van wine1.6-amd64 (uit .../wine1.6-amd64_1.6~rc2-0ubuntu1~ppa1_amd64.deb) ...
    Selecting previously unselected package wine1.6-i386:i386.
    Uitpakken van wine1.6-i386:i386 (uit .../wine1.6-i386_1.6~rc2-0ubuntu1~ppa1_i386.deb) ...
    Uitpakken van wine1.6 (uit .../wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb) ...
    dpkg: fout bij afhandelen van /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb (--unpack):
     trying to overwrite '/usr/bin/wine64-preloader', which is also in package wine1.6-amd64 1.6~rc2-0ubuntu1~ppa1
    dpkg-deb: error: subprocess paste was killed by signal (Gebroken pijp)
    Fouten gevonden tijdens behandelen van:
     /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb
    E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by watgrad on 2013-06-15
Wine was also broken for me with the last update.  My errors:
```
trying to overwrite '/usr/bin/wine64-preloader', which is also in package wine1.6-amd64 1.6~rc2-0ubuntu1~ppa1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I expect that this will be resolved shortly as it seems to be a problem with the packages...


> **www2 said:**
> Hi i have a when i update wine 1.6 on my system i get this error:


---

### Post by dresnu on 2013-06-15
I confirm the issue

---

### Post by nu2linux6 on 2013-06-15
Yes, same thing happens here as well. Is Scott Richie aware of this?

---

### Post by Xelort on 2013-06-15
wine: Depends: wine1.6 but it is not installed
wine1.6-amd64: PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.16.1.2ubuntu7.1 is installed
               Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.4 is installed
               Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
               Depends: libglib2.0-0 (>= 2.12.0) but 2.32.4-0ubuntu1 is installed
               Depends: libgphoto2-2 (>= 2.4.10.1) but 2.4.13-1ubuntu1.2 is installed
               Depends: libgphoto2-port0 (>= 2.4.10.1) but 2.4.13-1ubuntu1.2 is installed
               Depends: liblcms1 (>= 1.15-1) but 1.19.dfsg-1ubuntu3 is installed
               Depends: libldap-2.4-2 (>= 2.4.7) but 2.4.28-1.1ubuntu4.2 is installed
               Depends: libmpg123-0 (>= 1.6.2) but 1.12.1-3.2ubuntu1 is installed
               Depends: libopenal1 (>= 1:1.13) but 1:1.13-4ubuntu3 is installed
               Depends: libpulse0 (>= 1:0.99.1) but 1:1.1-0ubuntu15.3 is installed
               Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-5.1ubuntu4.4 is installed
               Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
               Depends: wine1.6:any (= 1.6~rc2-0ubuntu1~ppa1) but it is a virtual package
wine1.6-i386:i386: PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.16.1.2ubuntu7.1 is installed
                   Depends: libc6 (>= 2.11) but 2.15-0ubuntu10.4 is installed
                   Depends: libglib2.0-0 (>= 2.12.0) but 2.32.4-0ubuntu1 is installed
                   Depends: libgphoto2-2 (>= 2.4.10.1) but 2.4.13-1ubuntu1.2 is installed
                   Depends: libgphoto2-port0 (>= 2.4.10.1) but 2.4.13-1ubuntu1.2 is installed
                   Depends: liblcms1 (>= 1.15-1) but 1.19.dfsg-1ubuntu3 is installed
                   Depends: libldap-2.4-2 (>= 2.4.7) but 2.4.28-1.1ubuntu4.2 is installed
                   Depends: libmpg123-0 (>= 1.6.2) but 1.12.1-3.2ubuntu1 is installed
                   Depends: libopenal1 (>= 1:1.13) but 1:1.13-4ubuntu3 is installed
                   Depends: libpulse0 (>= 1:0.99.1) but 1:1.1-0ubuntu15.3 is installed
                   Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-5.1ubuntu4.4 is installed
                   Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
                   Depends: wine1.6:any (= 1.6~rc2-0ubuntu1~ppa1) but it is a virtual package


I guess the problem is the libglib2 dependency.

---

### Post by dino99 on 2013-06-15
****Is Scott Richie aware of this?*****

if you have pm him, then yes, otherwise no :(

[email]scottritchie@ubuntu.com[/email]

---

### Post by Xelort on 2013-06-15
What is the right channel to contact PPA mantainers? I was about to send them a message, but then i saw this section in ubuntu forums cited from the PPA itself. Is it ok to just mention our problems here, or we should contact the PPA mantainters directly?

---

### Post by Xelort on 2013-06-15
> **dino99 said:**
> ****Is Scott Richie aware of this?*****

if you have pm him, then yes, otherwise no :(

[EMAIL="scottritchie@ubuntu.com"]scottritchie@ubuntu.com[/EMAIL]


Well... i contacted the PPA people using the form here: [https://launchpad.net/~ubuntu-wine/+contactuser](https://launchpad.net/~ubuntu-wine/+contactuser)

Hope it's nothing serious.

---

### Post by Altusanew on 2013-06-15
I can confirm as well. Does anyone know of a bug report that can be followed/ help out on for this issue?

```
:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ttf-umefont libgraphicsmagick3 libegl1-mesa-drivers libutouch-evemu1 libutouch-geis1 libutouch-frame1 libopenvg1-mesa wine-mono0.0.4 libgbm1 wine-gecko1.7
  wine-gecko1.7:i386 wine-gecko1.8 wine-gecko1.8:i386 wine-gecko1.9 wine-gecko1.9:i386 libegl1-mesa libutouch-grail1 libwayland0 ttf-unfonts-core libxcb-xfixes0
  graphicsmagick
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine1.6 wine1.6-amd64 wine1.6-i386:i386
Suggested packages:
  dosbox:any
The following NEW packages will be installed:
  wine1.6
The following packages will be upgraded:
  wine1.6-amd64 wine1.6-i386:i386
2 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
6 not fully installed or removed.
Need to get 0 B/50.2 MB of archives.
After this operation, 6,411 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 769362 files and directories currently installed.)
Unpacking wine1.6 (from .../wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/wine64-preloader', which is also in package wine1.6-amd64 1.6~rc1-0ubuntu1~ppa2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by vivienneanthony on 2013-06-16
I'm having the same problem. Is there anyway to fix apt-get until wine1.6 is fixed?


The following extra packages will be installed:
  wine1.6
Suggested packages:
  dosbox:any
The following NEW packages will be installed:
  wine1.6
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1,206 kB of archives.
After this operation, 6,235 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 756699 files and directories currently installed.)
Unpacking wine1.6 (from .../wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/wine64-preloader', which is also in package wine1.6-amd64 1.6~rc2-0ubuntu1~ppa1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by boliston on 2013-06-16
I have had to untick the wine ppa from the software sources tab, which causes wine 1.4 to show in the list of available wine software.

I then installed wine 1.4 which seems to work, but hopefully wine 1.6 will get fixed eventually so I can re tick the wine ppa

---

### Post by stemberk on 2013-06-16
this command solved this problem:

sudo apt-get  -o Dpkg::Options::="--force-overwrite" -f install

---

### Post by twisteddeeds on 2013-06-16
I'm running 12.04 i386 I also have problems installing wine 1.6 ended up having to remove wine completely as the package was broken

I had 1.5 installed then when I updated software, (if i remember correctly it was a kernel update) it then tried to update wine to 1.6

---

### Post by KeesM on 2013-06-16
There is a discussion on this on launchpad ([https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1191276]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1191276")); with a method to clean up the problem, for installing without having to force installation. But I guess I just wait till the problem is solved by the maintainers.

---

### Post by digi007 on 2013-06-16
> **stemberk said:**
> this command solved this problem:

sudo apt-get  -o Dpkg::Options::="--force-overwrite" -f install

I can confirm that this solution works flawlessly. Wine 1.6 is installed and working fine along with windows applications. 

Thank you so much for simplest solution. Hope they resolve this issue soon. 

Cheers,

digi007

---

### Post by jao_madn on 2013-06-17
> **stemberk said:**
> this command solved this problem:

sudo apt-get  -o Dpkg::Options::="--force-overwrite" -f install

I confirm this command works fine for me..It continue the installation.

---

### Post by John Nimrod on 2013-06-17
> **Altusanew said:**
> I can confirm as well. Does anyone know of a bug report that can be followed/ help out on for this issue?

```
:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ttf-umefont libgraphicsmagick3 libegl1-mesa-drivers libutouch-evemu1 libutouch-geis1 libutouch-frame1 libopenvg1-mesa wine-mono0.0.4 libgbm1 wine-gecko1.7
  wine-gecko1.7:i386 wine-gecko1.8 wine-gecko1.8:i386 wine-gecko1.9 wine-gecko1.9:i386 libegl1-mesa libutouch-grail1 libwayland0 ttf-unfonts-core libxcb-xfixes0
  graphicsmagick
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine1.6 wine1.6-amd64 wine1.6-i386:i386
Suggested packages:
  dosbox:any
The following NEW packages will be installed:
  wine1.6
The following packages will be upgraded:
  wine1.6-amd64 wine1.6-i386:i386
2 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
6 not fully installed or removed.
Need to get 0 B/50.2 MB of archives.
After this operation, 6,411 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 769362 files and directories currently installed.)
Unpacking wine1.6 (from .../wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/wine64-preloader', which is also in package wine1.6-amd64 1.6~rc1-0ubuntu1~ppa2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Confirming I have the identical issue to the above (with same terminal screen text as the one quoted by the above user). I am a very basic user so would appreciate some safe idiot proof advice such as "wait for Wine update to be resolved" or .. this works type " ...... " in terminal.

---

### Post by YokoZar on 2013-06-17
Fixed.  Sorry, I tested it in one way but not the most relevant way, so the breakage slipped through.  It was limited to 64-bit precise installs, at least.

---

### Post by YokoZar on 2013-06-17
To fix, you will need to run sudo apt-get -f install in a terminal, the interface buttons don't seem to help :/

---

### Post by monkeybrain2012 on 2013-06-17
> **YokoZar said:**
> Fixed.  Sorry, I tested it in one way but not the most relevant way, so the breakage slipped through.  It was limited to 64-bit precise installs, at least.

Hi,

actually I have problem with Precise 32 bit install as well

here is the error

```
E: /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_i386.deb: trying to overwrite '/usr/bin/wine', which is also in package wine1.6-i386 1.6~rc2-0ubuntu1~ppa1

```

Thanks.

---

### Post by jao_madn on 2013-06-18
> **John Nimrod said:**
> Confirming I have the identical issue to the above (with same terminal screen text as the one quoted by the above user). I am a very basic user so would appreciate some safe idiot proof advice such as "wait for Wine update to be resolved" or .. this works type " ...... " in terminal.

We have identical error messages and issue on my 64bit precise..Actually the safest and best recommended way is to wait for the developer incharge to fix the problem or wait for an official advise. But if your in a hurray just like me cause it affects all my icons in the system tray and i believe if im correct because the "xserver-xorg-video* update" and some few small updates didn't succed in installation on dpkg for the reason that it stops in the WINE part. In additon also my wifi network manager stops working im lucky i had a ethernet cable and connection at my disposal and also maybe im lucky the kernel update installation from 3.2.0-45-generic - 3.2.0-48-generic which stop also for the WINE reason thins doesn't put my system in a un usable or rescue mode state..

So i go with the command "sudo apt-get  -o Dpkg::Options::="--force-overwrite" -f install" and it continue the installation of wine1.6 and all the accompanied updates including the kernel.

---

### Post by YokoZar on 2013-06-18
> **monkeybrain2012 said:**
> Hi,

actually I have problem with Precise 32 bit install as well

here is the error

```
E: /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_i386.deb: trying to overwrite '/usr/bin/wine', which is also in package wine1.6-i386 1.6~rc2-0ubuntu1~ppa1

```

Thanks.

Ahh I forgot that file is in both.  Regardless the same fix fixed it and the remedy is the same (sudo apt-get -f install)

---

### Post by YokoZar on 2013-06-18
> **jao_madn said:**
> We have identical error messages and issue on my 64bit precise..Actually the safest and best recommended way is to wait for the developer incharge to fix the problem or wait for an official advise.
That would be literally me, and I'm telling you I fixed it and uploaded the fix and that you can just run sudo apt-get -f install now to fix it (since there's now a fixed version of the package in the PPA).

---

### Post by ubu_dynamite on 2013-06-18
I removed wine then tried installing it again but wine-mono0.0.8 recommends wine1.5.

```
~ $ sudo aptitude install wine
The following NEW packages will be installed:
  fonts-horai-umefont{a} gnome-exe-thumbnailer{a} icoutils{a} libasn1-8-heimdal:i386{a} libasound2:i386{a} libasound2-plugins:i386{a} libasyncns0:i386{a} libavahi-client3:i386{a} 
  libavahi-common-data:i386{a} libavahi-common3:i386{a} libcapi20-3{a} libcapi20-3:i386{a} libcups2:i386{a} libexif12:i386{a} libexpat1:i386{a} libflac8:i386{a} libfontconfig1:i386{a} 
  libfreetype6:i386{a} libgcrypt11:i386{a} libgd2-xpm:i386{a} libgettextpo0{a} libgif4:i386{a} libgl1-mesa-dri:i386{a} libgl1-mesa-glx:i386{a} libglapi-mesa:i386{a} libglu1-mesa:i386{a} 
  libgnutls26:i386{a} libgpg-error0:i386{a} libgphoto2-2:i386{a} libgphoto2-port0:i386{a} libgssapi-krb5-2:i386{a} libgssapi3-heimdal:i386{a} libgstreamer-plugins-base0.10-0:i386{a} 
  libgstreamer0.10-0:i386{a} libhcrypto4-heimdal:i386{a} libheimbase1-heimdal:i386{a} libheimntlm0-heimdal:i386{a} libhx509-5-heimdal:i386{a} libice6:i386{a} libieee1284-3:i386{a} 
  libjack-jackd2-0:i386{a} libjpeg-turbo8:i386{a} libjpeg8:i386{a} libjson0:i386{a} libk5crypto3:i386{a} libkeyutils1:i386{a} libkrb5-26-heimdal:i386{a} libkrb5-3:i386{a} libkrb5support0:i386{a} 
  liblcms1:i386{a} libldap-2.4-2:i386{a} libllvm3.0:i386{a} libltdl7:i386{a} libmpg123-0{a} libmpg123-0:i386{a} libodbc1{a} libogg0:i386{a} libopenal1:i386{a} liborc-0.4-0:i386{a} libosmesa6{a} 
  libosmesa6:i386{a} libp11-kit0:i386{a} libpam-winbind{a} libpulse0:i386{a} libroken18-heimdal:i386{a} libsamplerate0:i386{a} libsane:i386{a} libsasl2-2:i386{a} libsasl2-modules:i386{a} libsm6:i386{a} 
  libsndfile1:i386{a} libspeexdsp1:i386{a} libsqlite3-0:i386{a} libstdc++6:i386{a} libtasn1-3:i386{a} libtiff4:i386{a} libunistring0{a} libusb-0.1-4:i386{a} libv4l-0:i386{a} libv4lconvert0:i386{a} 
  libvorbis0a:i386{a} libvorbisenc2:i386{a} libwind0-heimdal:i386{a} libwrap0:i386{a} libx11-6:i386{a} libx11-xcb1:i386{a} libxau6:i386{a} libxcb-glx0:i386{a} libxcb1:i386{a} libxcomposite1:i386{a} 
  libxcursor1:i386{a} libxdamage1:i386{a} libxdmcp6:i386{a} libxext6:i386{a} libxfixes3:i386{a} libxi6:i386{a} libxinerama1:i386{a} libxml2:i386{a} libxpm4:i386{a} libxrandr2:i386{a} libxrender1:i386{a} 
  libxslt1.1:i386{a} libxt6:i386{a} libxxf86vm1:i386{a} odbcinst{a} odbcinst1debian2{a} unixodbc{a} winbind{a} wine wine-gecko2.21{a} wine-gecko2.21:i386{a} wine-mono0.0.8{a} wine1.5{a} wine1.6{ab} 
  wine1.6-amd64{a} wine1.6-i386:i386{a} winetricks{a} 
0 packages upgraded, 117 newly installed, 0 to remove and 0 not upgraded.
Need to get 221 MB of archives. After unpacking 547 MB will be used.
The following packages have unmet dependencies:
 wine1.6 : Conflicts: wine1.5 but 1.6~rc2-0ubuntu1~ppa2 is to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     wine1.5 [Not Installed]                            

     Leave the following dependencies unresolved:         
2)     wine-mono0.0.8 recommends wine1.5   
```

---

### Post by nu2linux6 on 2013-06-18
The latest ppa3 update seems to have solved all the error message problems for me. Thanks!

---

### Post by Altusanew on 2013-06-18
Thank you for all your help YokoZar.

I am now getting this error message when trying to run the fix:

```
~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ttf-umefont libgraphicsmagick3 libegl1-mesa-drivers libutouch-evemu1 libutouch-geis1 libutouch-frame1 libopenvg1-mesa wine-mono0.0.4 libgbm1 wine-gecko1.7
  wine-gecko1.7:i386 wine-gecko1.8 wine-gecko1.8:i386 wine-gecko1.9 wine-gecko1.9:i386 libegl1-mesa libutouch-grail1 libwayland0 ttf-unfonts-core libxcb-xfixes0
  graphicsmagick
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine1.6-amd64 wine1.6-i386:i386
The following packages will be upgraded:
  wine1.6-amd64 wine1.6-i386:i386
2 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
6 not fully installed or removed.
Need to get 0 B/49.0 MB of archives.
After this operation, 176 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of wine1.6-i386:i386:
 wine1.6-i386:i386 depends on wine1.6:any (= 1.6~rc1-0ubuntu1~ppa2); however:
  Version of wine1.6 on system is 1.6~rc2-0ubuntu1~ppa3.
dpkg: error processing wine1.6-i386:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.6:
 wine1.6 depends on wine1.6-amd64 (= 1.6~rc2-0ubuntu1~ppa3); however:
  Version of wine1.6-amd64 on system is 1.6~rc1-0ubuntu1~ppa2.
 wine1.6 depends on wine1.6-i386 (= 1.6~rc2-0ubuntu1~ppa3); however:
  Package wine1.6-i386 is not installed.
  Version of wine1.6-i386:i386 on system is 1.6~rc1-0ubuntu1~ppa2.
dpkg: error processing wine1.6 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of wine1.6-amd64:
 wine1.6-amd64 depends on wine1.6:any (= 1.6~rc1-0ubuntu1~ppa2); however:
  Version of wine1.6 on system is 1.6~rc2-0ubuntu1~ppa3.
dpkg: error processing wine1.6-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.6; however:
  Package wine1.6 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.5-amd64:
 wine1.5-amd64 depends on wine1.6-amd64; however:
  Package wine1.6-amd64 is not configured yet.
dpkg: error processing wine1.5-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.5-i386:i386:
 wine1.5-i386:i386 depends on wine1.6-i386; however:
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                               No apport report written because MaxReports is reached already
                                                                                                               Package wine1.6-i386:i386 is not configured yet.
dpkg: error processing wine1.5-i386:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine1.6-i386:i386
 wine1.6
 wine1.6-amd64
 wine
 wine1.5-amd64
 wine1.5-i386:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by kukuku on 2013-06-20
I'm also in a somewhat similar situation...

```
~$ sudo apt-get install -f
<snip>
Get:1 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main wine1.6-amd64 amd64 1.6~rc2-0ubuntu1~ppa4 [24.7 MB]
Get:2 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main wine1.6 amd64 1.6~rc2-0ubuntu1~ppa4 [1,199 kB]
Get:3 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main wine1.6-i386 i386 1.6~rc2-0ubuntu1~ppa4 [24.4 MB]
Fetched 50.2 MB in 11s (4,249 kB/s)                                                        
(Reading database ... 632403 files and directories currently installed.)
Preparing to replace wine1.6-amd64 1.6~rc1-0ubuntu1~ppa2 (using .../wine1.6-amd64_1.6~rc2-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement wine1.6-amd64 ...
dpkg: error processing /var/cache/apt/archives/wine1.6-amd64_1.6~rc2-0ubuntu1~ppa4_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/wine64-preloader', which is also in package wine1.6 1.6~rc2-0ubuntu1~ppa1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/wine1.6-amd64_1.6~rc2-0ubuntu1~ppa4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Trying to run autoremove gives just *wine1.6 : Depends: wine1.6-amd64 (= 1.6~rc2-0ubuntu1~ppa1) but 1.6~rc1-0ubuntu1~ppa2 is installed*

---

### Post by ubu_dynamite on 2013-06-20
The latest ppa4 update has solved the dependency problems i had thanks.

---

### Post by dynabar on 2013-06-20
This is what I get

sudo apt-get install -f
[sudo] password for dynabar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  wine1.6 wine1.6-i386
The following packages will be upgraded:
  wine1.6 wine1.6-i386
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
4 not fully installed or removed.
Need to get 0 B/25.5 MB of archives.
After this operation, 12.3 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of wine1.6:
 wine1.6 depends on wine1.6-i386 (= 1.6~rc2-0ubuntu1~ppa2); however:
  Version of wine1.6-i386 on system is 1.6~rc2-0ubuntu1~ppa1.
dpkg: error processing wine1.6 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of wine1.6-i386:
 wine1.6-i386 depends on wine1.6:any (= 1.6~rc2-0ubuntu1~ppa1); however:
  Version of wine1.6 on system is 1.6~rc2-0ubuntu1~ppa2.
dpkg: error processing wine1.6-i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.6; however:
  Package wine1.6 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of wine1.5-i386:
 wine1.5-i386 depends on wine1.6-i386; however:
  Package wine1.6-i386 is not configured yet.
dpkg: error processing wine1.5-i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 wine1.6
 wine1.6-i386
 wine
 wine1.5-i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Altusanew on 2013-06-22
Yeah I am now getting this error message as well.

```
~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ttf-umefont libgraphicsmagick3 libegl1-mesa-drivers libutouch-evemu1 libutouch-geis1 libutouch-frame1 libopenvg1-mesa wine-mono0.0.4 libgbm1 wine-gecko1.7
  wine-gecko1.7:i386 wine-gecko1.8 wine-gecko1.8:i386 wine-gecko1.9 wine-gecko1.9:i386 libegl1-mesa libutouch-grail1 libwayland0 ttf-unfonts-core libxcb-xfixes0
  graphicsmagick
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine1.6 wine1.6-amd64 wine1.6-i386:i386
Suggested packages:
  dosbox:any
The following packages will be upgraded:
  wine1.6 wine1.6-amd64 wine1.6-i386:i386
3 upgraded, 0 newly installed, 0 to remove and 43 not upgraded.
6 not fully installed or removed.
Need to get 0 B/50.2 MB of archives.
After this operation, 176 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of wine1.6-amd64:
 wine1.6-amd64 depends on wine1.6:any (= 1.6~rc1-0ubuntu1~ppa2); however:
  Version of wine1.6 on system is 1.6~rc2-0ubuntu1~ppa3.
dpkg: error processing wine1.6-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.6:
 wine1.6 depends on wine1.6-amd64 (= 1.6~rc2-0ubuntu1~ppa3); however:
  Version of wine1.6-amd64 on system is 1.6~rc1-0ubuntu1~ppa2.
 wine1.6 depends on wine1.6-i386 (= 1.6~rc2-0ubuntu1~ppa3); however:
  Package wine1.6-i386 is not installed.
  Version of wine1.6-i386:i386 on system is 1.6~rc1-0ubuntu1~ppa2.
dpkg: error processing wine1.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.6-i386:i386:
 wine1.6-i386:i386 depends on wine1.6:any (= 1.6~rc1-0ubuntu1~ppa2); however:
  Version of wine1.6 on system is 1.6~rc2-0ubuntu1~ppa3.
dpkg: error processing wine1.6-i386:i386 (--configNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                            No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                 No apport report written because the error message indicates its a followup error from a previous failure.
                                      No apport report written because MaxReports is reached already
                                                                                                    ure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.6; however:
  Package wine1.6 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.5-amd64:
 wine1.5-amd64 depends on wine1.6-amd64; however:
  Package wine1.6-amd64 is not configured yet.
dpkg: error processing wine1.5-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.5-i386:i386:
 wine1.5-i386:i386 depends on wine1.6-i386; however:
  Package wine1.6-i386:i386 is not configured yet.
dpkg: error processing wine1.5-i386:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine1.6-amd64
 wine1.6
 wine1.6-i386:i386
 wine
 wine1.5-amd64
 wine1.5-i386:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Is there some step that I am missing? Should I be trying to get Wine uninstalled before running the upgrade?

---

### Post by John Nimrod on 2013-06-23
I removed the "clash" by removing wine completely through Synaptic package manager. I aim to leave it a few weeks and reinstall Wine - Any comments on the reinstall or should it be fine then? I admit I keep Wine purely to run one program so not missing it much yet.

---

### Post by kukuku on 2013-06-24
That may be the best option available, since it blocks all other updates as well. I see there's another newer version out too in the PPA, but it gives me the same error as the one a few posts back.

---

### Post by ubu_dynamite on 2013-06-24
Try removing all wine packages update your sources then install again adleast that worked for me.

---

### Post by dynabar on 2013-06-27
> **ubu_dynamite said:**
> Try removing all wine packages update your sources then install again adleast that worked for me.

I did the same thing using Synaptics to completely remove wine. This corrected the Update Manager. I then updated everything else and reinstalled wine. Everything seems to be working for me now.

---

### Post by Altusanew on 2013-07-04
Just a quick update. I had to remove every Wine related package from my system through Muon Package Manager and then reinstall Wine + other packages that I took off (Play on Linux, etc.). Seems that took care of the issue.

Thank you to all those who provided support on this.

---

