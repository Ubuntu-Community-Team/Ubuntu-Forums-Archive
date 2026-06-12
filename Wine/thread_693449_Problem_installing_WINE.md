---
title: "Problem installing WINE"
date: 2008-02-11
forum: Wine
---

### Post by Espedine on 2008-02-11
hi im currently new to ubuntu and i've just tried installing wine and got some problem with it... heres the terminal log

espedine@Ubuntu:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
OK
espedine@Ubuntu:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
--14:58:09--  [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184, 88.159.206.7, 2001:4de0:aaac:0:2456::2
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

100%[====================================>] 181           --.--K/s             

14:58:09 (12.00 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [181/181]

espedine@Ubuntu:~$ 
espedine@Ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_SG
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_SG
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_SG               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_SG               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release       
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_SG
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Fetched 3B in 3s (1B/s)
Reading package lists... Done
espedine@Ubuntu:~$ sudo apt-get install wine
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
  wine: Depends: libaudio2 but it is not installable
E: Broken packages
espedine@Ubuntu:~$ 


please help thanks :)

---

### Post by jan quark on 2008-02-11
what does happen when you run this
```

sudo apt-get install libaudio2
```

---

### Post by Ferrat on 2008-02-11
Installing it won't work since

> The following packages have unmet dependencies:
wine: Depends: libaudio2 [COLOR="Red"]but it is not installable[/COLOR]
E: Broken packages

easiest way is to open Synaptic go to Edit and select Fix Broken Packages, if this works as it should then you should be able to install libaudio2 without any problems

---

