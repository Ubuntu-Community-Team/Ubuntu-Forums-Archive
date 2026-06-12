---
title: "Install Adobe Acrobat Professional on Ubuntu 11.10"
date: 2011-12-21
forum: Wine
---

### Post by huntkey on 2011-12-21
Hi experts,

I have tried different versions of Acrobat (version 9 and version 10) but they all failed. It just says "installation interrupted" at the end. I also tried to have the following "dependencies" installed but still no luck.

```
$ winetricks msxml6
$ winetricks gdiplus
$ winetricks gecko
$ winetricks vcrun2005sp1
$ winetricks vcrun2008
$ winetricks msxml3
$ winetricks atmlib

```

I found a link on Google about how to install v8 on Suse. It requires a working acrobat installed on a windows machine first then just copy the files and registries over. Do I really have to do that??

Btw I also want to give a my wine a fresh start. Do I just delete the $HOME/.wine directory? Do I also need to delete $HOME/.cache/winetricks?

Thanks!

---

### Post by huntkey on 2011-12-23
... still waiting for any possible solutions here... Thanks!

---

### Post by Toz on 2011-12-23
According to wineHQ ([appdb.winehq.org/appview.php?appId=847]("appdb.winehq.org/appview.php?appId=847")), acrobat has a good rating. The page for version X ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=22012]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=22012")) notes that the installer fails, but that the application still works fine. Also, the EULA may be a problem. See: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20793]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20793").

To give wine a fresh start, yes, you can just delete $HOME/.wine (note that this is the default prefix and if you delete it, you will also delete any other wine applications that you may have installed into the default prefix). I would however _not_ delete $HOME/.cache/winetricks. This directory is used to cache those components that you download - saving you the need to download them at a later date if you need them again.

One other thing to consider is the wine version you are using:
```
wine --version
```
You can grab the latest wine version from the wine PPA ([https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa")). Basic instructions to use this PPA are:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```

---

### Post by huntkey on 2011-12-24
Hi Toz, my Wine version is wine-1.3.35. I already have the repository added...

I have read the links and I knew that they had the successes but none of them provided an instruction. Once the installation was stopped all the installation files was deleted too so I never could try to run it.

I have also tried to copy the installation files from a windows xp machine but still with no success. The windows machine is 32 bit while my ubuntu is 64 bit. I still have very limit understanding of Wine. How do I setup the enviroment for the programs? I only need Acrobat to run on my machine/wine but nothing else... Thank you Toz!!

---

### Post by Toz on 2011-12-24
Try it with a new wine prefix:
```
rm -rf ~/.wine
```
...install ie6
```
winetricks ie6
```
...then install Acrobat again.

Any luck?

---

### Post by huntkey on 2011-12-24
Hey Toz I saw that requirement too however I can't install the ie6 for same reason...

winetricks ie6
------------------------------------------------------
Downloading [http://browsers-us.mirrors.zensoft.net/ie/win32/6.0/ie60.exe](http://browsers-us.mirrors.zensoft.net/ie/win32/6.0/ie60.exe) failed
------------------------------------------------------

Happy holidays!

---

### Post by Toz on 2011-12-25
Out of curiosity, what does the following return?
```
apt-cache policy winetricks
```

If its not installed, then install it:
```
sudo apt-get install winetricks
```

You can always get the latest version of winetricks from: [http://winetricks.org/winetricks]("http://winetricks.org/winetricks"). Save it to /usr/bin overwriting the existing file (use sudo to copy the file). This version has the links fixed for internet explorer.

---

### Post by BC59 on 2011-12-25
I think if you use the ppa:ubuntu-wine/ppa, when installing Wine 1.3, Winetricks is installed as well.

---

### Post by Toz on 2011-12-25
> **BC59 said:**
> I think if you use the ppa:ubuntu-wine/ppa, when installing Wine 1.3, Winetricks is installed as well.
Thats what I thought, but he's getting an error message that comes from using an older version of winetricks.

---

### Post by huntkey on 2011-12-27
Hey you guys don't have holiday breaks or what lol anyway I appreciate so much for your quick help.

```
$ apt-cache policy winetricks
winetricks:
  Installed: 0.0+20110629
  Candidate: 0.0+20110629
  Version table:
 *** 0.0+20110629 0
        500 http://ca.archive.ubuntu.com/ubuntu/ oneiric/universe amd64 Packages
```

I have completely removed wine and reinstalled them but still got the same when I tried to install the IE6 with winetricks. What command do I use to make sure that I have the correct PPA added? I added some PPA by following another link. It might or might not be the same PPA Toz provided... I want to make sure that my Wine uses the correct PPA...

Thanks!
Difan

---

### Post by huntkey on 2011-12-27
Hey guys just did a little reading on the PPA or repository stuff. Here is my current wine-ppa config:

```
/etc/apt/sources.list.d$ cat ubuntu-wine-ppa-oneiric.list
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main

/etc/apt/sources.list.d$ cat ubuntu-wine-ppa-oneiric.list.save 
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
```I think I first added it via "Ubuntu software center" GUI. When I ran "sudo add-apt-repository ppa:ubuntu-wine/ppa" I got this:

```
You are about to add the following PPA to your system:
 Latest official WineHQ releases
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie, and is a replacement for the WineHQ budgetdedicated.com repository used for Jaunty and earlier.
 More info: https://launchpad.net/~ubuntu-wine/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.A4Zsb8EVqs --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```Looks like nothing has changed. Anyway I still couldn't get IE6 installed... I have tried to install IE7 which went well but Adobe couldn't be installed. The IE6 component can be the key to my problem...

Thanks!

---

### Post by BC59 on 2011-12-27
Look here, they explain in every version how to do it:
[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=vendor&iId=12&sAction=view&sTitle=View+Developer](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=vendor&iId=12&sAction=view&sTitle=View+Developer)

---

### Post by Toz on 2011-12-27
Try:
```
wget -c http://winetricks.org/winetricks
sudo cp winetricks /usr/bin
winetricks ie6

```

---

### Post by huntkey on 2011-12-27
Hey Toz, now I can install IE6! However the Adobe still failed!! I'm trying to install the trial version X Pro that I downloaded from Adobe official website. I shouldn't have license problems. It is the same version that other guys tried and succeed and reported on WineHQ test result page. Here is the link about the version:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22052](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22052)

He mentioned something like:

> You have to install it like adobe 8 pro, including ie6

Where is the instruction on how to install v8...? By the way does Wine care whether your PC is 32 bit or 64 bit? The test result doesn't include their PC's information so I guess it is irrelevant.

Hey BC59 they show that they had success but didn't really say how they installed it...

Thanks guys!

---

