---
title: "Problems compiling WINE."
date: 2006-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by saberz on 2006-03-26
Hello everyone, switched last night over from my XP box after much frustration with Windows XP and XP64 and Dual Core CPU's. Heard good things about ubuntu and took the plunge with Ubuntu 64 and have to say, its great!.

Set this site as my homepage and have been reading, searching and installing drivers, and software and trying to avoid posts like this.

Onto the reason for my post!


I have been trying now for many hours to install WINE and I am close to having it done.

I downloaded the source through APT did the other commands to download the dependencies, but as soon as I run **[COLOR="DarkRed"] apt-get --build source wine[/COLOR]** it moves along quickly and then spits out this error:

**checking for C compiler default output file name... configure: error: C compiler cannot create executables See `config.log' for more details. make: *** [config.status] Error 77 Build command 'cd wine-0.9.10~winehq1 && dpkg-buildpackage -b -uc' failed. E: Child process failed**


No idea what to do ](*,) 

The reason for using WINE is because I got Elderscroll IV: Oblivion(amazing game) and wanted to attempt to run it(far fetched I know).

I checked Synaptic and it shows I have multiple versions of GNCC++ installed, 3.4,3.6 and 4.0. Didnt install those myself probably off the cd or the online default updater *shrug so I dont know if those are correct or there is an issue with the compilers themselves.

---

### Post by Sutekh on 2006-03-27
This is a shot in the dark, but seeing as you've only just started using Ubuntu I assume you haven't installed build-essential. 


It depends on and will install gcc, g++, and other dev tools, specifically make and dpkg-dev, which according to [Ubuntu Packages - dpkg-dev](http://packages.ubuntu.com/breezy/utils/dpkg-dev)[QUOTE=Ubuntu Packages]This package contains the tools (including dpkg-source) required to unpack, build and upload Debian source packages.[/QUOTE]
This code will install that package for you
```
sudo apt-get install build-essential
```

---

