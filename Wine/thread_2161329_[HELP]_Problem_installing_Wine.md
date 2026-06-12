---
title: "[HELP] Problem installing Wine :/"
date: 2013-07-10
forum: Wine
---

### Post by protoss96 on 2013-07-10
Hello,

When I am trying to install Wine from Ubuntu Software Center i get this message:
```
 Package dependencies cannot be resolved
 The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.1.2ubuntu7.1 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.3 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1~precise1~ppa4) but 1.4.1-0ubuntu1~precise1~ppa4 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa4) but it is a virtual package


```

How can i solve this problem? Thank you so much for any helpful answer :D

---

### Post by DeathByDenim on 2013-07-10
Could you try opening a terminal and type the following commands?
```
sudo apt-get update
sudo apt-get install wine
```

Do you get the same errors then?

---

### Post by protoss96 on 2013-07-10
After update nothing, but when i try to install wine i get this:
```
 Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

 
```

---

### Post by DeathByDenim on 2013-07-10
wine1.6? That one is not available in the default Ubuntu repositories. Did you by any chance add the PPA's from WineHQ?

In any case, it seems apt is somewhat broken at the moment for you. Can you try to fix it by running this command?
```
sudo apt-get -f install
```

---

### Post by protoss96 on 2013-07-10
im getting this :/
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

 
```

and thats it, no more no less...

---

### Post by monkeybrain2012 on 2013-07-10
Did you use the wine ppa and then disabled or removed it? If so add back the ppa and try again, if not, add the ppa anyway and see if it solves your problem. 

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine

```
On the other hand, if you already have the ppa added and it is giving you problem, disable it.

---

### Post by protoss96 on 2013-07-10
No, i didn't have PPA on my system, i just installied is right now, updated and tryed to install wine then this:
```
 The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages. 
```

Again this same error, 'you have held broken packages'... omg what this means, i am going crazy because of this, i gets more complicated everytime i try to fix this on some new way... :/ i don't know what to do, i can't install wine..

---

### Post by DeathByDenim on 2013-07-11
I still don't quite get how you could have a dependency on wine1.6, but try this:
```
sudo apt-get purge wine
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```
Then try again.

---

### Post by Lightning Dragon on 2013-07-11
Hi,

Wine1.6? That's not out yet, weird. 

After you purge and clean the system using DeathByDenim's commands and reboot your computer--but instead do "sudo apt-get purge wine*" and then make sure you do not have hidden wine folders left by deleting them and the cache--try getting around it by trying this "sudo apt-get install wine1.5" instead. If that doesn't work, could you try the following link at this page?

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by hackyogi on 2013-07-12
you can check out this link:   [http://hackyogi.com/how-to-install-windows-software-on-linux/](http://hackyogi.com/how-to-install-windows-software-on-linux/)

---

### Post by protoss96 on 2013-07-12
I reinstallied whole OS, :/ and installied Wine with no problems, btw thank you so much guys for your ideas and time.

---

### Post by DeathByDenim on 2013-07-12
Ha, well. That works too. Glad you fixed it. :)

---

