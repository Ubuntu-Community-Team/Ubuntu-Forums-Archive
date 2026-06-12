---
title: "Installing wine is not possible"
date: 2013-11-15
forum: Wine
---

### Post by freakyhorst on 2013-11-15
Hi,

I'm currently running a fresh Ubuntu Saucy and trying to install wine.

After reading online that there will be some archtitecture problems, I started like this:
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install wine1.4

```
But the install command gives me an error:
```
The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu7)
E: Unable to correct problems, you have held broken packages.

```

Next, i tried installing from ppa:
```
sudo apt-get install ppa-purge
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install wine1.7

```
Which will give me a similar error:
```
The following packages have unmet dependencies:
 wine1.7 : Depends: wine1.7-i386 (= 1.7.4-0ubuntu4~saucy1)
E: Unable to correct problems, you have held broken packages.

```

Trying to install wine1.7-i386 will lead to other unmet dependencies which I can't resolve!

Does anybody have any ideas?? I'm out of luck on this one ...

---

### Post by deadflowr on 2013-11-15
Try running
```
sudo apt-get -f install
```
See if and what those broken packages are.

I'm guessing you're running 64-bit.
In that case wine will install just normally.
I've never used the arch flag to point to i386 and wine works fine on a 64-bit.
```
sudo apt-get install wine winetricks
```
is usually good enough.

Whether installing apps in wine works is another matter entirely.

---

### Post by freakyhorst on 2013-11-15
> **deadflowr said:**
> Try running
```
sudo apt-get -f install
```
See if and what those broken packages are.


*sudo apt-get -f install wine* will give me the usual output:
```
The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```


> **deadflowr said:**
> 
I'm guessing you're running 64-bit.


Indeed!

> **deadflowr said:**
> 
```
sudo apt-get install wine winetricks
```
is usually good enough.

Usually it works quite flawless!

If I try to install *wine1.7-i386* directly I'll get this output:
```
The following packages have unmet dependencies:
 wine1.7-i386:i386 : Depends: libgphoto2-6:i386 (>= 2.4.10.1) but it is not going to be installed
                     Depends: libgphoto2-port10:i386 (>= 2.5.2) but it is not going to be installed
                     Recommends: libsane:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by deadflowr on 2013-11-15
No.
Don't add wine to the apt-get -f install command.
run that as I left it.
```
sudo apt-get -f install
```
This command tries to fix broken packages.

---

### Post by freakyhorst on 2013-11-15
> **deadflowr said:**
> No.
Don't add wine to the apt-get -f install command.
run that as I left it.
```
sudo apt-get -f install
```
This command tries to fix broken packages.

Output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Edit: No change after an upgrade either

---

### Post by Bucky Ball on 2013-11-15
Just wondering: Did you try installing it from the repositories first? It's in there (Software Centre).

---

### Post by freakyhorst on 2013-11-15
> **Bucky Ball said:**
> Just wondering: Did you try installing it from the repositories first? It's in there (Software Centre).

Jep, did it before. But with the same error.

---

### Post by deadflowr on 2013-11-15
By upgrade, I hope you mean
```
sudo apt-get upgrade
```
and not
```
sudo apt-get update
```
The upgrade command will actually upgrade the system, where as the update command updates the packages the system can get.

---

### Post by freakyhorst on 2013-11-15
Yes I *upgraded* it.

---

### Post by ian-weisser on 2013-11-15
> **freakyhorst said:**
> If I try to install *wine1.7-i386* directly I'll get this output:
```
The following packages have unmet dependencies:
 wine1.7-i386:i386 : Depends: libgphoto2-6:i386 (>= 2.4.10.1) but it is not going to be installed
                     Depends: libgphoto2-port10:i386 (>= 2.5.2) but it is not going to be installed
                     Recommends: libsane:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

> **freakyhorst said:**
> Jep, did it before. But with the same error.

First, do recognize that the PPA version of wine is supported by the PPA maintainers...not by the community. The community supports software in the Ubuntu Repositories (PPAs are not in there).
Add PPAs at your own risk. Most of the broken Package Managers that I see are due to PPAs. 

Second, we need to get your package manager working again.
Disable the PPA (do you know how?)
Purge all PPA packages that did install. (do you need help locating them?)
Undo the --add-architecture=i386
Confirm that your package manager is working with a **sudo apt-get update && sudo apt-get upgrade**

Third, after your package manager is working properly try adding wine again
First try **sudo apt-get install wine**
If you get error messages, show us the session

---

### Post by freakyhorst on 2013-11-15
Getting rid of the wine-ppa (there is nothing installed from it)
```
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-saucy.list*
```

```
sudo dpkg --remove-architecture i386
```
Did give me an error:```
dpkg: error: cannot remove architecture 'i386' currently in use by the database
```
So i manually removed 'i386' from */var/lib/dpkg/arch*


```
sudo apt-get update && sudo apt-get upgrade
```
... showed the usual (clean update, no upgrade needed)

Finally:
```
sudo apt-get install wine
```
... gives me the same error again:
```
The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

:(

Any other ideas?

---

### Post by ian-weisser on 2013-11-15
Two things to try:

**sudo dpkg --configure -a**
This may clarify the dependency problem

[B]dpkg -l | grep wine
[/B]This will tell us if any wine packages are (unexpectedly, unknowingly) installed...causing the problem.

---

### Post by freakyhorst on 2013-11-16
> **ian-weisser said:**
> 
**sudo dpkg --configure -a**
This may clarify the dependency problem

[B]dpkg -l | grep wine
[/B]This will tell us if any wine packages are (unexpectedly, unknowingly) installed...causing the problem.

Neither of the commands showed any output.


I followed the trail of unmet dependencies and in the end 'wine1.4-i386' seems to be missing:```
E: Package 'wine1.4-i386' has no installation candidate
```

---

### Post by ian-weisser on 2013-11-16
Run **sudo apt-get -f install** to get a detailed error message on the problem. Please show us the entire session.

---

### Post by freakyhorst on 2013-11-17
OK ... by re-enabling i386-architecture I was able to follow the dependencies further.

The entire session:
```

horst@CFB:~$ **sudo dpkg --add-architecture i386**
horst@CFB:~$ **sudo dpkg --print-architecture**
amd64
horst@CFB:~$ **sudo dpkg --print-foreign-architectures**
i386
horst@CFB:~$ **sudo apt-get update**
Ign http://archive.canonical.com saucy InRelease
Ign http://de.archive.ubuntu.com saucy InRelease                                     
Ign http://extras.ubuntu.com saucy InRelease                                         
Hit http://archive.canonical.com saucy Release.gpg                                   
Hit http://de.archive.ubuntu.com saucy Release.gpg                                                    
Get:1 http://extras.ubuntu.com saucy Release.gpg [72 B]                                               
Hit http://de.archive.ubuntu.com saucy Release                                                                                       
Hit http://archive.canonical.com saucy Release                                                        
Hit http://extras.ubuntu.com saucy Release                                                             
Hit http://de.archive.ubuntu.com saucy/main Sources                                                                          
Hit http://archive.canonical.com saucy/partner amd64 Packages                                         
Hit http://extras.ubuntu.com saucy/main amd64 Packages                                                
Hit http://de.archive.ubuntu.com saucy/restricted Sources                                             
Get:2 http://archive.canonical.com saucy/partner i386 Packages [3.150 B]                              
Get:3 http://extras.ubuntu.com saucy/main i386 Packages [14 B]                                        
Hit http://de.archive.ubuntu.com saucy/universe Sources                                                           
Hit http://de.archive.ubuntu.com saucy/multiverse Sources                                  
Hit http://de.archive.ubuntu.com saucy/main amd64 Packages           
Hit http://repo.steampowered.com precise InRelease                   
Hit http://de.archive.ubuntu.com saucy/restricted amd64 Packages                              
Hit http://de.archive.ubuntu.com saucy/universe amd64 Packages       
Hit http://de.archive.ubuntu.com saucy/multiverse amd64 Packages
Get:4 http://de.archive.ubuntu.com saucy/main i386 Packages [1.238 kB]
Hit http://repo.steampowered.com precise/steam amd64 Packages                                        
Ign http://archive.canonical.com saucy/partner Translation-en_US                                     
Ign http://extras.ubuntu.com saucy/main Translation-en_US                                                      
Ign http://archive.canonical.com saucy/partner Translation-en                                                  
Ign http://extras.ubuntu.com saucy/main Translation-en                                                         
Get:5 http://repo.steampowered.com precise/steam i386 Packages [806 B]          
Get:6 http://de.archive.ubuntu.com saucy/restricted i386 Packages [9.688 B]     
Get:7 http://de.archive.ubuntu.com saucy/universe i386 Packages [5.652 kB]  
Ign http://repo.steampowered.com precise/steam Translation-en_US                                                                                                                                                                            
Get:8 http://de.archive.ubuntu.com saucy/multiverse i386 Packages [133 kB]                                                                                                                                                                  
Ign http://repo.steampowered.com precise/steam Translation-en                                                                                                                                                                               
Hit http://de.archive.ubuntu.com saucy/main Translation-en                                                                                                                                                                                  
Hit http://de.archive.ubuntu.com saucy/multiverse Translation-en                                                                                                                                                                            
Hit http://de.archive.ubuntu.com saucy/restricted Translation-en                                                                                                                                                                            
Hit http://de.archive.ubuntu.com saucy/universe Translation-en                                                                                                                                                                              
Ign http://de.archive.ubuntu.com saucy/main Translation-en_US                                                                                                                                                                               
Ign http://de.archive.ubuntu.com saucy/multiverse Translation-en_US                                                                                                                                                                         
Ign http://de.archive.ubuntu.com saucy/restricted Translation-en_US                                                                                                                                                                         
Ign http://de.archive.ubuntu.com saucy/universe Translation-en_US                                                                                                                                                                           
Fetched 7.036 kB in 10s (642 kB/s)                                                                                                                                                                                                          
Reading package lists... Done

horst@CFB:~$ **sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

horst@CFB:~$ **sudo apt-get -f install wine**
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

horst@CFB:~$ **sudo apt-get -f install wine1.4**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu7)
E: Unable to correct problems, you have held broken packages.

horst@CFB:~$ **sudo apt-get -f install wine1.4-i386**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4-i386:i386 : Depends: libgphoto2-6:i386 (>= 2.4.10.1) but it is not going to be installed
                     Depends: libgphoto2-port10:i386 (>= 2.5.2) but it is not going to be installed
                     Recommends: libsane:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

horst@CFB:~$ **sudo apt-get -f install libgphoto2-port10:i386**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgphoto2-port10:i386 : Depends: libusb-1.0-0:i386 (>= 2:1.0.8) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

horst@CFB:~$ **sudo apt-get -f install libusb-1.0-0:i386**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libusb-1.0-0:i386 : Depends: libudev1:i386 (>= 183) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

horst@CFB:~$ **sudo apt-get -f install libudev1:i386**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  efibootmgr linux-headers-generic python-cddb python-gst0.10 python-mmkeys python-mutagen
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
 
############ 100+ Packages I really like to keep! ############

The following NEW packages will be installed:
  libudev1:i386
0 upgraded, 1 newly installed, 265 to remove and 0 not upgraded.
Need to get 37,1 kB of archives.
After this operation, 440 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

As you see it comes down to libudev1:i386, which would remove the entire productive system

---

### Post by freakyhorst on 2013-11-17
Alright ... I think I got it...

_What I did from the beginning:_

This site: [https://wiki.debian.org/Multiarch/HOWTO](https://wiki.debian.org/Multiarch/HOWTO) suggests to make /etc/apt/sources.list support multiarch by adding* [arch=amd64,i386]* to the deb-line. e.g.:
```

deb [arch=amd64,i386] http://de.archive.ubuntu.com/ubuntu/ saucy universe

```

Next I added the PPA again (because I need the newest Version of wine) and took care that dpkg recognizes i386.
```

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo dpkg --add-architecture i386
sudo apt-get update

```
Update of the database now showed separate amd64 and i386 repos to be loaded.


Next I switched to aptitude, because of the more sophisticated dependency-solver:
```

**sudo aptitude --full-resolver -f install wine1.7**
The following NEW packages will be installed:
  binfmt-support{a} fonts-horai-umefont{a} fonts-unfonts-core{a} gnome-exe-thumbnailer{a} icoutils{a} imagemagick{a} imagemagick-common{a} libasn1-8-heimdal:i386{a} libasound2:i386{a} 
  libasound2-plugins:i386{a} libasyncns0:i386{a} libavahi-client3:i386{a} libavahi-common-data:i386{a} libavahi-common3:i386{a} libcapi20-3{a} libcapi20-3:i386{a} libcomerr2:i386{a} 
  libcups2:i386{a} libdb5.1:i386{a} libdbus-1-3:i386{a} libexif12:i386{a} libflac8:i386{a} libfontconfig1:i386{a} libfreetype6:i386{a} libgcrypt11:i386{a} libgd3:i386{a} libgif4{a} 
  libgif4:i386{a} libglib2.0-0:i386{a} libglu1-mesa:i386{a} libgnutls26:i386{a} libgpg-error0:i386{a} libgphoto2-6:i386{a} libgphoto2-port10:i386{a} libgpm2:i386{a} 
  libgssapi-krb5-2:i386{a} libgssapi3-heimdal:i386{a} libgstreamer-plugins-base0.10-0:i386{a} libgstreamer0.10-0:i386{a} libhcrypto4-heimdal:i386{a} libheimbase1-heimdal:i386{a} 
  libheimntlm0-heimdal:i386{a} libhx509-5-heimdal:i386{a} libice6:i386{a} libieee1284-3:i386{a} libjack-jackd2-0:i386{a} libjbig0:i386{a} libjpeg-turbo8:i386{a} libjpeg8:i386{a} 
  libjson-c2:i386{a} libk5crypto3:i386{a} libkeyutils1:i386{a} libkrb5-26-heimdal:i386{a} libkrb5-3:i386{a} libkrb5support0:i386{a} liblcms2-2:i386{a} libldap-2.4-2:i386{a} 
  liblqr-1-0{a} libltdl7:i386{a} liblzma5:i386{a} libmagickcore5{a} libmagickcore5-extra{a} libmagickwand5{a} libmpg123-0:i386{a} libncurses5:i386{a} libnetpbm10{a} libodbc1{a} 
  libogg0:i386{a} libopenal1:i386{a} liborc-0.4-0:i386{a} libosmesa6{a} libosmesa6:i386{a} libp11-kit0:i386{a} libpcre3:i386{a} libpng12-0:i386{a} libpulse0:i386{a} 
  libroken18-heimdal:i386{a} libsamplerate0:i386{a} libsane:i386{a} libsasl2-2:i386{a} libsasl2-modules:i386{a} libsasl2-modules-db:i386{a} libselinux1:i386{a} libsm6:i386{a} 
  libsndfile1:i386{a} libspeexdsp1:i386{a} libsqlite3-0:i386{a} libssl1.0.0:i386{a} libtasn1-3:i386{a} libtiff5:i386{a} libtinfo5:i386{a} libudev1:i386{ab} libusb-1.0-0:i386{a} 
  libuuid1:i386{a} libv4l-0:i386{a} libv4lconvert0:i386{a} libvorbis0a:i386{a} libvorbisenc2:i386{a} libvpx1:i386{a} libwind0-heimdal:i386{a} libwrap0:i386{a} libxcomposite1:i386{a} 
  libxcursor1:i386{a} libxi6:i386{a} libxinerama1:i386{a} libxml2:i386{a} libxpm4:i386{a} libxrandr2:i386{a} libxrender1:i386{a} libxslt1.1:i386{a} libxt6:i386{a} netpbm{a} odbcinst{a} 
  odbcinst1debian2{a} unixodbc{a} winbind{a} wine-gecko2.24{a} wine-gecko2.24:i386{a} wine-mono0.0.8{a} wine1.7 wine1.7-amd64{a} wine1.7-i386:i386{a} winetricks{a} 
0 packages upgraded, 123 newly installed, 0 to remove and 0 not upgraded.
Need to get 200 MB of archives. After unpacking 557 MB will be used.
The following packages have unmet dependencies:
 libudev1 : Breaks: libudev1:i386 (!= 204-0ubuntu19) but 204-0ubuntu18 is to be installed.
 libudev1:i386 : Breaks: libudev1 (!= 204-0ubuntu18) but 204-0ubuntu19 is installed.
The following actions will resolve these dependencies:

      Keep the following packages at their current version:                  
1)      libgphoto2-6:i386 [Not Installed]                                    
2)      libgphoto2-port10:i386 [Not Installed]                               
3)      libsane:i386 [Not Installed]                                         
4)      libudev1:i386 [Not Installed]                                        
5)      libusb-1.0-0:i386 [Not Installed]                                    
6)      wine1.7 [Not Installed]                                              
7)      wine1.7-amd64 [Not Installed]                                        
8)      wine1.7-i386:i386 [Not Installed]                                    

      Leave the following dependencies unresolved:                           
9)      winetricks recommends wine1.5 | wine1.4 | wine | cxoffice5 | cxgames5
10)     wine-gecko2.24 recommends wine1.5-amd64                              
11)     wine1.7-i386:i386 recommends libsane:i386                            
12)     wine-gecko2.24:i386 recommends wine1.5-i386:i386                     

Accept this solution? [Y/n/q/?] 6
Action "6": Removing wine1.7

Package: wine1.7
New: yes
State: not installed; will be installed automatically
Multi-Arch: allowed
Version: 1.7.4-0ubuntu4~saucy1
Priority: optional
Section: otherosfs
Maintainer: Scott Ritchie <scottritchie@ubuntu.com>
Architecture: amd64
Uncompressed Size: 6.255 k
Depends: debconf (>= 0.5) | debconf-2.0, libc6 (>= 2.17), libgettextpo0, wine1.7-amd64 (= 1.7.4-0ubuntu4~saucy1), binfmt-support (>= 1.1.2), procps, wine1.7-i386 (= 1.7.4-0ubuntu4~saucy1)
PreDepends: dpkg (>= 1.15.7.2~)
Recommends: cups-bsd, gnome-exe-thumbnailer | kde-runtime, fonts-droid, fonts-liberation, ttf-mscorefonts-installer, fonts-horai-umefont, fonts-unfonts-core, ttf-wqy-microhei, winbind,
            winetricks, xdg-utils
Suggests: dosbox:any
Conflicts: wine1.0, wine1.0, wine1.2, wine1.2, wine1.3, wine1.3, wine1.4, wine1.4, wine1.7
Replaces: wine, wine, wine1.0, wine1.0, wine1.2, wine1.2, wine1.3, wine1.3, wine1.4, wine1.4, wine1.5, wine1.5, wine1.6, wine1.6
Provides: wine, wine1.7:any
Description: Microsoft Windows Compatibility Layer (Binary Emulator and Library)
 Wine is a compatibility layer for running Windows applications on Linux. Applications are run at full speed without the need of cpu emulation. Wine does not require Microsoft Windows,
 however it can use native system dll files in place of its own if they are available. 
 
 This package includes a program loader for running unmodified Windows executables as well as the Wine project's free version of the Windows API for running programs ported from Windows.


This action was selected because wine1.7 depends upon wine1.7-i386 (= 1.7.4-0ubuntu4~saucy1).

Enter "r 6" to prevent this action from appearing in new solutions.
Enter "a 6" to require that new solutions include this action if possible.

Accept this solution? [Y/n/q/?] r 6
Rejecting the removal of wine1.7
The following actions will resolve these dependencies:

      Keep the following packages at their current version:                  
1)      libgphoto2-6:i386 [Not Installed]                                    
2)      libgphoto2-port10:i386 [Not Installed]                               
3)      libsane:i386 [Not Installed]                                         
4)      libudev1:i386 [Not Installed]                                        
5)      libusb-1.0-0:i386 [Not Installed]                                    
6)  R   wine1.7 [Not Installed]                                              
7)      wine1.7-amd64 [Not Installed]                                        
8)      wine1.7-i386:i386 [Not Installed]                                    

      Leave the following dependencies unresolved:                           
9)      winetricks recommends wine1.5 | wine1.4 | wine | cxoffice5 | cxgames5
10)     wine-gecko2.24 recommends wine1.5-amd64                              
11)     wine1.7-i386:i386 recommends libsane:i386                            
12)     wine-gecko2.24:i386 recommends wine1.5-i386:i386  

Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     **Downgrade** the following packages:                        
1)     libudev1 [204-0ubuntu19 (now) -> 204-0ubuntu18 (saucy)]
2)     udev [204-0ubuntu19 (now) -> 204-0ubuntu18 (saucy)]    

Accept this solution? [Y/n/q/?] Y
The following packages will be DOWNGRADED:
  libudev1 udev 
The following NEW packages will be installed:
  binfmt-support{a} fonts-horai-umefont{a} fonts-unfonts-core{a} gnome-exe-thumbnailer{a} icoutils{a} imagemagick{a} imagemagick-common{a} libasn1-8-heimdal:i386{a} libasound2:i386{a} 
  libasound2-plugins:i386{a} libasyncns0:i386{a} libavahi-client3:i386{a} libavahi-common-data:i386{a} libavahi-common3:i386{a} libcapi20-3{a} libcapi20-3:i386{a} libcomerr2:i386{a} 
  libcups2:i386{a} libdb5.1:i386{a} libdbus-1-3:i386{a} libexif12:i386{a} libflac8:i386{a} libfontconfig1:i386{a} libfreetype6:i386{a} libgcrypt11:i386{a} libgd3:i386{a} libgif4{a} 
  libgif4:i386{a} libglib2.0-0:i386{a} libglu1-mesa:i386{a} libgnutls26:i386{a} libgpg-error0:i386{a} libgphoto2-6:i386{a} libgphoto2-port10:i386{a} libgpm2:i386{a} 
  libgssapi-krb5-2:i386{a} libgssapi3-heimdal:i386{a} libgstreamer-plugins-base0.10-0:i386{a} libgstreamer0.10-0:i386{a} libhcrypto4-heimdal:i386{a} libheimbase1-heimdal:i386{a} 
  libheimntlm0-heimdal:i386{a} libhx509-5-heimdal:i386{a} libice6:i386{a} libieee1284-3:i386{a} libjack-jackd2-0:i386{a} libjbig0:i386{a} libjpeg-turbo8:i386{a} libjpeg8:i386{a} 
  libjson-c2:i386{a} libk5crypto3:i386{a} libkeyutils1:i386{a} libkrb5-26-heimdal:i386{a} libkrb5-3:i386{a} libkrb5support0:i386{a} liblcms2-2:i386{a} libldap-2.4-2:i386{a} 
  liblqr-1-0{a} libltdl7:i386{a} liblzma5:i386{a} libmagickcore5{a} libmagickcore5-extra{a} libmagickwand5{a} libmpg123-0:i386{a} libncurses5:i386{a} libnetpbm10{a} libodbc1{a} 
  libogg0:i386{a} libopenal1:i386{a} liborc-0.4-0:i386{a} libosmesa6{a} libosmesa6:i386{a} libp11-kit0:i386{a} libpcre3:i386{a} libpng12-0:i386{a} libpulse0:i386{a} 
  libroken18-heimdal:i386{a} libsamplerate0:i386{a} libsane:i386{a} libsasl2-2:i386{a} libsasl2-modules:i386{a} libsasl2-modules-db:i386{a} libselinux1:i386{a} libsm6:i386{a} 
  libsndfile1:i386{a} libspeexdsp1:i386{a} libsqlite3-0:i386{a} libssl1.0.0:i386{a} libtasn1-3:i386{a} libtiff5:i386{a} libtinfo5:i386{a} libudev1:i386{a} libusb-1.0-0:i386{a} 
  libuuid1:i386{a} libv4l-0:i386{a} libv4lconvert0:i386{a} libvorbis0a:i386{a} libvorbisenc2:i386{a} libvpx1:i386{a} libwind0-heimdal:i386{a} libwrap0:i386{a} libxcomposite1:i386{a} 
  libxcursor1:i386{a} libxi6:i386{a} libxinerama1:i386{a} libxml2:i386{a} libxpm4:i386{a} libxrandr2:i386{a} libxrender1:i386{a} libxslt1.1:i386{a} libxt6:i386{a} netpbm{a} odbcinst{a} 
  odbcinst1debian2{a} unixodbc{a} winbind{a} wine-gecko2.24{a} wine-gecko2.24:i386{a} wine-mono0.0.8{a} wine1.7 wine1.7-amd64{a} wine1.7-i386:i386{a} winetricks{a} 
0 packages upgraded, 123 newly installed, 2 downgraded, 0 to remove and 0 not upgraded.
Need to get 201 MB of archives. After unpacking 557 MB will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 http://de.archive.ubuntu.com/ubuntu/ saucy/main libgpg-error0 i386 1.12-0.2 [12,5 kB]
Get: 2 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ saucy/main wine-gecko2.24 amd64 2.24-0ubuntu1~ppa1 [23,5 MB]
...

############ The usual Stuff goes here ... ############


```

What I did in short:
- aptitude suggested a solution where *wine1.7* would not be installed
- This solution was rejected with '*r 6*'
- The new suggestion was to downgrade both *libudev1* and *udev* by one version (All dependencies met!)
- i did that! AND: it works!

---

