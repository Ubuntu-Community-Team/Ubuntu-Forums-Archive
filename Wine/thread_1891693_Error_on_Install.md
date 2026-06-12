---
title: "Error on Install"
date: 2011-12-06
forum: Wine
---

### Post by bigtel on 2011-12-06
I am using Ubuntu 10.11 and trying to install wine 1.3 (the latest version through update manager) 

My Ubuntu was a clean install and had not previously had wine installed. I get errors on the install screen, which I have managed to capture below, can anyone tell me why this is happening and what I can do to resolve this?

Once the package manager refreshes after the install window has closed, it still says 'wine' is there to install. I get the same error code if I try to install it again. The code below is from a second try at installing....


```
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 1. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 1. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 1. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 1. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 1. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 1. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 1. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 1. 
Preconfiguring packages ... 
(Reading database ... 184076 files and directories currently installed.) 
Preparing to replace wine1.3 1.3.34-0ubuntu1~ppa1~oneiric1 (using .../wine1.3_1.3.34-0ubuntu1~ppa1~oneiric1_i386.deb) ... 
Unpacking replacement wine1.3 ... 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for man-db ... 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
Setting up wine1.3 (1.3.34-0ubuntu1~ppa1~oneiric1) ... 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103. 
procps stop/waiting 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 

```

---

### Post by ergo-proxy on 2011-12-06
Add Wine ppa repository instead of using ubuntu repository.

---

### Post by BC59 on 2011-12-06
As @ergo-proxy suggested you should use the Wine PPA. From a terminal run:


```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install wine1.3
```

---

### Post by BC59 on 2011-12-06
I forgot to tell you to run first:

```
sudo dpkg --configure -a
sudo apt-get -f install
```

to ensure there are not previous broken packages.

And after adding the Wine PPA you can install Wine 1.3 from Ubuntu Software Center.

---

### Post by bigtel on 2011-12-06
OK here is my output from the steps you gave...


```
terry@terry-A7N8X-E:~$ sudo dpkg --configure -a
[sudo] password for terry: 
terry@terry-A7N8X-E:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
terry@terry-A7N8X-E:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
You are about to add the following PPA to your system:
 Latest official WineHQ releases
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie, and is a replacement for the WineHQ budgetdedicated.com repository used for Jaunty and earlier.
 More info: https://launchpad.net/~ubuntu-wine/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.dMSpIWDc8i --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
terry@terry-A7N8X-E:~$ sudo apt-get update
Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://gb.archive.ubuntu.com oneiric InRelease                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://gb.archive.ubuntu.com oneiric-security InRelease                    
Hit http://archive.canonical.com oneiric Release.gpg                           
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Ign http://deb.playonlinux.com oneiric InRelease                               
Hit http://gb.archive.ubuntu.com oneiric Release.gpg                           
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Get:2 http://gb.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Hit http://gb.archive.ubuntu.com oneiric-security Release.gpg                  
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://deb.playonlinux.com oneiric Release.gpg                             
Hit http://packages.medibuntu.org oneiric InRelease                            
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://gb.archive.ubuntu.com oneiric Release                               
Get:3 http://gb.archive.ubuntu.com oneiric-updates Release [32.4 kB]  
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://deb.playonlinux.com oneiric Release                                 
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://gb.archive.ubuntu.com oneiric-security Release                      
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://gb.archive.ubuntu.com oneiric/main Sources                          
Hit http://gb.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://gb.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://gb.archive.ubuntu.com oneiric/universe Sources                      
Hit http://gb.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://gb.archive.ubuntu.com oneiric/restricted i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:4 http://gb.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]   
Hit http://deb.playonlinux.com oneiric/main i386 Packages                      
Ign http://deb.playonlinux.com oneiric/main TranslationIndex                   
Hit http://packages.medibuntu.org oneiric/free Sources                         
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Hit http://packages.medibuntu.org oneiric/non-free Sources                     
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://packages.medibuntu.org oneiric/free i386 Packages                   
Ign http://deb.playonlinux.com oneiric/main Translation-en_GB                  
Ign http://deb.playonlinux.com oneiric/main Translation-en                     
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages               
Ign http://packages.medibuntu.org oneiric/free TranslationIndex
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex            
Hit http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://gb.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric/universe TranslationIndex
Get:5 http://gb.archive.ubuntu.com oneiric-updates/restricted Sources [1,348 B]
Get:6 http://gb.archive.ubuntu.com oneiric-updates/main Sources [94.3 kB] 
Get:7 http://gb.archive.ubuntu.com oneiric-updates/multiverse Sources [1,992 B]
Get:8 http://gb.archive.ubuntu.com oneiric-updates/universe Sources [25.8 kB]  
Get:9 http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages [219 kB] 
Get:10 http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,935 B]
Get:11 http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages [64.1 kB]
Get:12 http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [4,396 B]
Get:13 http://gb.archive.ubuntu.com oneiric-updates/main TranslationIndex [73 B]
Get:14 http://gb.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:15 http://gb.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:16 http://gb.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://gb.archive.ubuntu.com oneiric-security/restricted Sources           
Hit http://gb.archive.ubuntu.com oneiric-security/main Sources
Hit http://gb.archive.ubuntu.com oneiric-security/multiverse Sources
Hit http://gb.archive.ubuntu.com oneiric-security/universe Sources
Hit http://gb.archive.ubuntu.com oneiric-security/main i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-security/universe i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-security/main TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en_GB           
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en              
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB     
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en        
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://gb.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com oneiric-security/main Translation-en          
Hit http://gb.archive.ubuntu.com oneiric-security/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com oneiric-security/restricted Translation-en    
Hit http://gb.archive.ubuntu.com oneiric-security/universe Translation-en      
Ign http://packages.medibuntu.org oneiric/free Translation-en_GB               
Ign http://packages.medibuntu.org oneiric/free Translation-en                  
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_GB
Ign http://packages.medibuntu.org oneiric/non-free Translation-en
99% [4 Packages bzip2 23.6 MB]                                      777 kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://gb.archive.ubuntu.com oneiric/universe i386 Packages                
  
Err http://gb.archive.ubuntu.com oneiric/universe i386 Packages                
  
Err http://gb.archive.ubuntu.com oneiric/universe i386 Packages
  404  Not Found
Fetched 4,915 kB in 22s (223 kB/s)
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
terry@terry-A7N8X-E:~$ sudo apt-get install wine1.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  wine1.3
1 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
Need to get 0 B/12.7 MB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 184124 files and directories currently installed.)
Preparing to replace wine1.3 1.3.34-0ubuntu1~ppa1~oneiric2 (using .../wine1.3_1.3.34-0ubuntu1~ppa1~oneiric4_i386.deb) ...
Unpacking replacement wine1.3 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Setting up wine1.3 (1.3.34-0ubuntu1~ppa1~oneiric4) ...
procps stop/waiting
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
terry@terry-A7N8X-E:~$ 

```


I think it has upgraded WINE successfully and I seem to able to access the wine configuration utility. Great thanks.

---

