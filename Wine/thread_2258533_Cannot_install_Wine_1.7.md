---
title: "Cannot install Wine 1.7"
date: 2014-12-28
forum: Wine
---

### Post by rebekah-p on 2014-12-28
I'll get straight to the point.  I recently switched my hard-drive to a 128-gigabyte one, and attempted to install wine.  Instead of the easy Software Center download I had expected, I got this error:
~
The following packages have unmet dependencies:

wine1.6: Depends: wine1.6-amd64 (= 1:1.6.2-0ubuntu6) but 1:1.6.2-0ubuntu6 is to be installed
         Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu6) but it is not going to be installed
~
Miffed a bit, I tried the command line way:
~
sudo apt-get install wine
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
~
The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed or
                 wine1.7 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

I then tried a repository method, a git-clone method, and downloading it from the website, as well as using Synaptic Package Manager, to no avail.  Could anyone help me out with this?  I'm not sure how to check my Ubuntu version, I believe it's 14.04.

---

### Post by aysiu on 2014-12-28
Sounds as if you have some conflicting repositories. Can you post the output of these commands? ```
sudo apt-get update
cat /etc/apt/sources.list
```

---

### Post by DigitalForecast on 2014-12-30
Run the following commands as root:
```

apt-add-repository ppa:ubuntu-wine/ppa
apt-get update
apt-get install wine1.7

```
Reply if there is still a problem

---

