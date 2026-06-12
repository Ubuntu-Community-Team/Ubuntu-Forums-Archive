---
title: "The basics not working"
date: 2012-10-21
forum: Wine
---

### Post by StevenHodges92 on 2012-10-21
Okay, so I'm completely new to Linux and am using Ubuntu.  When I try to install wine 1.4 it pops up a message that says this:

```
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
```so what do I have to install to get wine 1.4 to work?  This is a fresh installation of ubuntu

Here are the details

he following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

So how do I install these?

When I try to install the package "wine1.4" it gives me this

```
wine1.4:
 Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1)
 Depends: wine1.4-i386 (=1.4.1-0ubuntu1) but it is not installable
 Recommends: gnome-exe-thumbnailer but it is not going to be installed or
     kde-runtime but it is not going to be installed
 Recommends: ttf-droid
 Recommends: ttf-mscorefonts-installer but it is not going to be installed
 Recommends: ttf-umefont but it is not going to be installed
 Recommends: ttf-unfonts-core but it is not going to be installed
 Recommends: winbind but it is not going to be installed
 Recommends: winetricks but it is not going to be installed


```


In the synaptic package manager, it marks wine1.4-common and  wine1.4-smf64 green but puts an exclamation point and red over "wine1.4"  so I cant install any of them, what do I do?

---

### Post by wademac on 2012-10-24
I have the same issue I assume that wine 1.4 and 1.5 need a older version of the package manager to install as I have 1.16.7 installed and it wants package manager 1.15.7.2 .. hmm any takers on a fix for this besides a force install.

---

