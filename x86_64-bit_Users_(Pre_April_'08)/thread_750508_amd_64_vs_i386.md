---
title: "amd 64 vs i386"
date: 2008-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bookmaster on 2008-04-09
Hi everyone,

I'm just a rookie with Ubuntu. I did install amd 64 desktop version on my lap top (turion 64 cpu), but I have problems with drivers for graphic card GeForce Go6100. I did find drivers but they are only for i386 version.

Also when I want to play any compresed movie (e.g. divx) I cannot download or install any drivers to run that movie.

On my lap top I have installed winxp pro and Ubuntu amd 64 version.
I want to install i386 version over that amd 64 version.

What do I have to do?

If I just install it over existing amd 64 version will my lap top have dual boot like I have it now please?

Or is there any other way that I can run driver (first I have to find it) for my GeForce GO 6100 and play divx movies?

---

### Post by Kilz on 2008-04-09
If you think installing the i386 version is going to solve the graphics driver and codec issues, you are incorrect. There is a 64bit driver and all of the amd64bit users can see video. It appears to me that you are a new user and have little knowledge of Ubuntu. Going to i386 isnt going to change that. There is a learning curve when moving to linux. You are going to have to learn things and find what works regardless of what version you install.
[Go here for the video driver install]("http://www.albertomilone.com/nvidia_scripts1.html")
For movies, install either mplayer or vlc. [Go here to learn about installing software in Ubuntu.]("http://www.monkeyblog.org/ubuntu/installing/#installing_with_synaptic")

---

### Post by weh on 2008-04-10
That envy script should do the job.  I've got Hardy amd64 running on my Compaq f730us with that same graphics card, and I got it to work using Envy.  Don't give up on 64-bit. :) This forum is great, and the people are very helpful.

---

### Post by Bookmaster on 2008-04-11
I did try that envy but couldn't install it. Here is message from my Ubuntu :(

Any advice please?

---

### Post by LoneWolfJack on 2008-04-11
open a terminal window and type

[HTML]sudo apt-get install debhelper[/HTML]

then try again

---

### Post by Bookmaster on 2008-04-18
Still nothing. I just cannot install driver for my GeForce Go 6100 on Ubuntu amd 64 desktop version 7.10

Does anybody have any other advice please?

Another vierd thing is that I cannot install additional codecs for mp3 or divx files.


Is it better if I leave amd 64 and go for i386 platform?

---

### Post by Artemis3 on 2008-04-18
For mp3 etc you have to install ubuntu-restricted-extras.
For java in Firefox Install icedtea-java7-plugin.
To watch videos Install VLC media player and or Mplayer.

---

### Post by LoneWolfJack on 2008-04-18
> Still nothing.

Could you be less specific?

Are you still getting the error about the missing dependency?

---

### Post by Bookmaster on 2008-04-18
Another question:

Whatever I want to install from Ubuntu addons it says that is not for amd 64.

Is it better if I install i386 version please?

---

### Post by Bookmaster on 2008-04-18
> **LoneWolfJack said:**
> Could you be less specific?

Are you still getting the error about the missing dependency?

Yes all the time.

Now is enough. I'm going to install i386 version over amd64. If I try to install it over existing amd64 version will I loose dual boot on my lap top?

I have installed Winxp pro and Ubuntu amd64 v 7,10.

---

### Post by Rhubarb on 2008-04-18
Before you do anything it's very important to back up any documents / media that's important to you, as there's always a chance you could wipe the hard drive clean by accident.

By all means try 32bit, but there will be very little difference between 32 and 64bit.

---

### Post by Bookmaster on 2008-04-18
When I try to install automatix2 I'm getting error: Dependency is not satisfiable: tango-icon-theme-common

When I try to install envy I'm getting error: Dependency is not satisfiable: phyton2,4

When I try to install etc.... every time I'm getting different error messages.

If I go to i386 Ubuntu will that solve my problems please?

---

### Post by Kilz on 2008-04-18
> **Rhubarb said:**
> By all means try 32bit, **but there will be very little difference between 32 and 64bit**.
That is misinformation.  That depends on the uses the user makes of their computer. You cant make a blanket statement like that.


> **Bookmaster said:**
> When I try to install automatix2 I'm getting error: Dependency is not satisfiable: tango-icon-theme-common

When I try to install envy I'm getting error: Dependency is not satisfiable: phyton2,4

When I try to install etc.... every time I'm getting different error messages.

If I go to i386 Ubuntu will that solve my problems please?

No, it wont
[URL="http://packages.ubuntu.com/gutsy/tango-icon-theme-common"]
tango-icon-theme-common is available[/URL] but I [wouldnt install automatix.]("http://mjg59.livejournal.com/77440.html")
[Python is available.]("http://packages.ubuntu.com/gutsy/python")
These pages linked to are official Ubuntu pages to show what is in the repositories. They are avilable as All, meaning all versions have them. My guess is that you have a messed up /etc/apt/sources.list . Please copy/paste it to a reply.

---

### Post by Akita on 2008-04-18
64-bit recognised and let me switch to the proprietary nVidia driver on my Turion lappy with a Go7600 chipset.  Strange that it wouldn't detect the Go6xxx.

---

### Post by Jouke74 on 2008-04-18
The simple problem of Bookmaster is that he does not seem to fully understand how to install software... That and he wants a quick fix for his drivers. AMD64 or i386 won't change that, at least drastically.

Let me have an attempt...

Unlike windows install.exe's you should not download a single DEB package and double click it. It comes close, but it fails to install the dependencies which are not present in the DEB, which is also the error that you are getting. To install the dependencies (name says it all, the software is dependent on it) you need to install other software, namely the DEBS which have the dependencies :-) As a result you keep downloading different debs until your whole dependency tree is complete (the dependency hell). 

Also DEBS come in various tastes: ALL, AMD64, and I386 versions. AMD64 is for 64 bit , i386 is for the 32 bit and ALL is for both. If you attempt to install a i386 DEB on an AMD64 structure it will complain about the architecture. So match your "bits / deb extensions" with the version you downloaded (for now AMD64 / and yes there are exceptions).

First Bookmaster needs to make sure he has connection to the internet from within Ubuntu, if not, life will be more difficult and he needs to make sure he has internet connection first (I don't mean booting into windows and going from there). The easiest and most familiar way to check this is with the Firefox browser. See if you can get to [www.google.nl](www.google.nl) or fill in whatever country code behind Google you want. If this is not working, ie. connection not found get back here and write that your Ubuntu internet is not working. If it is continue, or check your mail first :-) 

With internet? Now I assume that you did not mess with the repositories yet. If you did, go again to system > administration > Software sources and in the Ubuntu Software tab check all but the source code (Main, Universe , Restricted, Multiverse). If you wish you could disable the CDRom. If you change things it will complain that the (software) repostories have changed and you need to reload (read resync) your list with the list at the Ubuntu software server from which you will start downloading your DEB packages.

Now to install software (the non-commandline way) go to Go to System > administration > synaptic package manager. Click it and do reload. It should state downloading package information... And then you can select all the software you want to install. To install  dependencies just search for the name of the package that you are missing. Continue until you have all the packages installed you want, or select them all at once, and install then. Reading the help of this program and the Wiki might give you some more insight into this as well. 
I suggest you start with installing the "build-essential". That will save you some problems later on. Build essential should also indicate how synaptic deals with the dependencies. Ie, they are automagically selected from here and installed. 

Drivers: 
Afterwards go to System > administration > Restricted drivers manager. And see if you can activate your Nvidia driver from there (for now). Get to know the system and then start messing with Envy or restricted driver updates. Envy and Automatix are basically external script programs which install software for you. And go through difficult steps automatically. The problem which Kilz is refering to is, that if for some reason an error is coccuring, because there is something different on your system, then these scripts might not solve this problem. AND you won't see the error occuring. If you install stuff manually, you do see these errors and it is up to you to deal with it. ....

pff. long post.

Best of luck, JJ.

---

### Post by jocko on 2008-04-18
> **Jouke74 said:**
> To install  dependencies just search for the name of the package that you are missing. Continue until you have all the packages installed you want, or select them all at once, and install then.

Actually, it's a lot easier than that. If you try to install a package through synaptic (or any of the other ways to use apt) it will automatically get all the dependencies. No need to find them one by one. Even the restricted-manager gets the dependencies.

---

### Post by Jouke74 on 2008-04-18
That was what I was saying about one paragraph lower.... 

"I suggest you start with installing the "build-essential". That will save you some problems later on. Build essential should also indicate how synaptic deals with the dependencies. Ie, they are automagically selected from here and installed."

---

### Post by Kilz on 2008-04-18
> **jocko said:**
> Actually, it's a lot easier than that. If you try to install a package through synaptic (or any of the other ways to use apt) it will automatically get all the dependencies. No need to find them one by one. Even the restricted-manager gets the dependencies.

But if you dont have an internet connection ( a good possibility) and you downloaded and transfered one package, it isnt going to work. It isnt going to work if you are running the 32bit version either. The other possibility is that the sources list is messed up ( a good possibility of a failed automatix install). Either way its fixable if the original poster comes back and posts.

---

### Post by Roberticus on 2008-04-18
> **Rhubarb said:**
> By all means try 32bit, but there will be very little difference between 32 and 64bit.
Nope, big difference when eg. using Gimp, all the effects and plugins are 10x faster in 64bit. Try Line Nova and you'll see what I mean ;)

Use either Add/Remove (found in Applications menu) or Synaptic Package Manager (admin menu) to install software in 64bit Ubuntu. That's what I did and it works flawlessly :P

As for the Geforce 6xxx, what did Restricted Hardware say? The green card icon? Says something about proprietary drivers? Install them, unless you want to use free open drivers.

---

### Post by Bookmaster on 2008-04-21
> As for the Geforce 6xxx, what did Restricted Hardware say? The green card icon? Says something about proprietary drivers? Install them, unless you want to use free open drivers.



Here is what I'm getting

---

### Post by Kilz on 2008-04-21
> **Bookmaster said:**
> Here is what I'm getting

1. Do you have an internet connection working in Ubuntu?
2. If you have internet, open a terminal and type in ```
gedit /etc/apt/sources.list
```
The text editor will open, copy the contents of the file to a post here.

---

### Post by Jouke74 on 2008-04-21
I guess he has internet, since he is downloading packages and updating his system in his screenshots. But something definitively is messed up completely if his dependency problems are lib6c related, which is one of the main system libraries. That means he is using packages of a newer or older Ubuntu version to install. His sources list might indeed be very helpfull.

---

### Post by dptxp on 2008-04-21
I use 64-bit Ubuntu and 64-bit sidux. Everything works including Flash, ndiswrapper, wine.
ATI Graphics, Atheros wifi, ENE cardreader, GAMBAS, ........

What does not work for you ?

---

### Post by Bookmaster on 2008-04-22
Here is what I'm getting:


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

And yes I have working internet connection.

---

### Post by FredB on 2008-04-22
Remove # on every single line following the one that says :

> # Line commented out by installer because it failed to verify:

---

### Post by Bookmaster on 2008-04-23
> **FredB said:**
> Remove # on every single line following the one that says :

I didn't quite understand what do I have to do please?

---

### Post by LoneWolfJack on 2008-04-23
change

```
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
```

to

```
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
```

repeat for all lines after "# Line commented out by installer because it failed to verify:" that start with "deb"

---

### Post by Bookmaster on 2008-04-24
I did it. Here is what I done:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


And now?

---

### Post by Bookmaster on 2008-04-24
> **dptxp said:**
> I use 64-bit Ubuntu and 64-bit sidux. Everything works including Flash, ndiswrapper, wine.
ATI Graphics, Atheros wifi, ENE cardreader, GAMBAS, ........

What does not work for you ?

Following things are not working for me:

- cannot install NVidia GeForce GO 6100 driver
- cannot play mp3 files. It asks for suitable codecs (e.g. GStreamer extra plugins) which it cannot allows me to install.
- cannot install modem drivers as well :(

---

### Post by Kilz on 2008-04-24
> **Bookmaster said:**
> Following things are not working for me:

- cannot install NVidia GeForce GO 6100 driver
- cannot play mp3 files. It asks for suitable codecs (e.g. GStreamer extra plugins) which it cannot allows me to install.
- cannot install modem drivers as well :(

You only uncommented 3/4ths of the lines in your last post.

---

### Post by Bookmaster on 2008-04-24
> **Bookmaster said:**
> Following things are not working for me:

- cannot install NVidia GeForce GO 6100 driver
- cannot play mp3 files. It asks for suitable codecs (e.g. GStreamer extra plugins) which it cannot allows me to install.
- cannot install modem drivers as well :(

mp3 files solved.

still cannot install modem drivers and NVidia GeForce GO 6100 drivers :(

---

### Post by philinux on 2008-04-24
> **Kilz said:**
> You only uncommented 3/4ths of the lines in your last post.

Like kilz said you're sources list needs attention.

---

