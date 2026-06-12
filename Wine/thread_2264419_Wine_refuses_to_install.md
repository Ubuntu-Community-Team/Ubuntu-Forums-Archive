---
title: "Wine refuses to install"
date: 2015-02-07
forum: Wine
---

### Post by klyndt on 2015-02-07
I have a problem that has been asked before by others, but not solved.  I have read through the forums and AskUbuntu and none of those solutions have worked either. Wine will not install.  Trying to install the dependencies forces removal of basic things like software-center, ubuntu-desktop, shotwell....

When I try to install Wine1.6 with the software center, I get this error:

[INDENT]wine1.6: Depends: wine1.6-amd64 (= 1:1.6.2-0ubuntu4) but 1:1.6.2-0ubuntu4 is to be installed 
Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu4) but it is a virtual package
[/INDENT]

When I use apt-get I get the same sort of error.
Based on the information other posts have asked for, here is the output from various commands:
$$ dpkg --print-architecture
[INDENT]amd64
[/INDENT]$$ uname -m
[INDENT]x86_64
[/INDENT]$$ dpkg --print-foreign-architectures
[INDENT]i386
[/INDENT]$$ lsb_release -a; uname -a; dpkg -l | grep -i wine
[INDENT]No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 14.04.1 LTS
Release: 14.04
Codename: trusty
Linux Home 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
[/INDENT]
$$ apt-cache policy wine1.6
[INDENT]wine1.6:
  Installed: (none)
  Candidate: 1:1.6.2-0ubuntu4
  Version table:
     1:1.6.2-0ubuntu4 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
[/INDENT]

**UPDATE:**
I went ahead and uninstalled all my i386 packages using the command:
```
sudo apt-get remove --purge `dpkg --get-selections | grep i386 | awk '{print $1}'`

```
After that I went into Software Center and did a search for i386.  This brought up a number of items and after looking through them determined that Skype and my Brother printer drivers were actually using i386.  So I uninstalled them.  That allowed me to remove the architecture using:
```
sudo dpkg --remove-architecture i386
```
Now when I try to install Wine, I get a different error.  Instead of wine1.6-i386 needing other dependencies installed which forces items to be removed from my machine, the error I get now makes it look like there is no i386 package
```
$ sudo apt-get install wine1.6-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine1.6-i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

How can that be?  One other thing that bothers me (though it might not mean anything).  Why is there a space in the URL / trusty/ you can see in the output from the apt-get policy command done above?

---

### Post by klyndt on 2015-02-20
Is there no one who can help with a basic installation?  If I try to install Wine and the package is not available, what do I need to do?

---

### Post by mc4man on 2015-02-20
Well if one was to try to install i386 packages on amd64 then packagename-i386 is wrong. It's packagename:i386
Anyway If I wanted to install wine I'd do just that, install wine.

What does this produce (simulation
```
sudo apt-get update 
```
```
sudo apt-get -s install wine
```

---

### Post by klyndt on 2015-02-20
```
~$ sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://us.archive.ubuntu.com trusty-security InRelease                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty-security Release.gpg
Ign http://ppa.launchpad.net trusty InRelease  
Hit http://us.archive.ubuntu.com trusty Release
Hit http://us.archive.ubuntu.com trusty-security Release                       
Hit http://archive.getdeb.net trusty-getdeb InRelease                 
Ign http://ppa.launchpad.net trusty InRelease                           
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages             
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages   
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-security/main amd64 Packages           
Hit http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages     
Hit http://ppa.launchpad.net trusty/main amd64 Packages                  
Hit http://us.archive.ubuntu.com trusty-security/universe amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages     
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-security/main i386 Packages            
Hit http://us.archive.ubuntu.com trusty-security/restricted i386 Packages      
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-security/universe i386 Packages        
Hit http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages      
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Hit http://ppa.launchpad.net trusty/main amd64 Packages               
Hit http://ppa.launchpad.net trusty/main i386 Packages             
Hit http://ppa.launchpad.net trusty/main Translation-en            
Hit http://ppa.launchpad.net trusty/main amd64 Packages                  
Hit http://ppa.launchpad.net trusty/main i386 Packages             
Hit http://ppa.launchpad.net trusty/main Translation-en            
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done
```
```
~$ sudo apt-get -s install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed or
                 wine1.7 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

And if you ask about the held packages, there appears to be no held packages
```
~$ dpkg --get-selections|grep hold
~$
```

---

### Post by mc4man on 2015-02-20
Are you using a wine ppa or some other repo that has wine?  asking because I don't see any mention of 1.7 in normal repo's
```
ls /etc/apt/sources.list.d
```

Also 
```
apt-cache madison wine
```
```
apt-cache show wine
```

---

### Post by klyndt on 2015-02-20
Yes, I have the Wine PPA running.

```
$ cat /etc/apt/sources.list.d/*
deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main
deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu trusty main
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu trusty main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main

```

```
$ apt-cache madison wine
      wine | 1:1.7.34-0ubuntu1~ppa1 | http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ trusty/main amd64 Packages
      wine | 1:1.6.2-0ubuntu4 | http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```

```
$ apt-cache show wine
Package: wine
Source: wine1.7
Priority: extra
Section: metapackages
Installed-Size: 21
Maintainer: Scott Ritchie <scottritchie@ubuntu.com>
Architecture: amd64
Version: 1:1.7.34-0ubuntu1~ppa1
Depends: wine1.6 | wine1.7
Filename: pool/main/w/wine1.7/wine_1.7.34-0ubuntu1~ppa1_amd64.deb
Size: 982
MD5sum: b06576fd4b76bf8d5f62afee5b3b3d5c
SHA1: 993ede5355617a1d2d518c85e2c3b664e9d8e570
SHA256: fff58435768c37bb82d0657ce53e4e189de88fcec7487308a0e3c097bfa37fd9
Description-en: Microsoft Windows Compatibility Layer (meta-package)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine
 does not require Microsoft Windows, however it can use native system dll
 files in place of its own if they are available.
 .
 This meta-package always depends on the latest stable version of Wine.
Description-md5: 7ca999b13ee007110685ad22b3ecb3b6
Multi-Arch: foreign

Package: wine
Priority: extra
Section: universe/otherosfs
Installed-Size: 21
Maintainer: Scott Ritchie <scottritchie@ubuntu.com>
Architecture: amd64
Source: wine1.6
Version: 1:1.6.2-0ubuntu4
Depends: wine1.6
Filename: pool/universe/w/wine1.6/wine_1.6.2-0ubuntu4_amd64.deb
Size: 968
MD5sum: fa532a90c316e7679d2281985748e093
SHA1: 558c2b93b3d5feb5b077939e4d51db8fbe28fc95
SHA256: d3e711eeefb2d921fd486b8a5f20c1e333f090b254be322fcabf35f3cf23c728
Description-en: Microsoft Windows Compatibility Layer (meta-package)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine
 does not require Microsoft Windows, however it can use native system dll
 files in place of its own if they are available.
 .
 This meta-package always depends on the default version of Wine.
Description-md5: 6474b3e541944944e61aec502ceb28f2
Multi-Arch: foreign
Homepage: http://www.winehq.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

Thanks for your help!

---

### Post by mc4man on 2015-02-20
So if I add the ppa then - 
'sudo apt-get install wine' would install wine1.6, wine1.6-amd64, wine1.6-i386:i386 & 168 other packages  from the Ubuntu repo

'sudo apt-get install wine1.7'  would install wine1.7, wine1.7-amd64,  wine1.7-i386:i386 from the ppa & 155 other packages

You could try```
sudo apt-get install wine1.7
```

If that doesn't work (40-60 it doesn't) then post
```
apt-cache policy wine wine1.6  wine1.6-amd64 wine1.7 wine1.7-amd64
```

Also make sure that Software & Updates > Updates tab > first 2 are enabled, ie. security & updates

---

### Post by mc4man on 2015-02-22
Maybe you got, maybe not..
another thing that would cause this - 
If you upgraded some packages from trusty-proposed, then disabled the proposed repo  wine could fail as you've posted. The most likely culprit would be winbind failing on the fact some samba libs that now can't be installed unless -proposed is re-enabled

So sudo apt-get install winbind could show
Ex. proposed disabled but was previously used

```

sudo apt-get install wine1.7
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.7 : Depends: wine1.7-i386 (= 1:1.7.34-0ubuntu1~ppa1)
E: Unable to correct problems, you have held broken packages.
doug@doug-Lenovo-IdeaPad-Y510P:~$ ^C
doug@doug-Lenovo-IdeaPad-Y510P:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed or
                 wine1.7 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


sudo apt-get -s install winbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winbind : Depends: samba (= 2:4.1.6+dfsg-1ubuntu2.14.04.5) but it is not going to be installed
           Depends: libwbclient0 (= 2:4.1.6+dfsg-1ubuntu2.14.04.5) but 2:4.1.6+dfsg-1ubuntu2.14.04.6 is to be installed
           Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.5) but 2:4.1.6+dfsg-1ubuntu2.14.04.6 is to be installed
E: Unable to correct problems, you have held broken packages.
```

after re-enabling proposed - (just winbind
```
sudo apt-get  install winbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libdvdread-dev
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  libhdb9-heimdal libkdc2-heimdal python-dnspython python-samba samba
  samba-common samba-common-bin samba-dsdb-modules tdb-tools
Suggested packages:
  bind9 bind9utils ldb-tools ntp smbldap-tools heimdal-clients
Recommended packages:
  attr samba-vfs-modules libnss-winbind libpam-winbind
The following NEW packages will be installed:
  libhdb9-heimdal libkdc2-heimdal python-dnspython python-samba samba
  samba-common samba-common-bin samba-dsdb-modules tdb-tools winbind
0 upgraded, 10 newly installed, 0 to remove and 12 not upgraded.
Need to get 3,201 kB of archives.
After this operation, 24.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] n

```

If winbind will install so will wine..

---

### Post by Mike_Walsh on 2015-02-24
Seems a lot of hassle, don't it? I've installed Wine scores of times during my 'distro-hopping' days, and I don't think I EVER had a problem with it. I've settled down now to Ubuntu 'Trusty' and Puppy Linux 'TahrPup' 6.02.

Installing Wine IS quite a slow process in Ubuntu at the best of times; but with Puppy? I KNEW it was fast, everything being 'stripped-down' & minimal, but I'd no sooner clicked on 'Install' than, less than 20 seconds later, there it was; installed.

It does rather sound like a case of things being enabled, then disabled (for whatever reason), with the resultant expected failures at critical moments. And the snag with Wine is that it's not the easiest beast to remove, so that you can attempt re-installation, neither...


Regards,

Mike. ;)

---

