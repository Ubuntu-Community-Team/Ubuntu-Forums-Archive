---
title: "Wine not Installing"
date: 2016-12-09
forum: Wine
---

### Post by auran2 on 2016-12-09
Hi,
So, I'll get straight to the point, I've recently tried to install Wine on my Compaq Presario CQ60 Series laptop, which is running Ubuntu 16.04, I followed the instructions from [this site ]("https://wiki.winehq.org/Ubuntu")however it did not work, here's my Terminal log thingy:
```
auran@Ubuntu:~$ sudo dpkg --add-architecture i386
[sudo] password for auran: 
auran@Ubuntu:~$ sudo add-apt-repository ppa:wine/wine-builds
 
 More info: [https://launchpad.net/~wine/+archive/ubuntu/wine-builds](https://launchpad.net/~wine/+archive/ubuntu/wine-builds)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpem1k9hma/secring.gpg' created
gpg: keyring `/tmp/tmpem1k9hma/pubring.gpg' created
gpg: requesting key 77C899CB from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpem1k9hma/trustdb.gpg: trustdb created
gpg: key 77C899CB: public key "Launchpad PPA for Wine" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
auran@Ubuntu:~$ sudo apt update
Hit:1 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Hit:3 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Hit:6 [http://ppa.launchpad.net/appgrid/stable/ubuntu](http://ppa.launchpad.net/appgrid/stable/ubuntu) xenial InRelease          
Hit:7 [http://archive.canonical.com](http://archive.canonical.com) xenial InRelease                            
Hit:8 [http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu](http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu) xenial InRelease
Ign:9 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial InRelease
Get:10 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease [18,1 kB]
Err:11 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial Release
  404  Not Found
Get:12 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial/main amd64 Packages [2.464 B]
Get:13 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial/main i386 Packages [2.412 B]
Get:14 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial/main Translation-en [980 B]
Reading package lists... Done   
E: The repository 'http://ppa.launchpad.net/mlankhorst/ppa/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
auran@Ubuntu:~$ sudo apt install winehq-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-devel : Depends: wine-devel (= 1.9.24~ubuntu16.04.1)
E: Unable to correct problems, you have held broken packages.
auran@Ubuntu:~$ sudo dpkg --add-architecture i386 
[sudo] password for auran: 
auran@Ubuntu:~$ sudo add-apt-repository ppa:wine/wine-builds
 
 More info: [https://launchpad.net/~wine/+archive/ubuntu/wine-builds](https://launchpad.net/~wine/+archive/ubuntu/wine-builds)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp5p0mho8q/secring.gpg' created
gpg: keyring `/tmp/tmp5p0mho8q/pubring.gpg' created
gpg: requesting key 77C899CB from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp5p0mho8q/trustdb.gpg: trustdb created
gpg: key 77C899CB: public key "Launchpad PPA for Wine" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
auran@Ubuntu:~$ sudo apt-get update
Hit:1 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Hit:3 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Hit:6 [http://ppa.launchpad.net/appgrid/stable/ubuntu](http://ppa.launchpad.net/appgrid/stable/ubuntu) xenial InRelease          
Hit:7 [http://archive.canonical.com](http://archive.canonical.com) xenial InRelease                            
Hit:8 [http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu](http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu) xenial InRelease
Ign:9 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial InRelease          
Hit:10 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease       
Ign:11 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial Release
Ign:12 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 Packages
Ign:13 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main i386 Packages
Ign:14 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main all Packages
Ign:15 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en_US
Ign:16 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en
Ign:17 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:18 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:12 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 Packages
Ign:13 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main i386 Packages
Ign:14 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main all Packages
Ign:15 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en_US
Ign:16 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en
Ign:17 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:18 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:12 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 Packages
Ign:13 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main i386 Packages
Ign:14 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main all Packages 
Ign:15 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en_US
Ign:16 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en
Ign:17 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:18 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:12 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 Packages
Ign:13 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main i386 Packages
Ign:14 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main all Packages 
Ign:15 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en_US
Ign:16 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en
Ign:17 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:18 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:12 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 Packages
Ign:13 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main i386 Packages
Ign:14 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main all Packages 
Ign:15 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en_US
Ign:16 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en
Ign:17 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:18 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main DEP-11 64x64 Icons
Err:12 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 Packages
  404  Not Found
Err:13 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main i386 Packages
  404  Not Found
Ign:14 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main all Packages
Ign:15 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en_US
Ign:16 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main Translation-en
Ign:17 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:18 [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu) xenial/main DEP-11 64x64 Icons
Fetched 102 kB in 16s (6.285 B/s)
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/mlankhorst/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/mlankhorst/ppa/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/mlankhorst/ppa/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
auran@Ubuntu:~$ sudo apt-get install --install-recommends winehq-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-devel : Depends: wine-devel (= 1.9.24~ubuntu16.04.1)
E: Unable to correct problems, you have held broken packages.
```

What do I do?

---

### Post by ian-weisser on 2016-12-09
You didn't follow the instructions: 

> If you have previously installed a Wine package from another repository, please remove it and any packages that depend on it (e.g., wine-mono, wine-gecko, winetricks) before attempting to install the WineHQ packages, as they may cause dependency conflicts.

That's exactly what happened to you - the old PPA packages are still installed, and causing dependency conflicts.

Completely uninstall ALL wine packages.
Then delete the old PPA.
Then apt update (because you just changed your sources).



Are you deliberately trying to install unsupported or experimental versions of Wine?
There is a fine version of Wine already in the Ubuntu repositories; much easier for new or unskilled users to install and use.

---

### Post by wildmanne39 on 2016-12-10
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by auran2 on 2016-12-10
>  			 				[INDENT] 					You didn't follow the instructions: 

[QUOTE] 	 		 			 			 				If you have previously installed a Wine package from another  repository, please remove it and any packages that depend on it (e.g.,  wine-mono, wine-gecko, winetricks) before attempting to install the  WineHQ packages, as they may cause dependency conflicts. 			 		

 	
 
That's exactly what happened to you - the old PPA packages are still installed, and causing dependency conflicts.

Completely uninstall ALL wine packages.
Then delete the old PPA.
Then apt update (because you just changed your sources).



Are you deliberately trying to install unsupported or experimental versions of Wine?
There is a fine version of Wine already in the Ubuntu repositories; much easier for new or unskilled users to install and use. 				
[/INDENT] 			
  			   		
[/QUOTE]

Well, thank you for the response, is there anyway for me to see what wine packages I have installed exactly? And, yes, I am trying to install unsupported versions, I like to get new features sooner, even if it's something as silly as compability with a program I know I'll never use

---

