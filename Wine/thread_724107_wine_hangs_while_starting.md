---
title: "wine hangs while starting"
date: 2008-03-14
forum: Wine
---

### Post by joe3204 on 2008-03-14
hello...i have ubuntu 7.10 installed....recently i installed wine, first by synaptic and then by compiling thru the source....the problem i am facing is that ubuntu hangs 1 or 2 seconds after i start wine...i don't get any error messages, and i have resolved all the dependency issues.. ](*,)

please help!!!!!

---

### Post by erginemr on 2008-03-15
The latest version of Wine also comes in Debian packages. I suggest you to uninstall the one you have installed from source first:

1. Download the same package, reinstall with ./configure -> make -> sudo checkinstall. This will create a Debian package inject it your your dkpg / apt-get database.

2. Now you can uninstall it with: sudo aptitude remove wine

3. Go to [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and either download the latest Debian package (I suggest version 0.9.56 though, as the latest package seems to have several bits and pieces missing, such as Gnome menu shortcuts)...

4. Or add the Wine repository to your "Software Repositories" by following the instructions stated therein.

---

### Post by joe3204 on 2008-03-17
i have tried everything installing through synaptic, .deb packages and through source.....nothing works......it just hangs the system....nothing works as soon as i issue any command related to wine....except "wine --version"

---

### Post by erginemr on 2008-03-17
OK. Chances are low but please try this anyway: There is a hidden directory ".wine" in your home folder that holds the settings related to Wine. Maybe some mis-configured setting there may be causing it to malfunction, thus bringing your system to its knees.

So, long story short, try locating and deleting this folder altogether and see what happens. 

You can also experiment its behavior with and without desktop effects.

---

