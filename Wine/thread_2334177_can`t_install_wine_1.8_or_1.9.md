---
title: "can`t install wine 1.8 or 1.9"
date: 2016-08-17
forum: Wine
---

### Post by waranty922 on 2016-08-17
Hi guys I am on Ubuntu 16.04.1 X64 and haveing issue with installing wine [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu) tried online method and get this answer 
```
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-devel : Depends: wine-devel (= 1.9.16~ubuntu16.04.1)
E: Unable to correct problems, you have held broken packages.
```
when I try installing wine1.8 like this 
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.8
I get this error 
```
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.8 : Depends: wine1.8-amd64 (= 1:1.8.0-0ubuntu1~ubuntu15.10.1~ppa1) but it is not going to be installed
           Depends: wine1.8-i386 (= 1:1.8.0-0ubuntu1~ubuntu15.10.1~ppa1)
           Recommends: fonts-droid but it is not installable
E: Unable to correct problems, you have held broken packages.
```
what should i do to correctly install wine ?

Thank you in advance

---

### Post by Portaro on 2016-08-18
Have you install other version of wine in the past, if yes you need to purge it and then try to install other version but the new version that you should be install is the present on the synaptic or the reference of &#8594; apt-cache search wine


In other way try to do this commands if is the first install of wine &#8594;
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
then search for wine and install it.


You also can install Playonlinux to install different versions of wine in the program he can do this easily all you need is install playonlinux and then install software and in this process you can install many versions of wine to have better compatibility with some programs.


:P

---

### Post by waranty922 on 2016-08-19
> **Portaro said:**
> Have you install other version of wine in the past, if yes you need to purge it and then try to install other version but the new version that you should be install is the present on the synaptic or the reference of &#8594; apt-cache search wine


In other way try to do this commands if is the first install of wine &#8594;
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
then search for wine and install it.


You also can install Playonlinux to install different versions of wine in the program he can do this easily all you need is install playonlinux and then install software and in this process you can install many versions of wine to have better compatibility with some programs.


:P

thank you I got it installed

---

