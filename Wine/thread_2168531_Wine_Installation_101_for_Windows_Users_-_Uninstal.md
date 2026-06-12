---
title: "Wine Installation 101 for Windows Users? - Uninstallable Dependencies"
date: 2013-08-18
forum: Wine
---

### Post by bewildered2 on 2013-08-18
New to Ubuntu 12.04 and am trying to install Wine, but without any success. Had hoped it'd be as easy as an .exe installation but it's proving very frustrating!!!

From what I understand I need to run terminal then enter:

sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update

sudo apt-get install wine1.6

My problem is that third step. It returns the results below

 wine1.6 : Depends: libgettextpo0 but it is not installable
           Depends: binfmt-support (>= 1.1.2) but it is not installable
           Depends: wine1.6-i386 (= 1.6-0ubuntu1~ppa1)
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not installable
           Recommends: fonts-droid but it is not going to be installed
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: fonts-horai-umefont but it is not going to be installed
           Recommends: fonts-unfonts-core but it is not installable
           Recommends: winbind but it is not installable


I've no idea how to get around this so am hoping someone will be able to help!!! Hopefully it's something simple and I'm just a Luddite when it comes to Ubuntu :-)

---

### Post by GwL3eNC on 2013-08-18
Hello,

you have done everything right. Now it seems that you have some unsolved dependencies.
I would know try a

sudo apt-get -f install 

and hopefully it would solve your problem. If not i would do a

sudo apt-get dist-upgrade

---

### Post by bewildered2 on 2013-08-21
Tried both, no joy :-(

sudo .... upgrade seemed to update an nvidia file but nothing else.

Stumbled over Play on Linux which from  my basic understanding would give me an alternative form of Wine. That's failing on icoutils being uninstallable. Also tried via the software centre but that lists additional failed dependancies.

---

### Post by texaswriter on 2013-08-23
I'm downloading a 12.04 ISO and will attempt this in a VM installation of the LTS using this PPA. Will update again in a couple of hours.

---

### Post by texaswriter on 2013-08-23
I think you must have done something wrong... From a fully updated Ubuntu 12.04, I performed the following functions. 

```
sudo apt-get update; sudo apt-get upgrade
``` and ENTER to install all updates

I added the repository and updated again (note that wine wasn't installed before I performed this).

```
sudo apt-get install wine1.6
``` and 'Y' to install the suggested packages. libgettexpo0 was among the suggested packages. Everything finished installing fine. 

So, I'd remove whatever wine packages is currently installed, remove the repository, update your system fully with sudo apt-get update; sudo apt-get upgrade, then add the repository, update your system again, and install wine1.6,

---

