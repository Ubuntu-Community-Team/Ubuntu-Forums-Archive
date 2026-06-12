---
title: "[SOLVED] Help! Cannot install 32-bit libraries!"
date: 2007-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by master_kernel on 2007-09-15
I was trying to install Flash player for Firefox and I had to reinstall the 32-bit libraries because I screwed up /usr/lib32 with 64 bit libs.

Now, when I try to install ia32-libs, dpkg exits with an error.

> xxxxxxx@Ubuntrue:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ia32-libs
The following NEW packages will be installed:
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 17.9MB of archives.
After unpacking 48.8MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main ia32-libs 1.5ubuntu9 [17.9MB]
Fetched 17.9MB in 40s (438kB/s)                                                
(Reading database ... 138465 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_1.5ubuntu9_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb (--unpack):
 unable to create `./usr/lib32/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Could it be that I rm -rf'd /usr/lib32 after uninstalling these libs?
Any help is welcome.

---

### Post by Kilz on 2007-09-15
> **master_kernel said:**
> I was trying to install Flash player for Firefox and I had to reinstall the 32-bit libraries because I screwed up /usr/lib32 with 64 bit libs.

Now, when I try to install ia32-libs, dpkg exits with an error.



Could it be that I rm -rf'd /usr/lib32 after uninstalling these libs?
Any help is welcome.

How did you mess up lib32 with 64bit libs? What exactly did you do. Lets hope you didnt rm the /usr/lib32 folder. Take a look and see if the folder exists.  You should be able to navigate there, or ls -al /usr/lib32 should list contents.

---

### Post by master_kernel on 2007-09-16
> **Kilz said:**
> How did you mess up lib32 with 64bit libs? What exactly did you do. Lets hope you didnt rm the /usr/lib32 folder. Take a look and see if the folder exists.  You should be able to navigate there, or ls -al /usr/lib32 should list contents.

I did, and I'm screwed. I just installed this fresh Feisty 2 days ago. Guess it's time for another one. Here is exactly what I did:

> 
sudo cp -a /usr/lib/* /usr/lib32
Sometime after this....
sudo apt-get remove --purge ia32-libs
sudo rm -rf /usr/lib32
sudo apt-get install ia32-libs

I'm gonna reinstall Feisty today, lately the Gutsy CD has been oversized, and the alternate CD can't detect my network.

Thanks for your help though,
master_kernel

---

### Post by Kilz on 2007-09-16
> **master_kernel said:**
> I did, and I'm screwed. I just installed this fresh Feisty 2 days ago. Guess it's time for another one. Here is exactly what I did:

I'm gonna reinstall Feisty today, lately the Gutsy CD has been oversized, and the alternate CD can't detect my network.

Thanks for your help though,
master_kernel

Ya, that sure did mess up your 32bit libraries.

---

### Post by JIMW428 on 2007-09-16
I seem to have the same problem although I didn't knowingly do anything to remove the 32-bit libraries. The folder is still on my system, but it doesn't contain any recognizable 32-bit files. Is a Feisty re-installation the only way to restore the libraries? I tried this ```
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2 
``` from the Ubuntu guide, but to no avail. This entire process of installing flash on a 64-bit system makes me feel really stupid! This is my first experience with Linux and while in general, I'm very pleased with it,  I feel like it's somewhat incomplete (64-bit) and very fragile. 

I do realize that for knowledgeable users, these are trivial issues, but for a first time newbie they are pretty aggravating.

---

### Post by master_kernel on 2007-09-16
> **JIMW428 said:**
> I seem to have the same problem although I didn't knowingly do anything to remove the 32-bit libraries. The folder is still on my system, but it doesn't contain any recognizable 32-bit files. Is a Feisty re-installation the only way to restore the libraries? I tried this ```
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2 
``` from the Ubuntu guide, but to no avail. This entire process of installing flash on a 64-bit system makes me feel really stupid! This is my first experience with Linux and while in general, I'm very pleased with it,  I feel like it's somewhat incomplete (64-bit) and very fragile. 

I do realize that for knowledgeable users, these are trivial issues, but for a first time newbie they are pretty aggravating.

I'm not sure what happened to yours, but over the past year I've gone through about 20 Feisty reinstalls on my computer. I like to play around with Ubuntu a lot, and it's given me my share of aggravation too.

Anyway, after a fresh install of Feisty, and running Kilz's script, I have Flash.

---

### Post by JIMW428 on 2007-09-16
Are there any tricks for the re-install or do I simply boot from my installation CD?  Do I lose my files?

---

### Post by Kilz on 2007-09-16
> **JIMW428 said:**
> I seem to have the same problem although I didn't knowingly do anything to remove the 32-bit libraries. The folder is still on my system, but it doesn't contain any recognizable 32-bit files. Is a Feisty re-installation the only way to restore the libraries? I tried this ```
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2 
``` from the Ubuntu guide, but to no avail. This entire process of installing flash on a 64-bit system makes me feel really stupid! This is my first experience with Linux and while in general, I'm very pleased with it,  I feel like it's somewhat incomplete (64-bit) and very fragile. 

I do realize that for knowledgeable users, these are trivial issues, but for a first time newbie they are pretty aggravating.

Being that you are so new, exactly how did you come to the conclusion that the files you tried to install didnt? In other words, are you sure the files didnt install?

---

### Post by JIMW428 on 2007-09-16
When I run the code shown above, I receive the following response:

Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ia32-libs-gtk
E: Package ia32-libs has no installation candidate

When I run your flash installation script I get this response:

Selecting previously deselected package nspluginwrapper.
(Reading database ... 104277 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.4_amd64.deb) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on lib32gcc1 (>= 1:4.1.2); however:
  Package lib32gcc1 is not installed.
 nspluginwrapper depends on libc6-i386 (>= 2.5-0ubuntu1); however:
  Package libc6-i386 is not installed.
 nspluginwrapper depends on ia32-libs; however:
  Package ia32-libs is not installed.
 nspluginwrapper depends on ia32-libs-sdl; however:
  Package ia32-libs-sdl is not installed.
 nspluginwrapper depends on ia32-libs-gtk; however:
  Package ia32-libs-gtk is not installed.
 nspluginwrapper depends on linux32; however:
  Package linux32 is not installed.
 nspluginwrapper depends on lib32asound2; however:
  Package lib32asound2 is not installed.
 nspluginwrapper depends on gsfonts-x11; however:
  Package gsfonts-x11 is not installed.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper
--12:47:28--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.210.70
Connecting to fpdownload.macromedia.com|72.247.210.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

100%[====================================>] 2,608,602    872.01K/s             

12:47:31 (869.29 KB/s) - `install_flash_player_9_linux.tar.gz' saved [2608602/2608602]

install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer.xpt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
*** NSPlugin Viewer *** preloader not found
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by Kilz on 2007-09-16
What version of Ubuntu are you running? Secondly, can you look in synaptic and tell me what version of lib32gcc1 is available to be installed. Just do a search. There is a latest version column that will have the version thats available.

---

### Post by JIMW428 on 2007-09-16
I'm running version 7.04, when I search lib32gcc1, nothing is shown in the package window. 
When I scroll thru the packages, it's not listed. When I  reload the packages, I get the following error message:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences. 

These addr are listed in the error msg window

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:) Sub-process gzip returned an error code (1)

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:) Sub-process gzip returned an error code (1)

I'm guessing this is the source of the problem but I'm at a loss as to what to do now.

---

### Post by Kilz on 2007-09-16
> **JIMW428 said:**
> I'm running version 7.04, when I search lib32gcc1, nothing is shown in the package window. 
When I scroll thru the packages, it's not listed. When I  reload the packages, I get the following error message:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences. 

These addr are listed in the error msg window

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:) Sub-process gzip returned an error code (1)

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:) Sub-process gzip returned an error code (1)

I'm guessing this is the source of the problem but I'm at a loss as to what to do now.

It may be that you have a problem with your /etc/apt/sources.list because multiple packages are not showing up.

---

### Post by JIMW428 on 2007-09-16
OK, so what now coach? Does this indicate the need for a re-installation? BTW, thanks for the help.

---

### Post by Kilz on 2007-09-16
> **JIMW428 said:**
> OK, so what now coach? Does this indicate the need for a re-installation? BTW, thanks for the help.

Nope, just copy and past the /etc/apt/sources.list or attach it so we can look at it.

---

### Post by JIMW428 on 2007-09-16
Here goes

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe

---

### Post by Kilz on 2007-09-16
Hmmmm I dont see a problem, but perhaps someone else will. Your list looks like mine (attached). There is aslo a possibility that 
```
sudo apt-get clean 
sudo apt-get install -f
```
could help.

---

### Post by JIMW428 on 2007-09-16
Here are the results. Should I remove the ones that are no longer required? None of this seems to address the issue of the missing 32-bit  libraries. Any thoughts about how to install these?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tclcurl libdigest-md4-perl gstreamer0.10-ffmpeg libgtkglext1
  libcrypt-smbhash-perl libunicode-map-perl libjcode-pm-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Kilz on 2007-09-16
> **JIMW428 said:**
> Here are the results. Should I remove the ones that are no longer required? None of this seems to address the issue of the missing 32-bit  libraries. Any thoughts about how to install these?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tclcurl libdigest-md4-perl gstreamer0.10-ffmpeg libgtkglext1
  libcrypt-smbhash-perl libunicode-map-perl libjcode-pm-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

No, I would leave them. What those commands do is clear out the apt/synaptic cache in case there was a corrupted file and fix the package database in case it got messed up. Its a long shot but sometimes those things can stop packages from installing. Please try and search for lib32gcc1 again.

---

### Post by JIMW428 on 2007-09-17
Still no luck, same result as before. BTW, I searched my source CD as well, and lib32gcc1 isn't there either.

---

### Post by Kilz on 2007-09-17
But we can check the repositoryy/package site and find that [lib32gcc1 is in the repository ]("http://packages.ubuntu.com/feisty/libs/lib32gcc1")main section (not the universe or multiverse). Why you cant install or find it in synaptic is a mystery to me.

---

### Post by Termight on 2007-09-18
Sorry to be a pest, but I'm running into exactly the same problem.  Anyone have *any* idea why it's doing this?

---

### Post by Kilz on 2007-09-18
> **Termight said:**
> Sorry to be a pest, but I'm running into exactly the same problem.  Anyone have *any* idea why it's doing this?

No, if you cant find packages in the main repositories that the Ubuntu package sits says are there its a Ubuntu error. You might want to file a bug report on launchpad stating that the packages cant be found.

Just to be clear, by the same errors, are you saying that you cant find lib32gcc1 in a synaptic search when running the 64bit version of Ubuntu?

---

### Post by JIMW428 on 2007-09-18
I followed the link, downloaded and installed lib32gcc1. I then went to synaptic and guess what, no lib32gcc1. I'm at my wits end and frankly I'm tired of fooling with it. I don't know if it's just my install or a bug somewhere else, but I think I'll just wait for the next release. This one just isn't ready for prime time. I think it's fine for the hobbyist that enjoys the challenge of chasing down and fixing bugs, but for someone that just wants something to use that works, this ain't it. Just a thought, but this is my initial install of Ubuntu, could it be that those who upgraded from a previous version aren't having this problem?

In spite of my frustration and my little rant, I really do appreciate all the help from Kilz, and all the others, who have given their time and efforts to advance the product, and guide nitwits like me through the learning process. Thanks!

---

### Post by Termight on 2007-09-18
Tha packages are there, it just won't let me install them.  When I run:

sudo apt-get install lib32gcc1

I get:

Package lib32gcc1 is not installed.
nspluginwrapper depends on libc6-i386 (>= 2.5-0ubuntu1); however:

---

### Post by Kilz on 2007-09-18
> **JIMW428 said:**
> I followed the link, downloaded and installed lib32gcc1. I then went to synaptic and guess what, no lib32gcc1. I'm at my wits end and frankly I'm tired of fooling with it. I don't know if it's just my install or a bug somewhere else, but I think I'll just wait for the next release. This one just isn't ready for prime time. I think it's fine for the hobbyist that enjoys the challenge of chasing down and fixing bugs, but for someone that just wants something to use that works, this ain't it. Just a thought, but this is my initial install of Ubuntu, could it be that those who upgraded from a previous version aren't having this problem?

In spite of my frustration and my little rant, I really do appreciate all the help from Kilz, and all the others, who have given their time and efforts to advance the product, and guide nitwits like me through the learning process. Thanks!

I understand that you are frustrated. But you honestly cant compare your experiences to anyone elses. You have a problem with the package database. This is telling you that packages you should see in the main repository are not there. You cant say that because you have a bug that no one else seems to have that the distro is not ready. 
By the way, do you have a link to the bug report on launchpad you filed?

---

### Post by Kilz on 2007-09-18
> **Termight said:**
> Tha packages are there, it just won't let me install them.  When I run:

sudo apt-get install lib32gcc1

I get:

Package lib32gcc1 is not installed.
nspluginwrapper depends on libc6-i386 (>= 2.5-0ubuntu1); however:

Then you dont have the same problem. JIMW428 cant even bring them up.
But if sudo apt-get install lib32gcc1 brings up any mention of nspluginwrapper without running the script something isnt right. Can you open up Synaptic, search for lib32gcc1, and please get me the available version of lib32gcc1. Second, exactly what version of Ubuntu are you running.

---

