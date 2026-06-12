---
title: "Can't run WINE due to unresolved package dependencies"
date: 2013-01-03
forum: Wine
---

### Post by bluepop13 on 2013-01-03
I hope someone can help me here.

I'll give you the information you need as best I can.

I am trying to install wine.

1. Ubuntu software center.
2. type in Wine.
3. Click on the 5th Wine Microsoft Windows Compatibility Layer (Binary Emulator and Library)
4. Click install and put in the password.
5. An error comes up that says:

"Package Dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between sofware packages which are not allowed to be installed at this time."

6. ...Then, an error comes up that says:

"The application Ubuntu Software Center has experienced an internal error.

There was an error submitting the transaction.

Send an error report to help fix this problem."

--

What does this mean and what can I do to fix this?

Thank you for any and all help.

**P.S. I am running Ubuntu 12.10 on an HP Laptop.**

---

### Post by fdrake on 2013-01-04
open Terminal (Press Ctrl+Alt+T) ```

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine
sudo apt-get install winetricks

```
if you expirience errors copy and post them here.


google is your best friend: [http://www.noobslab.com/2012/06/install-wine-156-in-ubuntu-1204.html](http://www.noobslab.com/2012/06/install-wine-156-in-ubuntu-1204.html)

---

### Post by bluepop13 on 2013-01-04
This is what I got:

I don't know what this means or what to do from here so, once again, any advice...?

```
seel@ubuntu:~$ sudo apt-get-repository ppa:ubuntu-wine/ppa
[sudo] password for seel: 
sudo: apt-get-repository: command not found
seel@ubuntu:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
You are about to add the following PPA to your system:
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpagz69h/secring.gpg' created
gpg: keyring `/tmp/tmpagz69h/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpagz69h/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
seel@ubuntu:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed InRelease              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages        
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg [933 B]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages      
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed Release.gpg [933 B] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en            
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports Release.gpg [933 B]
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release [11.9 kB]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release [49.6 kB]     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages 
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed Release [49.6 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports Release [49.6 kB]      
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources [2429 B]
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages [3000 B]           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages [161 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages [1970 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe amd64 Packages [135 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [7936 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted amd64 Packages [14 B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main amd64 Packages [40.9 kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse amd64 Packages [14 B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe amd64 Packages [69.0 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe Translation-en         
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted amd64 Packages [14 B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main amd64 Packages [14 B]  
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse amd64 Packages [1118 B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe amd64 Packages [6741 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Translation-en        
Fetched 593 kB in 7s (76.6 kB/s)                                               
Reading package lists... Done
seel@ubuntu:~$ sudo apt-get install wine
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
E: Unable to correct problems, you have held broken packages.
seel@ubuntu:~$ sudo apt-get install winetricks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support cabextract unrar
Recommended packages:
  wine1.5 wine1.4 wine cxoffice5 cxgames5
The following NEW packages will be installed:
  binfmt-support cabextract unrar winetricks
0 upgraded, 4 newly installed, 0 to remove and 33 not upgraded.
Need to get 378 kB of archives.
After this operation, 1332 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe cabextract amd64 1.4-3 [42.8 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe winetricks amd64 0.0+20120912 [148 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main binfmt-support amd64 2.0.12 [79.6 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/multiverse unrar amd64 1:4.1.4-1 [108 kB]
Fetched 378 kB in 1s (222 kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously unselected package cabextract.
(Reading database ... 212255 files and directories currently installed.)
Unpacking cabextract (from .../cabextract_1.4-3_amd64.deb) ...
Selecting previously unselected package winetricks.
Unpacking winetricks (from .../winetricks_0.0+20120912_amd64.deb) ...
Selecting previously unselected package binfmt-support.
Unpacking binfmt-support (from .../binfmt-support_2.0.12_amd64.deb) ...
Selecting previously unselected package unrar.
Unpacking unrar (from .../unrar_1%3a4.1.4-1_amd64.deb) ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up cabextract (1.4-3) ...
Setting up winetricks (0.0+20120912) ...
Setting up binfmt-support (2.0.12) ...
binfmt-support stop/waiting
Setting up unrar (1:4.1.4-1) ...
update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode
Processing triggers for ureadahead ...
seel@ubuntu:~$ sudo apt-get install wine
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
E: Unable to correct problems, you have held broken packages.
```

---

### Post by False_Karma on 2013-01-05
Well, since it's saying that it depends on wine1.5 but you're not installing it, you should probably try to do that (sudo apt-get install wine1.5).

---

### Post by fdrake on 2013-01-05
there is a package that influences the installation of google earth and wine, which is the cause of many installation failures: ia32-libs-multiarch

My only left suggestion is this:
[http://ubuntuforums.org/showthread.php?t=1966013](http://ubuntuforums.org/showthread.php?t=1966013)
[http://ubuntuforums.org/showpost.php?p=12246372&postcount=7](http://ubuntuforums.org/showpost.php?p=12246372&postcount=7)

---

### Post by dino99 on 2013-01-05
correct commands are:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
```
sudo apt-get install wine1.5
```

---

### Post by bluepop13 on 2013-01-05
False_Karma and dino99, I tried both your ideas and looks like the same thing...

seel@ubuntu:~$ sudo apt-get install wine1.5
[sudo] password for seel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.20-0ubuntu2) but it is not installable
           Recommends: ttf-droid
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
seel@ubuntu:~$ sudo apt-get install wine1.4
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
           Recommends: ttf-droid
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
seel@ubuntu:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
You are about to add the following PPA to your system:
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpr8vl1_/secring.gpg' created
gpg: keyring `/tmp/tmpr8vl1_/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpr8vl1_/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
seel@ubuntu:~$ sudo apt-get install wine1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.20-0ubuntu2) but it is not installable
           Recommends: ttf-droid
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by uteck on 2013-01-05
Wine seems to have problems installing on 64bit ubuntu systems now.   I installed 32bit virsion in a chroot which works okay, but is a bit of a pain to set up.

---

### Post by fdrake on 2013-01-05
check post #33 . install the package and follow the directions the OP did.

---

### Post by False_Karma on 2013-01-06
> **bluepop13 said:**
> 

False_Karma and dino99, I tried both your ideas and looks like the same thing...


It's the same thing indeed. If you're still willing to try, post the output of "sudo apt-get install wine1.5-i386" and "sudo apt-get install wine1.5-i386:i386" (without the "s). It might be something helpful.

---

### Post by bluepop13 on 2013-01-07
False_Karma

In the order you suggested, here's what happened...

seel@ubuntu:~$ sudo apt-get install wine1.5-i386
[sudo] password for seel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine1.5-i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'wine1.5-i386' has no installation candidate



seel@ubuntu:~$ sudo apt-get install wine1.5-i386:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wine1.5-i386
E: Couldn't find any package by regex 'wine1.5-i386'
seel@ubuntu:~$

---

### Post by fdrake on 2013-01-07
> **fdrake said:**
> check post #33 . install the package and follow the directions the OP did.
regarding to this thread [http://ubuntuforums.org/showthread.php?t=2100827](http://ubuntuforums.org/showthread.php?t=2100827)

---

### Post by bluepop13 on 2013-01-13
Well, first of all, thanks for all the help.

I actually went ahead and re-installed ubuntu 12.10 figuring it might fix the problem and it didn't.

So I'm going to install 12.04 and see it that works.

Either way, I'm learning as I go.

---

### Post by bluepop13 on 2013-01-15
The bad news is, when I reinstalled Ubuntu 12.04 I had the same problem with Wine. Not only was it not installed but it wouldn't install due to the same problem in 12.10: unmet dependencies and all.

While I still don't know all about what all the lingo means, I did run the following commands, it took a while to finish and now Wine runs just fine including allowing me to use YNAB and Netflix.

The commands I used were:

sudo apt-get autoremove
sudo apt-get remove wine
sudo dpkg -p Wine
sudo apt-get install wine

These are the commands that worked for me. I hope this may help someone else out if they have similar problems, or should I have the same or similar problems in the future.

I've also learned to keep notes of what I do, how I do it, what happens and all that in Evernote. Very handy indeed!

---

### Post by gadengo on 2013-01-15
Hello everyone,
I have the exact same problem. I am new to computers, and don't really understand any of this. Why doesn't the default Ubuntu software just come out with Wine?

A lot of programs today miss out on Ubuntu, so it would be great if someone could solve this problem quickly please!

---

