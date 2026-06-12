---
title: "Reinstalling Wine"
date: 2013-10-06
forum: Wine
---

### Post by blueboy1 on 2013-10-06
I was running Wine and ran into a **synaptic package broken** problem which has been resolved since. However, I am trying to reinstall Wine without any sussess. Bashing-om was on this one.

---

### Post by Bashing-om on 2013-10-06
blueboy1;  Here to help;

Ok, Lets start this by making a backup file of what files are  currently installed for wine - if these files are still in existence.
Let's look at what there is:
```

ls -la /var/lib/dpkg/info/wine.*

``` This is for reference if required later.
Next will see if we can "purge" wine back to what is available within ubuntu's repository.
Failing that (expected) we will try apt-get to manage this situation;
Failing that we will revert to manually hunting up all the files and removing them - one by one - YUK, a lot of time and effort.
Then:
 
We will (re-)install Wine from the repository in one way or another.

[INDENT][INDENT]we do have a plan
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-06
This is all their is.

```
alrick@Home:~$ ls -la /var/lib/dpkg/info/wine.*
ls: cannot access /var/lib/dpkg/info/wine.*: No such file or directory

```

---

### Post by Bashing-om on 2013-10-06
blueboy1; Yuk, OK;

That complicates things just a bit. Let's go ahead and see what results from:
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-wine/ppa

``` I do not expect anything productive, I am interested in what the package manager returns.
Then we are done with the PPA; .. After seeing those results I will advise on removing the PPA.

[INDENT][INDENT]what will be will be
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-06
Here we go,

```
alrick@Home:~$ sudo apt-get install ppa-purge
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree... 50%
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl ppa-purge
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,924 kB of archives.
After this operation, 9,049 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main libboost-iostreams1.46.1 amd64 1.46.1-7ubuntu3 [39.2 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise/main libcwidget3 amd64 0.5.16-3.1ubuntu1 [406 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise-updates/main aptitude amd64 0.6.6-1ubuntu1.2 [2,372 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ precise/main libsub-name-perl amd64 0.05-1build2 [9,656 B]
Get:5 http://archive.ubuntu.com/ubuntu/ precise/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ precise/main libio-string-perl all 1.08-2 [12.0 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ precise/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1 [54.0 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ precise/universe ppa-purge all 0.2.8+bzr56 [4,360 B]
Fetched 2,924 kB in 1s (1,494 kB/s)                      
Selecting previously unselected package libboost-iostreams1.46.1.
(Reading database ... 329263 files and directories currently installed.)
Unpacking libboost-iostreams1.46.1 (from .../libboost-iostreams1.46.1_1.46.1-7ubuntu3_amd64.deb) ...
Selecting previously unselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3.1ubuntu1_amd64.deb) ...
Selecting previously unselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.6-1ubuntu1.2_amd64.deb) ...
Selecting previously unselected package libsub-name-perl.
Unpacking libsub-name-perl (from .../libsub-name-perl_0.05-1build2_amd64.deb) ...
Selecting previously unselected package libclass-accessor-perl.
Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.34-1_all.deb) ...
Selecting previously unselected package libio-string-perl.
Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
Selecting previously unselected package libparse-debianchangelog-perl.
Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.2.0-1ubuntu1_all.deb) ...
Selecting previously unselected package ppa-purge.
Unpacking ppa-purge (from .../ppa-purge_0.2.8+bzr56_all.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up libboost-iostreams1.46.1 (1.46.1-7ubuntu3) ...
Setting up libcwidget3 (0.5.16-3.1ubuntu1) ...
Setting up aptitude (0.6.6-1ubuntu1.2) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up libsub-name-perl (0.05-1build2) ...
Setting up libclass-accessor-perl (0.34-1) ...
Setting up libio-string-perl (1.08-2) ...
Setting up libparse-debianchangelog-perl (1.2.0-1ubuntu1) ...
Setting up ppa-purge (0.2.8+bzr56) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...

```

```
alrick@Home:~$ sudo ppa-purge ppa:ubuntu-wine/ppa
Updating packages lists
PPA to be removed: ubuntu-wine ppa
Warning:  Could not find package list for PPA: ubuntu-wine ppa

```

---

### Post by Bashing-om on 2013-10-06
blueboy1; Well, well, well ---

That is an output that I sure did not expect for just installing "ppa-purge", kinda wonder where they were hiding at.
Let's make sure all is still well with our world.
```

sudo apt-get update
sudo apt-get upgrade

```
and to continue to address preparations to remove Wine:
show me:
```

sudo dpkg --list | grep wine
apt-cache policy wine
ls -la $HOME/.wine
ls -la $HOME/.winetrickscache
ls -la $HOME/.config/menus/applications-merged/wine*
ls -la $HOME/.local/share/applications/wine
ls -la $HOME/.local/share/desktop-directories/wine*
ls -la $HOME/.local/share/icons/????_*.xpm
ls -la .local/share/applications/wine/Programs/

```
And then to cover some more bases, what does a search in synaptic show for:
```

wine* 
wine-gecko*

```

Now I hope we are ready to remove Wine and winetricks.

[INDENT][INDENT]prior prudent planning prevents *iss poor performance
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-06
It's all here.

```
alrick@Home:~$ sudo apt-get update
[sudo] password for alrick: 
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://archive.ubuntu.com precise Release.gpg
Hit http://archive.ubuntu.com precise-backports Release.gpg
Hit http://archive.ubuntu.com precise-updates Release.gpg
Hit http://security.ubuntu.com precise-security Release
Hit http://archive.ubuntu.com precise Release
Hit http://archive.ubuntu.com precise-backports Release
Hit http://archive.ubuntu.com precise-updates Release                 
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://archive.ubuntu.com precise/universe Sources
Hit http://archive.ubuntu.com precise/main Sources
Hit http://archive.ubuntu.com precise/multiverse Sources
Hit http://archive.ubuntu.com precise/restricted Sources
Hit http://archive.ubuntu.com precise/main amd64 Packages
Hit http://archive.ubuntu.com precise/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://archive.ubuntu.com precise/restricted amd64 Packages
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise/main i386 Packages
Hit http://archive.ubuntu.com precise/universe i386 Packages
Hit http://archive.ubuntu.com precise/restricted i386 Packages
Hit http://archive.ubuntu.com precise/multiverse i386 Packages
Hit http://archive.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://archive.ubuntu.com precise/universe TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://archive.ubuntu.com precise-backports/main i386 Packages
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://archive.ubuntu.com precise-updates/main i386 Packages
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://archive.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise/multiverse Translation-en
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Hit http://archive.ubuntu.com precise-backports/main Translation-en
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/main Translation-en
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Reading package lists... Done

```

```
alrick@Home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
alrick@Home:~$ sudo dpkg --list | grep wine
rc  wine1.6                                                     1.7.1-0ubuntu1                          Microsoft Windows Compatibility Layer (Binary Emulator and Library)
rc  wine1.6-amd64                                               1.7.1-0ubuntu1                          Microsoft Windows Compatibility Layer (64-bit support)
rc  wine1.6-i386:i386                                           1.7.1-0ubuntu1                          Microsoft Windows Compatibility Layer (32-bit support)
ii  winetricks                                                  0.0+20130707~precise1~ppa1              Microsoft Windows Compatibility Layer (winetricks)

```

```
alrick@Home:~$ apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1.4-0ubuntu4.1
  Version table:
     1.4-0ubuntu4.1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/universe amd64 Packages
     1.4-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages

```


```
alrick@Home:~$ ls -la $HOME/.wine
total 6960
drwxrwxr-x   4 alrick alrick    4096 Sep 18 09:20 .
drwxr-xr-x 104 alrick alrick   20480 Oct  6 20:57 ..
drwxrwxr-x   2 alrick alrick    4096 Sep 18 09:20 dosdevices
drwxrwxr-x   8 alrick alrick    4096 May 13  2012 drive_c
-rw-rw-r--   1 alrick alrick 6708086 Sep 18 09:20 system.reg
-rw-rw-r--   1 alrick alrick      11 Sep 12 15:11 .update-timestamp
-rw-rw-r--   1 alrick alrick    2169 Mar 26  2012 userdef.reg
-rw-rw-r--   1 alrick alrick  365592 Sep 18 09:20 user.reg
-rw-rw-r--   1 alrick alrick      14 Mar 26  2012 winetricks.log

```

```
alrick@Home:~$ ls -la $HOME/.winetrickscache
ls: cannot access /home/alrick/.winetrickscache: No such file or directory

```

```
alrick@Home:~$ ls -la $HOME/.config/menus/applications-merged/wine*
-rw------- 1 alrick alrick 451 May  1  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Citrix Receiver.menu
-rw------- 1 alrick alrick 588 May 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-EGW Research-EGW Research.menu
-rw------- 1 alrick alrick 598 May 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-EGW Research-Online Support Session.menu
-rw------- 1 alrick alrick 598 May 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-EGW Research-Uninstall EGW Research.menu
-rw------- 1 alrick alrick 599 May 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-EGW Research-View Keyboard Shortcuts.menu
-rw------- 1 alrick alrick 592 May 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-EGW Research-View Readme File.menu
-rw------- 1 alrick alrick 616 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Access 2007.menu
-rw------- 1 alrick alrick 615 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Excel 2007.menu
-rw------- 1 alrick alrick 618 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office InfoPath 2007.menu
-rw------- 1 alrick alrick 617 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office OneNote 2007.menu
-rw------- 1 alrick alrick 617 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Outlook 2007.menu
-rw------- 1 alrick alrick 620 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office PowerPoint 2007.menu
-rw------- 1 alrick alrick 619 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Publisher 2007.menu
-rw------- 1 alrick alrick 828 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Tools-Digital Certificate for VBA Projects.menu
-rw------- 1 alrick alrick 816 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Tools-Microsoft Clip Organizer.menu
-rw------- 1 alrick alrick 831 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Tools-Microsoft Office 2007 Language Settings.menu
-rw------- 1 alrick alrick 820 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Tools-Microsoft Office Diagnostics.menu
-rw------- 1 alrick alrick 824 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Tools-Microsoft Office Picture Manager.menu
-rw------- 1 alrick alrick 614 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Word 2007.menu
-rw------- 1 alrick alrick 565 Mar 24  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-mIRC-IRCIntro Help.menu
-rw------- 1 alrick alrick 561 Mar 24  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-mIRC-mIRC Help.menu
-rw------- 1 alrick alrick 556 Mar 24  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-mIRC-mIRC.menu
-rw------- 1 alrick alrick 562 Mar 24  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-mIRC-Readme.txt.menu
-rw------- 1 alrick alrick 564 Mar 24  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-mIRC-Versions.txt.menu
-rw------- 1 alrick alrick 581 Jul 26  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-WolfQuest-Play WolfQuest.menu
-rw------- 1 alrick alrick 586 Jul 26  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-WolfQuest-Uninstall WolfQuest.menu

```

```
alrick@Home:~$ ls -la $HOME/.local/share/applications/wine
total 20
drwxrwxr-x 3 alrick alrick  4096 Mar 24  2012 .
drwx------ 3 alrick alrick 12288 Sep 22 09:18 ..
drwxrwxr-x 9 alrick alrick  4096 Jul 22 18:36 Programs

```

```
alrick@Home:~$ ls -la $HOME/.local/share/desktop-directories/wine*
-rw-rw-r-- 1 alrick alrick 66 Mar 26  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-Citrix ICA Client.directory
-rw-rw-r-- 1 alrick alrick 57 Mar 24  2012 /home/alrick/.local/share/desktop-directories/wine-Programs.directory
-rw-rw-r-- 1 alrick alrick 61 May 13  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-EGW Research.directory
-rw-rw-r-- 1 alrick alrick 71 Jul 22 18:36 /home/alrick/.local/share/desktop-directories/wine-Programs-Euro Truck Simulator 2.directory
-rw-rw-r-- 1 alrick alrick 64 Jul 22 18:36 /home/alrick/.local/share/desktop-directories/wine-Programs-Euro Truck Simulator 2-Troubleshooting.directory
-rw-rw-r-- 1 alrick alrick 65 Mar 26  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-Microsoft Office.directory
-rw-rw-r-- 1 alrick alrick 71 Mar 26  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-Microsoft Office-Microsoft Office Tools.directory
-rw-rw-r-- 1 alrick alrick 53 Mar 24  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-mIRC.directory
-rw-rw-r-- 1 alrick alrick 58 Jul 26  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-WolfQuest.directory
-rw-rw-r-- 1 alrick alrick 68 Sep 24  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-YS FLIGHT SIMULATOR.directory
-rw-rw-r-- 1 alrick alrick 51 Mar 24  2012 /home/alrick/.local/share/desktop-directories/wine-wine.directory

```

```
alrick@Home:~$ ls -la $HOME/.local/share/icons/????_*.xpm
ls: cannot access /home/alrick/.local/share/icons/????_*.xpm: No such file or directory

```

```
alrick@Home:~$ ls -la .local/share/applications/wine/Programs/
total 40
drwxrwxr-x 9 alrick alrick 4096 Jul 22 18:36 .
drwxrwxr-x 3 alrick alrick 4096 Mar 24  2012 ..
drwxrwxr-x 2 alrick alrick 4096 May  5  2012 Citrix ICA Client
-rw-rw-r-- 1 alrick alrick  422 May  1  2012 Citrix Receiver.desktop
drwxrwxr-x 2 alrick alrick 4096 May 13  2012 EGW Research
drwxrwxr-x 3 alrick alrick 4096 Aug 27 20:42 Euro Truck Simulator 2
drwxrwxr-x 3 alrick alrick 4096 Mar 26  2012 Microsoft Office
drwxrwxr-x 2 alrick alrick 4096 Mar 24  2012 mIRC
drwxrwxr-x 2 alrick alrick 4096 Jul 26  2012 WolfQuest
drwxrwxr-x 2 alrick alrick 4096 Aug 27 20:42 YS FLIGHT SIMULATOR

```

```
alrick@Home:~$ wine* 
wine*: command not found

```

```
alrick@Home:~$ wine-gecko*
wine-gecko*: command not found

```

---

### Post by Bashing-om on 2013-10-07
blueboy1; Looking Outstanding from the package manager's point of view.

OK, Here goes nothing.
```

sudo apt-get remove --purge wine wine1.6-amd64 wine1.6-i386:i386 winetricks

```
and let's see the package manager work some magic !

And that concludes my thinking for this eve. Will resume with a refreshed mind.

[INDENT][INDENT]no step for a stepper, when rested
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-07
It's been a long day, you sure put in a days work. I appreciate. Be fresh my friend. 


```
alrick@Home:~$ sudo apt-get remove --purge wine wine1.6-amd64 wine1.6-i386:i386 winetricks
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages will be REMOVED:
  wine1.6-amd64* wine1.6-i386:i386* winetricks*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 710 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 285388 files and directories currently installed.)
Removing wine1.6-amd64 ...
Purging configuration files for wine1.6-amd64 ...
Removing wine1.6-i386:i386 ...
Purging configuration files for wine1.6-i386:i386 ...
Removing winetricks ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...

```

---

### Post by Bashing-om on 2013-10-07
blueboy1; Got any better we probably could not stand it.

do once more:
```

ls -la $HOME/.wine
ls -la $HOME/.winetrickscache
ls -la $HOME/.config/menus/applications-merged/wine*
ls -la $HOME/.local/share/applications/wine
ls -la $HOME/.local/share/desktop-directories/wine*
ls -la $HOME/.local/share/icons/????_*.xpm
ls -la .local/share/applications/wine/Programs/

``` and let's see if magic has been done.
Also fire up synaptic -really is a great utility - and select "installed" and in the search box see what now returns from the search terms:
> 
wine*
wine-gecko*


will look this over in my AM . See if we are ready to try and (RE-)install Wine !
[INDENT][INDENT]maybe, just maybe[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-07
```
alrick@Home:~$ uname -r
3.2.0-54-generic

```

```
alrick@Home:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        97G  9.8G   83G  11% /
udev            3.7G  4.0K  3.7G   1% /dev
tmpfs           1.5G  1.2M  1.5G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.7G  232K  3.7G   1% /run/shm
/dev/sda1       324M  104M  203M  34% /boot
/dev/sda4       1.2T  122G  967G  12% /home
none            3.7G  2.2M  3.7G   1% /tmp/guest-aeCWSN

```

```
alrick@Home:~$ ls -la $HOME/.wine
total 6960
drwxrwxr-x   4 alrick alrick    4096 Sep 18 09:20 .
drwxr-xr-x 104 alrick alrick   20480 Oct  7 00:36 ..
drwxrwxr-x   2 alrick alrick    4096 Sep 18 09:20 dosdevices
drwxrwxr-x   8 alrick alrick    4096 May 13  2012 drive_c
-rw-rw-r--   1 alrick alrick 6708086 Sep 18 09:20 system.reg
-rw-rw-r--   1 alrick alrick      11 Sep 12 15:11 .update-timestamp
-rw-rw-r--   1 alrick alrick    2169 Mar 26  2012 userdef.reg
-rw-rw-r--   1 alrick alrick  365592 Sep 18 09:20 user.reg
-rw-rw-r--   1 alrick alrick      14 Mar 26  2012 winetricks.log
alrick@Home:~$ #########################################
alrick@Home:~$ ls -la $HOME/.winetrickscache
ls: cannot access /home/alrick/.winetrickscache: No such file or directory
alrick@Home:~$ ##########################################
alrick@Home:~$ ls -la $HOME/.config/menus/applications-merged/wine*
-rw------- 1 alrick alrick 451 May  1  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Citrix Receiver.menu
-rw------- 1 alrick alrick 588 May 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-EGW Research-EGW Research.menu
-rw------- 1 alrick alrick 598 May 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-EGW Research-Online Support Session.menu
-rw------- 1 alrick alrick 598 May 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-EGW Research-Uninstall EGW Research.menu
-rw------- 1 alrick alrick 599 May 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-EGW Research-View Keyboard Shortcuts.menu
-rw------- 1 alrick alrick 592 May 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-EGW Research-View Readme File.menu
-rw------- 1 alrick alrick 616 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Access 2007.menu
-rw------- 1 alrick alrick 615 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Excel 2007.menu
-rw------- 1 alrick alrick 618 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office InfoPath 2007.menu
-rw------- 1 alrick alrick 617 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office OneNote 2007.menu
-rw------- 1 alrick alrick 617 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Outlook 2007.menu
-rw------- 1 alrick alrick 620 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office PowerPoint 2007.menu
-rw------- 1 alrick alrick 619 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Publisher 2007.menu
-rw------- 1 alrick alrick 828 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Tools-Digital Certificate for VBA Projects.menu
-rw------- 1 alrick alrick 816 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Tools-Microsoft Clip Organizer.menu
-rw------- 1 alrick alrick 831 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Tools-Microsoft Office 2007 Language Settings.menu
-rw------- 1 alrick alrick 820 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Tools-Microsoft Office Diagnostics.menu
-rw------- 1 alrick alrick 824 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Tools-Microsoft Office Picture Manager.menu
-rw------- 1 alrick alrick 614 Oct 13  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-Microsoft Office-Microsoft Office Word 2007.menu
-rw------- 1 alrick alrick 565 Mar 24  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-mIRC-IRCIntro Help.menu
-rw------- 1 alrick alrick 561 Mar 24  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-mIRC-mIRC Help.menu
-rw------- 1 alrick alrick 556 Mar 24  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-mIRC-mIRC.menu
-rw------- 1 alrick alrick 562 Mar 24  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-mIRC-Readme.txt.menu
-rw------- 1 alrick alrick 564 Mar 24  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-mIRC-Versions.txt.menu
-rw------- 1 alrick alrick 581 Jul 26  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-WolfQuest-Play WolfQuest.menu
-rw------- 1 alrick alrick 586 Jul 26  2012 /home/alrick/.config/menus/applications-merged/wine-Programs-WolfQuest-Uninstall WolfQuest.menu

```

```
alrick@Home:~$ ls -la $HOME/.local/share/applications/wine
total 20
drwxrwxr-x 3 alrick alrick  4096 Mar 24  2012 .
drwx------ 3 alrick alrick 12288 Sep 22 09:18 ..
drwxrwxr-x 9 alrick alrick  4096 Jul 22 18:36 Programs

```

```
alrick@Home:~$ ls -la $HOME/.local/share/desktop-directories/wine*
-rw-rw-r-- 1 alrick alrick 66 Mar 26  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-Citrix ICA Client.directory
-rw-rw-r-- 1 alrick alrick 57 Mar 24  2012 /home/alrick/.local/share/desktop-directories/wine-Programs.directory
-rw-rw-r-- 1 alrick alrick 61 May 13  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-EGW Research.directory
-rw-rw-r-- 1 alrick alrick 71 Jul 22 18:36 /home/alrick/.local/share/desktop-directories/wine-Programs-Euro Truck Simulator 2.directory
-rw-rw-r-- 1 alrick alrick 64 Jul 22 18:36 /home/alrick/.local/share/desktop-directories/wine-Programs-Euro Truck Simulator 2-Troubleshooting.directory
-rw-rw-r-- 1 alrick alrick 65 Mar 26  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-Microsoft Office.directory
-rw-rw-r-- 1 alrick alrick 71 Mar 26  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-Microsoft Office-Microsoft Office Tools.directory
-rw-rw-r-- 1 alrick alrick 53 Mar 24  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-mIRC.directory
-rw-rw-r-- 1 alrick alrick 58 Jul 26  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-WolfQuest.directory
-rw-rw-r-- 1 alrick alrick 68 Sep 24  2012 /home/alrick/.local/share/desktop-directories/wine-Programs-YS FLIGHT SIMULATOR.directory
-rw-rw-r-- 1 alrick alrick 51 Mar 24  2012 /home/alrick/.local/share/desktop-directories/wine-wine.directory

```

```
alrick@Home:~$ ls -la $HOME/.local/share/icons/????_*.xpm
ls: cannot access /home/alrick/.local/share/icons/????_*.xpm: No such file or directory

```

```
alrick@Home:~$ ls -la .local/share/applications/wine/Programs/
total 40
drwxrwxr-x 9 alrick alrick 4096 Jul 22 18:36 .
drwxrwxr-x 3 alrick alrick 4096 Mar 24  2012 ..
drwxrwxr-x 2 alrick alrick 4096 May  5  2012 Citrix ICA Client
-rw-rw-r-- 1 alrick alrick  422 May  1  2012 Citrix Receiver.desktop
drwxrwxr-x 2 alrick alrick 4096 May 13  2012 EGW Research
drwxrwxr-x 3 alrick alrick 4096 Aug 27 20:42 Euro Truck Simulator 2
drwxrwxr-x 3 alrick alrick 4096 Mar 26  2012 Microsoft Office
drwxrwxr-x 2 alrick alrick 4096 Mar 24  2012 mIRC
drwxrwxr-x 2 alrick alrick 4096 Jul 26  2012 WolfQuest
drwxrwxr-x 2 alrick alrick 4096 Aug 27 20:42 YS FLIGHT SIMULATOR

```

```

```

---

### Post by Bashing-om on 2013-10-07
blueboy1; Looks like "apt-get" was not so magical after all.

Roll our sleeves up and do this manually. 

Will continue this in my AM.

[INDENT][INDENT]But, we can do this
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-07
blueboy1; Hello, my good morning.

As a critical control file is missing, we have to remove wine manually.
Terminal codes:
```

sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save
rm -rf $HOME/.wine
rm -rf $HOME/.winetrickscache
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

```
Some of these will return void, and that is all right.
Now, let's see what else is left on the system, show me the output of terminal code:
```

sudo find / -name "wine*"

```
Here we must use discretion as to what is removed. This "find" command will return ANY instance of a file beginning with "wine" not necessaryily just the ones we are interested in.

[INDENT][INDENT]progressing onward
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-07
Great afternoon my friend, I have some codes for you.

```
alrick@Home:~$ sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
rm: cannot remove `/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list': No such file or directory

```

```
alrick@Home:~$ sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save
```

```
alrick@Home:~$ rm -rf $HOME/.wine

```

```
alrick@Home:~$ rm -rf $HOME/.winetrickscache

```

```
alrick@Home:~$ rm -f $HOME/.config/menus/applications-merged/wine*

```

```
alrick@Home:~$ rm -rf $HOME/.local/share/applications/wine

```

```
alrick@Home:~$ rm -f $HOME/.local/share/desktop-directories/wine*

```

```
alrick@Home:~$ rm -f $HOME/.local/share/icons/????_*.xpm

```

```
alrick@Home:~$ sudo find / -name "wine*"
/usr/share/evolution/3.2/mail-autoconfig/wine.plala.or.jp
/usr/share/app-install/desktop/winetricks:wine-winetricks.desktop
/usr/share/app-install/desktop/wine1.4:wine.desktop
/usr/share/app-install/desktop/winefish:winefish.desktop
/usr/share/app-install/icons/wine.png
/usr/share/app-install/icons/wine-winetricks.png
/usr/share/icons/oxygen/128x128/apps/wine.png
/usr/share/icons/oxygen/22x22/apps/wine.png
/usr/share/icons/oxygen/64x64/apps/wine.png
/usr/share/icons/oxygen/16x16/apps/wine.png
/usr/share/icons/oxygen/32x32/apps/wine.png
/usr/share/icons/oxygen/48x48/apps/wine.png
/usr/share/kde4/apps/katepart/syntax/winehq.xml
/etc/xdg/menus/applications-merged/wine.menu
/home/alrick/.PlayOnLinux/wineprefix
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winepath.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/wineps.drv
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winejoystick.drv
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/wineboot.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/wined3d.dll
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winevdm.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/wineoss.drv
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winebrowser.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winemsibuilder.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winecfg.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winemp3.acm
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winemine.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winegstreamer.dll
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/wineps16.drv
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winemenubuilder.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winefile.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winedevice.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/gecko/1.4/wine_gecko
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/wineconsole.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winedbg.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winemapi.dll
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winex11.drv
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/syswow64/winealsa.drv
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winepath.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/wineps.drv
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winejoystick.drv
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/wineboot.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/wined3d.dll
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/wineoss.drv
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winebrowser.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winemsibuilder.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winecfg.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winemp3.acm
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winemine.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winegstreamer.dll
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winemenubuilder.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winefile.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winedevice.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/gecko/1.4/wine_gecko
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/wineconsole.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winedbg.exe
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winemapi.dll
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winex11.drv
/home/alrick/.PlayOnLinux/wineprefix/mIRC/drive_c/windows/system32/winealsa.drv
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winepath.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/wineps.drv
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winejoystick.drv
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/wineboot.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/wined3d.dll
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winevdm.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/wineoss.drv
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winebrowser.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winemsibuilder.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winecfg.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winemp3.acm
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winemine.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winegstreamer.dll
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/wineps16.drv
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winemenubuilder.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winefile.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winedevice.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/gecko/1.4/wine_gecko
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/wineconsole.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winedbg.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winemapi.dll
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winex11.drv
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/syswow64/winealsa.drv
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winepath.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/wineps.drv
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winejoystick.drv
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/wineboot.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/wined3d.dll
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/wineoss.drv
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winebrowser.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winemsibuilder.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winecfg.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winemp3.acm
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winemine.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winegstreamer.dll
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winemenubuilder.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winefile.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winedevice.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/gecko/1.4/wine_gecko
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/wineconsole.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winedbg.exe
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winemapi.dll
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winex11.drv
/home/alrick/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winealsa.drv
/home/alrick/.PlayOnLinux/plugins/Capture/software/usr/bin64/wine-pthread
/home/alrick/.PlayOnLinux/plugins/Capture/software/usr/bin/wine-pthread
/home/alrick/.PlayOnLinux/plugins/Wine Look/scripts/wine_colors_from_gnome.py
/home/alrick/.PlayOnLinux/wine
/home/alrick/.local/share/applications/wine-extension-ppsm.desktop
/home/alrick/.local/share/applications/wine-extension-vdx.desktop
/home/alrick/.local/share/applications/wine-extension-ica.desktop
/home/alrick/.local/share/applications/wine-extension-mdw.desktop
/home/alrick/.local/share/applications/wine-extension-accdu.desktop
/home/alrick/.local/share/applications/wine-extension-oft.desktop
/home/alrick/.local/share/applications/wine-extension-url.desktop
/home/alrick/.local/share/applications/wine-extension-mag.desktop
/home/alrick/.local/share/applications/wine-extension-txt.desktop
/home/alrick/.local/share/applications/wine-extension-accdc.desktop
/home/alrick/.local/share/applications/wine-extension-mdt.desktop
/home/alrick/.local/share/applications/wine-extension-exc.desktop
/home/alrick/.local/share/applications/wine-extension-docm.desktop
/home/alrick/.local/share/applications/wine-extension-gif.desktop
/home/alrick/.local/share/applications/wine-extension-xlk.desktop
/home/alrick/.local/share/applications/wine-extension-accda.desktop
/home/alrick/.local/share/applications/wine-extension-msg.desktop
/home/alrick/.local/share/applications/wine-extension-xsf.desktop
/home/alrick/.local/share/applications/wine-extension-xsn.desktop
/home/alrick/.local/share/applications/wine-extension-hol.desktop
/home/alrick/.local/share/applications/wine-extension-accdr.desktop
/home/alrick/.local/share/applications/wine-extension-png.desktop
/home/alrick/.local/share/applications/wine-extension-xlm.desktop
/home/alrick/.local/share/applications/wine-extension-ppt.desktop
/home/alrick/.local/share/applications/wine-extension-ics.desktop
/home/alrick/.local/share/applications/wine-extension-emptybinaryregistry.desktop
/home/alrick/.local/share/applications/wine-extension-dqy.desktop
/home/alrick/.local/share/applications/wine-extension-dic.desktop
/home/alrick/.local/share/applications/wine-extension-xltm.desktop
/home/alrick/.local/share/applications/wine-extension-ibc.desktop
/home/alrick/.local/share/applications/wine-extension-rtf.desktop
/home/alrick/.local/share/applications/wine-extension-cr.desktop
/home/alrick/.local/share/applications/wine-extension-mpf.desktop
/home/alrick/.local/share/applications/wine-extension-onetoc.desktop
/home/alrick/.local/share/applications/wine-extension-pptm.desktop
/home/alrick/.local/share/applications/wine-extension-potx.desktop
/home/alrick/.local/share/applications/wine-extension-chm.desktop
/home/alrick/.local/share/applications/wine-extension-pwz.desktop
/home/alrick/.local/share/applications/wine-extension-xlam.desktop
/home/alrick/.local/share/applications/wine-extension-xll.desktop
/home/alrick/.local/share/applications/wine-extension-iqy.desktop
/home/alrick/.local/share/applications/wine-extension-vcs.desktop
/home/alrick/.local/share/applications/wine-extension-wri.desktop
/home/alrick/.local/share/applications/wine-extension-hlp.desktop
/home/alrick/.local/share/applications/wine-extension-docx.desktop
/home/alrick/.local/share/applications/wine-extension-doc.desktop
/home/alrick/.local/share/applications/wine-extension-accde.desktop
/home/alrick/.local/share/applications/wine-extension-mdbhtml.desktop
/home/alrick/.local/share/applications/wine-extension-ppam.desktop
/home/alrick/.local/share/applications/wine-extension-onepkg.desktop
/home/alrick/.local/share/applications/wine-extension-thmx.desktop
/home/alrick/.local/share/applications/wine-extension-htm.desktop
/home/alrick/.local/share/applications/wine-extension-dotx.desktop
/home/alrick/.local/share/applications/wine-extension-slk.desktop
/home/alrick/.local/share/applications/wine-extension-ppsx.desktop
/home/alrick/.local/share/applications/wine-extension-dothtml.desktop
/home/alrick/.local/share/applications/wine-extension-maf.desktop
/home/alrick/.local/share/applications/wine-extension-nfl.desktop
/home/alrick/.local/share/applications/wine-extension-mdn.desktop
/home/alrick/.local/share/applications/wine-extension-one.desktop
/home/alrick/.local/share/applications/wine-extension-ini.desktop
/home/alrick/.local/share/applications/wine-extension-xlthtml.desktop
/home/alrick/.local/share/applications/wine-extension-jpe.desktop
/home/alrick/.local/share/applications/wine-extension-mau.desktop
/home/alrick/.local/share/applications/wine-extension-pothtml.desktop
/home/alrick/.local/share/applications/wine-extension-mad.desktop
/home/alrick/.local/share/applications/wine-extension-dotm.desktop
/home/alrick/.local/share/applications/wine-extension-xlt.desktop
/home/alrick/.local/share/applications/wine-extension-accdb.desktop
/home/alrick/.local/share/applications/wine-extension-sdw.desktop
/home/alrick/.local/share/applications/wine-extension-mav.desktop
/home/alrick/.local/share/applications/wine-extension-xlsx.desktop
/home/alrick/.local/share/applications/wine-extension-ppthtml.desktop
/home/alrick/.local/share/applications/wine-extension-maw.desktop
/home/alrick/.local/share/applications/wine-extension-xla.desktop
/home/alrick/.local/share/applications/wine-extension-mar.desktop
/home/alrick/.local/share/applications/wine-extension-xlw.desktop
/home/alrick/.local/share/applications/wine-extension-mas.desktop
/home/alrick/.local/share/applications/wine-extension-onetoc2.desktop
/home/alrick/.local/share/applications/wine-extension-dot.desktop
/home/alrick/.local/share/applications/wine-extension-xltx.desktop
/home/alrick/.local/share/applications/wine-extension-pot.desktop
/home/alrick/.local/share/applications/wine-extension-jfif.desktop
/home/alrick/.local/share/applications/wine-extension-mde.desktop
/home/alrick/.local/share/applications/wine-extension-wbk.desktop
/home/alrick/.local/share/applications/wine-extension-xevgenxml.desktop
/home/alrick/.local/share/applications/wine-extension-xlsb.desktop
/home/alrick/.local/share/applications/wine-extension-msp.desktop
/home/alrick/.local/share/applications/wine-extension-dochtml.desktop
/home/alrick/.local/share/applications/wine-extension-infopathxml.desktop
/home/alrick/.local/share/applications/wine-extension-potm.desktop
/home/alrick/.local/share/applications/wine-extension-pps.desktop
/home/alrick/.local/share/applications/wine-extension-vsd.desktop
/home/alrick/.local/share/applications/wine-extension-xlshtml.desktop
/home/alrick/.local/share/applications/wine-extension-pptxml.desktop
/home/alrick/.local/share/applications/wine-extension-adn.desktop
/home/alrick/.local/share/applications/wine-extension-ade.desktop
/home/alrick/.local/share/applications/wine-extension-rels.desktop
/home/alrick/.local/share/applications/wine-extension-pptx.desktop
/home/alrick/.local/share/applications/wine-extension-accdt.desktop
/home/alrick/.local/share/applications/wine-extension-csv.desktop
/home/alrick/.local/share/applications/wine-extension-vbs.desktop
/home/alrick/.local/share/applications/wine-extension-ols.desktop
/home/alrick/.local/share/applications/wine-extension-pub.desktop
/home/alrick/.local/share/applications/wine-extension-wizhtml.desktop
/home/alrick/.local/share/applications/wine-extension-nfo.desktop
/home/alrick/.local/share/applications/wine-extension-xls.desktop
/home/alrick/.local/share/applications/wine-extension-xlsm.desktop
/home/alrick/.local/share/applications/wine-extension-xml.desktop
/home/alrick/.local/share/applications/wine-extension-ppa.desktop
/home/alrick/.local/share/applications/wine-extension-mam.desktop
/home/alrick/.local/share/applications/wine-extension-vcf.desktop
/home/alrick/.local/share/applications/wine-extension-mdb.desktop
/home/alrick/.local/share/applications/wine-extension-adp.desktop
/home/alrick/.cache/winetricks
/home/alrick/.config/teamviewer8/logfiles/winelog
/home/alrick/.config/teamviewer8/drive_c/windows/system32/winemenubuilder.exe
/home/alrick/.teamviewer/7/winelog
/home/alrick/.teamviewer/7/drive_c/users/alrick/Application Data/TeamViewer/winelog
/var/lib/dpkg/info/wine1.6.postrm
/var/lib/dpkg/info/wine1.6.list
/tmp/guest-aeCWSN/.config/teamviewer8/drive_c/windows/system32/winemenubuilder.exe
/tmp/guest-aeCWSN/.config/teamviewer8/logfiles/winelog
/opt/teamviewer8/tv_bin/wine
/opt/teamviewer8/tv_bin/wine/lib/wine
/opt/teamviewer8/tv_bin/wine/lib/wine/winedbg.exe.so
/opt/teamviewer8/tv_bin/wine/lib/wine/wineboot.exe.so
/opt/teamviewer8/tv_bin/wine/lib/wine/winemapi.dll.so
/opt/teamviewer8/tv_bin/wine/lib/wine/winecfg.exe.so
/opt/teamviewer8/tv_bin/wine/lib/wine/winealsa.drv.so
/opt/teamviewer8/tv_bin/wine/lib/wine/wined3d.dll.so
/opt/teamviewer8/tv_bin/wine/lib/wine/winex11.drv.so
/opt/teamviewer8/tv_bin/wine/share/wine
/opt/teamviewer8/tv_bin/wine/share/wine/wine.inf
/opt/teamviewer8/tv_bin/wine/drive_c/windows/system32/winemenubuilder.exe
/opt/teamviewer8/tv_bin/wine/bin/wineserver
/opt/teamviewer8/tv_bin/wine/bin/wine
/opt/teamviewer8/tv_bin/wine/bin/wine-preloader

```

---

### Post by Bashing-om on 2013-10-07
blueboy1; Getting squared away;

With "playonlinux" and "teamviewer" installed, I do not know how this is all going to play out when "Wine" is (re-)installed. But continuing in the process of identification -> show me:
```

cat /var/lib/dpkg/info/wine1.6.list

```

and we shall carry on.

[INDENT][INDENT]we still be look'n
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-07
```
alrick@Home:~$ cat /var/lib/dpkg/info/wine1.6.list
/etc
/etc/xdg
/etc/xdg/menus
/etc/xdg/menus/applications-merged
/etc/xdg/menus/applications-merged/wine.menu

```

---

### Post by Bashing-om on 2013-10-07
blueboy1, Things look to be pretty well cleaned up. I do not think the .desktop files and the config files will bother us as I truly expect them to be overwritten in the new install. However,
This bothers me a bit,
> 
/usr/share/kde4/apps/katepart/syntax/winehq.xml
where does (K)ubuntu - kde4- enter into the picture ?

We are fix'n to see what happens.

[INDENT][INDENT]90 yard line and goal to go
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-07
I understand that you are bothered by this, let me know if you need any further response from me.

---

### Post by Bashing-om on 2013-10-07
blueboy1; Well,
Let's see what happens;
```

rm /home/alrick/.cache/winetricks
sudo apt-get install wine

```
[INDENT][INDENT]and take it from there
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-07
```
alrick@Home:~$ rm /home/alrick/.cache/winetricks
rm: cannot remove `/home/alrick/.cache/winetricks': Is a directory

```

```
alrick@Home:~$ sudo apt-get install wine
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  m4 pax rpm librpmbuild2 librpmsign0 ncurses-term
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine-gecko1.4 wine-gecko1.4:i386 wine1.4 wine1.4-amd64 wine1.4-common
  wine1.4-i386:i386 winetricks
Suggested packages:
  dosbox
Recommended packages:
  gettext:i386
The following packages will be REMOVED:
  alien debhelper gettext google-earth-stable intltool-debian lsb-core
  po-debconf
The following NEW packages will be installed:
  wine wine-gecko1.4 wine-gecko1.4:i386 wine1.4 wine1.4-amd64 wine1.4-common
  wine1.4-i386:i386 winetricks
0 upgraded, 8 newly installed, 7 to remove and 0 not upgraded.
Need to get 72.1 MB of archives.
After this operation, 107 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise/multiverse wine-gecko1.4 amd64 1.4.0-0ubuntu2 [14.9 MB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise/multiverse wine-gecko1.4 i386 1.4.0-0ubuntu2 [14.7 MB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise-updates/universe wine1.4-common all 1.4-0ubuntu4.1 [956 B]
Get:4 http://archive.ubuntu.com/ubuntu/ precise-updates/universe wine1.4-amd64 amd64 1.4-0ubuntu4.1 [21.5 MB]
Get:5 http://archive.ubuntu.com/ubuntu/ precise-updates/universe wine1.4-i386 i386 1.4-0ubuntu4.1 [19.9 MB]
Get:6 http://archive.ubuntu.com/ubuntu/ precise-updates/universe wine1.4 amd64 1.4-0ubuntu4.1 [1,064 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ precise/universe winetricks amd64 0.0+20120308 [146 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ precise-updates/universe wine amd64 1.4-0ubuntu4.1 [914 B]
Fetched 72.1 MB in 20s (3,531 kB/s)                                            
Preconfiguring packages ...
(Reading database ... 311558 files and directories currently installed.)
Removing google-earth-stable ...
Removing lsb-core ...
Removing alien ...
Removing debhelper ...
Removing po-debconf ...
Removing intltool-debian ...
Removing gettext ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for doc-base ...
Processing 1 removed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
Selecting previously unselected package wine-gecko1.4.
(Reading database ... 310628 files and directories currently installed.)
Unpacking wine-gecko1.4 (from .../wine-gecko1.4_1.4.0-0ubuntu2_amd64.deb) ...
Selecting previously unselected package wine-gecko1.4:i386.
Unpacking wine-gecko1.4:i386 (from .../wine-gecko1.4_1.4.0-0ubuntu2_i386.deb) ...
Selecting previously unselected package wine1.4-common.
Unpacking wine1.4-common (from .../wine1.4-common_1.4-0ubuntu4.1_all.deb) ...
Selecting previously unselected package wine1.4-amd64.
Unpacking wine1.4-amd64 (from .../wine1.4-amd64_1.4-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package wine1.4-i386:i386.
Unpacking wine1.4-i386:i386 (from .../wine1.4-i386_1.4-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package wine1.4.
Unpacking wine1.4 (from .../wine1.4_1.4-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package winetricks.
Unpacking winetricks (from .../winetricks_0.0+20120308_amd64.deb) ...
Selecting previously unselected package wine.
Unpacking wine (from .../wine_1.4-0ubuntu4.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up wine-gecko1.4 (1.4.0-0ubuntu2) ...
Setting up wine-gecko1.4:i386 (1.4.0-0ubuntu2) ...
Setting up winetricks (0.0+20120308) ...
Setting up wine1.4-common (1.4-0ubuntu4.1) ...
Setting up wine1.4-amd64 (1.4-0ubuntu4.1) ...
Setting up wine1.4-i386:i386 (1.4-0ubuntu4.1) ...
Setting up wine1.4 (1.4-0ubuntu4.1) ...
Setting up wine (1.4-0ubuntu4.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by Bashing-om on 2013-10-07
blueboy1; Looks good !

I did not recognize "/home/alrick/.cache/winetricks" to be a directory. Maybe things worked out anyway.

Try "Wine" now and see if it works .. as well see if there are any problems with "PlayOnLinix" and "teamviewer".
Are we home free ?
[INDENT][INDENT]not over 'till it is over
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-07
We are doing better, the miestro is at it again!!  
When I tried to use say word in Windows it informs me that there is "No Windows program configured to open this type of file." Does that mean the I just need to reinstall Office for Windows again?

-Also Teamviewer works fine. 
-
PlayonLinix, not sure what to test it on. 
Please let me know. We are just about there.

---

### Post by Bashing-om on 2013-10-07
blueboy1; Sorry,


I do not use Wine, and I have no use for Windows. You are now out of my depth (and area of interest). Others will have to advise you further.

Will await further developments.

[INDENT][INDENT]it's ubuntu, all things are possible
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-08
Bashing-om, I know you are limited here. It seems in order for Explorer to work I need to have Wine installed properly.  I am counting on you to help me get pass this step. So I am trying to complete the installation of wine and Explorer. 
Show your smarts like you have always done.

---

### Post by Bashing-om on 2013-10-08
blueboy1; Well;

I expect that Wine is installed fully. We can check.
```

dpkg -l wine
apt-cache policy wine
apt-get check
dpkg -C

```

Then see what there is to do.

[INDENT][INDENT]see what is, is
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-08
Bashing-om, this is what we have,

```
alrick@Home:~$ dpkg -l wine
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  wine           1.4-0ubuntu4.1 Microsoft Windows Compatibility Layer (meta-

```

```
alrick@Home:~$ apt-cache policy wine
wine:
  Installed: 1.4-0ubuntu4.1
  Candidate: 1.4-0ubuntu4.1
  Version table:
 *** 1.4-0ubuntu4.1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.4-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages

```

```
alrick@Home:~$ apt-get check
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

```
alrick@Home:~$ dpkg -C
a
```

---

### Post by Bashing-om on 2013-10-08
blueboy1; My bad.
Must have the authorization to run that command.
```

sudo apt-get check

```

All looks good, seems the problem thus far is not in wine. Perhaps a config file for "explorer" ??

[INDENT][INDENT]seek and ye shall find
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-08
```
alrick@Home:~$ sudo apt-get check
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

---

### Post by Bashing-om on 2013-10-08
blueboy1; All looks good,

I don't think we can point a finger at Wine.
How 'bout this;
Close this thread as "solved" -> wine is installed and functional, and open ->
A new thread in the wine subformum to get the attention of those who are familiar with Wine and it's applications. You will get a much broader audience in the wine subforum.

It's been real, it's been fun
[INDENT][INDENT][INDENT]it's been real fun
[/INDENT][/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-08
power, and promise, to ubuntu nation.

---

