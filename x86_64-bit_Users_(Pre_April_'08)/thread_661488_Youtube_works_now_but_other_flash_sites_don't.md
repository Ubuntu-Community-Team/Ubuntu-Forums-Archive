---
title: "Youtube works now but other flash sites don't"
date: 2008-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ksujason on 2008-01-08
After running the script for Flash from Kilz, some sites like Youtube began to work. I have noticed that others like [www.cbs.com](www.cbs.com) do not work when trying to watch show episodes.

Do sites like this that play show episodes use a different type of plugin?

I have the 64 bit version of ubuntu loaded.

Thank you.

---

### Post by browndruid on 2008-01-08
That's rather strange. I'd say that it's probably a different plugin. You might just want to run the script from [here]("http://ubuntuforums.org/showthread.php?t=202537") to install 32-bit Firefox and all related plugins. Works great for me.

---

### Post by ksujason on 2008-01-08
So is it true that if I have the 64 bit ubuntu installed then I will have the 64 bit firefox? 

I guess that could cause some of the strange problems I have with flash sites. One site that has a flash intro will not work unless I go to that page first, then go onto another site and go back to the original page with the back button. I have never seen anything like this.

Does anyone think this could be helped with the 32 bit version?

Thanks.

---

### Post by Kilz on 2008-01-08
> **ksujason said:**
> So is it true that if I have the 64 bit ubuntu installed then I will have the 64 bit firefox? 

I guess that could cause some of the strange problems I have with flash sites. One site that has a flash intro will not work unless I go to that page first, then go onto another site and go back to the original page with the back button. I have never seen anything like this.

Does anyone think this could be helped with the 32 bit version?

Thanks.

No, the 32bit version uses the exact same plugin. If you want to see, why not just install the 32bit version of firefox like the above poster recommended.

---

### Post by Wiifreak on 2008-01-08
Check at Add/remove programs if the flash-plug-in-packet is installed.
If not, select, install, reboot.

---

### Post by ksujason on 2008-01-08
I went ahead and ran the script to install the 32bit firefox and add ons. I loaded Firefox, flash, and java. It seemed to run and complete without any errors, but flash does not work at all when I open the 32 bit browser. 

I left the 64bit firefox installed when I ran the script. Could this be causing problems having both installed?

Thank you.

---

### Post by ksujason on 2008-01-08
I ran the script again to install the 32bit firefox. I notice some errors this time when I ran it. I thought I would post the results as I saw them in the terminal window. Hopefully it will make sense to someone.

Thanks.
mkdir: cannot create directory `/tmp/ff32': File exists
--21:39:28--  [http://home.comcast.net/~ubuntume/ia32-lib-firefox-amd64.deb](http://home.comcast.net/~ubuntume/ia32-lib-firefox-amd64.deb)
           => `ia32-lib-firefox-amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

(Reading database ... 91531 files and directories currently installed.)
Preparing to replace ia32-lib-firefox 0.1 (using ia32-lib-firefox-amd64.deb) ...
Unpacking replacement ia32-lib-firefox ...
Setting up ia32-lib-firefox (0.1) ...

This script is used to setup your system for a 32bit browser.

Please select the version of the Ubuntu you are installing to.
Install options are :

1 : Dapper Drake 6.06 LTR
2 : Edgy Eft 6.10
3 : Feisty Fawn 7.04
4 : Gutsy Gibbon 7.10

Install option (1-4)? : 4
Gutsy Gibbon 7.10

This script is used to setup your system for a 32bit browser.
You can choose to install a browser now from the list.
You can also just install the base files and select
a browser later. This script only needs to be run once.
Afterward you may install as many browsers from the
howto page as you wish.

Please select the browser you would like to install.
Install options are :

1 : Swiftweasel for Intel processors
2 : Swiftweasel for AMD processors
3 : 32bit Firefox web browser
4 : 32bit Flock web browser
5 : 32bit Iceweasel web browser
6 : Base install, you will install another browser at a later time

If unsure,just hit enter.
Install option (1-6)? : 3
32bit Firefox 2.0.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
gsfonts is already the newest version.
alsa-oss is already the newest version.
lib32gcc1 is already the newest version.
lib32stdc++6 is already the newest version.
The following packages were automatically installed and are no longer required:
  libavutil1d libboost-date-time1.34.1 libdvbpsi4 libavcodec1d
  libboost-thread1.34.1 libmatroska0 libpostproc1d libgsm1 libdvdnav4
  libdc1394-13 libavformat1d libebml0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lib32asound2 is already the newest version.
lib32ncurses5 is already the newest version.
lib32z1 is already the newest version.
libc6-i386 is already the newest version.
The following packages were automatically installed and are no longer required:
  libavutil1d libboost-date-time1.34.1 libdvbpsi4 libavcodec1d
  libboost-thread1.34.1 libmatroska0 libpostproc1d libgsm1 libdvdnav4
  libdc1394-13 libavformat1d libebml0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--21:39:41--  [http://home.comcast.net/~ubuntume/firefox32-2.0.0.11-ubuntu_7.10_amd64.deb](http://home.comcast.net/~ubuntume/firefox32-2.0.0.11-ubuntu_7.10_amd64.deb)
           => `firefox32-2.0.0.11-ubuntu_7.10_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

(Reading database ... 91531 files and directories currently installed.)
Preparing to replace firefox32 2.0.0.11 (using .../firefox32-2.0.0.11-ubuntu_7.10_amd64.deb) ...
Unpacking replacement firefox32 ...
Setting up firefox32 (2.0.0.11) ...
--21:39:43--  [http://mirrors.kernel.org/ubuntu/pool/main/g/gtk-qt-engine/gtk-qt-engine_0.71~svn20070224-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gtk-qt-engine/gtk-qt-engine_0.71~svn20070224-0ubuntu3_i386.deb)
           => `gtk-qt-engine_0.71~svn20070224-0ubuntu3_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

cp: omitting directory `/tmp/ff32/install2/usr/lib/gtk-2.0/2.10.0'
mkdir: cannot create directory `/usr/lib32/kde3': File exists
--21:39:43--  [http://mirrors.kernel.org/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.20build1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.20build1_all.deb)
           => `gsfonts-x11_0.20build1_all.deb'
Resolving mirrors.kernel.org... 204.152.191.7, 204.152.191.39
Connecting to mirrors.kernel.org|204.152.191.7|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

(Reading database ... 91531 files and directories currently installed.)
Preparing to replace gsfonts-x11 0.20build1 (using .../gsfonts-x11_0.20build1_all.deb) ...
Unpacking replacement gsfonts-x11 ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
Setting up gsfonts-x11 (0.20build1) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

--21:39:44--  [http://home.comcast.net/~ubuntume/ia32-alsa-oss_1.0.10-1_amd64.deb](http://home.comcast.net/~ubuntume/ia32-alsa-oss_1.0.10-1_amd64.deb)
           => `ia32-alsa-oss_1.0.10-1_amd64.deb'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

(Reading database ... 91531 files and directories currently installed.)
Preparing to replace ia32-alsa-oss 1.0.10-1 (using ia32-alsa-oss_1.0.10-1_amd64.deb) ...
Unpacking replacement ia32-alsa-oss ...
Setting up ia32-alsa-oss (1.0.10-1) ...




Would you like to install the Flash plugin?
Install option (Yes=1 No=2)? : 1
--21:39:59--  [http://home.comcast.net/~ubuntume/flash.tar.gz](http://home.comcast.net/~ubuntume/flash.tar.gz)
           => `flash.tar.gz'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

libflashplayer.so
cp: cannot stat `/tmp/ff32/install_flash_player_9_linux/libflashplayer.so': No such file or directory




Would you like to install the Java 6 plugin?
Install option (Yes=1 No=2)? : 1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
The following packages were automatically installed and are no longer required:
  libavutil1d libboost-date-time1.34.1 libdvbpsi4 libavcodec1d
  libboost-thread1.34.1 libmatroska0 libpostproc1d libgsm1 libdvdnav4
  libdc1394-13 libavformat1d libebml0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-sun-java6-bin is already the newest version.
The following packages were automatically installed and are no longer required:
  libavutil1d libboost-date-time1.34.1 libdvbpsi4 libavcodec1d
  libboost-thread1.34.1 libmatroska0 libpostproc1d libgsm1 libdvdnav4
  libdc1394-13 libavformat1d libebml0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ln: creating symbolic link `/usr/lib32/firefox32/plugins/libjavaplugin_oji.so' to `/usr/lib/jvm/ia32-java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so': File exists

---

### Post by Kilz on 2008-01-09
It looks like comcast was down, can you click on the links in your post and see if firefox wants to download , or if it errors?

---

