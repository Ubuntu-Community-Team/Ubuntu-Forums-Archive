---
title: "Probably the Usual Wine Install Errors"
date: 2013-05-01
forum: Wine
---

### Post by ceil210 on 2013-05-01
I have tried and tried but I get a pretty bad error.  I am using 12.04.

> alex@ubuntu:~$ sudo apt-get install wine
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages

Any help is good help! <3

---

### Post by Microrobot on 2013-05-04
Using Terminal
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.5 
Try this let me know how it goes

---

### Post by ceil210 on 2013-05-04
Thanks for the reply.  I get the following error:

> alex@ubuntu:~$ sudo apt-get install wine1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.29-0ubuntu1) but it is not installable
           Recommends: fonts-droid but it is not going to be installed
           Recommends: fonts-horai-umefont but it is not going to be installed
           Recommends: fonts-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

