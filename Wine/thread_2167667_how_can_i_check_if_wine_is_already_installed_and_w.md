---
title: "how can i check if wine is already installed and working in my system??"
date: 2013-08-14
forum: Wine
---

### Post by syedmahmood14 on 2013-08-14
hi
i am using an acer aspire  v3-571g  machine

with the following details

release 12.04 (precise) 64-bit
Kernel Linux 3.5.0-36-generic
GNOME 3.4.2

memory:7.6 GiB
processor:Intel® Core™ i5-3230M CPU @ 2.60GHz × 4

how do i check if wine is installed and working perfectly??? and can i play games like counter strike after wine is working??

---

### Post by GwL3eNC on 2013-08-14
Hi,

open a terminal (STRG+ALT+T in ubuntu) or over the menu and type 

wine

if you get an error it is not instralled.

You can install wine with

sudo apt-get update
sudo apt-get install wine

(or use the software center)
To get the newest version you must add the ppa [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)
you can do that manualy with 

sudp apt-add-repository [B]ppa:ubuntu-wine/ppa 

[/B]or using the software center.

To see if your desired app works with wine take always a look at [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

