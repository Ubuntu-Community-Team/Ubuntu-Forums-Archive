---
title: "Can't install WINE on Ubuntu Studio (18.04)"
date: 2019-11-07
forum: Wine
---

### Post by eric-hepperle on 2019-11-07
Linux novice here. After doing months of due diligence, I determined that installing Linux may be more beneficial to prevent Windows holding my computer hostage while it does updates. So I installed Ubuntu Studio after watching this video, as one of the main purposes besides avoiding forced updates holding me hostage is to install a stand-alone Adobe CS5 (legally purchased forever licencse) and do graphic design with those apps. Sure I know about and love Gimp, InkScape, and Scribus, but as a professional I am stuck with CS5.

I tried to install WINE following this tutorial but it failed. The errors and feedback I got from Terminal was almost identical to this post: [https://ubuntuforums.org/showthread.php?t=2408029](https://ubuntuforums.org/showthread.php?t=2408029), except replace "staging" with "stable".

I'm not sure where to go from here. I like the idea of all Ubuntu Studio has to offer, but I'm confused on why it isn't working the way the tutorial from *only a year ago* says it should. Fun fact: I've almost never been able to get any major Linux project to work the first time, especially Guest Additions in VirtualBox and installing something called "Composer" for sofware development workflow. I follow the instructions to the letter every time. But, there's always something that doesn't go right. How was your first experience like that?:(

I'm not sure it will help, and hopefully I'm not revealing any passwords or sensitive data, but here is a copy of the commands and feedback I typed into Terminal:

```
 complete [-abcdefgjksuv] [-pr] [-DE] >  select NAME [in WORDS ... ;] do COMM>
 compopt [-o|+o option] [-DE] [name ..>  set [-abefhkmnptuvxBCHP] [-o option->
 continue [n]                            shift [n]
 coproc [NAME] command [redirections]    shopt [-pqsu] [-o] [optname ...]
 declare [-aAfFgilnrtux] [-p] [name[=v>  source filename [arguments]
 dirs [-clpv] [+N] [-N]                  suspend [-f]
 disown [-h] [-ar] [jobspec ... | pid >  test [expr]
 echo [-neE] [arg ...]                   time [-p] pipeline
 enable [-a] [-dnps] [-f filename] [na>  times
 eval [arg ...]                          trap [-lp] [[arg] signal_spec ...]
 exec [-cl] [-a name] [command [argume>  true
 exit [n]                                type [-afptP] name [name ...]
 export [-fn] [name[=value] ...] or ex>  typeset [-aAfFgilnrtux] [-p] name[=v>
 false                                   ulimit [-SHabcdefiklmnpqrstuvxPT] [l>
 fc [-e ename] [-lnr] [first] [last] o>  umask [-p] [-S] [mode]
 fg [job_spec]                           unalias [-a] name [name ...]
 for NAME [in WORDS ... ] ; do COMMAND>  unset [-f] [-v] [-n] [name ...]
 for (( exp1; exp2; exp3 )); do COMMAN>  until COMMANDS; do COMMANDS; done
 function name { COMMANDS ; } or name >  variables - Names and meanings of so>
 getopts optstring name [arg]            wait [-n] [id ...]
 hash [-lr] [-p pathname] [-dt] [name >  while COMMANDS; do COMMANDS; done
 help [-dms] [pattern ...]               { COMMANDS ; }
eric@eric-Inspiron-3531:~$ clear

eric@eric-Inspiron-3531:~$ uname -a
Linux eric-Inspiron-3531 4.15.0-66-lowlatency #75-Ubuntu SMP PREEMPT Tue Oct 1 06:11:04 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
eric@eric-Inspiron-3531:~$ cat /proc/version
Linux version 4.15.0-66-lowlatency (buildd@lgw01-amd64-044) (gcc version 7.4.0 (Ubuntu 7.4.0-1ubuntu1~18.04.1)) #75-Ubuntu SMP PREEMPT Tue Oct 1 06:11:04 UTC 2019
eric@eric-Inspiron-3531:~$ wget -O- -q https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/Release.key | sudo apt-key add -    
[sudo] password for eric: 
Sorry, try again.
[sudo] password for eric: 
OK
eric@eric-Inspiron-3531:~$ wget -O- -q https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/Release.key | sudo apt-key add -
OK
eric@eric-Inspiron-3531:~$ echo "deb http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04 ./" | sudo tee /etc/apt/sources.list.d/wine-obs.list
deb http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04 ./
eric@eric-Inspiron-3531:~$ sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Get:3 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Get:4 http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04 ./ InRelease [1,562 B]
Hit:5 https://dl.winehq.org/wine-builds/ubuntu disco InRelease                 
Hit:6 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease                
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Get:8 http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04 ./ Packages [61.3 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [768 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [601 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [295 kB]
Get:12 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [38.5 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [73.8 kB]
Get:14 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [41.5 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [143 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted i386 Packages [9,304 B]
Get:17 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [18.7 kB]
Get:18 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [42.0 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,022 kB]
Get:20 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [16.4 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [990 kB]
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [116 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [264 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [199 kB]
Get:25 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:26 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [447 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:28 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,972 B]
Fetched 5,413 kB in 5s (1,025 kB/s)                           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
17 packages can be upgraded. Run 'apt list --upgradable' to see them.
eric@eric-Inspiron-3531:~$ apt list --upgradable
Listing... Done
bind9-host/bionic-updates 1:9.11.3+dfsg-1ubuntu1.10 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.9]
dnsutils/bionic-updates 1:9.11.3+dfsg-1ubuntu1.10 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.9]
gdb/bionic-updates 8.1-0ubuntu3.2 amd64 [upgradable from: 8.1-0ubuntu3.1]
gdbserver/bionic-updates 8.1-0ubuntu3.2 amd64 [upgradable from: 8.1-0ubuntu3.1]
libbind9-160/bionic-updates 1:9.11.3+dfsg-1ubuntu1.10 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.9]
libdns-export1100/bionic-updates 1:9.11.3+dfsg-1ubuntu1.10 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.9]
libdns1100/bionic-updates 1:9.11.3+dfsg-1ubuntu1.10 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.9]
libirs160/bionic-updates 1:9.11.3+dfsg-1ubuntu1.10 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.9]
libisc-export169/bionic-updates 1:9.11.3+dfsg-1ubuntu1.10 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.9]
libisc169/bionic-updates 1:9.11.3+dfsg-1ubuntu1.10 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.9]
libisccc160/bionic-updates 1:9.11.3+dfsg-1ubuntu1.10 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.9]
libisccfg160/bionic-updates 1:9.11.3+dfsg-1ubuntu1.10 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.9]
liblwres160/bionic-updates 1:9.11.3+dfsg-1ubuntu1.10 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.9]
libnma0/bionic-updates 1.8.10-2ubuntu3 amd64 [upgradable from: 1.8.10-2ubuntu2]
network-manager-gnome/bionic-updates 1.8.10-2ubuntu3 amd64 [upgradable from: 1.8.10-2ubuntu2]
python3-gdbm/bionic-updates 3.6.9-1~18.04 amd64 [upgradable from: 3.6.8-1~18.04]
python3-tk/bionic-updates 3.6.9-1~18.04 amd64 [upgradable from: 3.6.8-1~18.04]
eric@eric-Inspiron-3531:~$ sudo apt --upgrade
apt 1.6.12 (amd64)
Usage: apt [options] command

apt is a commandline package manager and provides commands for
searching and managing as well as querying information about packages.
It provides the same functionality as the specialized APT tools,
like apt-get and apt-cache, but enables options more suitable for
interactive use by default.

Most used commands:
  list - list packages based on package names
  search - search in package descriptions
  show - show package details
  install - install packages
  remove - remove packages
  autoremove - Remove automatically all unused packages
  update - update list of available packages
  upgrade - upgrade the system by installing/upgrading packages
  full-upgrade - upgrade the system by removing/installing/upgrading packages
  edit-sources - edit the source information file

See apt(8) for more information about the available commands.
Configuration options and syntax is detailed in apt.conf(5).
Information about how to configure sources can be found in sources.list(5).
Package and version choices can be expressed via apt_preferences(5).
Security details are available in apt-secure(8).
                                        This APT has Super Cow Powers.
eric@eric-Inspiron-3531:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bind9-host dnsutils gdb gdbserver libbind9-160 libdns-export1100 libdns1100
  libirs160 libisc-export169 libisc169 libisccc160 libisccfg160 liblwres160
  libnma0 network-manager-gnome python3-gdbm python3-tk
17 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,219 kB of archives.
After this operation, 460 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libisc-export169 amd64 1:9.11.3+dfsg-1ubuntu1.10 [163 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libdns-export1100 amd64 1:9.11.3+dfsg-1ubuntu1.10 [749 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libirs160 amd64 1:9.11.3+dfsg-1ubuntu1.10 [19.1 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 bind9-host amd64 1:9.11.3+dfsg-1ubuntu1.10 [53.6 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 dnsutils amd64 1:9.11.3+dfsg-1ubuntu1.10 [145 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libbind9-160 amd64 1:9.11.3+dfsg-1ubuntu1.10 [27.6 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libisccfg160 amd64 1:9.11.3+dfsg-1ubuntu1.10 [48.5 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libisccc160 amd64 1:9.11.3+dfsg-1ubuntu1.10 [17.9 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libdns1100 amd64 1:9.11.3+dfsg-1ubuntu1.10 [968 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libisc169 amd64 1:9.11.3+dfsg-1ubuntu1.10 [237 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 liblwres160 amd64 1:9.11.3+dfsg-1ubuntu1.10 [34.5 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 python3-gdbm amd64 3.6.9-1~18.04 [17.8 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 gdb amd64 8.1-0ubuntu3.2 [2,938 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 gdbserver amd64 8.1-0ubuntu3.2 [282 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 network-manager-gnome amd64 1.8.10-2ubuntu3 [318 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libnma0 amd64 1.8.10-2ubuntu3 [80.4 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 python3-tk amd64 3.6.9-1~18.04 [119 kB]
Fetched 6,219 kB in 5s (1,217 kB/s)  
(Reading database ... 299681 files and directories currently installed.)
Preparing to unpack .../00-libisc-export169_1%3a9.11.3+dfsg-1ubuntu1.10_amd64.deb ...
Unpacking libisc-export169:amd64 (1:9.11.3+dfsg-1ubuntu1.10) over (1:9.11.3+dfsg-1ubuntu1.9) ...
Preparing to unpack .../01-libdns-export1100_1%3a9.11.3+dfsg-1ubuntu1.10_amd64.deb ...
Unpacking libdns-export1100 (1:9.11.3+dfsg-1ubuntu1.10) over (1:9.11.3+dfsg-1ubuntu1.9) ...
Preparing to unpack .../02-libirs160_1%3a9.11.3+dfsg-1ubuntu1.10_amd64.deb ...
Unpacking libirs160:amd64 (1:9.11.3+dfsg-1ubuntu1.10) over (1:9.11.3+dfsg-1ubuntu1.9) ...
Preparing to unpack .../03-bind9-host_1%3a9.11.3+dfsg-1ubuntu1.10_amd64.deb ...
Unpacking bind9-host (1:9.11.3+dfsg-1ubuntu1.10) over (1:9.11.3+dfsg-1ubuntu1.9) ...
Preparing to unpack .../04-dnsutils_1%3a9.11.3+dfsg-1ubuntu1.10_amd64.deb ...
Unpacking dnsutils (1:9.11.3+dfsg-1ubuntu1.10) over (1:9.11.3+dfsg-1ubuntu1.9) ...
Preparing to unpack .../05-libbind9-160_1%3a9.11.3+dfsg-1ubuntu1.10_amd64.deb ...
Unpacking libbind9-160:amd64 (1:9.11.3+dfsg-1ubuntu1.10) over (1:9.11.3+dfsg-1ubuntu1.9) ...
Preparing to unpack .../06-libisccfg160_1%3a9.11.3+dfsg-1ubuntu1.10_amd64.deb ...
Unpacking libisccfg160:amd64 (1:9.11.3+dfsg-1ubuntu1.10) over (1:9.11.3+dfsg-1ubuntu1.9) ...
Preparing to unpack .../07-libisccc160_1%3a9.11.3+dfsg-1ubuntu1.10_amd64.deb ...
Unpacking libisccc160:amd64 (1:9.11.3+dfsg-1ubuntu1.10) over (1:9.11.3+dfsg-1ubuntu1.9) ...
Preparing to unpack .../08-libdns1100_1%3a9.11.3+dfsg-1ubuntu1.10_amd64.deb ...
Unpacking libdns1100:amd64 (1:9.11.3+dfsg-1ubuntu1.10) over (1:9.11.3+dfsg-1ubuntu1.9) ...
Preparing to unpack .../09-libisc169_1%3a9.11.3+dfsg-1ubuntu1.10_amd64.deb ...
Unpacking libisc169:amd64 (1:9.11.3+dfsg-1ubuntu1.10) over (1:9.11.3+dfsg-1ubuntu1.9) ...
Preparing to unpack .../10-liblwres160_1%3a9.11.3+dfsg-1ubuntu1.10_amd64.deb ...
Unpacking liblwres160:amd64 (1:9.11.3+dfsg-1ubuntu1.10) over (1:9.11.3+dfsg-1ubuntu1.9) ...
Preparing to unpack .../11-python3-gdbm_3.6.9-1~18.04_amd64.deb ...
Unpacking python3-gdbm:amd64 (3.6.9-1~18.04) over (3.6.8-1~18.04) ...
Preparing to unpack .../12-gdb_8.1-0ubuntu3.2_amd64.deb ...
Unpacking gdb (8.1-0ubuntu3.2) over (8.1-0ubuntu3.1) ...
Preparing to unpack .../13-gdbserver_8.1-0ubuntu3.2_amd64.deb ...
Unpacking gdbserver (8.1-0ubuntu3.2) over (8.1-0ubuntu3.1) ...
Preparing to unpack .../14-network-manager-gnome_1.8.10-2ubuntu3_amd64.deb ...
Unpacking network-manager-gnome (1.8.10-2ubuntu3) over (1.8.10-2ubuntu2) ...
Preparing to unpack .../15-libnma0_1.8.10-2ubuntu3_amd64.deb ...
Unpacking libnma0:amd64 (1.8.10-2ubuntu3) over (1.8.10-2ubuntu2) ...
Preparing to unpack .../16-python3-tk_3.6.9-1~18.04_amd64.deb ...
Unpacking python3-tk:amd64 (3.6.9-1~18.04) over (3.6.8-1~18.04) ...
Setting up libisc169:amd64 (1:9.11.3+dfsg-1ubuntu1.10) ...
Setting up libisccc160:amd64 (1:9.11.3+dfsg-1ubuntu1.10) ...
Setting up libisc-export169:amd64 (1:9.11.3+dfsg-1ubuntu1.10) ...
Setting up libdns-export1100 (1:9.11.3+dfsg-1ubuntu1.10) ...
Setting up python3-gdbm:amd64 (3.6.9-1~18.04) ...
Setting up gdbserver (8.1-0ubuntu3.2) ...
Setting up libnma0:amd64 (1.8.10-2ubuntu3) ...
Setting up python3-tk:amd64 (3.6.9-1~18.04) ...
Setting up libdns1100:amd64 (1:9.11.3+dfsg-1ubuntu1.10) ...
Setting up gdb (8.1-0ubuntu3.2) ...
Setting up liblwres160:amd64 (1:9.11.3+dfsg-1ubuntu1.10) ...
Setting up network-manager-gnome (1.8.10-2ubuntu3) ...
Setting up libisccfg160:amd64 (1:9.11.3+dfsg-1ubuntu1.10) ...
Setting up libirs160:amd64 (1:9.11.3+dfsg-1ubuntu1.10) ...
Setting up libbind9-160:amd64 (1:9.11.3+dfsg-1ubuntu1.10) ...
Setting up bind9-host (1:9.11.3+dfsg-1ubuntu1.10) ...
Setting up dnsutils (1:9.11.3+dfsg-1ubuntu1.10) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for libglib2.0-0:amd64 (2.56.4-0ubuntu0.18.04.4) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
eric@eric-Inspiron-3531:~$ apt list --upgradable
Listing... Done
eric@eric-Inspiron-3531:~$ sudo apt install --install-recommends winehq-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-stable : Depends: wine-stable (= 4.0.2~disco)
E: Unable to correct problems, you have held broken packages.
eric@eric-Inspiron-3531:~$ sudo apt install --install-recommends winehq-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-stable : Depends: wine-stable (= 4.0.2~disco)
E: Unable to correct problems, you have held broken packages.
eric@eric-Inspiron-3531:~$ sudo apt install --install-recommends wine-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-stable : Depends: wine-stable-amd64 (= 4.0.2~disco) but it is not going to be installed
               Depends: wine-stable-i386 (= 4.0.2~disco)
E: Unable to correct problems, you have held broken packages.
eric@eric-Inspiron-3531:~$ sudo apt install --install-recommends wine-stable-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-stable-i386:i386 : Depends: libc6:i386 (>= 2.29) but 2.27-3ubuntu1 is to be installed
                         Depends: libvkd3d1:i386 (>= 1.0) but it is not installable
                         Recommends: libcapi20-3:i386 but it is not going to be installed
                         Recommends: libcups2:i386 but it is not going to be installed
                         Recommends: libglu1-mesa:i386 but it is not going to be installed or
                                     libglu1:i386
                         Recommends: libgsm1:i386 but it is not going to be installed
                         Recommends: libgssapi-krb5-2:i386 but it is not going to be installed
                         Recommends: libkrb5-3:i386 but it is not going to be installed
                         Recommends: libodbc1:i386 but it is not going to be installed
                         Recommends: libosmesa6:i386 but it is not going to be installed
                         Recommends: libsane:i386 or
                                     libsane1:i386 but it is not going to be installed
                         Recommends: libsdl2-2.0-0:i386 but it is not going to be installed
                         Recommends: libv4l-0:i386 but it is not going to be installed
                         Recommends: libxcomposite1:i386 but it is not going to be installed
                         Recommends: libxcursor1:i386 but it is not going to be installed
                         Recommends: libxfixes3:i386 but it is not going to be installed
                         Recommends: libxi6:i386 but it is not going to be installed
                         Recommends: libxinerama1:i386 but it is not going to be installed
                         Recommends: libxrandr2:i386 but it is not going to be installed
                         Recommends: libxrender1:i386 but it is not going to be installed
                         Recommends: libxslt1.1:i386 but it is not going to be installed
                         Recommends: libxxf86vm1:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
eric@eric-Inspiron-3531:~$ wmctrl -m

Command 'wmctrl' not found, but can be installed with:

sudo apt install wmctrl

eric@eric-Inspiron-3531:~$ sudo apt-get install wmctrl
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  wmctrl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.0 kB of archives.
After this operation, 54.3 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 wmctrl amd64 1.07-7build1 [20.0 kB]
Fetched 20.0 kB in 0s (72.3 kB/s) 
Selecting previously unselected package wmctrl.
(Reading database ... 299700 files and directories currently installed.)
Preparing to unpack .../wmctrl_1.07-7build1_amd64.deb ...
Unpacking wmctrl (1.07-7build1) ...
Setting up wmctrl (1.07-7build1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
eric@eric-Inspiron-3531:~$ wmctrl -m
Name: Xfwm4
Class: xfwm4
PID: 1105
Window manager's "showing the desktop" mode: N/A
eric@eric-Inspiron-3531:~$ printf 'Desktop: %s\nSession: %s\n' "$XDG_CURRENT_DESKTOP" "$GDMSESSION"
Desktop: XFCE
Session: ubuntustudio
```

---

### Post by CatKiller on 2019-11-07
> **eric-hepperle said:**
> I tried to install WINE following this tutorial but it failed.

You haven't said *which* tutorial you were following, but your issue stems from adding repositories for the wrong distro, leading to ```
wine-stable : Depends: wine-stable-amd64 (= 4.0.2~disco)
```

You aren't using disco (19.04), you're using bionic (18.04). And you *definitely* aren't using OpenSUSE. 

The instructions are [here.](https://wiki.winehq.org/Ubuntu)

---

### Post by eric-hepperle on 2019-11-09
Thanks for your help @CatKiller. I followed the instructions at the link you provided. Here is the feedback I received:

> 
eric@eric-Inspiron-3531:~$ sudo dpkg --add-architecture i386
[sudo] password for eric: 
eric@eric-Inspiron-3531:~$ sudo dpkg --add-architecture i386
eric@eric-Inspiron-3531:~$ wget -nc [https://dl.winehq.org/wine-builds/winehq.keyFile](https://dl.winehq.org/wine-builds/winehq.keyFile) &#8216;winehq.key&#8217; already there; not retrieving.

eric@eric-Inspiron-3531:~$ sudo apt-key add winehq.key
OK
eric@eric-Inspiron-3531:~$ sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main' 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) disco InRelease                 
Hit:4 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease                
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease              
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Hit:7 [http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04](http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04) ./ InRelease
Reading package lists... Done                      
eric@eric-Inspiron-3531:~$ sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04](http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04) ./ InRelease
Hit:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) disco InRelease                 
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease              
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:6 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease         
Hit:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Reading package lists... Done                                                  
Building dependency tree       
Reading state information... Done
All packages are up to date.
eric@eric-Inspiron-3531:~$ sudo apt install --install-recommends winehq-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-stable : Depends: wine-stable (= 4.0.2~disco)
E: Unable to correct problems, you have held broken packages.
eric@eric-Inspiron-3531:~$


As you can see, I am following the instructions for "***Ubuntu 18.04/Linux Mint 19.x***" (Bionic Beaver), yet the install fails saying I have dependencies  that depends on elements of "Disco". Not sure if I'm understanding that correctly.

Not knowing how to solve this issue, I pressed on with the rest of the commands:

> eric@eric-Inspiron-3531:~$ sudo apt install --install-recommends winehq-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-stable : Depends: wine-stable (= 4.0.2~disco)
E: Unable to correct problems, you have held broken packages.
eric@eric-Inspiron-3531:~$ sudo apt install --install-recommends winhq-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package winhq-stable
eric@eric-Inspiron-3531:~$ sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease              
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Hit:5 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) disco InRelease                 
Hit:6 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease                
Hit:7 [http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04](http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04) ./ InRelease
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up to date.
eric@eric-Inspiron-3531:~$ sudo apt install --install-recommends winhq-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package winhq-stable



How do I get WINE installed? What am I doing wrong? Thanks.

---

### Post by CatKiller on 2019-11-09
The issue is that as well as having the correct repository now, you still have the incorrect repository from whatever it was that you were doing before.

From your earlier output, you created an erroneous repository entry at /etc/apt/sources.list.d/wine-obs.list. You can remove that with ```
sudo rm /etc/apt/sources.list.d/wine-obs.list
``` Then ```
sudo apt update
``` should refresh the list of available packages and their versions. You need to run apt update whenever you've changed the repositories, or whenever your list of available packages might be out of date.

---

