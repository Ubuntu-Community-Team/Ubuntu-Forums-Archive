---
title: "Can't install wine. Crazy dependency problem?"
date: 2012-12-02
forum: Wine
---

### Post by avianbc on 2012-12-02
I have tried:

1) Adding official Wine PPA and installing from there
2) -f, clean, autoclean
3) aptitude
4) synaptic
5) software center

None have worked. Searched far and low and still no solution found.

Here is the exact error:

> avian@ubuntu:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not installable
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


> avian@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


Here is my sources.list:

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free

---

### Post by Sigshane on 2012-12-04
Yeah, I had this problem too, when I was trying to install wine from the website.

What I had to do was

```
sudo apt-get remove --purge wine wine1.4 
```

then, for good measure, 

```
sudo apt-get clean
```

and

```
sudo apt-get autoclean
```

After that, I was able to install the Software Center version of wine.

Hope this helps!

Shane

---

### Post by avianbc on 2012-12-04
Still the same error! Everyone else seems to be staying a mile away from this judging from the views/replies.

> avian@ubuntu:~$ sudo apt-get remove --purge wine wine1.4
[sudo] password for avian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'wine' is not installed, so not removed
Package 'wine1.4' is not installed, so not removed
The following package was automatically installed and is no longer required:
  icoutils
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
avian@ubuntu:~$ sudo apt-get clean
avian@ubuntu:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
avian@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


---

### Post by Tweak42 on 2012-12-04
Not sure if it makes any difference, but you don't need the Wine PPA if you are trying to install wine 1.4 in Ubuntu 12.10 since it ships in the stock repos.

Try disabling or removing the Wine PPA and installing 1.4. 
You'd use the Wine PPA if you are installing wine 1.5.

Is there a reason you are wanting to run 1.4?

---

### Post by avianbc on 2012-12-04
I want to install any version. I've tried installing 1.5, 1.4, 1.3, 1.2, and removing all the extra PPAs (look at my sources.list).

---

### Post by vladdy on 2012-12-05
Maybe try something like this? I'm guessing you used debootstrap or something to install..

sudo dpkg --add-architecture i386
sudo apt-get update

---

### Post by inzianand on 2012-12-10
Hi Mate,

Check this link. I had the same problem for almost two days and this saved my day!

I have Ubuntu 12.10 64 bit, freshly installed via wubi. 

[http://askubuntu.com/questions/214181/installing-wine-on-64-bit](http://askubuntu.com/questions/214181/installing-wine-on-64-bit)

Let me know if you still face the problem.

---

### Post by BrianL on 2012-12-13
Thank you for that! That worked for me. Wubi on a 64bit machine.:D

---

