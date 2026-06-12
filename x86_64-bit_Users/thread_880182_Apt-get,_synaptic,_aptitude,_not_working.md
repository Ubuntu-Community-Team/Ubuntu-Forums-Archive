---
title: "Apt-get, synaptic, aptitude, not working"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by tylerni7 on 2008-08-04
I'm not sure what happened, but after leaving on vacation and coming back home, I just discovered that none of the standard application management programs are working correctly. 

I currently have some broken packages, because I tried upgrading things and they started installing, but never finished. I'm not sure what the main problem is because I've been getting a few errors depending on what I try to do, but in general, I get something like 

" dpkg - warning: while removing nvidia-glx-new, unable to remove directory `/usr/bin/nvidia-xconfig': Operation not permitted - directory may be a mount point ? "

if I try to 'touch' the files in /usr/bin, I get permission denied, even as root, I'm not sure if that's the underlying cause for me not being able to install using apt, but it certainly seems to be affecting it.

---

### Post by cariboo on 2008-08-04
The nvidia-glx-new may still be in use, to remove it you may want to try Ctrl-Alt-F1 to get to a command prompt then:

```
sudo /etc/init.d/gdm stop
```

then try

```
sudo apt-get remove nvidia-glx-new
```

then

```
sudo /etc/init.d/gdm start
```

then Ctrl-Alt-F7 to get back to the desktop. Beware if the nvidia-glx-new was still in use it may render your desktop unusable.

Jim

---

### Post by tylerni7 on 2008-08-06
Thanks for the help, but I think the problem is deeper than that, it's not just that package, it's quite a few, here's the full output 

$sudo apt-get -f install
[sudo] password for tyler: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libservlet2.4-java libhsqldb-java libglu1-mesa-dev
  openoffice.org-filter-mobiledev openoffice.org-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libglib2.0-dev openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-writer python-central samba-common
  winbind wine
Suggested packages:
  libglib2.0-doc libmyodbc odbc-postgresql libsqliteodbc tdsodbc mdbtools
  libmysql-java libpg-java openoffice.org-gcj openoffice.org-report-builder
  openoffice.org-style-hicontrast openoffice.org-style-industrial
Recommended packages:
  openoffice.org-filter-binfilter
The following packages will be REMOVED:
  nvidia-glx-new openoffice.org-draw openoffice.org-impress
  openoffice.org-math smbclient sun-java6-bin sun-java6-jre unixodbc
The following packages will be upgraded:
  libglib2.0-dev openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-writer python-central samba-common
  winbind wine
10 upgraded, 0 newly installed, 8 to remove and 124 not upgraded.
21 not fully installed or removed.
Need to get 0B/64.2MB of archives.
After this operation, 135MB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 
dpkg: serious warning: files list file for package `winbind' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `unixodbc' missing, assuming package has no files currently installed.
165934 files and directories currently installed.)
Removing nvidia-glx-new ...
dpkg - warning: while removing nvidia-glx-new, unable to remove directory `/usr/bin/nvidia-xconfig': Operation not permitted - directory may be a mount point ?
dpkg: error processing nvidia-glx-new (--remove):
 failed to delete `/usr/bin/nvidia-bug-report.sh.dpkg-new': Operation not permitted
Removing openoffice.org-impress ...
dpkg: error processing openoffice.org-impress (--remove):
 failed to delete `/usr/bin/ooimpress.dpkg-new': Operation not permitted
Removing openoffice.org-draw ...
dpkg: error processing openoffice.org-draw (--remove):
 failed to delete `/usr/bin/oodraw.dpkg-new': Operation not permitted
Removing openoffice.org-math ...
dpkg: error processing openoffice.org-math (--remove):
 failed to delete `/usr/bin/oomath.dpkg-new': Operation not permitted
Removing smbclient ...
dpkg - warning: while removing smbclient, unable to remove directory `/usr/bin/smbcquotas': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing smbclient, unable to remove directory `/usr/bin/smbcacls': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing smbclient, unable to remove directory `/usr/bin/smbtree': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing smbclient, unable to remove directory `/usr/bin/smbspool': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing smbclient, unable to remove directory `/usr/bin/rpcclient': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing smbclient, unable to remove directory `/usr/bin/smbtar': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing smbclient, unable to remove directory `/usr/bin/smbget': Operation not permitted - directory may be a mount point ?
dpkg - warning: while removing smbclient, unable to remove directory `/usr/bin/smbclient': Operation not permitted - directory may be a mount point ?
dpkg: error processing smbclient (--remove):
 failed to delete `/usr/bin/findsmb.dpkg-new': Operation not permitted
Errors were encountered while processing:
 nvidia-glx-new
 openoffice.org-impress
 openoffice.org-draw
 openoffice.org-math
 smbclient
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by tuxxy on 2008-08-06
What happens when you run these commands

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by tylerni7 on 2008-08-07
> **tuxxy said:**
> What happens when you run these commands

```
sudo dpkg --configure -a
sudo apt-get update
```

```
tyler@tyler-desktop:~$ sudo dpkg --configure -a
[sudo] password for tyler: 
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.4.1-1ubuntu2); however:
  Version of openoffice.org-common on system is 1:2.4.1-1ubuntu1.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on unixodbc; however:
  Package unixodbc is not installed.
dpkg: error processing sun-java6-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine-dev:
 wine-dev depends on wine (= 1.0.0-1ubuntu4~hardy1); however:
  Package wine is not installed.
dpkg: error processing wine-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.4.1-1ubuntu2); however:
  Version of openoffice.org-core on system is 1:2.4.1-1ubuntu1.
 python-uno depends on python-central (>= 0.6.7); however:
  Package python-central is not installed.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
Setting up libglib2.0-0 (2.16.4-0ubuntu2) ...

dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-06-0ubuntu1) | ia32-sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not configured yet.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 openoffice.org-style-human
 sun-java6-bin
 wine-dev
 python-uno
 sun-java6-jre

```
and 

```
tyler@tyler-desktop:~$ sudo apt-get update
Get:1 http://security.ubuntu.com hardy-security Release.gpg [189B]
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg                   
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://packages.medibuntu.org hardy Release.gpg                  
Get:2 http://security.ubuntu.com hardy-security Release [58.5kB]               
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Get:3 http://us.archive.ubuntu.com hardy-updates Release.gpg [189B]            
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com hardy Release                                 
Get:4 http://us.archive.ubuntu.com hardy-updates Release [58.5kB]              
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://us.archive.ubuntu.com hardy/main Packages                           
Hit http://us.archive.ubuntu.com hardy/restricted Packages                     
Hit http://us.archive.ubuntu.com hardy/main Sources                            
Hit http://us.archive.ubuntu.com hardy/restricted Sources                      
Hit http://us.archive.ubuntu.com hardy/universe Packages                       
Hit http://us.archive.ubuntu.com hardy/universe Sources                        
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                      
Get:5 http://security.ubuntu.com hardy-security/main Packages [50.3kB]         
Get:6 http://us.archive.ubuntu.com hardy-updates/main Packages [289kB]         
Ign http://packages.medibuntu.org hardy Release                                
Get:7 http://security.ubuntu.com hardy-security/restricted Packages [6465B]
Get:8 http://security.ubuntu.com hardy-security/main Sources [12.3kB]          
Get:9 http://security.ubuntu.com hardy-security/restricted Sources [908B]      
Get:10 http://security.ubuntu.com hardy-security/universe Packages [28.1kB]    
Get:11 http://security.ubuntu.com hardy-security/universe Sources [3708B]      
Get:12 http://security.ubuntu.com hardy-security/multiverse Packages [3891B]   
Get:13 http://security.ubuntu.com hardy-security/multiverse Sources [14B]      
Ign http://packages.medibuntu.org hardy/free Packages                          
Get:14 http://us.archive.ubuntu.com hardy-updates/restricted Packages [6465B]
Get:15 http://us.archive.ubuntu.com hardy-updates/main Sources [85.0kB]        
Get:16 http://us.archive.ubuntu.com hardy-updates/restricted Sources [908B]    
Get:17 http://us.archive.ubuntu.com hardy-updates/universe Packages [76.5kB]   
Get:18 http://us.archive.ubuntu.com hardy-updates/universe Sources [18.9kB]    
Get:19 http://us.archive.ubuntu.com hardy-updates/multiverse Packages [16.1kB] 
Get:20 http://us.archive.ubuntu.com hardy-updates/multiverse Sources [2612B]   
Ign http://packages.medibuntu.org hardy/non-free Packages                    
Err http://packages.medibuntu.org hardy/free Packages                          
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Err http://packages.medibuntu.org hardy/non-free Packages
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Fetched 718kB in 2s (351kB/s)
W: Failed to fetch http://packages.medibuntu.org/dists/hardy/free/binary-amd64/Packages.gz  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

W: Failed to fetch http://packages.medibuntu.org/dists/hardy/non-free/binary-amd64/Packages.gz  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by tylerni7 on 2008-08-07
Sorry to post again, but my pwoer got shut off in a storm, and that rsetarted the computer, which now can't find the graphics driver that I can't install via apt-get, so... help would be even more appreciated.

dpkg keeps returning 'errors while processing' and fails to delete things because it isn't permitted. Hopefully I won't have to reinstall ubuntu :(

---

### Post by markbuntu on 2008-08-10
I had a similar problem the other day when I installed the rt kernel. My ati driver was kludged and nothing could remove it, apt, aptitude, or synaptic and fix broken packages did not work on it either. dpkg would not go past it. so no dpkg --configure -a, no apt-get update. I was really stuck, just like you are.

I could get no packages at all as long as that was broken, nothing.

The only way I could remove it was to do a force downgrade. Then I had no x server when I rebooted so I had to do recovery mode, fix x and then edit my etc/X11/xorg.conf and change fglrx to VESA and remove all the extras and options and just leave the barebones defaults, Then I rebooted and got my desktop back and reinstalled the driver.

You should try the x fix thing in recovery mode and the xorg.conf edit, changing nvidia to VESA of course and then try fix broken packages in Synaptic to fix the rest of the stuff.

---

### Post by tylerni7 on 2008-08-12
well, I had most everything backed up on a RAID array separate from the root directory and all that got messed up there, so I just backed up all the important things and reinstalled Ubuntu :/
hopefully this won't happen again... anyways, thanks for your help everyone!

---

