---
title: "Can't install Wine"
date: 2008-01-17
forum: Wine
---

### Post by alan_18 on 2008-01-17
I can't seem to get Wine to install on my laptop.  Whenever I try installing it with Synaptic or sudo apt-get install wine, I get the following messages:

```
alan@alan-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages
alan@alan-laptop:~$ 
```

I've added the Wine repository, updated apt-get to install the newest version of wine, nothing.

---

### Post by renzokuken on 2008-01-17
what version of ubuntu are you using?

---

### Post by alan_18 on 2008-01-17
7.10 Gutsy

---

### Post by QualityPancakes on 2008-05-25
I an having the same problem, but with two different packages.

```
The following packages have unmet dependencies:
  wine: Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
        PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
E: Broken packages

```

---

### Post by cogadh on 2008-05-25
> **alan_18 said:**
> 7.10 Gutsy

When you say you added the Wine repository, did you add the Gutsy repository or the current Hardy one?

> **QualityPancakes said:**
> I an having the same problem, but with two different packages.

```
The following packages have unmet dependencies:
  wine: Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
        PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
E: Broken packages

```
It sounds like you have a broken package installation somewhere. Run "sudo apt-get update" and see if it warns of broken package installs.

---

### Post by taffypride on 2008-06-23
I'm having problems with WINE and Ubuntu 8.04.

I haven't got a net connection working in Linux yet - although using WINE, I can see my usb data modem.

I got the following error:

Unpacking wine (from wine.deb) ...
dpkg: dependency problems prevent configuration of wine:
 wine depends on binfmt-support (>= 1.1.2); however:
  Package binfmt-support is not installed.
 wine depends on libaudio2; however:
  Package libaudio2 is not installed.
 wine depends on winbind; however:
  Package winbind is not installed.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine

got version 1.0 WINE and Ubuntu 8.04.  Any help is greatly appreciated.

---

### Post by plvick on 2008-06-23
You could install all those packages, or try to use Synaptic Package Manager to install wine. I, however, broke my wine by using native windows dlls and they were bad I suppose. Anyway, now mine doesn't work at all. Gerr. I have tried the apt-get purge routine, and reintstalled a few times. It's just not going to work now. I hate to reinstall everything at this point, so I must trouble-shoot it old fashioned style. Any help? ;)

---

