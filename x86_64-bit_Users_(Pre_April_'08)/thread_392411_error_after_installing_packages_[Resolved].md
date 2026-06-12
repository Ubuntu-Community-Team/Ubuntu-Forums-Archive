---
title: "error after installing packages [Resolved]"
date: 2007-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by alek66 on 2007-03-24
i get 
```
E: graphviz-cairo: subprocess post-installation script returned error exit status 127
```
after installing any packages any ideas how to fix this?

---

### Post by aysiu on 2007-03-25
This isn't the same program, but it is a similar error. Maybe [this thread](http://ubuntuforums.org/showthread.php?p=1700225) might help?

If not, can you post the entire output of these commands? ```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude install graphviz-cairo
cat /etc/apt/sources.list
```

---

### Post by alek66 on 2007-03-25
Thanks it helped me and now i dont have the problem anymore.
Thanks

---

### Post by Tux+ on 2007-04-01
How did you fix this error?
as for Aysiu my output is:
```

sudo dpkg --configure -a
/usr/bin/dpkg: /usr/bin/dpkg: cannot execute binary file

```
```

apttitude update
W: GPG error: http://medibuntu.sos-sts.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```
I only printed out the end of the apttitude because I feel it's relevant to print the whole output
```

aptitude install graphviz-cairo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libk3b2 
The following packages have been kept back:
  k3b libk3b2-mp3 
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo

```

```

cat /etc/apt/sources.list
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen

## Automatix repo
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

#java
deb http://download.tuxfamily.org/3v1deb edgy 3v1n0
#deb-src http://download.tuxfamily.org/3v1deb edgy 3v1n0

```

---

### Post by alek66 on 2007-04-07
The error came back and when trying to solve it this appears:

```
alek@DeathStar:~$ sudo dpkg --configure -a
Password:
alek@DeathStar:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 http://www.getautomatix.com edgy Release.gpg [189B]
Ign http://www.getautomatix.com edgy/main Translation-en_US
Get:2 http://archive.ubuntu.com edgy-backports Release.gpg [191B]    
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US  
Get:3 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Get:4 http://ar.archive.ubuntu.com edgy Release.gpg [191B]           
Ign http://ar.archive.ubuntu.com edgy/main Translation-en_US                    
Hit http://www.getautomatix.com edgy Release                         
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US       
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US         
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US       
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US       
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US       
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US         
Ign http://ar.archive.ubuntu.com edgy/restricted Translation-en_US              
Ign http://ar.archive.ubuntu.com edgy/multiverse Translation-en_US              
Ign http://ar.archive.ubuntu.com edgy/universe Translation-en_US                
Hit http://security.ubuntu.com edgy-security Release                            
Get:5 http://archive.ubuntu.com edgy-updates Release.gpg [191B]                 
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Get:6 http://ar.archive.ubuntu.com edgy-updates Release.gpg [191B] 
Ign http://ar.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://ar.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://ar.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Ign http://ar.archive.ubuntu.com edgy-updates/universe Translation-en_US
Hit http://ar.archive.ubuntu.com edgy Release                      
Get:7 http://archive.ubuntu.com edgy-security Release.gpg [191B]   
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US
Get:8 http://archive.ubuntu.com edgy Release.gpg [191B]            
Ign http://archive.ubuntu.com edgy/universe Translation-en_US      
Hit http://ar.archive.ubuntu.com edgy-updates Release                           
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                 
Hit http://archive.ubuntu.com edgy-backports Release                            
Hit http://archive.ubuntu.com edgy-updates Release                              
Hit http://www.getautomatix.com edgy/main Packages                              
Hit http://security.ubuntu.com edgy-security/main Packages                      
Hit http://archive.ubuntu.com edgy-security Release                  
Hit http://archive.ubuntu.com edgy Release                           
Hit http://ar.archive.ubuntu.com edgy/main Packages                             
Hit http://ar.archive.ubuntu.com edgy/restricted Packages                       
Hit http://ar.archive.ubuntu.com edgy/main Sources                              
Hit http://security.ubuntu.com edgy-security/restricted Packages                
Hit http://security.ubuntu.com edgy-security/main Sources            
Hit http://security.ubuntu.com edgy-security/restricted Sources      
Hit http://archive.ubuntu.com edgy-backports/main Packages                      
Hit http://archive.ubuntu.com edgy-backports/restricted Packages                
Hit http://ar.archive.ubuntu.com edgy/restricted Sources                        
Hit http://ar.archive.ubuntu.com edgy/multiverse Packages                       
Hit http://ar.archive.ubuntu.com edgy/universe Packages                         
Hit http://ar.archive.ubuntu.com edgy-updates/main Packages                     
Hit http://ar.archive.ubuntu.com edgy-updates/restricted Packages               
Hit http://ar.archive.ubuntu.com edgy-updates/main Sources                      
Hit http://security.ubuntu.com edgy-security/multiverse Packages                
Hit http://security.ubuntu.com edgy-security/universe Packages       
Hit http://archive.ubuntu.com edgy-backports/universe Packages       
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com edgy-updates/universe Packages
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://ar.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://ar.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://ar.archive.ubuntu.com edgy-updates/universe Packages
Hit http://archive.ubuntu.com edgy-security/main Packages
Hit http://archive.ubuntu.com edgy-security/restricted Packages
Hit http://archive.ubuntu.com edgy-security/universe Packages
Hit http://archive.ubuntu.com edgy-security/multiverse Packages
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Fetched 8B in 3s (3B/s)  
Reading package lists... Done
alek@DeathStar:~$ sudo aptitude install graphviz-cairo 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/29.0kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Selecting previously deselected package graphviz-cairo.
(Reading database ... 128241 files and directories currently installed.)
Preparing to replace graphviz-cairo 2.8-2 (using .../graphviz-cairo_2.8-2_amd64.deb) ...
Unpacking replacement graphviz-cairo ...
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo

```

---

### Post by alek66 on 2007-04-07
```
sudo rm -f /var/lib/dpkg/info/graphviz-cairo.postrm
sudo apt-get remove graphviz-cairo
```

This solves the problem

---

