---
title: "problem with 2.6.27-7 install on ubuntu 8.10"
date: 2009-01-27
forum: x86 64-bit Users
---

### Post by banter25 on 2009-01-27
5th time coming here to try to get this sorted out.  I am running 8.10.  I am getting the following error when I try to use the line command or the synaptic to install the linux-image-2.6.27-7-generic

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Does anyone know what to do on this?  I have tried the following

sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade

and 

sudo apt-get dist-upgrade

and 

sudo dpkg --configure -a 

and

sudo dpkg --configure -a

sudo apt-get -f install

and

sudo apt-get clean
sudo apt-get -f install
sudo dpkg --config -a
sudo apt-get update
sudo apt-get upgrade

and a myriad of other useless command sets.  ](*,)](*,):cry:

---

### Post by sarath_it on 2009-01-27
restart and try OR..

Remove that file.. 

sudo rm /var/cache/apt/archives/lock

---

### Post by ptn107 on 2009-01-28
I second that previous response.  Just also make sure 'Add/Remove...' and 'Synaptic' are not running.

---

### Post by banter25 on 2009-01-28
> **sarath_it said:**
> restart and try OR..

Remove that file.. 

sudo rm /var/cache/apt/archives/lock


Did that, and it got me over that hump...  THANK YOU.

BUT, it returned the following error when trying to upgrade, after the following command set

sudo apt-get clean
sudo apt-get -f install
sudo dpkg --config -a
sudo apt-get update
sudo apt-get upgrade

Unpacking replacement pulseaudio-module-x11 ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

