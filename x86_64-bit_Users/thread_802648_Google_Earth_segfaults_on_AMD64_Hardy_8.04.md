---
title: "Google Earth segfaults on AMD64 Hardy 8.04"
date: 2008-05-21
forum: x86 64-bit Users
---

### Post by komiapoika on 2008-05-21
Google-Earth doesn't seem to work on kubuntu 8.04 hardy, running on an amd64 machine.

I installed it "properly" via Medibuntu packages:

# sudo apt-get install googleearth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  googleearth-4.2 googleearth-4.2-data
The following NEW packages will be installed:
  googleearth googleearth-4.2 googleearth-4.2-data
0 upgraded, 3 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/22.9MB of archives.
After this operation, 68.2MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
Selecting previously deselected package googleearth-4.2-data.
(Reading database ... 135793 files and directories currently installed.)
Unpacking googleearth-4.2-data (from .../googleearth-4.2-data_4.2.205.5730-0medibuntu4_all.deb) ...
Selecting previously deselected package googleearth-4.2.
Unpacking googleearth-4.2 (from .../googleearth-4.2_4.2.205.5730-0medibuntu4_amd64.deb) ...
googleearth-eula has already been accepted
Selecting previously deselected package googleearth.
Unpacking googleearth (from .../googleearth_4.3.7191.6508-0medibuntu3_all.deb) ...
Setting up googleearth-4.2-data (4.2.205.5730-0medibuntu4) ...

Setting up googleearth-4.2 (4.2.205.5730-0medibuntu4) ...

Setting up googleearth (4.3.7191.6508-0medibuntu3) ...


Starting it crashes:

$ googleearth 
Segmentation fault

It isn't a permission problem:

$ sudo googleearth
[sudo] password for h: 
Segmentation fault


Using the generic Linux installer instead of the package doesn't help much:

Removing googleearth ...
Removing googleearth-4.2 ...
Removing googleearth-4.2-data ...

sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
h@wakinglife:~/Desktop$ sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...


~/bin$ ./googleearth
Segmentation fault

...

sudo sh googleearth 
Segmentation fault

installing as root doesn't help either:

sudo sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...


Segmentation fault both as user and su user


May 4.3.?:

sudo rm -rf /opt/google-earth/
sudo rm /usr/local/bin/googleearth 

sudo sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
h@wakinglife:~/Desktop$ sudo sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7204.836..............................................................
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...

$ googleearth 
Segmentation fault
$ sudo googleearth 
Segmentation fault

:(

I remember on Debian 4.0r3 64bit, if you force install a dirty library called ... geez I forgot  It's a Debian .deb package no longer in any port, some network layer to run 32 bits applications on 64bit AMD. It would half install, stop and crash at configuration, and not let you install any more package until you remove it; it would make Google Earth able to connect on network while it would only work offline without it. But even without it, Debian would start so I'm not even sure it is the same problem at all.

Google Earth has no command line, so it's hard to backtrace.

 lsb_release -rd
Description:    Ubuntu 8.04
Release:        8.04

googleearth:
  Installed: 4.3.7191.6508-0medibuntu3
  Candidate: 4.3.7191.6508-0medibuntu3
  Version table:
 *** 4.3.7191.6508-0medibuntu3 0
        500 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
        100 /var/lib/dpkg/status
:confused:

---

### Post by warp99 on 2008-05-21
I have the tar package from Google installed on my Kubuntu AMD64 machine without any hassles. It's pretty easy to install. First you need to download the bin file from Google:

[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Open a terminal and change to the directory that the file is in and make the file executable:
```
chmod +x GoogleEarthLinux.bin
```
Run the executable as root with sudo:
```
sudo ./GoogleEarthLinux.bin
```
remember the "./" in-front of the file and choose "/usr/local/" as the install directory since this is the default location for programs outside of the package management system for Debian based distros. Upgrading is done in the same manner and to remove Googe Earth there is an uninstall script in the googleearth directory.

Edit:

Google Earth, at least the version direct from Google, comes with its own set of  libraries so this may make a difference.

---

### Post by komiapoika on 2008-05-21
So, I just did exactly what you told me, and it still segfaults.

Just to make sure, should I install it in /usr/local/google-earth/ (like I just did) or am I supposed to actually install it in /usr/local/, dropping all the libraries and stuff there?

How can I find out why it segfaults?

I need Google Earth to work and will have to actually fall back to Debian if I can't resolve this.

---

### Post by Kilz on 2008-05-21
Do you have accelerated graphics?

---

### Post by Melk79 on 2008-05-21
I did just this and it worked out:

1. Install GE 4.3 via Synaptic Package Manager (rather than from Google)

2. At this point, I get Error 29 and no connection

3. Run sudo apt-get install lib32nss-mdns (thanks acope) (For 64bit anyways)

4. Error 29 is gone, but no earth appears as user. Only sudo googleearth works.

5. Remove .config/Google and .googleearth from my home directory and restart googleearth (thanks phoolish)

6. Everything works great.

Didn't see you had similar problems, but thought I'd pass along just in case.

---

### Post by warp99 on 2008-05-21
> **komiapoika said:**
> So, I just did exactly what you told me, and it still segfaults.

Just to make sure, should I install it in /usr/local/google-earth/ (like I just did) or am I supposed to actually install it in /usr/local/, dropping all the libraries and stuff there?

How can I find out why it segfaults?

I need Google Earth to work and will have to actually fall back to Debian if I can't resolve this.

You installed it in the right place, no problem with that. Are you using an ATI card and/or using compiz graphics?

---

### Post by BoredOutOfMyMind on 2008-05-22
> **komiapoika said:**
> So, I just did exactly what you told me, and it still segfaults.

Just to make sure, should I install it in /usr/local/google-earth/ (like I just did) or am I supposed to actually install it in /usr/local/, dropping all the libraries and stuff there?

How can I find out why it segfaults?

I need Google Earth to work and will have to actually fall back to Debian if I can't resolve this.


The latest version (Google Earth for GNU/Linux 4.3.7204.836.) installed to /opt/google-earth  not /usr/local/google-earth

hmmmmm  :confused:

running the install again seemed to repair the login issues on 64 bit for me.  


But only for root with sudo googleearth as command. 

....:(

---

### Post by C. Wizard on 2008-05-22
Google Earth 4.3 will not work for me. Installs and comes up, but without the globe.

Version 4.2 runs perfectly by installing the package from Google from a command prompt as follows,

sh GoogleEarthLinux.bin

---

### Post by komiapoika on 2008-05-22
So, I tried installing version 4.3 using Synaptic

sudo googleearth
[sudo] password
Segmentation fault

This is all I get to see from Google Earth. I don't even make it to the cosmos with stars or the login part. All I see is "Segmentation fault".

I have accelerated 3D using NVIDIA drivers from the NVIDIA installer for my GeForce 6800 GT.

---

### Post by philinux on 2008-05-22
I would go to synaptic remove all google-earth select complete removal.

Also delete any .google folders in you home folder.

sudo apt-get autoremove

sudo apt-get update && sudo apt-get upgrade

Then go for a reinstall from synaptic.

---

### Post by Yellow Pasque on 2008-05-22
This old thread might be of some use:
[http://ubuntuforums.org/showthread.php?t=520952](http://ubuntuforums.org/showthread.php?t=520952)

---

### Post by komiapoika on 2008-05-22
> **philinux said:**
> I would go to synaptic remove all google-earth select complete removal.

Also delete any .google folders in you home folder.

sudo apt-get autoremove

sudo apt-get update && sudo apt-get upgrade

Then go for a reinstall from synaptic.

well I just did exactly that, and it still segfaults. How can I trace why it segfaults??
:cry:

---

### Post by komiapoika on 2008-05-22
> **Temüjin said:**
> This old thread might be of some use:
[http://ubuntuforums.org/showthread.php?t=520952](http://ubuntuforums.org/showthread.php?t=520952)

I have NVIDIA card, not ATI, so ATI drivers can't be at fault...

faiw here's the output of fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6800 GT/AGP/SSE2
OpenGL version string: 1.4 (2.1.2 NVIDIA 169.12)

---

### Post by komiapoika on 2008-05-22
omg ... i wanted to create backtrace, so i ran googleearth as normal user and guess what .... IT WORKS !!!!

I think by installing mesa utils packages to get output of fglrxinfo, i installed something that was missing. Oh and btw it's 4.3 !!

I'm so glad ... I got Ubuntu, KDE4, Google Earth runnable as user... What else?! :guitar::guitar::lolflag::lolflag::lolflag::lolflag::popcorn::KS:

---

### Post by philinux on 2008-05-22
Good boy, sorted then.

---

### Post by warp99 on 2008-05-22
Good for you. Now I don't have to post the wonders of strace and ldd. :lolflag:

---

### Post by markbuntu on 2008-05-23
I just got google earth with synaptics and have no problem at all, it worked right out of the box. 

I already had lib32nss-mdns installed so maybe that made a difference but for sure the synaptics packager people fixed the install for amd64. 

Yay!!!
I will buy them a beer if I ever meet them, all of them.

Anyway, it is a quantum leap better than last week when I experienced just a horrible catastrophe when I tried to install it from the google earth site.

However, I will not dare to use it with desktop visual effects enabled until ATI fixes the indirect rendering problem with compiz.


HP 1330n Media Center (modified)
ASUS A8AE-LE motherboard (OEM)
AMD Athlon64 3800+ 2.9GHZ 939 socket
3GB 3200 DDR RAM
ATI Radeon Express 200M (disabled in bios)
ATI HD3650 1GB DDR2  PCI Express
AC97 on board sound
Realtek 810L on board 10/100 ethernet

SOYO 24 inch LCD wide screen monitor 1920x 1200
Samsung 930B 19 inch LCD 1280x1024
Big Desktop 

Ubuntu 8.04 "Hardy Heron" - Release amd64
Kernel Linux 2.6.24-16-generic
ATI Proprietary Linux Driver Version Identifier:8.47.3
Catalyst Control Center Version 1.8
Open GL version 2.1.7412 Release

---

### Post by pixel :-) on 2008-05-24
ignore this

---

### Post by komiapoika on 2008-05-25
I have a big problem ... Since today googleearth, which worked perfectly yesterday, segfaults on startup again!! I haven't done anything to my system except may be one or two routine apt-get upgrade.

Moving away .config/Google and .googleearth doesn't help

Reinstalling from Synaptic yields no result :( :(
:mad:

---

### Post by komiapoika on 2008-05-25
Here's the output of strace:

[http://pastebin.ca/1028987](http://pastebin.ca/1028987)

---

### Post by Amshu on 2008-05-25
I have the same problem with google earth. I'm also using nvidia.

---

### Post by komiapoika on 2008-06-02
This issue still unresolved :(

---

### Post by komiapoika on 2008-06-04
Okay I'm so ******* proud of myself on this one... I figured out the upgrade must have screwed something in the NVIDIA drivers, so I just upgraded them to NVIDIA-Linux-x86_64-173.14.05 (using the native installer) and it set itself back on top on every port's modification, then I rebooted, and there Google Earth 4.3 is back online :) :) :))))))))))

---

### Post by minhaaj on 2008-06-05
> **komiapoika said:**
> Google-Earth doesn't seem to work on kubuntu 8.04 hardy, running on an amd64 machine.

I installed it "properly" via Medibuntu packages:

# sudo apt-get install googleearth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  googleearth-4.2 googleearth-4.2-data
The following NEW packages will be installed:
  googleearth googleearth-4.2 googleearth-4.2-data
0 upgraded, 3 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/22.9MB of archives.
After this operation, 68.2MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
Selecting previously deselected package googleearth-4.2-data.
(Reading database ... 135793 files and directories currently installed.)
Unpacking googleearth-4.2-data (from .../googleearth-4.2-data_4.2.205.5730-0medibuntu4_all.deb) ...
Selecting previously deselected package googleearth-4.2.
Unpacking googleearth-4.2 (from .../googleearth-4.2_4.2.205.5730-0medibuntu4_amd64.deb) ...
googleearth-eula has already been accepted
Selecting previously deselected package googleearth.
Unpacking googleearth (from .../googleearth_4.3.7191.6508-0medibuntu3_all.deb) ...
Setting up googleearth-4.2-data (4.2.205.5730-0medibuntu4) ...

Setting up googleearth-4.2 (4.2.205.5730-0medibuntu4) ...

Setting up googleearth (4.3.7191.6508-0medibuntu3) ...


Starting it crashes:

$ googleearth 
Segmentation fault

It isn't a permission problem:

$ sudo googleearth
[sudo] password for h: 
Segmentation fault


Using the generic Linux installer instead of the package doesn't help much:

Removing googleearth ...
Removing googleearth-4.2 ...
Removing googleearth-4.2-data ...

sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
h@wakinglife:~/Desktop$ sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...


~/bin$ ./googleearth
Segmentation fault

...

sudo sh googleearth 
Segmentation fault

installing as root doesn't help either:

sudo sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...


Segmentation fault both as user and su user


May 4.3.?:

sudo rm -rf /opt/google-earth/
sudo rm /usr/local/bin/googleearth 

sudo sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
h@wakinglife:~/Desktop$ sudo sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7204.836..............................................................
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...

$ googleearth 
Segmentation fault
$ sudo googleearth 
Segmentation fault

:(

I remember on Debian 4.0r3 64bit, if you force install a dirty library called ... geez I forgot  It's a Debian .deb package no longer in any port, some network layer to run 32 bits applications on 64bit AMD. It would half install, stop and crash at configuration, and not let you install any more package until you remove it; it would make Google Earth able to connect on network while it would only work offline without it. But even without it, Debian would start so I'm not even sure it is the same problem at all.

Google Earth has no command line, so it's hard to backtrace.

 lsb_release -rd
Description:    Ubuntu 8.04
Release:        8.04

googleearth:
  Installed: 4.3.7191.6508-0medibuntu3
  Candidate: 4.3.7191.6508-0medibuntu3
  Version table:
 *** 4.3.7191.6508-0medibuntu3 0
        500 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
        100 /var/lib/dpkg/status
:confused:

I have Dell Inspiron 6400. I have installed Google Earth but is highly unstable. When i launch it screen is always blinking. It crashes the whole system. When it streams, whole screen flashes. Anyone else has this problem too? any help would be great.

---

### Post by Wynne G Oldman on 2008-06-06
> **minhaaj said:**
> I have Dell Inspiron 6400. I have installed Google Earth but is highly unstable. When i launch it screen is always blinking. It crashes the whole system. When it streams, whole screen flashes. Anyone else has this problem too? any help would be great.
If you have Compiz enabled, try disabling it and see if that makes a difference.

---

### Post by philinux on 2008-06-06
edit

disregard.

---

### Post by kystorms on 2008-10-01
> **philinux said:**
> I would go to synaptic remove all google-earth select complete removal.

Also delete any .google folders in you home folder.

sudo apt-get autoremove

sudo apt-get update && sudo apt-get upgrade

Then go for a reinstall from synaptic.


where you say sudo apt-get autoremove ---

what if the file is located in the following folder:
 /usr/local/bin/googleearth

would i then write that whole address of the google folder in after autoremove?

thank you:confused:

---

### Post by garuhhh on 2009-07-06
am sorry if this thread is quite old, but i seem to have found a solution..
am running ubuntu 9.04 64bit, and i experienced the same segmentation fault. Try this [link ]("http://basicubuntu.blogspot.com/2009/07/segmentation-fault-in-google-earth.html")for a possible solution.

---

### Post by ahhyes on 2009-09-17
+1 (for 9.04 though)

The 32 bit openGL libraries didn't get installed properly by the nvidia nCurses based installer (found a warning in the nvidia installer log).

Uninstalling and reinstalling the driver fixed the issue and google earth no longer segfaults.

---

### Post by Arup on 2009-09-18
> **ahhyes said:**
> +1 (for 9.04 though)

The 32 bit openGL libraries didn't get installed properly by the nvidia nCurses based installer (found a warning in the nvidia installer log).

Uninstalling and reinstalling the driver fixed the issue and google earth no longer segfaults.


Yep, that does the trick, strangely, if you install the nvidia driver via the hardware applet, this problem doesn't occur. Of course you get an older driver. Ncurses based gets you the latest one, even beta so its definitely better. Just do the install and uninstall and it works out fine.

---

### Post by nss0000 on 2009-09-19
> **BoredOutOfMyMind said:**
> The latest version (Google Earth for GNU/Linux 4.3.7204.836.) installed to /opt/google-earth  not /usr/local/google-earth

hmmmmm  :confused:

running the install again seemed to repair the login issues on 64 bit for me.  


But only for root with sudo googleearth as command. 

....:(

Yeah that's where my GOOGLE-EARTH got parked ... along with REALPLAYER: 

Never had a GE issue .. running AMD5400+/nv_7600 & x64v_8.04.1 LTS.

---

### Post by thehagman on 2009-10-08
HI all.
This thread was great help for me to get GE (mostly) running on AMD64 Jaunty 9.04
With a /usr/local install directly using the download from google, googleearth now starts and runs smoothly, apart from three issues:

1) MyPLaces do not work correctly. Looking at the file, it appears that GE stores coordinates using German locale and reads back using C locale (IMHO it should use C locale throughout). Thus a ground level point at 50°30'N 7°20'E is stored as
<coordinates>7,333333333333,50,50000000,0</coordinates>
Upon next start this is read as 180°N 7°E at 50m height (because 33333333 causes some overflow) - and written back as such.
Correcting the entry manually to 
<coordinates>7.333333333333,50.50000000,0</coordinates>
does not help.

2) upon startup I get a hint that GE could not write the current file location of Cache or my places. Values are set to
/home/hagman/.googleearth and /hom/hagman/.googleearth/Cahce, repsectively.
I observe however that GE does write to these files.

3) I must use the daylight option (and select local noon) to get correct colours. Without that option (i.e. immediately after the startup animation that does use daylight) I see patches of varying brightness all over the earth. Some of these patches are almost white. Using the daylight option the colours "behave well".

:mad: hagman

---

