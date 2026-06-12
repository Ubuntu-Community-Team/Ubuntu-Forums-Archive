---
title: "Wine install gone wrong."
date: 2013-08-18
forum: Wine
---

### Post by LordDraco on 2013-08-18
Hello everyone. I was installing wine from the software center and now it keeps giving me an error code as well as saying dependencies not met. I am running 12.04 64bit and have tried sudo apt-get remove and sudo apt-get purge. Each time it gives me an error code and says that dependecies not met. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4-0ubuntu4.1)
 wine1.4-i386:i386 : Depends: wine1.4-common:i386 (= 1.4.1-0ubuntu1~precise1~ppa4)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I have tried sudo apt-get -f install with no luck.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  language-pack-kde-en kde-l10n-engb libgsoap1 language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine1.4 wine1.4-amd64 wine1.4-common
Suggested packages:
  dosbox
The following packages will be upgraded:
  wine1.4 wine1.4-amd64 wine1.4-common
3 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0 B/22.7 MB of archives.
After this operation, 407 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of wine1.4-i386:i386:
 wine1.4-i386:i386 depends on wine1.4-common (= 1.4.1-0ubuntu1~precise1~ppa4); however:
  Version of wine1.4-common on system is 1.4-0ubuntu4.1.
dpkg: error processing wine1.4-i386:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4:
 wine1.4 depends on wine1.4-i386 (= 1.4-0ubuntu4.1); however:
  Package wine1.4-i386 is not installed.
  Version of wine1.4-i386:i386 on system is 1.4.1-0ubuntu1~precise1~ppa4.
dpkg: error processing wine1.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-common:
 wine1.4-common depends on wine1.4 (= 1.4-0ubuntu4.1); however:
  Package wine1.4 is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing wine1.4-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-amd64:
 wine1.4-amd64 depends on wine1.4-common (= 1.4-0ubuntu4.1); however:
  Package wine1.4-common is not configured yet.
dpkg: error processing wine1.4-amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 wine1.4-i386:i386
 wine1.4
 wine1.4-common
 wine1.4-amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
If anyone can help I would sure appreciate it.

---

### Post by GwL3eNC on 2013-08-18
Hello,

have you tried

sudo apt-get dist-upgrade

---

### Post by ian-weisser on 2013-08-18
> **LordDraco said:**
> The following packages have unmet dependencies:
 [COLOR=#ff0000]wine1.4[/COLOR] : Depends: wine1.4-i386 (= 1.4-0ubuntu4.1)
 [COLOR=#ff0000]wine1.4-i386:i386[/COLOR] : Depends: wine1.4-common:i386 (= 1.4.1-0ubuntu1~precise1~ppa4)

You are using multiarch support (32-bit packages on a 64-bit system.)
Often, this happens when you install Skype or Teamveiwer or some other non-Ubuntu or Ubuntu-partner package.
Multiarch for wine is more unusual, perhaps you have been follwing some old instructions you found somewhere?

1) Disable *all* PPAs and third-party repositories. Did you install wine from a PPA at some point?
```
software-properties-gtk    # Uncheck everything in the "other software" tab
```
2) Uninstall any multiarch applications that you know of (Skype, Teamviewer, etc.)
For example, you already know you have wine1.4 multiarch installed.
```
sudo apt-get autoremove wine1.4:386
```
3) See [http://askubuntu.com/questions/202669/12-10-wants-to-install-multiarch-i386-packages](http://askubuntu.com/questions/202669/12-10-wants-to-install-multiarch-i386-packages) to remove all multiarch packages.
```
sudo apt-get remove --purge `dpkg --get-selections | grep i386 | awk '{print $1}'`
sudo dpkg --remove-architecture i386 
```
4) Refesh your package list and upgrade
```
sudo apt-get update
sudo apt-get upgrade
```
5) Install Wine (This should be easy, since you already have it downloaded)
```
sudo apt-get install wine
```
6) OPTIONAL - Reinstall any multiarch applications.

---

