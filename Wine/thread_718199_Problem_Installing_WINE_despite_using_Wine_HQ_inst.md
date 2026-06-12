---
title: "Problem Installing WINE despite using Wine HQ instructions"
date: 2008-03-07
forum: Wine
---

### Post by Epiphyte on 2008-03-07
Hi All,

I have just installed Ubuntu V7.10 and wish to install WINE.

I went to WineHQ and followed the instructions here ([http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)) to the letter.

I get the following error:
>  W: Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.55~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.55~winehq0~ubuntu~7.10-1_i386.deb)
  404 Not Found
 
I have double & triple checked the repository entries but they seem correct.

Can someone please help?

Thanks.
Mitchell

---

### Post by cisforcojo on 2008-03-08
Can you show the printout of EXACTLY what you're doing from the command line? Copy & Paste it.

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```

That's what you should be doing.

---

### Post by Epiphyte on 2008-03-08
Here's what I get :

sysman@Ubuntu-Investech:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
[sudo] password for sysman:
OK
sysman@Ubuntu-Investech:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
--22:06:22--  [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

100%[====================================>] 181           --.--K/s             

22:06:22 (28.83 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [181/181]

sysman@Ubuntu-Investech:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                 
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_AU               
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release [1005B]                    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                              
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                     
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources [907B]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_AU     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_AU
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_AU
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_AU                                                                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_AU                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                                                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                                                                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                                                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                                                                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                                                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources                                                                                                      
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages [245kB]                                                                                         
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages [4263B]                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources                                                                                                    
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources [937B]                                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                                                                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources                                                                                                
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages [9942B]                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources                                                                                              
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release [51.2kB]                                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages                                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources                                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources                                                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages                                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources                                                                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources                                                                                             
Fetched 314kB in 13s (23.6kB/s)                                                                                                                             
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures were invalid: BADSIG 58403026387EE263 Scott Ritchie <scott@open-vote.org>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_gutsy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
sysman@Ubuntu-Investech:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 10.1MB of archives.
After unpacking 51.0MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main wine 0.9.55~winehq0~ubuntu~7.10-1
  404 Not Found
Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.55~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.55~winehq0~ubuntu~7.10-1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
sysman@Ubuntu-Investech:~$

---

### Post by happyhamster on 2008-03-08
Take a look at System-->Administration-->Software Sources-->Authentication

It shows the gpg keys in use. The one from Scott Ritchie is the wine key. There should be only one such key, and it should match 387EE263. If not, or if there are other Scott Ritchie keys, get rid of them.

WARNING: keep all other keys, and if you think something else's not right, don't delete anything.

Next, in the same menu, under the Third-Party-Software tab, check the WineHQ repositories: there should be two:

WineHQ - Ubuntu 7.10 "Gutsy Gibbon"

WineHQ - Ubuntu 7.10 "Gutsy Gibbon" (source code)

If there are other WineHQ repos, untick them.

---

### Post by newbieforever on 2008-03-08
hem, 
i dont know whether this could help, i even dont know how to use wine yet, but i had no problem to install the very last version through the winehq site:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

every things went smooth

i hope this help, and if you any links to learn using wine for games and utilities (uwc for example, but many others...), i will be glad...

thanks

---

### Post by YokoZar on 2008-03-08
Run apt-get update again.


I'm pretty sure this happens due to our web servers not being in sync.  You download an old index from one server, and then ask the updated server for the old file, and it tells you it's not there (or doesn't match the signature).

---

### Post by Epiphyte on 2008-03-09
Guys,

I have done all you suggested and still get the following:

> sysman@Ubuntu-Investech:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB of archives.
After unpacking 51.0MB of additional disk space will be used.
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main wine 0.9.55~winehq0~ubuntu~7.10-1
  404 Not Found
Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.55~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.55~winehq0~ubuntu~7.10-1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
sysman@Ubuntu-Investech:~$            

Sorry I cannot see what I am doing wrong.

---

### Post by mc4man on 2008-03-09
for the moment just go here
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
take your pick - dl and double click to install

---

### Post by Maxwell85 on 2008-03-10
I'm having a different problem with the same program, Ive installed 7.10 Gutsy, and have added repositories for WINE, I kept getting errors stating that dependencies could not be met, heres the code, also, the links to downloading work, however I get the same message from the package installer, and cannot install. 

[PHP]joseph@Maximus:~$ wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
OK
joseph@Maximus:~$ sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.
--22:49:01--  http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list
           => `/etc/apt/sources.'
Resolving wine.budgetdedicated.com... 88.159.206.7, 81.171.111.184, 2001:4de0:aaac:0:2456::2
Connecting to wine.budgetdedicated.com|88.159.206.7|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

100%[==================================>] 181           --.--K/s             

22:49:01 (25.74 MB/s) - `/etc/apt/sources.' saved [181/181]

joseph@Maximus:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Get:1 http://wine.budgetdedicated.com gutsy Release.gpg [191B]  
Ign http://wine.budgetdedicated.com gutsy/main Translation-en_US
Hit http://wine.budgetdedicated.com gutsy Release          
Ign http://wine.budgetdedicated.com gutsy/main Packages
Hit http://wine.budgetdedicated.com gutsy/main Sources
Hit http://wine.budgetdedicated.com gutsy/main Packages
Fetched 1B in 0s (1B/s)
Reading package lists... Done
joseph@Maximus:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: ia32-libs (>= 1.6) but it is not installable
        Depends: lib32asound2 (> 1.0.14) but it is not installable
        Depends: libc6-i386 (>= 2.6-1) but it is not installable
E: Broken packages[/PHP]

---

### Post by cisforcojo on 2008-03-11
Maxwell: 

Your problem lies in that you don't have enough repos added. You're using the CD's I see (I've removed them as package options) and don't have access to the newer versions accessible on the net.

You'll want to go to your /etc/apt/source.list and add some repos.

```
## +++ Gutsy (Ubuntu 7.10) +++
deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
```

That should do it.
Just run:
```
sudo gedit /etc/apt/sources.list
```

Add those repos and then run:

```
sudo apt-get update
```

Then try the install again.
If I were you, I'd also remove the CDs as a package source. It's a hassle putting them in your computer every time you want to install something.

---

### Post by Maxwell85 on 2008-03-11
Ah!  Great!  Worked perfectly, Wine is now installed.  Thanks a million!

---

