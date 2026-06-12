---
title: "Problems using the WineHQ repositories?"
date: 2018-04-02
forum: Wine
---

### Post by armrek on 2018-04-02
Hi All,

Recently I have been mostly trying to install WineHQ on Unbuntu 18.04 from a repo.

All attempts have ended up with repo not found or Http err 404 as you have it.

I followed this How To [https://www.ubuntupit.com/install-winehq-ubuntu-linux-mint-instantly/](https://www.ubuntupit.com/install-winehq-ubuntu-linux-mint-instantly/)

Here is the output from my attempt, any help on why I get Err 404 is appreciated
```

--------------------------------------------------------------------------

someuser@someuser-machinename:~/Private/psp8$ sudo dpkg --add-architecture i386

--------------------------------------------------------------------------

someuser@someuser-machinename:~/Private/psp8$ wget -nc [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key)
--2018-04-02 10:03:38--  [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key)
Resolving dl.winehq.org (dl.winehq.org)... 151.101.36.69
Connecting to dl.winehq.org (dl.winehq.org)|151.101.36.69|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3122 (3.0K) [application/pgp-keys]
Saving to: ‘Release.key’

Release.key         100%[===================>]   3.05K  --.-KB/s    in 0s      

2018-04-02 10:03:38 (11.6 MB/s) - ‘Release.key’ saved [3122/3122]

--------------------------------------------------------------------------

someuser@someuser-machinename:~/Private/psp8$ sudo apt-key add Release.key
OK

--------------------------------------------------------------------------

someuser@someuser-machinename:~/Private/psp8$ sudo apt-add-repository [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)
Hit:1 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) bionic-updates InRelease   
Hit:3 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) bionic-backports InRelease 
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease    
Ign:5 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease          
Err:6 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic Release            
  404  Not Found [IP: 151.101.36.69 443]
Reading package lists... Done
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

--------------------------------------------------------------------------

someuser@someuser-machinename:~/Private/psp8$ sudo apt-get update
Hit:1 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:3 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease              
Ign:5 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease                
Err:6 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic Release            
  404  Not Found [IP: 151.101.36.69 443]
Reading package lists... Done
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

--------------------------------------------------------------------------

someuser@someuser-machinename:~/Private/psp8$ sudo apt-get install --install-recommends winehq-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package winehq-devel

--------------------------------------------------------------------------

```

---

### Post by deadflowr on 2018-04-02
Currently no bionic repo set up yet:
[https://dl.winehq.org/wine-builds/ubuntu/dists/]("https://dl.winehq.org/wine-builds/ubuntu/dists/")

Anyway, The winehq-devel package is currently equal to that from the bionic Ubuntu repositories. (Ubuntu's is named wine-development)
So no real need to add the repo, yet.

Post final release of Ubuntu 18.04 should have an updated winehq repository list and include bionic.
At which point you can then add it and hopefully get their latest builds beyond that which the Ubuntu version would settle at.

---

### Post by 8Kuula on 2018-06-15
No bionic repo set up to date. Any idea when it is?

---

### Post by QIII on 2018-06-15
Hello!

When that repo is available is dependent on when WineHQ decides to create it.  

You might get an answer [here]("https://forum.winehq.org/viewforum.php?f=8").

---

### Post by cacacarrot on 2018-07-10
thx ,that helps

---

### Post by MikeCyber on 2018-07-12
winehq has been updated to include 18.04

---

