---
title: "flash plugin will not install"
date: 2007-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-12-17
I can't get Flash to work. I tried it in Firefox. Notice what I highlighted in red. The md5sum is wrong. What is causing this, and how can it be fixed? Why is the md5sum always incorrect? Maybe the file is corrupted, but why is it corrupted every time I redownload it?

```
kris@ubuntu:/boot/grub$ sudo apt-get install flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kris@ubuntu:/boot/grub$ sudo apt-get --reinstall install flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/18.1kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 101793 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 (using .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--20:50:07--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.202.70
Connecting to fpdownload.macromedia.com|72.247.202.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  656.09 KB/s
   50K .......... .......... .......... .......... ..........  3%    1.14 MB/s
  100K .......... .......... .......... .......... ..........  5%    1.17 MB/s
  150K .......... .......... .......... .......... ..........  6%    1.09 MB/s
  200K .......... .......... .......... .......... ..........  8%    1.15 MB/s
  250K .......... .......... .......... .......... .......... 10%    1.12 MB/s
  300K .......... .......... .......... .......... .......... 11%    1.08 MB/s
  350K .......... .......... .......... .......... .......... 13%    1.09 MB/s
  400K .......... .......... .......... .......... .......... 15%    1.11 MB/s
  450K .......... .......... .......... .......... .......... 16%    1.09 MB/s
  500K .......... .......... .......... .......... .......... 18%    1.11 MB/s
  550K .......... .......... .......... .......... .......... 20%    1.14 MB/s
  600K .......... .......... .......... .......... .......... 21%    1.07 MB/s
  650K .......... .......... .......... .......... .......... 23%    1.08 MB/s
  700K .......... .......... .......... .......... .......... 25%    1.08 MB/s
  750K .......... .......... .......... .......... .......... 26%    1.10 MB/s
  800K .......... .......... .......... .......... .......... 28%    1.05 MB/s
  850K .......... .......... .......... .......... .......... 30%    1.08 MB/s
  900K .......... .......... .......... .......... .......... 32%    1.06 MB/s
  950K .......... .......... .......... .......... .......... 33%    1.11 MB/s
 1000K .......... .......... .......... .......... .......... 35%    1.07 MB/s
 1050K .......... .......... .......... .......... .......... 37%    1.18 MB/s
 1100K .......... .......... .......... .......... .......... 38%    1.11 MB/s
 1150K .......... .......... .......... .......... .......... 40%    1.08 MB/s
 1200K .......... .......... .......... .......... .......... 42%    1.19 MB/s
 1250K .......... .......... .......... .......... .......... 43%    1.08 MB/s
 1300K .......... .......... .......... .......... .......... 45%    1.10 MB/s
 1350K .......... .......... .......... .......... .......... 47%    1.09 MB/s
 1400K .......... .......... .......... .......... .......... 48%    1.05 MB/s
 1450K .......... .......... .......... .......... .......... 50%    1.12 MB/s
 1500K .......... .......... .......... .......... .......... 52%    1.11 MB/s
 1550K .......... .......... .......... .......... .......... 53%    1.08 MB/s
 1600K .......... .......... .......... .......... .......... 55%    1.10 MB/s
 1650K .......... .......... .......... .......... .......... 57%    1.05 MB/s
 1700K .......... .......... .......... .......... .......... 59%    1.15 MB/s
 1750K .......... .......... .......... .......... .......... 60%    1.19 MB/s
 1800K .......... .......... .......... .......... .......... 62%    1.14 MB/s
 1850K .......... .......... .......... .......... .......... 64%    1.15 MB/s
 1900K .......... .......... .......... .......... .......... 65%    1.06 MB/s
 1950K .......... .......... .......... .......... .......... 67%    1.15 MB/s
 2000K .......... .......... .......... .......... .......... 69%    1.13 MB/s
 2050K .......... .......... .......... .......... .......... 70%    1.19 MB/s
 2100K .......... .......... .......... .......... .......... 72%    1.12 MB/s
 2150K .......... .......... .......... .......... .......... 74%    1.11 MB/s
 2200K .......... .......... .......... .......... .......... 75%    1.10 MB/s
 2250K .......... .......... .......... .......... .......... 77%    1.11 MB/s
 2300K .......... .......... .......... .......... .......... 79%    1.12 MB/s
 2350K .......... .......... .......... .......... .......... 80%    1.15 MB/s
 2400K .......... .......... .......... .......... .......... 82%    1.10 MB/s
 2450K .......... .......... .......... .......... .......... 84%    1.16 MB/s
 2500K .......... .......... .......... .......... .......... 86%    1.12 MB/s
 2550K .......... .......... .......... .......... .......... 87%    1.13 MB/s
 2600K .......... .......... .......... .......... .......... 89%    1.07 MB/s
 2650K .......... .......... .......... .......... .......... 91%    1.06 MB/s
 2700K .......... .......... .......... .......... .......... 92%    1.13 MB/s
 2750K .......... .......... .......... .......... .......... 94%    1.11 MB/s
 2800K .......... .......... .......... .......... .......... 96%    1.12 MB/s
 2850K .......... .......... .......... .......... .......... 97%    1.14 MB/s
 2900K .......... .......... .......... .......... .......... 99%    1.11 MB/s
 2950K .......... ....                                       100%    1.06 MB/s

20:50:10 (1.10 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
[COLOR="Red"]md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.[/COLOR]

kris@ubuntu:/boot/grub$ sudo apt-get --reinstall install flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/18.1kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 101793 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 (using .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--20:50:23--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.202.70
Connecting to fpdownload.macromedia.com|72.247.202.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  627.37 KB/s
   50K .......... .......... .......... .......... ..........  3%    1.03 MB/s
  100K .......... .......... .......... .......... ..........  5%    1.09 MB/s
  150K .......... .......... .......... .......... ..........  6%    1.17 MB/s
  200K .......... .......... .......... .......... ..........  8%    1.05 MB/s
  250K .......... .......... .......... .......... .......... 10%    1.11 MB/s
  300K .......... .......... .......... .......... .......... 11%    1.15 MB/s
  350K .......... .......... .......... .......... .......... 13%    1.08 MB/s
  400K .......... .......... .......... .......... .......... 15%    1.19 MB/s
  450K .......... .......... .......... .......... .......... 16%    1.08 MB/s
  500K .......... .......... .......... .......... .......... 18%    1.17 MB/s
  550K .......... .......... .......... .......... .......... 20%    1.10 MB/s
  600K .......... .......... .......... .......... .......... 21%    1.16 MB/s
  650K .......... .......... .......... .......... .......... 23%    1.12 MB/s
  700K .......... .......... .......... .......... .......... 25%    1.05 MB/s
  750K .......... .......... .......... .......... .......... 26%    1.17 MB/s
  800K .......... .......... .......... .......... .......... 28%    1.12 MB/s
  850K .......... .......... .......... .......... .......... 30%    1.09 MB/s
  900K .......... .......... .......... .......... .......... 32%    1.16 MB/s
  950K .......... .......... .......... .......... .......... 33%    1.07 MB/s
 1000K .......... .......... .......... .......... .......... 35%    1.13 MB/s
 1050K .......... .......... .......... .......... .......... 37%    1.13 MB/s
 1100K .......... .......... .......... .......... .......... 38%    1.07 MB/s
 1150K .......... .......... .......... .......... .......... 40%    1.12 MB/s
 1200K .......... .......... .......... .......... .......... 42%    1.16 MB/s
 1250K .......... .......... .......... .......... .......... 43%    1.11 MB/s
 1300K .......... .......... .......... .......... .......... 45%    1.12 MB/s
 1350K .......... .......... .......... .......... .......... 47%    1.11 MB/s
 1400K .......... .......... .......... .......... .......... 48%    1.11 MB/s
 1450K .......... .......... .......... .......... .......... 50%    1.11 MB/s
 1500K .......... .......... .......... .......... .......... 52%    1.16 MB/s
 1550K .......... .......... .......... .......... .......... 53%    1.15 MB/s
 1600K .......... .......... .......... .......... .......... 55%    1.11 MB/s
 1650K .......... .......... .......... .......... .......... 57%    1.13 MB/s
 1700K .......... .......... .......... .......... .......... 59%    1.15 MB/s
 1750K .......... .......... .......... .......... .......... 60%    1.12 MB/s
 1800K .......... .......... .......... .......... .......... 62%    1.17 MB/s
 1850K .......... .......... .......... .......... .......... 64%    1.15 MB/s
 1900K .......... .......... .......... .......... .......... 65%    1.10 MB/s
 1950K .......... .......... .......... .......... .......... 67%    1.10 MB/s
 2000K .......... .......... .......... .......... .......... 69%    1.09 MB/s
 2050K .......... .......... .......... .......... .......... 70%    1.20 MB/s
 2100K .......... .......... .......... .......... .......... 72%    1.09 MB/s
 2150K .......... .......... .......... .......... .......... 74%    1.09 MB/s
 2200K .......... .......... .......... .......... .......... 75%    1.14 MB/s
 2250K .......... .......... .......... .......... .......... 77%    1.15 MB/s
 2300K .......... .......... .......... .......... .......... 79%    1.17 MB/s
 2350K .......... .......... .......... .......... .......... 80%    1.11 MB/s
 2400K .......... .......... .......... .......... .......... 82%    1.13 MB/s
 2450K .......... .......... .......... .......... .......... 84%    1.15 MB/s
 2500K .......... .......... .......... .......... .......... 86%    1.11 MB/s
 2550K .......... .......... .......... .......... .......... 87%    1.10 MB/s
 2600K .......... .......... .......... .......... .......... 89%    1.08 MB/s
 2650K .......... .......... .......... .......... .......... 91%    1.10 MB/s
 2700K .......... .......... .......... .......... .......... 92%    1.09 MB/s
 2750K .......... .......... .......... .......... .......... 94%    1.16 MB/s
 2800K .......... .......... .......... .......... .......... 96%    1.15 MB/s
 2850K .......... .......... .......... .......... .......... 97%    1.10 MB/s
 2900K .......... .......... .......... .......... .......... 99%    1.14 MB/s
 2950K .......... ....                                       100%    1.29 MB/s

20:50:26 (1.10 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
[COLOR="Red"]md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.[/COLOR]

kris@ubuntu:/boot/grub$ 
kris@ubuntu:/boot/grub$ nspluginwrapper -a -v
kris@ubuntu:/boot/grub$ nspluginwrapper -l
kris@ubuntu:/boot/grub$ 

```

I tried deleting the deb packages, so that when I reinstalled, new ones would be downloaded. That did not fix the problem.

```
kris@ubuntu:/var/cache/apt/archives$ sudo rm flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb 
kris@ubuntu:/var/cache/apt/archives$ sudo rm nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb 
kris@ubuntu:/var/cache/apt/archives$ sudo apt-get --purge remove flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  nspluginwrapper
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kris@ubuntu:/var/cache/apt/archives$ sudo apt-get --purge autoremove Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper
The following packages will be REMOVED:
  nspluginwrapper*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 377kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 101782 files and directories currently installed.)
Removing nspluginwrapper ...
kris@ubuntu:/var/cache/apt/archives$ sudo apt-get install flashplugin-nonfree Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nspluginwrapper
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree nspluginwrapper
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 129kB of archives.
After unpacking 537kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com gutsy/multiverse nspluginwrapper 0.9.91.5-1ubuntu1 [111kB]
Get:2 http://us.archive.ubuntu.com gutsy/multiverse flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 [18.1kB]
Fetched 129kB in 1s (116kB/s)             
Preconfiguring packages ...
Selecting previously deselected package nspluginwrapper.
(Reading database ... 101759 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up nspluginwrapper (0.9.91.5-1ubuntu1) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--20:56:58--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.202.70
Connecting to fpdownload.macromedia.com|72.247.202.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  639.36 KB/s
   50K .......... .......... .......... .......... ..........  3%    1.13 MB/s
  100K .......... .......... .......... .......... ..........  5%    1.08 MB/s
  150K .......... .......... .......... .......... ..........  6%    1.13 MB/s
  200K .......... .......... .......... .......... ..........  8%    1.07 MB/s
  250K .......... .......... .......... .......... .......... 10%    1.12 MB/s
  300K .......... .......... .......... .......... .......... 11%    1.13 MB/s
  350K .......... .......... .......... .......... .......... 13%    1.04 MB/s
  400K .......... .......... .......... .......... .......... 15%    1.12 MB/s
  450K .......... .......... .......... .......... .......... 16%    1.11 MB/s
  500K .......... .......... .......... .......... .......... 18%    1.05 MB/s
  550K .......... .......... .......... .......... .......... 20%    1.16 MB/s
  600K .......... .......... .......... .......... .......... 21%    1.16 MB/s
  650K .......... .......... .......... .......... .......... 23%    1.10 MB/s
  700K .......... .......... .......... .......... .......... 25%    1.12 MB/s
  750K .......... .......... .......... .......... .......... 26%    1.14 MB/s
  800K .......... .......... .......... .......... .......... 28%    1.11 MB/s
  850K .......... .......... .......... .......... .......... 30%    1.10 MB/s
  900K .......... .......... .......... .......... .......... 32%    1.11 MB/s
  950K .......... .......... .......... .......... .......... 33%    1.06 MB/s
 1000K .......... .......... .......... .......... .......... 35%    1.13 MB/s
 1050K .......... .......... .......... .......... .......... 37%    1.12 MB/s
 1100K .......... .......... .......... .......... .......... 38%    1.13 MB/s
 1150K .......... .......... .......... .......... .......... 40%    1.04 MB/s
 1200K .......... .......... .......... .......... .......... 42%    1.12 MB/s
 1250K .......... .......... .......... .......... .......... 43%    1.13 MB/s
 1300K .......... .......... .......... .......... .......... 45%    1.12 MB/s
 1350K .......... .......... .......... .......... .......... 47%    1.15 MB/s
 1400K .......... .......... .......... .......... .......... 48%  398.24 KB/s
 1450K .......... .......... .......... .......... .......... 50%  159.19 MB/s
 1500K .......... .......... .......... .......... .......... 52%  760.31 KB/s
 1550K .......... .......... .......... .......... .......... 53%  823.33 KB/s
 1600K .......... .......... .......... .......... .......... 55%    1.03 MB/s
 1650K .......... .......... .......... .......... .......... 57%    1.12 MB/s
 1700K .......... .......... .......... .......... .......... 59%    1.04 MB/s
 1750K .......... .......... .......... .......... .......... 60%    1.15 MB/s
 1800K .......... .......... .......... .......... .......... 62%    1.13 MB/s
 1850K .......... .......... .......... .......... .......... 64%    1.10 MB/s
 1900K .......... .......... .......... .......... .......... 65%    1.16 MB/s
 1950K .......... .......... .......... .......... .......... 67%    1.17 MB/s
 2000K .......... .......... .......... .......... .......... 69%    1.00 MB/s
 2050K .......... .......... .......... .......... .......... 70%    1.14 MB/s
 2100K .......... .......... .......... .......... .......... 72%    1.16 MB/s
 2150K .......... .......... .......... .......... .......... 74%    1.08 MB/s
 2200K .......... .......... .......... .......... .......... 75%    1.13 MB/s
 2250K .......... .......... .......... .......... .......... 77%    1.13 MB/s
 2300K .......... .......... .......... .......... .......... 79%    1.13 MB/sReading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/18.1kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 101793 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 (using .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--20:50:07--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.202.70
Connecting to fpdownload.macromedia.com|72.247.202.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  656.09 KB/s
   50K .......... .......... .......... .......... ..........  3%    1.14 MB/s
  100K .......... .......... .......... .......... ..........  5%    1.17 MB/s
  150K .......... .......... .......... .......... ..........  6%    1.09 MB/s
  200K .......... .......... .......... .......... ..........  8%    1.15 MB/s
  250K .......... .......... .......... .......... .......... 10%    1.12 MB/s
  300K .......... .......... .......... .......... .......... 11%    1.08 MB/s
  350K .......... .......... .......... .......... .......... 13%    1.09 MB/s
  400K .......... .......... .......... .......... .......... 15%    1.11 MB/s
  450K .......... .......... .......... .......... .......... 16%    1.09 MB/s
  500K .......... .......... .......... .......... .......... 18%    1.11 MB/s
  550K .......... .......... .......... .......... .......... 20%    1.14 MB/s
  600K .......... .......... .......... .......... .......... 21%    1.07 MB/s
  650K .......... .......... .......... .......... .......... 23%    1.08 MB/s
  700K .......... .......... .......... .......... .......... 25%    1.08 MB/s
  750K .......... .......... .......... .......... .......... 26%    1.10 MB/s
  800K .......... .......... .......... .......... .......... 28%    1.05 MB/s
  850K .......... .......... .......... .......... .......... 30%    1.08 MB/s
  900K .......... .......... .......... .......... .......... 32%    1.06 MB/s
  950K .......... .......... .......... .......... .......... 33%    1.11 MB/s
 1000K .......... .......... .......... .......... .......... 35%    1.07 MB/s
 1050K .......... .......... .......... .......... .......... 37%    1.18 MB/s
 2350K .......... .......... .......... .......... .......... 80%    1.11 MB/s
 2400K .......... .......... .......... .......... .......... 82%    1.01 MB/s
 2450K .......... .......... .......... .......... .......... 84%    1.17 MB/s
 2500K .......... .......... .......... .......... .......... 86%    1.10 MB/s
 2550K .......... .......... .......... .......... .......... 87%    1.05 MB/s
 2600K .......... .......... .......... .......... .......... 89%    1.19 MB/s
 2650K .......... .......... .......... .......... .......... 91%    1.13 MB/s
 2700K .......... .......... .......... .......... .......... 92%  525.86 KB/s
 2750K .......... .......... .......... .......... .......... 94%  150.34 MB/s
 2800K .......... .......... .......... .......... .......... 96%    1.04 MB/s
 2850K .......... .......... .......... .......... .......... 97%  838.60 KB/s
 2900K .......... .......... .......... .......... .......... 99%  986.44 KB/s
 2950K .......... ....                                       100%  853.27 KB/s

20:57:01 (1.05 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

kris@ubuntu:/var/cache/apt/archives$ 
```

---

### Post by bran on 2007-12-17
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

shut down the browsers and install from the gz package

seems the flash in the repositories is broken.

---

### Post by go_beep_yourself on 2007-12-17
> **bran said:**
> [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

shut down the browsers and install from the gz package

seems the flash in the repositories is broken.

I tried that, but it is not working. Here is what happens.

```
kris@ubuntu:~/Desktop/install_flash_player_9_linux$ ./flashplayer-installer 

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

kris@ubuntu:~/Desktop/install_flash_player_9_linux$ linux32 ./flashplayer-installer 

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 9 will be installed in your home directory.

Support is available at http://www.adobe.com/support/flashplayer/

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...





----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/kris/.mozilla

Proceed with the installation? (y/n/q): y       

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n): n


Please log out of this session and log in for the changes to take effect.


The Adobe Flash Player installation is complete.

kris@ubuntu:~/Desktop/install_flash_player_9_linux$ nspluginwrapper -a -v
kris@ubuntu:~/Desktop/install_flash_player_9_linux$ nspluginwrapper -l
kris@ubuntu:~/Desktop/install_flash_player_9_linux$ 
```

---

### Post by John.Michael.Kane on 2007-12-17
You might want to have a look over these.
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)

[https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html](https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html)

Until they have decided how to proceed you may want to use one of these methods
[http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java)
[http://ubuntuforums.org/showpost.php?p=3941685&postcount=11](http://ubuntuforums.org/showpost.php?p=3941685&postcount=11)
[http://ubuntuforums.org/showthread.php?t=639029](http://ubuntuforums.org/showthread.php?t=639029)
[http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by Melcar on 2007-12-18
You need to extract the [flashplayer]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")    to the /usr/lib64/mozilla folder.  Inside that folder there is a file called libflashplayer.so; copy that file into /usr/lib64/mozilla/plugins.  Now download and install nspluginwrapper (with Synaptic) and do "sudo nspluginwrapper -i /usr/lib64/mozilla/plugins/libflashplayer.so".

---

### Post by srmantis on 2007-12-18
If you have the ubuntu 7.10 amd64 the solution is easy. The first step is uninstall the flashplugin-nonfree and gnash from synaptic. The next step is to erase all the files related to flash in the folder .mozilla/plugin in your /home/kris (to use control+H to see the file hidden), for example flashplayer.xpt, libflashplayer.so, etc.
To run firefox and you go: [www.seal.com](www.seal.com)
In the part of above of the window there is a bottom: plugin additional...click on bottom. you have two options:
-Adobe flash player (install)
-gnash swf player
then you select the adobe player flash player and click go on,
now it was asking if you install flashplugin-nonfree....yes
reboot firefox and you go again to [www.seal.com](www.seal.com).
again click on bottom plugin additionals and you install flash player.

that's all.

Flash player on ubuntu 7.04 amd64 it's not easy (for me :( ).

---

### Post by Kilz on 2007-12-18
> **srmantis said:**
> 

Flash player on ubuntu 7.04 amd64 it's not easy.

[Yes it is.]("http://ubuntuforums.org/showthread.php?t=476924")  :D

---

### Post by angryfirelord on 2007-12-18
nspluginwrapper is automated for amd64 debs now. Just download & install the latest flashplugin-nonfree package. Your error is there because gutsy's flash deb is pointing to an older version of flash.

[http://mirrors.kernel.org/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb]("http://mirrors.kernel.org/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb")

---

