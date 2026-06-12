---
title: "here is how you configure sound on acer 4520 and related laptops"
date: 2008-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by raaki_88 on 2008-02-10
i did face lot of problems in configuring sound drivers for ubuntu on acer finally i got them working now 

first of all it is recommended (atleast by me) to use 7.04 rather than 7.10 for resolution issues just boot in safe graphics mode that will do for a acer4520 no need of extra nvidia packages

next configuring sound 

simple first download the packages from the below site and copy them into one folder

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

next

you need one of the c libraries and curses libraries for this i guess you are done with adding extra repositories if not message me i will explain

open the terminal and fire the following
sudo synaptic
 
and next search for g++ library

after that search for curses library for c

after this automatically done by the synaptic
 
go the folder where you have downloaded the packages and extract each and everything like below

$tar xjf alsa-(name of the package)

after extarcting just type this

$cd alsa-(extracted package)

next 

$./configure

next

$make

next 

$sudo make install



follow this procedure for everything and after a reboot you will be hearing a login sound (hehe)

primarily the sound gets muted change it and now you have your system going and rocking

---

### Post by habuk on 2008-04-07
i have opened the URL to download the alsa driver but which package i have to download?

---

