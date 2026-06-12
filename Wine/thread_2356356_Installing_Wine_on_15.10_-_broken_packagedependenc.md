---
title: "Installing Wine on 15.10 - broken package/dependency errors"
date: 2017-03-22
forum: Wine
---

### Post by chellrose on 2017-03-22
I have a fresh install of Ubuntu 15.10.  I am trying to install Wine, and have so far tried 3 methods:

1) ```
sudo apt-get install wine
```
2) The [ubuntu-wine repository]("http://ubuntuhandbook.org/index.php/2015/12/install-wine-1-8-stable-new-ppa/")
3) The [official Wine HQ repository]("https://wiki.winehq.org/Ubuntu")

I have tried suggestions [here]("https://ubuntuforums.org/showthread.php?t=2284456"), [here]("https://forum.winehq.org/viewtopic.php?f=2&t=27246"), and [here]("https://ubuntuforums.org/showthread.php?t=2334177") to no avail.  I have added the i386 architecture via ```
sudo dpkg --add-architecture i386
``` and have verified that all of my software sources are for wily.  I currently have only the Wine HQ ppa (I removed the Ubuntu-wine ppa) and am trying to install from there.

Command:
```

 sudo apt-get install --install-recommends winehq-devel 
```

Result: [https://paste.ubuntu.com/24228453/](https://paste.ubuntu.com/24228453/)

   
Command:
```
sudo apt-get install --install-recommends wine-devel
```

Result: [https://paste.ubuntu.com/24228457/](https://paste.ubuntu.com/24228457/)

   
I am able to install wine-devel-amd64.  However, the i386 version creates errors:

Command:
```
sudo apt-get install --install-recommends wine-devel-i386
```

Result: [https://paste.ubuntu.com/24228465/](https://paste.ubuntu.com/24228465/)

   
And lastly, I tried using aptitude rather than apt-get as suggested in the first thread linked above:

```
sudo aptitude install wine-devel-i386
```

Result: [https://paste.ubuntu.com/24228469/](https://paste.ubuntu.com/24228469/)

   
Please help.   [IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABkAAAAPCAMAAAAmuJTXAAAALVBMVEUAAABFRUXKIgL nQD/tAD/zgD/6gD//RO9v7X//pP//8f// v8A/sAAAD///8sSPs8AAAADXRSTlP///////////////8APegihgAAAHVJREFUeJx1kFEOgDAIQ lwINP7n1c2nYLG97XspaQpFWd/QGe8aHXC/9bM6nBUynpn/F9VRCojGzQjErlUvAZTuajomdkATYWmYURjwSwI12By083TAPprajCM1I1ots7dPOQpGoKz6epkbPDabXH4u1va gBHqwqmUerTOAAAAABJRU5ErkJggg==[/IMG]  Thanks!

(Sorry for all the pastebins, it's the only way I could get the thread to post without error.)

---

### Post by howefield on 2017-03-22
Thread moved to the "*Wine*" forum for a better fit.

---

### Post by jeremy31 on 2017-03-22
Ubuntu 15.10 is no longer supported and the update servers are shut down.  Consider upgrading to Ubuntu 16.04.1 as it will be supported until 2021

---

### Post by chellrose on 2017-03-22
Thanks.  Unfortunately, I have to have fglrx/amdcccle in order to make my graphics card and TV play nicely together.  (The open-source driver doesn't work for my particular setup.)  So unfortunately, upgrading isn't an option for me.

Updated information: after doing some more reading, I tried installing wine via synaptic package manager.

If I choose to install ordinary "wine", Synaptic just tells me the package is broken.

However, if I mark "wine-hq-devel" for installation, it gives me a warning about removing packages.  Synaptic says that in order to install wine-hq-devel, it needs to remove (among others) fglrx-core and amdcccle.  I need these packages for my graphics card/TV setup, so having them removed isn't an option.

I don't have to have the latest development version of Wine; I would be content with whatever version is in the wily repositories.  However, ```
sudo apt-get install wine
``` has similar dependency problems to those I listed above.

---

### Post by howefield on 2017-03-22
I'm not sure if purging all that you have done with regards wine and changing your repository souces to point to "old-releases" would then allow you to install the wine1.6 package that came with 15.10 or not.

An alternative might be to install 14.04.5 which is supported till 2019 and will be able make use of the fglrx ect packages.

---

### Post by chellrose on 2017-03-22
How do I make the repository sources point to old-releases?  I tried ```
sudo add-apt-repository old-releases.ubuntu.com
``` and it said it was invalid.

---

### Post by howefield on 2017-03-22
> **chellrose said:**
> How do I make the repository sources point to old-releases?

Sorry, I think I'd recant the suggestion of using old-releases back. I don't see any mention of wily at [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/).

What does..

```
sudo apt-get install wine1.6
```

give you ?

---

### Post by chellrose on 2017-03-22
That gives me

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu10)
E: Unable to correct problems, you have held broken packages.


```

and ```
sudo apt-get install wine 1.6-i386
```

gives

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.6-i386:i386 : Depends: libasound2:i386 (>= 1.0.16)
                     Depends: libc6:i386 (>= 2.17) but it is not going to be installed
                     Depends: libglib2.0-0:i386 (>= 2.12.0) but it is not going to be installed
                     Depends: libglu1-mesa:i386 but it is not going to be installed or
                              libglu1:i386
                     Depends: libgphoto2-6:i386 (>= 2.5.2) but it is not going to be installed
                     Depends: libgphoto2-port12:i386 (>= 2.5.6) but it is not going to be installed
                     Depends: libgstreamer-plugins-base0.10-0:i386 (>= 0.10.22) but it is not going to be installed
                     Depends: libgstreamer0.10-0:i386 (>= 0.10.26) but it is not going to be installed
                     Depends: liblcms2-2:i386 (>= 2.2+git20110628) but it is not going to be installed
                     Depends: libldap-2.4-2:i386 (>= 2.4.7) but it is not going to be installed
                     Depends: libmpg123-0:i386 (>= 1.13.7) but it is not going to be installed
                     Depends: libopenal1:i386 (>= 1.14) but it is not going to be installed
                     Depends: libx11-6:i386 but it is not going to be installed
                     Depends: libxext6:i386 but it is not going to be installed
                     Depends: libxml2:i386 (>= 2.9.0) but it is not going to be installed
                     Depends: ocl-icd-libopencl1:i386 but it is not going to be installed or
                              libopencl1:i386
                     Depends: ocl-icd-libopencl1:i386 (>= 1.0) but it is not going to be installed or
                              libopencl-1.1-1:i386
                     Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
                     Depends: libncurses5:i386 but it is not going to be installed
                     Recommends: libasound2-plugins:i386 but it is not going to be installed
                     Recommends: libcapi20-3:i386 but it is not going to be installed
                     Recommends: libcups2:i386 but it is not going to be installed
                     Recommends: libdbus-1-3:i386 but it is not going to be installed
                     Recommends: libfontconfig1:i386 but it is not going to be installed or
                                 libfontconfig:i386
                     Recommends: libfreetype6:i386 but it is not going to be installed
                     Recommends: libgif4:i386 but it is not going to be installed
                     Recommends: libgnutls-deb0-28:i386 but it is not going to be installed
                     Recommends: libjpeg8:i386 but it is not going to be installed
                     Recommends: libosmesa6:i386 but it is not going to be installed
                     Recommends: libp11-kit-gnome-keyring:i386 but it is not going to be installed
                     Recommends: libpng12-0:i386 but it is not going to be installed
                     Recommends: libpulse0:i386 but it is not going to be installed
                     Recommends: libsane:i386 but it is not going to be installed
                     Recommends: libtiff5:i386 but it is not going to be installed
                     Recommends: libv4l-0:i386 but it is not going to be installed
                     Recommends: libxcomposite1:i386 but it is not going to be installed
                     Recommends: libxcursor1:i386 but it is not going to be installed
                     Recommends: libxi6:i386 but it is not going to be installed
                     Recommends: libxinerama1:i386 but it is not going to be installed
                     Recommends: libxrandr2:i386 but it is not going to be installed
                     Recommends: libxrender1:i386 but it is not going to be installed
                     Recommends: libxslt1.1:i386 but it is not going to be installed
                     Recommends: libxt6:i386 but it is not going to be installed
                     Recommends: libxxf86vm1:i386 but it is not going to be installed
                     Recommends: p11-kit-modules:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Edit: I've reinstalled 14.04 and have Wine and fglrx working.  Thanks for your help! :)

---

