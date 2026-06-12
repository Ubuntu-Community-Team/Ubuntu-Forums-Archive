---
title: "[Free Gaming] Easy Automatic Installation, without efforts, of CVScedega for Newbies"
date: 2006-06-10
forum: Wine
---

### Post by patrick295767 on 2006-06-10
Hi, 

**======== Update of Sept. 2007 ======version 2.2 =================**
A new version has been released of easy script cvscedega. To install it, just type this in your console:
```
sudo bash
cd /root
apt-get -f -y install flex cvs bison
wget -N http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.2.sh
sh http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.2.sh
exit
```
 
Beware this script is absolutely not Debian in terms of security and so on... Script not supported, but could install cvscedega on your machine :) . 
I just read a bit the thread, and could install cvscedega on my pc. Then, I quickly updated this script.
Now, let's game a bit ! :)

Nota: It will install you cvscedega in /usr/bin/
Enjoy Gaming with Linux 



[B]
working games with cvs/cedega: [http://cedegawiki.sweetleafstudios.com/wiki/Category:Working](http://cedegawiki.sweetleafstudios.com/wiki/Category:Working) (with right config)
======== Update of Jan 2007 ======version 2.1 =================[/B]
now: 

The version 2.1 of the automatic script is ready; you can run the following commands from console:  
[CODE ### version 2.1
sudo su
su 
cd /tmp
wget http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh
sh easy_cvscedega_patrick_version2.1.sh
[/CODE]

Good Luck !!
CVScedega is not so easy to install anymore, flex-old should be USED ! 
 
The script is now updated and working  for any serious distro (I use debian) & any type of GCC ! I am not sure it will work with Ubuntu. There is some troubles reported.

Enjoy gaming & Cvscedega !

Sorry that cvscedega profiles are getting less less easy to be installed
Howto with pics:  [http://patrick295767.pa.funpic.org/cvs.htm](http://patrick295767.pa.funpic.org/cvs.htm)   (sh should be version2.1 as above)


===
On one machine, I get this error 
[http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2582](http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2582)


**======== Long time ago in 2006 =========version 1.0 ==============**
After reading lot of problems to install cvscedega, I finally made a script which can maybe help some of new linux users. (It's also preparing installation of vmware/qt3)
 
Cvs cedega is normally easy to be installed, but even though some installation troubles can be observed.
  
I hope this script effortless will help some of you !
  
To Install cvscedega, without efforts, just type:
(this script is based on the *very great *WineCVS.sh script )
```
sudo bash
cd /root
apt-get -f -y install flex cvs bison
wget -N http://patrick295767.sitesled.com/miniram/easy_cvscedega_patrick.sh
sh easy_cvscedega_patrick.sh
exit
```

  When the [script]("http://patrick295767.sitesled.com/miniram/easy_cvscedega_patrick.sh") is running : get and run the **PROFILE Number _1_**
  
If our gaming master, artificial intelligence, that I thank a lot for his support in this forum, has any updates or improvements, plz do not hesitate to let me know. Thank you !! :-)  I am lazy for making gcc3.4 or gcc4.0 check ... 

Greetings to Linux Users & Gamers,

Patrick
  
  
   
===============    
ADDITIONAL INFORMATION:
===============   
   
Installation Problems &** Screenshots HowToInstall it**:
You can find the installation with screenshots at the following link:
[http://patrick295767.sitesled.com/cvscedega/screenshots_cvscedega.html](http://patrick295767.sitesled.com/cvscedega/screenshots_cvscedega.html)
or there : [http://patrick295767.pa.funpic.org/cvs.htm](http://patrick295767.pa.funpic.org/cvs.htm)
 
===============  
Before starting the installation script above, a clean and standard /etc/apt/sources.list file (for no bug's & problems I mean) is highly recommended.
If you are not sure of this /etc/apt/sources.list file that is present in your Ubuntu Linux Box installation, please do as follows:
  
```
wget http://patrick295767.sitesled.com/miniram/sources.list-dapper
sudo cp sources.list-dapper /etc/apt/sources.list
```
and start the script (above).;) 
  
===============
REFERENCES
===============   
  
[http://doc.gwos.org/index.php/CedegaCVSInstallation](http://doc.gwos.org/index.php/CedegaCVSInstallation)
[http://www.linux-gamers.net/](http://www.linux-gamers.net/)
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+INDEX+Wine+Games&back=HOWTO+Home](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+INDEX+Wine+Games&back=HOWTO+Home)

---

### Post by Runner on 2006-06-10
I tried the script and get this error
-------------------------

Checking out CVS ... May take a while




--------- Error log - file /home/runner/.WineCVS/sources/cvscedega/ErrorLog : ---------
/home/runner/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found


Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Sat Jun 10 19:17:59 EDT 2006
Installation Done
easy_cvscedega_patrick.sh: line 81: ======================: command not found
Type as User: cvscedega
------------------------------------------------------------------

I get the same error any time I try just running just the WineCVS.sh

---

### Post by patrick295767 on 2006-06-11
I corrected the error 81 
and started the script: cvscedega is installed.
  
I checked :
apt-get -f -y install cvs
is into the script too

...

---

### Post by tokez on 2006-06-12
just ran the script on my dapper 6 install and all went well.

however, i had to ```
apt-get install bison flex
``` and rerun the script to make it finish.

---

### Post by Adamant1988 on 2006-06-12
is this script safe? (sorry, I'm newbish).

---

### Post by Perfect Storm on 2006-06-12
```
#/bin/bash
clear
echo "========================="
echo "====== CVS Cedega ======="
echo "========================="
echo "= $(date) Vers.0.1="
echo "= By Patrick            ="
echo "========================="
echo " "
echo " Please make sure you have a correct /etc/apt/sources.list"
echo " "
echo " Preparing the computer:"
echo "Installing several packages for cvscedega, vmware, compiling ..."
echo "  "
apt-get update
################ make install !! ##############"
## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install make konsole
apt-get -f -y install build-essential
## for building, make ... checkinstall
apt-get install -f -y kdevelop kdevelop3-dev build-essential checkinstall
##### amsn  installation
apt-get -f -y install gcc 
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y install linux-headers-$(uname -r)
apt-get -f -y install build-essential 

## voor vmware
apt-get -f -y install make

apt-get -f -y install build-essential
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential 
apt-get -f -y install zenity
apt-get -f -y install linux-tree
apt-get -f -y install g++-3.4
cat /proc/version
ls /usr/bin/gcc*
rm -rf /usr/src/linux
apt-get -f -y install linux-headers-$(uname -r)
ls /usr/bin/gcc*
ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
rm /usr/bin/gccbug
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
CC=/usr/bin/gcc-3.4
export CC
apt-get -f -y install
apt-get -f -y install

######## installing qt3
apt-get -f -y install qt3-dev-tools
apt-get -f -y install qt3-apps-dev
apt-get -f -y install libqt3-headers
apt-get -f -y install qca-dev
apt-get -f -y install libqt3c102-mt
export QTDIR=/usr/share/qt3
##########end ###### make install !! ##############"


####################"
#installing cedega cvs
mkdir /root
mkdir /root/miniram
cd /root/miniram
rm -rf /root/miniram/WineCVS.sh
 wget [http://cvscedega.linux-gamers.net/WineCVS.sh](http://cvscedega.linux-gamers.net/WineCVS.sh)
cp WineCVS.sh WineCVS-linuxgamers.sh
 wget [http://patrick295767.sitesled.com/miniram/WineCVS.sh](http://patrick295767.sitesled.com/miniram/WineCVS.sh)
apt-get -f -y install cvs
apt-get -f -y install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
 apt-get -f -y install  
 apt-get -f -y install  
echo "Please download the profile number 1, and "
echo "run this downloaded profile"
sh WineCVS.sh
date
echo "Installation Done"
echo "====================== "
echo "Type as User: cvscedega"
```

code from the script. Looks harmless enough. What I'm a bit worry about with the script is it it changes /usr/bin/gcc which are symblink to gcc4 to gcc3.

```
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
```

---

### Post by Adamant1988 on 2006-06-12
Well, the script would only allow me to use profile 0 -_-...  so I just went with that... did I make a mistake?

---

### Post by tokez on 2006-06-12
[QUOTE=Adamant1988]Well, the script would only allow me to use profile 0 -_-...  so I just went with that... did I make a mistake?[/QUOTE]

you chose profile 1 for the main part -- then that profile became profile 0

if you did that, then it is correct

---

### Post by Perfect Storm on 2006-06-12
Patrick you should also mention that there's a world to diffrent from the pay version and the CVS version, like CD copy protection support etc.

---

### Post by bekok on 2006-06-23
[s]Patrick, if i go to: [http://winecvs.linux-gamers.net/WineCVS](http://winecvs.linux-gamers.net/WineCVS)
I get a message: Access forbidden! Do i need to get my profile from somewhere else?[/s]

nvm, it worked today :)

---

### Post by patrick295767 on 2006-06-26
[QUOTE=bekok][s]Patrick, if i go to: [http://winecvs.linux-gamers.net/WineCVS](http://winecvs.linux-gamers.net/WineCVS)
I get a message: Access forbidden! Do i need to get my profile from somewhere else?[/s]

nvm, it worked today :)[/QUOTE]

In case there was a prob to get the WineCVS.sh,
I placed into the script another link to be sure to get it.
the script should be workign (updates can be made for gcc) (lack of time)
  
```
rm -rf /root/miniram/WineCVS.sh
 wget http://cvscedega.linux-gamers.net/WineCVS.sh
cp WineCVS.sh WineCVS-linuxgamers.sh
 wget http://patrick295767.sitesled.com/miniram/WineCVS.sh
```

I can see it worked 
```
nvm, it worked today :)
```
I dont know what could have happen :confused: 
It's normally working all time to get the profile. 
  
Enjoy Linux & Gaming !
  
----
As mentioned Artif. Int., cedega non free is far better for gaming.

---

### Post by dom02 on 2006-06-30
I feel dumb asking this but how do u use it once it's done?  I ran the script and it installed with no problems. 

And i'm using Ubuntu 6.06 and it worked fine in case anyone was wondering.

---

### Post by patrick295767 on 2006-07-01
[QUOTE=dom02]I feel dumb asking this but how do u use it once it's done?  I ran the script and it installed with no problems. 

And i'm using Ubuntu 6.06 and it worked fine in case anyone was wondering.[/QUOTE]
  
As said artifi. Int., there is no GUI and automatic configuration.
  
For example, Type in xterm or rxvt ... :
```
cvscedega Setup.Exe
 
cvscedega starcraft.exe             
  
cvscedega bla bla 
```
  
You are now ready for gaming step !! :-) You might have a look on these two Internet links : 
[http://www.linux-gamers.net/modules/wfdownloads/](http://www.linux-gamers.net/modules/wfdownloads/)
[http://www.linux-gamers.net/modules/wiwimod/](http://www.linux-gamers.net/modules/wiwimod/)
  
your installed files will be in ~/.cvscedega
[http://ubuntuforums.org/attachment.php?attachmentid=11993&d=1151692028](http://ubuntuforums.org/attachment.php?attachmentid=11993&d=1151692028)

---

### Post by Cyraxzz on 2006-07-01
Is Cvs cedega non-profit now?

---

### Post by patrick295767 on 2006-07-01
[QUOTE=Cyraxzz]Is Cvs cedega non-profit now?[/QUOTE]
 
non-profit ... not sure 
  
but It is Free

---

### Post by Cyraxzz on 2006-07-01
A line from your shell script

```
"Please make sure you have a correct /etc/apt/sources.list"
```

What do you mean by a "correct sources list"? are there any repositories that I should add?, so this will install properly?

---

### Post by patrick295767 on 2006-07-01
[QUOTE=Cyraxzz]A line from your shell script

```
"Please make sure you have a correct /etc/apt/sources.list"
```

What do you mean by a "correct /etc/apt/sources list"? are there any repositories that I should add?, so this will install properly?[/QUOTE]
  
Some packages deb are installed based on the /etc/apt/sources.list  (dwloaded from the net). 
I would recommand to avoid buggy sources.list, and to have an "" official "" / standard sources.list to be sure the script will work. 
  
In my signature for breezy ubuntu linux:
For dapper: [http://patrick295767.sitesled.com/miniram/sources.list-dapper](http://patrick295767.sitesled.com/miniram/sources.list-dapper)

Greetz
  
= = = = 
If you'd like demos of games: [http://www.gamershell.com/](http://www.gamershell.com/)
can be useful for some of them.
--
Ref. site:
[http://www.linux-gamers.net/modules/wfdownloads/topten.php?list=hit](http://www.linux-gamers.net/modules/wfdownloads/topten.php?list=hit)

---

### Post by Cyraxzz on 2006-07-01
[QUOTE=patrick295767]Some packages deb are installed based on the /etc/apt/sources.list  (dwloaded from the net). 
I would recommand to avoid buggy sources.list, and to have an "" official "" / standard sources.list to be sure the script will work. 
  
In my signature for breezy ubuntu linux:
For dapper: [http://patrick295767.sitesled.com/miniram/sources.list-dapper](http://patrick295767.sitesled.com/miniram/sources.list-dapper)

Greetz
  
= = = = 
If you'd like demos of games: [http://www.gamershell.com/](http://www.gamershell.com/)
can be useful for some of them.[/QUOTE]

thanks

---

### Post by msixp_k7 on 2006-07-02
I ran the script and just look here> --15:07:38--  [http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz](http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz)
  (try: 4) => `defaults.tar.gz'
Connecting to winecvs.linux-gamers.net|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--15:10:51--  [http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz](http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz)
  (try: 5) => `defaults.tar.gz'
Connecting to winecvs.linux-gamers.net|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--15:14:05--  [http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz](http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz)
  (try: 6) => `defaults.tar.gz'
Connecting to winecvs.linux-gamers.net|1.0.0.0|:80...
Did I do something rough!!!

---

### Post by msixp_k7 on 2006-07-02
I think this is better>          root@jose-desktop:/home/jose# sudo bash
root@jose-desktop:/home/jose# cd /root
root@jose-desktop:~# wget -N [http://patrick295767.sitesled.com/miniram/easy_cvscedega_patrick.sh](http://patrick295767.sitesled.com/miniram/easy_cvscedega_patrick.sh)
--14:38:06--  [http://patrick295767.sitesled.com/miniram/easy_cvscedega_patrick.sh](http://patrick295767.sitesled.com/miniram/easy_cvscedega_patrick.sh)
           => `easy_cvscedega_patrick.sh'
Resolving patrick295767.sitesled.com... 216.198.209.150
Connecting to patrick295767.sitesled.com|216.198.209.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,727 (2.7K) [application/x-sh]
Server file no newer than local file `easy_cvscedega_patrick.sh' -- not retrieving.

root@jose-desktop:~# sh easy_cvscedega_patrick.sh

=========================
====== CVS Cedega =======
=========================
= Sun Jul  2 14:38:52 AST 2006 Vers.0.1=
= By Patrick            =
=========================

 Please make sure you have a correct /etc/apt/sources.list

 Preparing the computer:
Installing several packages for cvscedega, vmware, compiling ...

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
99% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to archive.ubuntErr [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg                            p  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Fetched 1B in 6m17s (0B/s)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
make is already the newest version.
konsole is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Package kdevelop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdesdk-scripts
E: Package kdevelop has no installation candidate
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
tcl8.4-dev is already the newest version.
tk8.4-dev is already the newest version.
imlib11-dev is already the newest version.
esound-clients is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-25-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
make is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
zenity is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-tree
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libstdc++6-dev
Suggested packages:
  gcc-3.4-doc lib64stdc++6 libstdc++6-doc
The following NEW packages will be installed:
  g++-3.4 libstdc++6-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3184kB of archives.
After unpacking 12.4MB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libstdc++6-dev 3.4.6-1ubuntu2 [1263kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main g++-3.4 3.4.6-1ubuntu2 [1921kB]
Fetched 3184kB in 2m17s (23.2kB/s)
Selecting previously deselected package libstdc++6-dev.
(Reading database ... 113139 files and directories currently installed.)
Unpacking libstdc++6-dev (from .../libstdc++6-dev_3.4.6-1ubuntu2_i386.deb) ...
Selecting previously deselected package g++-3.4.
Unpacking g++-3.4 (from .../g++-3.4_3.4.6-1ubuntu2_i386.deb) ...
Setting up g++-3.4 (3.4.6-1ubuntu2) ...
Setting up libstdc++6-dev (3.4.6-1ubuntu2) ...
Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
/usr/bin/gcc      /usr/bin/gcc-4.0  /usr/bin/gccbug-3.4
/usr/bin/gcc-3.4  /usr/bin/gccbug   /usr/bin/gccbug-4.0
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-25-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
/usr/bin/gcc      /usr/bin/gcc-4.0  /usr/bin/gccbug-3.4
/usr/bin/gcc-3.4  /usr/bin/gccbug   /usr/bin/gccbug-4.0
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  libqt3-mt-dev
The following NEW packages will be installed:
  qt3-dev-tools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1223kB of archives.
After unpacking 4194kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main qt3-dev-tools 3:3.3.6-1ubuntu6 [1223kB]
Fetched 1223kB in 47s (25.7kB/s)                                               tSelecting previously deselected package qt3-dev-tools.
(Reading database ... 113402 files and directories currently installed.)
Unpacking qt3-dev-tools (from .../qt3-dev-tools_3%3a3.3.6-1ubuntu6_i386.deb) ...Setting up qt3-dev-tools (3.3.6-1ubuntu6) ...

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libaudio-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libgl1-mesa-dev libglu1-mesa-dev liblcms1-dev libmng-dev libqt3-headers
  libqt3-mt-dev libxcursor-dev libxfixes-dev libxft-dev libxinerama-dev
  libxmu-dev libxmu-headers libxrandr-dev libxrender-dev mesa-common-dev
  x11proto-fixes-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xinerama-dev
Suggested packages:
  libqt3-i18n qt3-doc
Recommended packages:
  libqt3-compat-headers
The following NEW packages will be installed:
  libaudio-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libgl1-mesa-dev libglu1-mesa-dev liblcms1-dev libmng-dev libqt3-headers
  libqt3-mt-dev libxcursor-dev libxfixes-dev libxft-dev libxinerama-dev
  libxmu-dev libxmu-headers libxrandr-dev libxrender-dev mesa-common-dev
  qt3-apps-dev x11proto-fixes-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xinerama-dev
0 upgraded, 24 newly installed, 0 to remove and 0 not upgraded.
Need to get 5697kB of archives.
After unpacking 24.8MB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main x11proto-render-dev 1:0.9.2-0ubuntu2 [6090B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libxrender-dev 1:0.9.0.2-0ubuntu2 [23.5kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main x11proto-fixes-dev 1:3.0.2-0ubuntu2 [4858B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libxfixes-dev 1:3.0.1.2-0ubuntu3 [10.7kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libxcursor-dev 1.1.5.2-0ubuntu4 [29.2kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libexpat1-dev 1.95.8-3 [127kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libfontconfig1-dev 2.3.2-1.1ubuntu12 [532kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libfreetype6-dev 2.1.10-1ubuntu2.1 [677kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libxft-dev 2.1.8.2-0ubuntu2 [54.1kB]Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main x11proto-xinerama-dev 1.1.2-0ubuntu2 [4596B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libxinerama-dev 2:1.0.1-0ubuntu2 [3916B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libxmu-headers 2:1.0.0-0ubuntu3 [15.7kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main x11proto-randr-dev 1.1.2-0ubuntu2 [4252B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libxrandr-dev 1:1.1.0.2-0ubuntu4 [14.0kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main mesa-common-dev 6.4.1-0ubuntu8 [167kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libgl1-mesa-dev 6.4.1-0ubuntu8 [46.0kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libglu1-mesa-dev 6.4.1-0ubuntu8 [255kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main liblcms1-dev 1.13-1 [132kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libmng-dev 1.0.8-1 [249kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main libqt3-headers 3:3.3.6-1ubuntu6 [358kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libxmu-dev 2:1.0.0-0ubuntu3 [48.4kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libaudio-dev 1.7-3ubuntu3 [484kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main libqt3-mt-dev 3:3.3.6-1ubuntu6 [49.6kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main qt3-apps-dev 3:3.3.6-1ubuntu6 [2400kB]
Fetched 5697kB in 3m37s (26.2kB/s)
Selecting previously deselected package x11proto-render-dev.
(Reading database ... 113630 files and directories currently installed.)
Unpacking x11proto-render-dev (from .../x11proto-render-dev_1%3a0.9.2-0ubuntu2_all.deb) ...
Selecting previously deselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.0.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a3.0.2-0ubuntu2_all.deb) ...
Selecting previously deselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a3.0.1.2-0ubuntu3_i386.deb) ...
Selecting previously deselected package libxcursor-dev.
Unpacking libxcursor-dev (from .../libxcursor-dev_1.1.5.2-0ubuntu4_i386.deb) ...Selecting previously deselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_1.95.8-3_i386.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.1.10-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.3.2-1.1ubuntu12_i386.deb) ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.1.8.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.1.2-0ubuntu2_all.deb) ...
Selecting previously deselected package libxinerama-dev.
Unpacking libxinerama-dev (from .../libxinerama-dev_2%3a1.0.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package libxmu-headers.
Unpacking libxmu-headers (from .../libxmu-headers_2%3a1.0.0-0ubuntu3_all.deb) ...
Selecting previously deselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.1.2-0ubuntu2_all.deb) ...
Selecting previously deselected package libxrandr-dev.
Unpacking libxrandr-dev (from .../libxrandr-dev_1%3a1.1.0.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_6.4.1-0ubuntu8_all.deb) ...
Selecting previously deselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_6.4.1-0ubuntu8_i386.deb) ...Selecting previously deselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_6.4.1-0ubuntu8_i386.deb) ...
Selecting previously deselected package liblcms1-dev.
Unpacking liblcms1-dev (from .../liblcms1-dev_1.13-1_i386.deb) ...
Selecting previously deselected package libmng-dev.
Unpacking libmng-dev (from .../libmng-dev_1.0.8-1_i386.deb) ...
Selecting previously deselected package libqt3-headers.
Unpacking libqt3-headers (from .../libqt3-headers_3%3a3.3.6-1ubuntu6_i386.deb) ...
Selecting previously deselected package libxmu-dev.
Unpacking libxmu-dev (from .../libxmu-dev_2%3a1.0.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package libaudio-dev.
Unpacking libaudio-dev (from .../libaudio-dev_1.7-3ubuntu3_i386.deb) ...
Selecting previously deselected package libqt3-mt-dev.
Unpacking libqt3-mt-dev (from .../libqt3-mt-dev_3%3a3.3.6-1ubuntu6_i386.deb) ...Selecting previously deselected package qt3-apps-dev.
Unpacking qt3-apps-dev (from .../qt3-apps-dev_3%3a3.3.6-1ubuntu6_i386.deb) ...
Setting up x11proto-render-dev (0.9.2-0ubuntu2) ...
Setting up libxrender-dev (0.9.0.2-0ubuntu2) ...
Setting up x11proto-fixes-dev (3.0.2-0ubuntu2) ...
Setting up libxfixes-dev (3.0.1.2-0ubuntu3) ...
Setting up libxcursor-dev (1.1.5.2-0ubuntu4) ...
Setting up libexpat1-dev (1.95.8-3) ...

Setting up libfreetype6-dev (2.1.10-1ubuntu2.1) ...

Setting up libfontconfig1-dev (2.3.2-1.1ubuntu12) ...
Setting up libxft-dev (2.1.8.2-0ubuntu2) ...
Setting up x11proto-xinerama-dev (1.1.2-0ubuntu2) ...
Setting up libxinerama-dev (1.0.1-0ubuntu2) ...
Setting up libxmu-headers (1.0.0-0ubuntu3) ...
Setting up x11proto-randr-dev (1.1.2-0ubuntu2) ...
Setting up libxrandr-dev (1.1.0.2-0ubuntu4) ...
Setting up mesa-common-dev (6.4.1-0ubuntu8) ...
Setting up libgl1-mesa-dev (6.4.1-0ubuntu8) ...
Setting up libglu1-mesa-dev (6.4.1-0ubuntu8) ...
Setting up liblcms1-dev (1.13-1) ...
Setting up libmng-dev (1.0.8-1) ...
Setting up libqt3-headers (3.3.6-1ubuntu6) ...
Setting up libxmu-dev (1.0.0-0ubuntu3) ...
Setting up libaudio-dev (1.7-3ubuntu3) ...
Setting up libqt3-mt-dev (3.3.6-1ubuntu6) ...
Setting up qt3-apps-dev (3.3.6-1ubuntu6) ...
Reading package lists... Done
Building dependency tree... Done
libqt3-headers is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libqca1c2
The following NEW packages will be installed:
  libqca1c2 qca-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 38.2kB of archives.
After unpacking 193kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libqca1c2 1.0-8 [32.4kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe qca-dev 1.0-8 [5802B]
Fetched 38.2kB in 18s (2014B/s)
Selecting previously deselected package libqca1c2.
(Reading database ... 114903 files and directories currently installed.)
Unpacking libqca1c2 (from .../libqca1c2_1.0-8_i386.deb) ...
Selecting previously deselected package qca-dev.
Unpacking qca-dev (from .../qca-dev_1.0-8_i386.deb) ...
Setting up libqca1c2 (1.0-8) ...

Setting up qca-dev (1.0-8) ...
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
mkdir: cannot create directory `/root': File exists
--14:52:42--  [http://cvscedega.linux-gamers.net/WineCVS.sh](http://cvscedega.linux-gamers.net/WineCVS.sh)
           => `WineCVS.sh'
Resolving cvscedega.linux-gamers.net... 80.67.16.8
Connecting to cvscedega.linux-gamers.net|80.67.16.8|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://linux-gamers.net](http://linux-gamers.net) [following]
--14:53:03--  [http://linux-gamers.net/](http://linux-gamers.net/)
           => `index.html'
Resolving linux-gamers.net... 85.214.36.1
Connecting to linux-gamers.net|85.214.36.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [       <=>                           ] 36,873        24.50K/s

14:53:23 (24.44 KB/s) - `index.html' saved [36873]

cp: cannot stat `WineCVS.sh': No such file or directory
--14:53:23--  [http://patrick295767.sitesled.com/miniram/WineCVS.sh](http://patrick295767.sitesled.com/miniram/WineCVS.sh)
           => `WineCVS.sh'
Resolving patrick295767.sitesled.com... 216.198.209.150
Connecting to patrick295767.sitesled.com|216.198.209.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,438 (4.3K) [application/x-sh]

100%[====================================>] 4,438         23.12K/s

14:53:40 (23.00 KB/s) - `WineCVS.sh' saved [4438/4438]

Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  cvs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1442kB of archives.
After unpacking 3215kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main cvs 1:1.12.9-17 [1442kB]
Fetched 1442kB in 55s (25.9kB/s)
Preconfiguring packages ...
Selecting previously deselected package cvs.
(Reading database ... 114916 files and directories currently installed.)
Unpacking cvs (from .../cvs_1%3a1.12.9-17_i386.deb) ...
Setting up cvs (1.12.9-17) ...

Reading package lists... Done
Building dependency tree... Done
cvs is already the newest version.
build-essential is already the newest version.
E: Couldn't find package x-window-system-dev
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Please download the profile number 1, and
run this downloaded profile

Fetching default scripts:


--14:58:04--  [http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz](http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz)
           => `defaults.tar.gz'
Resolving winecvs.linux-gamers.net... 1.0.0.0
Connecting to winecvs.linux-gamers.net|1.0.0.0|:80...
apt-get run PROFILE Number 1
failed: Connection timed out.
Retrying.

--15:01:14--  [http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz](http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz)
  (try: 2) => `defaults.tar.gz'
Connecting to winecvs.linux-gamers.net|1.0.0.0|:80... rm -rf /root/miniram/WineCVS.sh
 wget [http://cvscedega.linux-gamers.net/WineCVS.sh](http://cvscedega.linux-gamers.net/WineCVS.sh)
cp WineCVS.sh WineCVS-linuxgamers.sh
 wget [http://patrick295767.sitesled.com/miniram/WineCVS.sh](http://patrick295767.sitesled.com/miniram/WineCVS.sh)
failed: Connection timed out.
Retrying.

--15:04:26--  [http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz](http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz)
  (try: 3) => `defaults.tar.gz'
Connecting to winecvs.linux-gamers.net|1.0.0.0|:80... rm -rf /root/miniram/WineCVS.sh
 wget [http://cvscedega.linux-gamers.net/WineCVS.sh](http://cvscedega.linux-gamers.net/WineCVS.sh)
cp WineCVS.sh WineCVS-linuxgamers.sh
 wget [http://patrick295767.sitesled.com/miniram/WineCVS.sh](http://patrick295767.sitesled.com/miniram/WineCVS.sh)
failed: Connection timed out.
Retrying.

--15:07:38--  [http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz](http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz)
  (try: 4) => `defaults.tar.gz'
Connecting to winecvs.linux-gamers.net|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--15:10:51--  [http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz](http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz)
  (try: 5) => `defaults.tar.gz'
Connecting to winecvs.linux-gamers.net|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--15:14:05--  [http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz](http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz)
  (try: 6) => `defaults.tar.gz'
Connecting to winecvs.linux-gamers.net|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--15:17:20--  [http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz](http://winecvs.linux-gamers.net/WineCVS/defaults.tar.gz)
  (try: 7) => `defaults.tar.gz'
Connecting to winecvs.linux-gamers.net|1.0.0.0|:80...

---

### Post by msixp_k7 on 2006-07-02
First!!! Thank you! for your work on this. I got it working its all done! Now I tried to type cvscedega Setup.Exe no such comand. Nubi sorry. Hay Im going to trie this to.ou may find my fvwm (videos & screenshot) :
[http://patrick295767.sitesled.com/fvwm/screenshot05.png](http://patrick295767.sitesled.com/fvwm/screenshot05.png)
[http://patrick295767.sitesled.com/fvwm/.fvwm2rc](http://patrick295767.sitesled.com/fvwm/.fvwm2rc)
(to get the last .fvwm2rc config, please send me an email)
(cheers)

To Install it :
Just run my script Smile (damn cool, no?)
[http://patrick295767.sitesled.com/fvwm/howtoinstallfvwm.htm](http://patrick295767.sitesled.com/fvwm/howtoinstallfvwm.htm)

---

### Post by Somenoob on 2006-07-03
When i am suppose to chose my profile, where and how do i chose profile number 1?

---

### Post by Cyraxzz on 2006-07-03
[QUOTE=Somenoob]When i am suppose to chose my profile, where and how do i chose profile number 1?[/QUOTE]

I had the exact same question,

ok, here is my problem:

I installed cvscedega with that shell script succesfully.

But I was unable to select your suggested profile, i didin't know how to chose one, and the installation ended without a selected profile.

And how good is cvscedega?, as good as the one they charge for?

---

### Post by patrick295767 on 2006-07-04
[QUOTE=Somenoob]When i am suppose to chose my profile, where and how do i chose profile number 1?[/QUOTE]
  
the **first screen** : you choose **profile 1**
  
then, you have to **run it,** then you 'll have to **select 0 **to run it.

then, say **Yes** to the rules and bla bla

bla bla
 
then, you get it installing ... take some time to compile...
 
I guess I'll have to make screenshots ... (lack of time :( )

---

### Post by patrick295767 on 2006-07-04
[QUOTE=tokez]you chose profile 1 for the main part -- then that profile became profile 0

if you did that, then it is correct[/QUOTE]
  
(this is example of right profile selection)
  
If you have time, more than me, you can send me HowTo snapshots/screenshots to add it into the first post of this thread to even be easier:
> sudo apt-get -f -y install ksnapshot
ksnapshot &
  
I hope that'll help & you'll have it installed !! :KS :-)

---

### Post by Somenoob on 2006-07-04
[QUOTE=patrick295767]the **first screen** : you choose **profile 1**
  
then, you have to **run it,** then you 'll have to **select 0 **to run it.

then, say **Yes** to the rules and bla bla

bla bla
 
then, you get it installing ... take some time to compile...
 
I guess I'll have to make screenshots ... (lack of time :( )[/QUOTE]


I get this menu

```
Profile menu

Here you can download new profiles, upgrade existing
or run existing

Command line options : recompile


  g) Get a profile from http://winecvs.linux-gamers.net/WineCVS
  c) Change command line action


=================WineCVS helpsystem (q will quit, b go back)=================

 Make your choice:

```

I type "profile 1" and push "enter" and nothing happends the characters do not even show in the terminal.

---

### Post by patrick295767 on 2006-07-04
[QUOTE=Somenoob]I get this menu

```
Profile menu

Here you can download new profiles, upgrade existing
or run existing

Command line options : recompile


  g) Get a profile from http://winecvs.linux-gamers.net/WineCVS
  c) Change command line action


=================WineCVS helpsystem (q will quit, b go back)=================

 Make your choice:

```

I type "profile 1" and push "enter" and nothing happends the characters do not even show in the terminal.[/QUOTE]
  
try pressing g key (certainly space, to read all the proposed profiles)
then, select profile 1
then, press the right key to run this downloaded profile, then
you ll see the profile in 0 (normally, if you didnt downloaded yet any profile)
and run it
  
Let me know your progress !! :KS ;) :D 
  
The light is soon at the end of the tunnel ! Dont worry !!

---

### Post by Somenoob on 2006-07-05
[QUOTE=patrick295767]try pressing g key (certainly space, to read all the proposed profiles)
then, select profile 1
then, press the right key to run this downloaded profile, then
you ll see the profile in 0 (normally, if you didnt downloaded yet any profile)
and run it
  
Let me know your progress !! :KS ;) :D 
  
The light is soon at the end of the tunnel ! Dont worry !![/QUOTE]

I got the correct profiles, thanks for your help :D

---

### Post by dreadhead90 on 2006-07-06
hmmmm..... i have installed it correctly (or that is what it seems atleast...). i did put it in my home instead of in /root, i thought this wouldn't matter...
and i've tried to install hitman 2 and soldat, and the installation works fine (exept one little thing in the end of the installation of soldat...), but i can't run the games...

> dreadhead@ubuntu:~/.cvscedega/drive_c/Program Files/Eidos Interactive/Hitman 2 Silent Assassin$ cvscedega hitman2.exe
err:module:PE_fixup_imports Module (file) HID.DLL (which is needed by C:\Program Files\Eidos Interactive\Hitman 2 Silent Assassin\p5dll.dll) not found
err:win32:PE_LoadLibraryExA can't load C:\Program Files\Eidos Interactive\Hitman 2 Silent Assassin\p5dll.dll
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\Program Files\Eidos Interactive\Hitman 2 Silent Assassin\p5dll.dll failed, check this file ! (GetLastError 14)
err:module:PE_fixup_imports Module (file) P5DLL.dll (which is needed by C:\Program Files\Eidos Interactive\Hitman 2 Silent Assassin\hitman2.exe) not found


that is what it said about hitman when i tried to start it...

and this is when i try to start soldat:

[IMG]http://img218.imageshack.us/img218/1128/screenshotexceptionraised6su.png[/IMG]

and then if i choose yes or no this comes:

[IMG]http://img81.imageshack.us/img81/1493/screenshotterminaldreadheadubu.png[/IMG]


and if i try to start soldat with wine instead, i come to the main screen followed by a couple of pop-ups whit warnimngs and stuff, and i can't choose any map or anything like it...

anyone???

---

### Post by vem0m on 2006-07-06
another option is pay for a subscription 1-3 months your choice($5 USD/mo) after that time u can still run Cedega with copy protection etc..... FULL VERSION! only thing is tell it to not log in nor look for updates as that is the only thing you won't get after u stop paying still worth getting it to get Full engine support :)

---

### Post by dreadhead90 on 2006-07-07
i also tried et for windows (just to test  a different game:P) and as usuak the installation worked beatifly, but when i start...well se for your selves...

[IMG]http://img142.imageshack.us/img142/3067/screenshotetconsole9ll.png[/IMG]

---

### Post by nickless on 2006-07-07
Hrm I get no sound under Xubuntu. Well Im searching now some Audio How-Tos, but exept cedega my sound works perfektly... hope I won't break it. Is there anything that can be done in the cedega cfg only? :D

---

### Post by dreadhead90 on 2006-07-07
is there any games which works perfectly with cvscedega so i can try some more??

like warcraft 3...is there any prob at all with that one?

---

### Post by gurgle on 2006-07-07
id like to know this as well, thanks.

---

### Post by voiceofxile on 2006-07-07
I have ran the script and it worked. Although after the configuration there is an error in the compile/make routine. I do not know what I should do to correct this error, can anyone assist me please?

```
Compiling ...




--------- Error log - file /home/xile/.WineCVS/sources/cvscedega/ErrorLog : ---------
make[1]: Entering directory `/home/xile/.WineCVS/sources/cvscedega/winex/unicode'
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o casemap.o casemap.c
In file included from ../include/winnt.h:10,
                 from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/basetsd.h:153:3: #error Unknown CPU architecture!
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1035:2: #error You need to define a CONTEXT for your CPU
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1038: error: syntax error before '*' token
../include/winnt.h:1038: warning: type defaults to `int' in declaration of `PCONTEXT'
../include/winnt.h:1038: warning: data definition has no type or storage class
../include/winnt.h:2073: error: syntax error before "PCONTEXT"
../include/winnt.h:2073: warning: no semicolon at end of struct or union
../include/winnt.h:2074: warning: type defaults to `int' in declaration of `EXCEPTION_POINTERS'
../include/winnt.h:2074: warning: type defaults to `int' in declaration of `PEXCEPTION_POINTERS'
../include/winnt.h:2074: warning: data definition has no type or storage class
../include/winnt.h:2086: error: syntax error before "PCONTEXT"
../include/winnt.h:2098: error: syntax error before "ExceptionInfo"
../include/winnt.h:2101: error: syntax error before "epointers"
In file included from ../include/winnls.h:5,
                 from ../include/wine/unicode.h:11,
                 from casemap.c:4:
../include/winbase.h:121: error: syntax error before "LPCONTEXT"
../include/winbase.h:121: warning: type defaults to `int' in declaration of `LPCONTEXT'
../include/winbase.h:121: warning: data definition has no type or storage class
../include/winbase.h:123: error: syntax error before "LPEXCEPTION_POINTERS"
../include/winbase.h:123: warning: type defaults to `int' in declaration of `LPEXCEPTION_POINTERS'
../include/winbase.h:123: warning: data definition has no type or storage class
../include/winbase.h:1366: error: syntax error before "CONTEXT"
../include/winbase.h:1503: warning: type defaults to `int' in declaration of `CONTEXT'
../include/winbase.h:1503: error: syntax error before '*' token
make[1]: *** [casemap.o] Error 1
make[1]: Leaving directory `/home/xile/.WineCVS/sources/cvscedega/winex/unicode'
make: *** [unicode/libwine_unicode.so] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Fri Jul  7 13:49:44 EDT 2006
Installation Done
======================
Type as User: cvscedega
```

---

### Post by Random Roadkill on 2006-07-07
at the end when it tells me to type cvscedega as user it just says
> andy@AndyUbuntu:~$ cvscedega
bash: cvscedega: command not found

any ideas as to how to sort this??

---

### Post by Somenoob on 2006-07-07
```
mern@mern:~$ cvscedega test
bash: cvscedega: command not found
```

I'm pretty sure i installed it correcty, it has a folder and everything :-k

---

### Post by kigina on 2006-07-07
how do i actually launch cvscedega.  i closed the terminal and now i have no idea how to get back to it.

---

### Post by kigina on 2006-07-08
?

---

### Post by vem0m on 2006-07-08
> **dreadhead90 said:**
> is there any games which works perfectly with cvscedega so i can try some more??

like warcraft 3...is there any prob at all with that one?


try ummm World of Warcraft i have no issues with it and its a supported game

---

### Post by kigina on 2006-07-08
nvm i got it

---

### Post by frup on 2006-07-08
Warcraft 3 works in plain wine

---

### Post by Random Roadkill on 2006-07-08
reply to Somenoob and Myself!!
maybe you did the same as me? what i did was press (r) to read basics at the last screen. i then thought i had finished, and quit. But what you should do (i think) is to go back and press (1) to finish the instillation. (I am about to do this now) I will try copying all off the output from the terminal to help othes know what and when to choose stuff. 
Vem0n & Dreadhead: try [http://www.linux-gamers.net/](http://www.linux-gamers.net/) [http://transgaming.org/](http://transgaming.org/) and [http://doc.gwos.org/index.php/Non_Native_Game](http://doc.gwos.org/index.php/Non_Native_Game) for surpported games

---

### Post by dreadhead90 on 2006-07-08
> **vem0m said:**
> try ummm World of Warcraft i have no issues with it and its a supported game

so it's just to put in the cd, cd to the cd and then do (kinda) cvscedega install.exe  and after installation do the cvscedega wow.exe (don't know the files name...) and it should work?

> Warcraft 3 works in plain wine

so it works with cvscedega to then? when i look after compatible games like on transgamings site, which version of cedega should i look for?

---

### Post by Random Roadkill on 2006-07-08
> **dreadhead90 said:**
> 
so it works with cvscedega to then? when i look after compatible games like on transgamings site, which version of cedega should i look for?

unless u have payed for cedega it will be CedegaCVS

Edit: i have just installed cvscedega (i hope), but at the end when it says
> Sat Jul  8 12:24:06 BST 2006
Installation Done
======================
Type as User: cvscedega
root@AndyUbuntu:/root# cvscedega
does it actually mean as user? cos i tryd it as root (as it didnt work as user b4) and it seems to have worked:
> Type as User: cvscedega
root@AndyUbuntu:/root# cvscedega

Enter Path for first Drive (C:) (Default: /home/andy/.cvscedega/drive_c)
Newbies, press enter

Making fake C drive...


Edit the /home/andy/.cvscedega/config file to fit your system

Installing registry...
Done

cvscedega Features:
Reinsert default registry: cvscedega --reregister
Install .reg with regapi:    cvscedega regapi <regfilename.reg>
Install .reg with regedit:   cvscedega regedit [regfilename.reg]
Install a .dll with regedit: cvscedega regsvr32 [filename.dll]
Start winecfg:               cvscedega winecfg
Log to file:                 cvscedega log <normal params>
         eg:                 cvscedega log -debugmsg=+ddraw,+err -- hl.exe -console

Cedega CVS

Usage: /usr/lib/cvscedega/bin/wine [options] [--] program_name [arguments]
The -- has to be used if you specify arguments (of the program)

Options:
   --debugmsg name  Turn debugging-messages on or off
   --dll name       Enable or disable built-in DLLs
   --dosver x.xx    DOS version to imitate (e.g. 6.22)
                    Only valid with --winver win31
   --help,-h        Show this help message
   --managed        Allow the window manager to manage created windows
   --version,-v     Display the Wine version
   --winver         Version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win20,win30,win31)
   --dt             Defer trace until Alt+F12
   --use-dos-cwd    Used to set the DOS current working directory for the process (needs a path)
   --cmdline        Specifies the application's command line
   --monitor-cdrom-eject        Activate monitoring of CD-ROM ejection requests


---

### Post by Random Roadkill on 2006-07-08
maybe it didnt work...*sigh*
maybe you could make your howto slightly more clear as to the exact things to do, patrick??

anyway i put in the Guild Wars disk...which i know is surpported (EDIT: actually no its not lol..)
went to the directry and wel...u can see the rest. any ideas as to the problem??

> andy@AndyUbuntu:/media/cdrom0$ sudo cvscedega setup.exe
err:font:WineEngInit FreeType support is not compiled in to wine, some font functionality will be disabled.
Building font metrics. This may take some time...
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--13-120-75-75-c-70-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--13-120-75-75-c-80-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--14-130-75-75-c-70-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--15-140-75-75-c-90-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--18-120-100-100-c-90-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-semicondensed--13-120-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-o-normal--13-120-75-75-c-70-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-o-normal--13-120-75-75-c-80-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-o-semicondensed--13-120-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--6-60-75-75-c-40-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--7-70-75-75-c-50-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--8-80-75-75-c-50-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--9-90-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--13-120-75-75-c-70-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--13-120-75-75-c-80-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--14-130-75-75-c-70-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--15-140-75-75-c-90-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--18-120-100-100-c-90-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--20-200-75-75-c-100-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-semicondensed--12-110-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
Done building font metrics
err:keyboard:LoadKeyboardLayoutA Only default system keyboard layout supported. Call ignored.
err:bitmap:X11DRV_DIB_CreateShmPixmap pitch mismatch in ShmPixmap creation
err:x11drv:error_handler BadImplementation (server does not implement operation) error (17) for X request 129 minor 5 serial 757 from thread 0x00000002
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  129 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  757
  Current serial number in output stream:  763
err:x11drv:error_handler BadDrawable (invalid Pixmap or Window parameter) error (9) for X request 55 minor 0 serial 760 from thread 0x00000002
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x30000ec
  Serial number of failed request:  760
  Current serial number in output stream:  763


---

### Post by patrick295767 on 2006-07-08
> **Somenoob said:**
> ```
mern@mern:~$ cvscedega test
bash: cvscedega: command not found
```

I'm pretty sure i installed it correcty, it has a folder and everything :-k

back !
  
You should type : 
```
sudo whereis cvscedega 
```
to chekc where / if it is installed.
  
I hope the script could help some persons to install cvscedega. :D 
  
You should get sthg like:
```
whereis cvscedega
cvscedega: /usr/bin/cvscedega /usr/lib/cvscedega /usr/bin/X11/cvscedega

```

---

### Post by patrick295767 on 2006-07-08
There is also a file that is called : 
/usr/lib/transgaming_cedega/.transgaming/config :-#

---

### Post by patrick295767 on 2006-07-08
[http://www.lokigames.com/development/setup-shot.php3](http://www.lokigames.com/development/setup-shot.php3)
  
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+INDEX+Wine+Games&back=HOWTO+Home](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+INDEX+Wine+Games&back=HOWTO+Home)

---

### Post by Random Roadkill on 2006-07-08
ah...i dont seem to have this file
/usr/lib/transgaming_cedega/.transgaming/config
although i know i installed it correctly 

i have installed all the packages suggested on 
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS&back=HOWTO+INDEX+Wine](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS&back=HOWTO+INDEX+Wine)
exept it cant find package:x-window-system-dev
and there is an error with msttcorefonts. i tryed reinstalling this with synpatic and got this error: 
> E: msttcorefonts: subprocess post-installation script returned error exit status 1
any idea what this means??

i dont get it...i have installed exactly as to your instructions, and it just wont work](*,)  plz help a poor depressed person :cry: :cry:

EDIT: sorted...any one else with this problem look [HERE]("http://www.ubuntuforums.org/showthread.php?t=76655&page=2")

---

### Post by patrick295767 on 2006-07-08
> **Random Roadkill said:**
> maybe it didnt work...*sigh*
maybe you could make your howto slightly more clear as to the exact things to do, patrick??

anyway i put in the Guild Wars disk...which i know is surpported 
went to the directry and wel...u can see the rest. any ideas as to the problem??

Hi Roadkill, 
  
The idea of this thread was to install cvscedega for newbies. I will try to make for you guys screenshots as soon as possible. I cant promise exactly when. I'll try within 1-2 weeks to make this howto with screenshots.  
I am glad that this thread helped some of in installing cvscedega. That's a good first step. 

Concerning installing games, for all the existing games, it is now so easy as it can be with cedega Non Free, paying ... & for all the games.
It would be maybe nice to start a thread dedicated only in configuring cvscedega. Maybe (I dont know) ?
  
Greetings.

---

### Post by dreadhead90 on 2006-07-08
is there really such a good suport with the non free cedega?? that's really awsome..

if now just some nicer company could make lika a copy for free to...:P

---

### Post by patrick295767 on 2006-07-08
Ok, Done !!

I made screenshots of the installation to help some of you
(I am uploading them now ... ) 

Installation Problems & Screenshots HowToInstall it:
You can find the installation with screenshots at the following link:
[http://patrick295767.sitesled.com/cvscedega/screenshots_cvscedega.html](http://patrick295767.sitesled.com/cvscedega/screenshots_cvscedega.html)
  
I also added this link into the first post.

 
I hope that will help some of you & make the installation easier !
  
Greetings

---

### Post by Random Roadkill on 2006-07-08
Great guide Patrick especially with the screenshots now!:-D :-D 
mabe I'll actually haveto spend some money!!:-k 
maybe i will start a trouble shooting thread for game instillation on cvscedega...

anyway thanks for all your help

---

### Post by patrick295767 on 2006-07-08
> **Random Roadkill said:**
> Great guide Patrick especially with the screenshots now!:-D :-D 
mabe I'll actually haveto spend some money!!:-k 
maybe i will start a trouble shooting thread for game instillation on cvscedega...

anyway thanks for all your help

  
Look also the great loki installers !! :KS :) 
[http://www.liflg.org/?catid=7](http://www.liflg.org/?catid=7)

---

### Post by Random Roadkill on 2006-07-08
:D :shock::D  nice...i'll try some of them out. Also 'm now using wine which is working fine.

btw Guild Was is not surported on cvs only the pay for cedega, apperantly it is practically impossible to play  using cvscedega

---

### Post by Somenoob on 2006-07-08
> **patrick295767 said:**
> back !
  
You should type : 
```
sudo whereis cvscedega 
```
to chekc where / if it is installed.
  
I hope the script could help some persons to install cvscedega. :D 
  
You should get sthg like:
```
whereis cvscedega
cvscedega: /usr/bin/cvscedega /usr/lib/cvscedega /usr/bin/X11/cvscedega

```

> mern@mern:~$ whereis cvscedega
cvscedega:

I got this output

What did i do wrong?, according to the installation it was installed successfully.

---

### Post by bocmaxima on 2006-07-08
I might be doing this wrong, but I tried to install Warcraft III, and I went to /media/cdrom0

then put in 

```
cvscedega install.exe
```

And got this back

```
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
err:module:BUILTIN_LoadModule loaded .so but dll winealsa.drv still not found

```

Any suggestions?


I think Im just going to DualBoot windows XP, lolz

---

### Post by patrick295767 on 2006-07-08
> **Somenoob said:**
> I got this output

What did i do wrong?, according to the installation it was installed successfully.

It doestn look installed then:
Have a look there : [http://patrick295767.sitesled.com/cvscedega/screenshots_cvscedega.html](http://patrick295767.sitesled.com/cvscedega/screenshots_cvscedega.html)

This might help you

---

### Post by patrick295767 on 2006-07-08
> **bocmaxima said:**
> I might be doing this wrong, but I tried to install Warcraft III, and I went to /media/cdrom0

then put in 

```
cvscedega install.exe
```

And got this back

```
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
err:module:BUILTIN_LoadModule loaded .so but dll winealsa.drv still not found

```

Any suggestions?


I think Im just going to DualBoot windows XP, lolz

  
I would recommand you this way for warcraft III:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Warcraft3&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Warcraft3&back=HOWTO+INDEX+Wine+Games)

:cool:

---

### Post by bocmaxima on 2006-07-09
> **patrick295767 said:**
> I would recommand you this way for warcraft III:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Warcraft3&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Warcraft3&back=HOWTO+INDEX+Wine+Games)

:cool:

I dont get that at all... :(

I had it working in Wine, without a No-CD crack last install, I dont get why all of a sudden Im getting a nasty string of errors, and CVSCedega doesnt want to install it.

---

### Post by Somenoob on 2006-07-09
I got it to work, the problem was that it required some packages, I worked better on the Konsole terminal.

---

### Post by Somenoob on 2006-07-09
Just one question, is it able to install .exe files desgined for Windows?

Or just execute the games?

---

### Post by vem0m on 2006-07-09
well u have to install them to play them so it does both :P

---

### Post by Somenoob on 2006-07-09
Another problem

```
wine: Unhandled exception, starting debugger...
```

And then i get a message window with this written on it:

```
Unhandled page fault on read access to 0x303edd40 at address 0x1502365e.
Do you wish to debug it?
```

If i debug or not, i get this message from cvscedega: 

```
err:ntdll:MODULE_THREAD_WaitThreadModuleSafe this should never happen. (unless wine crashed)
```

I am trying to run StarCraft.exe(one of my favorite games:D ) and i installed it correctly and succesfully.

How do i fix this debugging problem?

---

### Post by patrick295767 on 2006-07-09
> **Somenoob said:**
> Another problem

```
wine: Unhandled exception, starting debugger...
```

And then i get a message window with this written on it:

```
Unhandled page fault on read access to 0x303edd40 at address 0x1502365e.
Do you wish to debug it?
```

If i debug or not, i get this message from cvscedega: 

```
err:ntdll:MODULE_THREAD_WaitThreadModuleSafe this should never happen. (unless wine crashed)
```

I am trying to run StarCraft.exe(one of my favorite games:D ) and i installed it correctly and succesfully.

How do i fix this debugging problem?

I am running starcraft / broodwar also with Wine
(with cvscedega, it's working great too) 
```
err:ntdll:MODULE_THREAD_WaitThreadModuleSafe this should never happen. (unless wine crashed)
``` ... no easy error msg 
and with wine ? Is it working ?

---

### Post by Somenoob on 2006-07-09
> **patrick295767 said:**
> I am running starcraft / broodwar also with Wine
(with cvscedega, it's working great too) 
```
err:ntdll:MODULE_THREAD_WaitThreadModuleSafe this should never happen. (unless wine crashed)
``` ... no easy error msg 
and with wine ? Is it working ?

With wine i get an error message saying that it needs a required file, and my StarCraft CD may not be in my CD rom drive. But it is in my CD drive.

I should just uninstall Wine, and get the newest version for it, plus check for any extra packages for Wine that supports gaming under wine.

---

### Post by Simest on 2006-07-09
How do I get rid of this thing!? The script doesnt do it and I have not a clue what it changed......

---

### Post by vem0m on 2006-07-09
> **Simest said:**
> How do I get rid of this thing!? The script doesnt do it and I have not a clue what it changed......


get rid of what?

---

### Post by Simest on 2006-07-10
The script provided via the commands above install's something. I tried using the same script to remove it (C and then E) but it does not. How do I get rid of the stuff it installed?

---

### Post by Polygon on 2006-07-10
> **Somenoob said:**
> With wine i get an error message saying that it needs a required file, and my StarCraft CD may not be in my CD rom drive. But it is in my CD drive.

I should just uninstall Wine, and get the newest version for it, plus check for any extra packages for Wine that supports gaming under wine.

winehq has the fix for this:

> 
INE has no trouble with Starcraft and Broodwars' copy protection. If you've installed it and still get the "Insert Starcraft CD" message, make sure your CD-ROM drive is listed in your config - and that it's marked as a CD-rom drive, not a local hard drive.

1) run wine config (winecfg)

2) Click drives. If yours isn't listed, Add it.

3) Select your cdrom drive, click show advanced, then set type to CD-ROM drive.
4) Hit "OK" to save and exit.

If this changes your the drive letter that it was installed from, you might have to run regedit, and manually update this registry key: "HKEY_LOCAL_MACHINE\Software\Blizzard Entertainment\StarCD" to reflect this.


---

### Post by Simest on 2006-07-10
> **Simest said:**
> The script provided via the commands above install's something. I tried using the same script to remove it (C and then E) but it does not. How do I get rid of the stuff it installed?

Nevermind I will just do what I do with Windows......FORMAT!

---

### Post by ramasdf123 on 2006-07-12
i am gettin this error, and i am not sure wat to do next

> Configuring ...


    TIP: You can get basic support for Wine/Cedega by IRC:
    Server: irc.freenode.net
--------- Error log - file /home/rama/.WineCVS/sources/cvscedega/ErrorLog : ---------ine support:  go to channel #winehq
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... /usr/bin/gcc-3.4
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether /usr/bin/gcc-3.4 accepts -g... yes
checking for /usr/bin/gcc-3.4 option to accept ANSI C... none needed
checking how to run the C preprocessor... /usr/bin/gcc-3.4 -E
checking for X... libraries /usr/X11R6/lib, headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for yacc... no
checking for bison... no
checking for yacc... no
configure: error: no suitable bison/yacc found. Please install the 'bison' package.


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


and is it possible for me to uninstall and change back everything it did so i can start over again?

---

### Post by patrick295767 on 2006-07-12
> **ramasdf123 said:**
> i am gettin this error, and i am not sure wat to do next



and is it possible for me to uninstall and change back everything it did so i can start over again?

It's saying that something happened with Bison.
Is your /etc/apt/sources.list   standard .
  
(Normally, the script install bison )

Try maybe this dapper list:
[http://patrick295767.sitesled.com/miniram/sources.list-dapper](http://patrick295767.sitesled.com/miniram/sources.list-dapper)

---

### Post by ramasdf123 on 2006-07-12
> **patrick295767 said:**
> It's saying that something happened with Bison.
Is your /etc/apt/sources.list   standard .
  
(Normally, the script install bison )

Try maybe this dapper list:
[http://patrick295767.sitesled.com/miniram/sources.list-dapper](http://patrick295767.sitesled.com/miniram/sources.list-dapper)

i am new to this, but how would i use that to install it?

---

### Post by Towncivilian on 2006-07-12
Hey,

I get this error:

> 
Compiling ...




--------- Error log - file /home/matt/.WineCVS/sources/cvscedega/ErrorLog : ---------
../include/winbase.h:1503: warning: type defaults to `int' in declaration of `CONTEXT'
../include/winbase.h:1503: error: syntax error before '*' token
/usr/bin/gcc-3.4 -shared -Wl,-soname,libwine_port.so  port.o mmap.o      -ldl -lm  -o libwine_port.so.1.0
rm -f libwine_port.so && ln -s libwine_port.so.1.0 libwine_port.so
make[1]: *** [async.o] Error 1
make[1]: Leaving directory `/home/matt/.WineCVS/sources/cvscedega/winex/server'
make: *** [server/libwineserver.so] Error 2
make: *** Waiting for unfinished jobs....
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o compose.o compose.c
make[1]: *** [casemap.o] Error 1
make[1]: *** Waiting for unfinished jobs....
make[1]: Leaving directory `/home/matt/.WineCVS/sources/cvscedega/winex/port'
In file included from ../include/winnt.h:10,
                 from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from compose.c:4:
../include/basetsd.h:153:3: #error Unknown CPU architecture!
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from compose.c:4:
../include/winnt.h:1035:2: #error You need to define a CONTEXT for your CPU
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from compose.c:4:
../include/winnt.h:1038: error: syntax error before '*' token
../include/winnt.h:1038: warning: type defaults to `int' in declaration of `PCONTEXT'
../include/winnt.h:1038: warning: data definition has no type or storage class
../include/winnt.h:2073: error: syntax error before "PCONTEXT"
../include/winnt.h:2073: warning: no semicolon at end of struct or union
../include/winnt.h:2074: warning: type defaults to `int' in declaration of `EXCEPTION_POINTERS'
../include/winnt.h:2074: warning: type defaults to `int' in declaration of `PEXCEPTION_POINTERS'
../include/winnt.h:2074: warning: data definition has no type or storage class
../include/winnt.h:2086: error: syntax error before "PCONTEXT"
../include/winnt.h:2098: error: syntax error before "ExceptionInfo"
../include/winnt.h:2101: error: syntax error before "epointers"
In file included from ../include/winnls.h:5,
                 from ../include/wine/unicode.h:11,
                 from compose.c:4:
../include/winbase.h:121: error: syntax error before "LPCONTEXT"
../include/winbase.h:121: warning: type defaults to `int' in declaration of `LPCONTEXT'
../include/winbase.h:121: warning: data definition has no type or storage class
../include/winbase.h:123: error: syntax error before "LPEXCEPTION_POINTERS"
../include/winbase.h:123: warning: type defaults to `int' in declaration of `LPEXCEPTION_POINTERS'
../include/winbase.h:123: warning: data definition has no type or storage class
../include/winbase.h:1366: error: syntax error before "CONTEXT"
../include/winbase.h:1503: warning: type defaults to `int' in declaration of `CONTEXT'
../include/winbase.h:1503: error: syntax error before '*' token
make[1]: *** [compose.o] Error 1
make[1]: Leaving directory `/home/matt/.WineCVS/sources/cvscedega/winex/unicode'make: *** [unicode/libwine_unicode.so] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Wed Jul 12 16:36:38 EDT 2006
Installation Done
======================
Type as User: cvscedega
root@mattlinux:/root#


I had to install bison and some other packages to get this far, but this error baffles me.

I'm running on Ubuntu 6.06 amd64. Perhaps this doesn't work on AMD64?

Any ideas?

---

### Post by Perfect Storm on 2006-07-13
> **ramasdf123 said:**
> i am new to this, but how would i use that to install it?

This way:
```
sudo gedit /etc/apt/sources.list
sudo apt-get update
```

---

### Post by patrick295767 on 2006-07-13
> **Artificial Intelligence said:**
> This way:
```
sudo gedit /etc/apt/sources.list
sudo apt-get update
```

I added into the first post of this thread the link to dapper's sources.list. thx.
  
Concerning installations, I might be quoting the msi and dcom 98 links from linux gamers:

To play HL2 for instance, you'll need MSI Microsoft Installers(Installshield/MSI );) 


> Issue:

No 3D accleration with ATI in games



Solution:

$ export LD_PRELOAD=/usr/lib/libGL.so; cvscedega game.exe




--------------------------------------------------------------------------------



Issue:

err:font:WineEngInit FreeType support is not compiled in to wine, some font functionality will be disabled.


Solution:

Install Fontconfig, Freetype2 (libfreetype6) and Freetype2-devel


Here are some more hints about Cedega and Installshield/MSI installers from [http://www.frankscorner.org](http://www.frankscorner.org)



The CVS version of Cedega has no support for Installshield installers, but a lot of games use this installer. To make installation possible you must install the DCOM98 utility.



[B]You can download DCOM98 here:
[http://www.microsoft.com/com/dcom/dcom98/download.asp](http://www.microsoft.com/com/dcom/dcom98/download.asp)
Type $ cvscedega dcom98.exe to install DCOM98.[/B]



**To install .msi (Microsoft Installer) files get [http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe](http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe) and install it with the command You can install Windows Installer by typing $ cvscedega instmsia.exe Now type $ cvscedega msiexec /i somefile.msi and the application will be installed.**


---

### Post by ramasdf123 on 2006-07-13
> **patrick295767 said:**
> I added into the first post of this thread the link to dapper's sources.list. thx.


I did this and still i am getting the same error as before.

---

### Post by Perfect Storm on 2006-07-14
Try see if you can find bison via synaptic package manager then and o it through there.

---

### Post by patrick295767 on 2006-07-14
> **ramasdf123 said:**
> I did this and still i am getting the same error as before.

That's weird. I hope that this:
> Try see if you can find bison via synaptic package manager then and o it through there. will make it...:-k 
  
Could you send me the result of ```
sudo dpkg -l > /root/mypackages.txt 
sudo gedit /root/mypackages.txt &

```of your Ubuntu Linux Box config (I PMed)?

---

### Post by .Maleficus. on 2006-07-17
I just tried installing this, and got the same error that Runner got on the first page.  I installed bison flex, so I want to see if it will finish the install now.  How do I do that?  I couldn't get WineCVS.sh to run again.

Also, is there anything else I need to install besides bison flex?  This is what I get.

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... /usr/bin/gcc-3.4
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether /usr/bin/gcc-3.4 accepts -g... yes
checking for /usr/bin/gcc-3.4 option to accept ANSI C... none needed
checking how to run the C preprocessor... /usr/bin/gcc-3.4 -E
checking for X... libraries /usr/X11R6/lib, headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for yacc... no
checking for bison... no
checking for yacc... no
configure: error: no suitable bison/yacc found. Please install the 'bison' package.
```

This is what I installed.

```
apt-get install bison flex
```

Is that right?  When I type WineCVS.sh I get Command Not Found.

---

### Post by vem0m on 2006-07-17
try typing "sh WineCVS.sh"
if that don't work then try "sudo sh WineCVS.sh"

---

### Post by .Maleficus. on 2006-07-17
I tried both of those and neither worked.

---

### Post by vem0m on 2006-07-17
hmmm u might have to start the compilation over

---

### Post by .Maleficus. on 2006-07-18
Well it installed now, but when I try to run it typing cvscedega I get bash: command not found.

---

### Post by citylife on 2006-07-18
thanks for your knowladge

---

### Post by nickless on 2006-07-20
Installation went fine, but cedega tells me I have insufficient disc space, when I try to install something. Starting non-install .exe's works fine (except the sound, but never mind that for now)
I want to install partypoker and I'm shure I have enough space in my home and the /tmp folder. In google I have found some people with the same error, but no solutions. Any ideas?

edit: Folders are owned be me

---

### Post by Matrix101 on 2006-07-20
Worked perfect thx :D 

The only problem was that bison + flex weren´t installed.

BTW:Why does the script install some parts of KDE?

---

### Post by nalmeth on 2006-07-21
Stuck @ make, different error than others:
```
--------- Error log - file /home/nalmeth/.WineCVS/sources/cvscedega/ErrorLog : ---------
rm -f libwow32.so && ln -s wow32/libwow32.so libwow32.so
rm -f libcabinet.so && ln -s cabinet/libcabinet.so libcabinet.so
make[2]: Entering directory `/home/nalmeth/.WineCVS/sources/cvscedega/winex/dlls/winspool'
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_SPOOL32_ -D_REENTRANT  -o info.o info.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o cpsf.o cpsf.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o cstub.o cstub.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o ndr_marshall.o ndr_marshall.c
ndr_marshall.c: In function `ReadConformance':
ndr_marshall.c:237: warning: int format, ULONG_PTR arg (arg 5)
ndr_marshall.c: In function `ComputeConformance':
ndr_marshall.c:342: warning: int format, ULONG_PTR arg (arg 5)
ld -r  des.o handle.o implglue.o md2.o mpi.o rc2.o rc4.o rsa.o rsaenh.o      -o rsaenh.tmp.o
strip --strip-unneeded rsaenh.tmp.o
LD_LIBRARY_PATH="../../unicode:$LD_LIBRARY_PATH" ../../tools/winebuild/winebuild -fPIC -L../../dlls -sym rsaenh.tmp.o -o rsaenh.spec.c -spec ./rsaenh.spec
./rsaenh.spec:9: could not open .so file for crypt32.dll
make[2]: *** [rsaenh.spec.c] Error 1
make[2]: Leaving directory `/home/nalmeth/.WineCVS/sources/cvscedega/winex/dlls/rsaenh'
make[1]: *** [rsaenh/librsaenh.so] Error 2
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o ndr_midl.o ndr_midl.c
make[1]: *** Waiting for unfinished jobs....
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o ndr_ole.o ndr_ole.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_SPOOL32_ -D_REENTRANT  -o wspool.o wspool.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o ndr_stubless.o ndr_stubless.c
ld -r  info.o wspool.o      -o winspool.drv.tmp.o
strip --strip-unneeded winspool.drv.tmp.o
LD_LIBRARY_PATH="../../unicode:$LD_LIBRARY_PATH" ../../tools/winebuild/winebuild -fPIC -L../../dlls -sym winspool.drv.tmp.o -o winspool.drv.spec.c -spec ./winspool.drv.spec
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpc_binding.o rpc_binding.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_SPOOL32_ -D_REENTRANT  -o winspool.drv.spec.o winspool.drv.spec.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpc_epmap.o rpc_epmap.c
/usr/bin/gcc-3.4 -shared  -Wl,-Bsymbolic winspool.drv.spec.o  info.o wspool.o      -o libwinspool.drv.so -L../../dlls  -L../../library -lwine  -lm
make[2]: Leaving directory `/home/nalmeth/.WineCVS/sources/cvscedega/winex/dlls/winspool'
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpc_message.o rpc_message.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpc_server.o rpc_server.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpcrt4_main.o rpcrt4_main.c
rpc_server.c: In function `RPCRT4_io_thread':
rpc_server.c:278: warning: unused variable `packet'
rpc_server.c: In function `RpcServerRegisterIf2':
rpc_server.c:689: warning: int format, LONG_PTR arg (arg 5)
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpcss_np_client.o rpcss_np_client.c
rpc_server.c: At top level:
rpc_server.c:102: warning: 'RPCRT4_push_packet' defined but not used
rpc_server.c:258: warning: 'RPCRT4_create_worker_if_needed' defined but not used
ld -r  cproxy.o cpsf.o cstub.o ndr_marshall.o ndr_midl.o ndr_ole.o ndr_stubless.o rpc_binding.o rpc_epmap.o rpc_message.o rpc_server.o rpcrt4_main.o rpcss_np_client.o      -o rpcrt4.tmp.o
strip --strip-unneeded rpcrt4.tmp.o
LD_LIBRARY_PATH="../../unicode:$LD_LIBRARY_PATH" ../../tools/winebuild/winebuild -fPIC -L../../dlls -sym rpcrt4.tmp.o -o rpcrt4.spec.c -spec ./rpcrt4.spec
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpcrt4.spec.o rpcrt4.spec.c
/usr/bin/gcc-3.4 -shared  -Wl,-Bsymbolic rpcrt4.spec.o  cproxy.o cpsf.o cstub.o ndr_marshall.o ndr_midl.o ndr_ole.o ndr_stubless.o rpc_binding.o rpc_epmap.o rpc_message.o rpc_server.o rpcrt4_main.o rpcss_np_client.o      -o librpcrt4.so -L../../dlls  -L../../library -lwine -L../../ole -lwine_uuid -lm
make[2]: Leaving directory `/home/nalmeth/.WineCVS/sources/cvscedega/winex/dlls/rpcrt4'
make[1]: Leaving directory `/home/nalmeth/.WineCVS/sources/cvscedega/winex/dlls'
make: *** [dlls] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Fri Jul 21 02:30:41 MDT 2006
Installation Done
======================
Type as User: cvscedega

```
bison and flex installed, had to pick 0 instead of 1 for first option.

Any ideas?

---

### Post by Matrix101 on 2006-07-22
Try to compile it with flex-old

---

### Post by DeemanXu on 2006-07-23
Hi guys.

Managed to get CedegaCVS installed alright, but when i came to installing Anarchy Online i get this, unfotunate Installer Kernel Error: The Installshield Engine (Kernel.exe) could not be launched. (ox80070057).

Would be greatful if any of you good people could shed some light on this.

Dee.
:D

---

### Post by mehaga on 2006-07-28
I can not get past the CVS checkout :( iT says something like 'EOF from server, retrying...'. Help!

---

### Post by rabid9797 on 2006-07-28
scratch taht, i figured it out

---

### Post by ubernoob on 2006-07-30
> **nalmeth said:**
> Stuck @ make, different error than others:
```
--------- Error log - file /home/nalmeth/.WineCVS/sources/cvscedega/ErrorLog : ---------
rm -f libwow32.so && ln -s wow32/libwow32.so libwow32.so
rm -f libcabinet.so && ln -s cabinet/libcabinet.so libcabinet.so
make[2]: Entering directory `/home/nalmeth/.WineCVS/sources/cvscedega/winex/dlls/winspool'
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_SPOOL32_ -D_REENTRANT  -o info.o info.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o cpsf.o cpsf.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o cstub.o cstub.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o ndr_marshall.o ndr_marshall.c
ndr_marshall.c: In function `ReadConformance':
ndr_marshall.c:237: warning: int format, ULONG_PTR arg (arg 5)
ndr_marshall.c: In function `ComputeConformance':
ndr_marshall.c:342: warning: int format, ULONG_PTR arg (arg 5)
ld -r  des.o handle.o implglue.o md2.o mpi.o rc2.o rc4.o rsa.o rsaenh.o      -o rsaenh.tmp.o
strip --strip-unneeded rsaenh.tmp.o
LD_LIBRARY_PATH="../../unicode:$LD_LIBRARY_PATH" ../../tools/winebuild/winebuild -fPIC -L../../dlls -sym rsaenh.tmp.o -o rsaenh.spec.c -spec ./rsaenh.spec
./rsaenh.spec:9: could not open .so file for crypt32.dll
make[2]: *** [rsaenh.spec.c] Error 1
make[2]: Leaving directory `/home/nalmeth/.WineCVS/sources/cvscedega/winex/dlls/rsaenh'
make[1]: *** [rsaenh/librsaenh.so] Error 2
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o ndr_midl.o ndr_midl.c
make[1]: *** Waiting for unfinished jobs....
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o ndr_ole.o ndr_ole.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_SPOOL32_ -D_REENTRANT  -o wspool.o wspool.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o ndr_stubless.o ndr_stubless.c
ld -r  info.o wspool.o      -o winspool.drv.tmp.o
strip --strip-unneeded winspool.drv.tmp.o
LD_LIBRARY_PATH="../../unicode:$LD_LIBRARY_PATH" ../../tools/winebuild/winebuild -fPIC -L../../dlls -sym winspool.drv.tmp.o -o winspool.drv.spec.c -spec ./winspool.drv.spec
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpc_binding.o rpc_binding.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_SPOOL32_ -D_REENTRANT  -o winspool.drv.spec.o winspool.drv.spec.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpc_epmap.o rpc_epmap.c
/usr/bin/gcc-3.4 -shared  -Wl,-Bsymbolic winspool.drv.spec.o  info.o wspool.o      -o libwinspool.drv.so -L../../dlls  -L../../library -lwine  -lm
make[2]: Leaving directory `/home/nalmeth/.WineCVS/sources/cvscedega/winex/dlls/winspool'
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpc_message.o rpc_message.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpc_server.o rpc_server.c
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpcrt4_main.o rpcrt4_main.c
rpc_server.c: In function `RPCRT4_io_thread':
rpc_server.c:278: warning: unused variable `packet'
rpc_server.c: In function `RpcServerRegisterIf2':
rpc_server.c:689: warning: int format, LONG_PTR arg (arg 5)
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpcss_np_client.o rpcss_np_client.c
rpc_server.c: At top level:
rpc_server.c:102: warning: 'RPCRT4_push_packet' defined but not used
rpc_server.c:258: warning: 'RPCRT4_create_worker_if_needed' defined but not used
ld -r  cproxy.o cpsf.o cstub.o ndr_marshall.o ndr_midl.o ndr_ole.o ndr_stubless.o rpc_binding.o rpc_epmap.o rpc_message.o rpc_server.o rpcrt4_main.o rpcss_np_client.o      -o rpcrt4.tmp.o
strip --strip-unneeded rpcrt4.tmp.o
LD_LIBRARY_PATH="../../unicode:$LD_LIBRARY_PATH" ../../tools/winebuild/winebuild -fPIC -L../../dlls -sym rpcrt4.tmp.o -o rpcrt4.spec.c -spec ./rpcrt4.spec
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_RPCRT4_ -D_REENTRANT  -o rpcrt4.spec.o rpcrt4.spec.c
/usr/bin/gcc-3.4 -shared  -Wl,-Bsymbolic rpcrt4.spec.o  cproxy.o cpsf.o cstub.o ndr_marshall.o ndr_midl.o ndr_ole.o ndr_stubless.o rpc_binding.o rpc_epmap.o rpc_message.o rpc_server.o rpcrt4_main.o rpcss_np_client.o      -o librpcrt4.so -L../../dlls  -L../../library -lwine -L../../ole -lwine_uuid -lm
make[2]: Leaving directory `/home/nalmeth/.WineCVS/sources/cvscedega/winex/dlls/rpcrt4'
make[1]: Leaving directory `/home/nalmeth/.WineCVS/sources/cvscedega/winex/dlls'
make: *** [dlls] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Fri Jul 21 02:30:41 MDT 2006
Installation Done
======================
Type as User: cvscedega

```
bison and flex installed, had to pick 0 instead of 1 for first option.

Any ideas?


I think i figured it out... try:
cd .WineCVS/sources/cvscedega/winex/dlls/
sudo make
then go back and run ./WineCVS.sh

that worked for me.

---

### Post by Boneman on 2006-07-30
Ok, I finally got Cedega installed, but I'm having a heck of a time installing games! I tried to install DCOM98, but everytime I do I get this:> matt@Jordan-Home:~/Desktop$ cvscedega DCOM98.EXE
fixme:win32:PE_CreateModule Security directory ignored
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:module:CreateProcessA (E:\IXP000.TMP\install.exe,...): NORMAL_PRIORITY_CLASS ignored
/usr/lib/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804c9dc)
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
err:module:MODULE_LoadLibraryExA Loading of native DLL E:\IXP000.TMP\W95INF16.DLL failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL E:\IXP000.TMP\W95INF16.DLL failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\windows\system32\w95inf16.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\windows\system32\w95inf16.dll failed, check this file ! (GetLastError 193)
fixme:setupapi:SETUPX_CreateStandardLDDs LDID_SRCPATH: what exactly do we have to do here ?
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
err:module:MODULE_LoadLibraryExA Loading of native DLL E:\IXP000.TMP\compobj.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\windows\system32\compobj.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL E:\IXP000.TMP\compobj.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\windows\system32\compobj.dll failed, check this file ! (GetLastError 193)
err:ver:VerQueryValueW called on NE resource!
err:setupapi:SetupDefaultQueueCallbackA copy error 32 "E:\\IXP000.TMP\\compobj.dll" -> "C:\\WINDOWS\\SYSTEM32\\compobj.dll"
err:module:MODULE_LoadLibraryExA Loading of native DLL E:\IXP000.TMP\ole2.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\windows\system32\ole2.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL E:\IXP000.TMP\ole2.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\windows\system32\ole2.dll failed, check this file ! (GetLastError 193)
err:ver:VerQueryValueW called on NE resource!
err:setupapi:SetupDefaultQueueCallbackA copy error 32 "E:\\IXP000.TMP\\ole2.dll" -> "C:\\WINDOWS\\SYSTEM32\\ole2.dll"
err:module:MODULE_LoadLibraryExA Loading of native DLL E:\IXP000.TMP\storage.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\windows\system32\storage.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL E:\IXP000.TMP\storage.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\windows\system32\storage.dll failed, check this file ! (GetLastError 193)
err:ver:VerQueryValueW called on NE resource!
err:setupapi:SetupDefaultQueueCallbackA copy error 32 "E:\\IXP000.TMP\\storage.dll" -> "C:\\WINDOWS\\SYSTEM32\\storage.dll"
err:module:MODULE_LoadLibraryExA Loading of native DLL E:\IXP000.TMP\compobj.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\windows\Sysbckup\compobj.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL E:\IXP000.TMP\compobj.dll failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\windows\Sysbckup\compobj.dll failed, check this file ! (GetLastError 193)
err:ver:VerQueryValueW called on NE resource!
err:setupapi:SetupDefaultQueueCallbackA copy error 32 "E:\\IXP000.TMP\\compobj.dll" -> "C:\\WINDOWS\\Sysbckup\\compobj.dll"
err:module:MODULE_LoadLibraryExA Loading of native DLL E:\IXP000.TMP\dcom98.inf failed, check this file ! (GetLastError 193)
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\windows\inf\dcom98.inf failed, check this file ! (GetLastError 193)
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "E:\\IXP000.TMP\\dcom98.inf" -> "C:\\WINDOWS\\inf\\dcom98.inf"
fixme:setupapi:vcpUICallbackProc16 (0xf9a0, 0705, 0000, 00000000, b7b22f74) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf9a0, 070f, 0000, 00000000, b7b22f74) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf9a0, 0710, 0000, 00000000, b7b22f74) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf9a0, 070b, 0000, 00000000, b7b22f74) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf9a0, 070c, 0000, 00000000, b7b22f74) - semi-stub
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:reg:RegFlushKey (cc): stub


I also then tried to follow up with the .msi installer:> The installer has encounteredand unexpected error installing this package. This may indicate a problem with this package. The error code for this error is 2235

this is what it looks like in the terminal that happens at the same time: > matt@Jordan-Home:~/Desktop$ cvscedega InstMsiA.exe
fixme:win32:PE_CreateModule Security directory ignored
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:module:CreateProcessA (E:\IXP000.TMP\msiinst.exe,...): NORMAL_PRIORITY_CLASS ignored
/usr/lib/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804c9dc)
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:ntdll:NtOpenThreadToken (0xfffffffe,0x00000004,0x00000001,0xb7b21850): stub
fixme:advapi:SetThreadToken ((nil), 0): stub (NT impl. only)
fixme:ntdll:NtQueryInformationToken (00000048,1,0xb7b21688,80,0xb7b216d8): stub
fixme:advapi:SetThreadToken ((nil), cafe): stub (NT impl. only)
fixme:module:CreateProcessA (MsiExec.exe,...): NORMAL_PRIORITY_CLASS ignored
fixme:module:CreateProcessA (MsiExec.exe,...): STARTF_FORCEONFEEDBACK ignored
/usr/lib/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804c9dc)
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:module:CreateProcessA (MsiExec.exe,...): NORMAL_PRIORITY_CLASS ignored
fixme:module:CreateProcessA (MsiExec.exe,...): STARTF_FORCEONFEEDBACK ignored
/usr/lib/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804c9dc)
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:ntdll:NtOpenThreadToken (0xfffffffe,0x00000004,0x00000001,0xb7b20a0c): stub
fixme:advapi:SetThreadToken ((nil), 0): stub (NT impl. only)
fixme:ntdll:NtQueryInformationToken (00000050,1,0xb7b20844,80,0xb7b20894): stub
fixme:advapi:SetThreadToken ((nil), cafe): stub (NT impl. only)
Created not existing system directory 'C:\WINDOWS\Start Menu\Programs\Administrative Tools'
fixme:thread:SetThreadExecutionState (0x80000001): stub, harmless (power management).
fixme:thread:SetThreadExecutionState (0x80000000): stub, harmless (power management).
fixme:module:CreateProcessA (MsiExec.exe,...): NORMAL_PRIORITY_CLASS ignored
fixme:module:CreateProcessA (MsiExec.exe,...): STARTF_FORCEONFEEDBACK ignored
/usr/lib/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804c9dc)
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"


---

### Post by nalmeth on 2006-07-31
> Try to compile it with flex-old
Tried this, and made the installer finish, but can't execute cvscedega at all. Command not found.

Thanks for the tip ubernoob, I guess I'll try that with the current flex.

---

### Post by Matrix101 on 2006-07-31
If the command is not found, it has nothing to do if you compiled it with flex or flex-old. Flex-Old is simply the flex-Version appropiate for cvscedega, because cvscedega was never modified for newer compilers. If you cant execute it, try whereis cvscedega. Then the path to the executable should be shown.

---

### Post by ubernoob on 2006-07-31
I cant find DCOM98 in either [TransGaming.Org Games Database]("http://transgaming.org/gamesdb/") or [the Unofficial TransGaming Wiki]("http://cedegawiki.sweetleafstudios.com/wiki/Main_Page"), so i guess you will have a hard time getting it to work

Edit: never mind. I googled and found out that DCOM98 isn't a game :) And from what i saw, it should be possible to install it. So i guess your up to alot of googling :rolleyes:

---

### Post by patrick295767 on 2006-07-31
DCOM98: 
  
  (the MSI installers is for halflife2)
  
 > Issue:
No 3D accleration with ATI in games
Solution:
$ export LD_PRELOAD=/usr/lib/libGL.so; cvscedega game.exe

--------------------------------------------------------------------------------
Issue:
err:font:WineEngInit FreeType support is not compiled in to wine, some font functionality will be disabled.
Solution:
Install Fontconfig, Freetype2 (libfreetype6) and Freetype2-devel


Here are some more hints about Cedega and Installshield/MSI installers from [http://www.frankscorner.org](http://www.frankscorner.org)



The CVS version of Cedega has no support for Installshield installers, but a lot of games use this installer. To make installation possible you must install the DCOM98 utility.



[B]You can download DCOM98 here:
[http://www.microsoft.com/com/dcom/dcom98/download.asp](http://www.microsoft.com/com/dcom/dcom98/download.asp)
Type $ cvscedega dcom98.exe to install DCOM98.[/B]



**To install .msi (Microsoft Installer) files get [http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe](http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe) and install it with the command You can install Windows Installer by typing $ cvscedega instmsia.exe Now type $ cvscedega msiexec /i somefile.msi and the application will be installed.**

 
(I still didnt have time to look if with bison and flex ... )
(It was working on my machines)
  
Greetings,

(To configure and run the games, the configuration of cvscedega / cedega files are in /usr/ ... lib ) that could help you maybe to exchange working  confs.

---

### Post by ex00r on 2006-08-01
for me its even wors, the WineCVS.sh script doesn't work at all!

```

.
.
.
19:40:25 (12.45 KB/s) - `WineCVS.sh' saved [4438/4438]

Reading package lists... Done
Building dependency tree... Done
cvs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
cvs is already the newest version.
build-essential is already the newest version.
E: Couldn't find package x-window-system-dev
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Please download the profile number 1, and
run this downloaded profile

test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
Tue Aug  1 19:40:27 CEST 2006
Installation Done
======================
Type as User: cvscedega
root@ex00r-desktop:/root# cvscedega
bash: cvscedega: command not found
root@ex00r-desktop:/root#

```

nobody has this problem... i hope you know what this means!

---

### Post by patrick295767 on 2006-08-01
> **ex00r said:**
> for me its even wors, the WineCVS.sh script doesn't work at all!

```

.
.
.
19:40:25 (12.45 KB/s) - `WineCVS.sh' saved [4438/4438]

Reading package lists... Done
Building dependency tree... Done
cvs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
cvs is already the newest version.
build-essential is already the newest version.
E: Couldn't find package x-window-system-dev
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Please download the profile number 1, and
run this downloaded profile

test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
Tue Aug  1 19:40:27 CEST 2006
Installation Done
======================
Type as User: cvscedega
root@ex00r-desktop:/root# cvscedega
bash: cvscedega: command not found
root@ex00r-desktop:/root#

```

nobody has this problem... i hope you know what this means!

The error from the WineCVS.sh script is coming from there  
```
# Functions
# ----------

function Alert()
{
	test -n "$RunsInX" -a -n "`which xkbbell 2>/dev/null`" && ALERT="xkbbell" || ALERT='echo -en \a'
	
	Times=$1
	
	while test "$Times" -gt "0"
	do
		$ALERT
		sleep "0.5"
		Times=$[$Times-1]
	done
	
	return 0
}
```

Hmm, Is everthg and gcc installed ? Try to check your /etc/apt/sources.list before running the script (dwld it from the first post of this thread maybe)
  
Let us know the progresses !

Cheers

---

### Post by ex00r on 2006-08-01
Yea, it's actually pretty weard and i am sure if i'd install a new copy of dapper it would work... But i don't want to set up the whole stuff again.

However, i tried it with your suggested sources.list and got this one (not every package could be installed)

same error as allways. Probably somebody knows what file should be installed:

```
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
make is already the newest version.
konsole is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Package kdevelop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdesdk-scripts
E: Package kdevelop has no installation candidate
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
tcl8.4-dev is already the newest version.
tk8.4-dev is already the newest version.
imlib11-dev is already the newest version.
esound-clients is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-26-k7 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
make is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
zenity is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-tree
Reading package lists... Done
Building dependency tree... Done
g++-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Linux version 2.6.15-26-k7 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Mon Jul 17 20:36:04 UTC 2006
/usr/bin/gcc      /usr/bin/gcc-3.4  /usr/bin/gccbug      /usr/bin/gccbug-3.4
/usr/bin/gcc-3.3  /usr/bin/gcc-4.0  /usr/bin/gccbug-3.3  /usr/bin/gccbug-4.0
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-26-k7 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
/usr/bin/gcc      /usr/bin/gcc-3.4  /usr/bin/gccbug      /usr/bin/gccbug-3.4
/usr/bin/gcc-3.3  /usr/bin/gcc-4.0  /usr/bin/gccbug-3.3  /usr/bin/gccbug-4.0
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
qt3-dev-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
qt3-apps-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
libqt3-headers is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
qca-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
mkdir: cannot create directory `/root': File exists
mkdir: cannot create directory `/root/miniram': File exists
--03:30:10--  http://cvscedega.linux-gamers.net/WineCVS.sh
           => `WineCVS.sh'
Resolving cvscedega.linux-gamers.net... 80.67.16.8
Connecting to cvscedega.linux-gamers.net|80.67.16.8|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://linux-gamers.net [following]
--03:30:10--  http://linux-gamers.net/
           => `index.html.4'
Resolving linux-gamers.net... 85.214.36.1
Connecting to linux-gamers.net|85.214.36.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [     <=>                             ] 36,096        26.71K/s

03:30:13 (26.67 KB/s) - `index.html.4' saved [36096]

cp: cannot stat `WineCVS.sh': No such file or directory
--03:30:13--  http://patrick295767.sitesled.com/miniram/WineCVS.sh
           => `WineCVS.sh'
Resolving patrick295767.sitesled.com... 216.198.209.150
Connecting to patrick295767.sitesled.com|216.198.209.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,438 (4.3K) [application/x-sh]

100%[====================================>] 4,438         13.85K/s

03:30:15 (13.80 KB/s) - `WineCVS.sh' saved [4438/4438]

Reading package lists... Done
Building dependency tree... Done
cvs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
cvs is already the newest version.
build-essential is already the newest version.
E: Couldn't find package x-window-system-dev
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Please download the profile number 1, and
run this downloaded profile

test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
Wed Aug  2 03:30:17 CEST 2006
Installation Done
======================
Type as User: cvscedega
root@ex00r-desktop:/root#

```

linux-tree or libqt3c102-mt? I don't know.

I don't know much about developing, so if somebody knew what package would be necessary for this code line:

```
# Functions
# ----------

function Alert()
{
	test -n "$RunsInX" -a -n "`which xkbbell 2>/dev/null`" && ALERT="xkbbell" || ALERT='echo -en \a'
	
	Times=$1
	
	while test "$Times" -gt "0"
	do
		$ALERT
		sleep "0.5"
		Times=$[$Times-1]
	done
	
	return 0
}
```

Would be great if somebody would know!

Kind regards

---

### Post by spacepirates on 2006-08-02
I've looked through this entire thread,  and still cannot find a solution to the "error in make". please help

"make: *** [library/libwine.so] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Wed Aug  2 21:46:46 EDT 2006
Installation Done
======================
Type as User: cvscedega
root@Fusion:/root# cvscedega test
bash: cvscedega: command not found
"

please help!

---

### Post by ubernoob on 2006-08-03
> **spacepirates said:**
> I've looked through this entire thread,  and still cannot find a solution to the "error in make". please help

"make: *** [library/libwine.so] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Wed Aug  2 21:46:46 EDT 2006
Installation Done
======================
Type as User: cvscedega
root@Fusion:/root# cvscedega test
bash: cvscedega: command not found
"

please help!


Try to go into the directory "library" and run "make" there. If that doesn't fail, you should be able to run the script after that. See my previous answer for an example.

---

### Post by spacepirates on 2006-08-03
I hate to ask this, but i just got dapper drake a few weeks ago, and i have maybe a dozen "lib" directories. including "lib" "lib32" and "lib64". Which one has make in it?

---

### Post by mehaga on 2006-08-03
> **vekaz said:**
> I can not get past the CVS checkout :( iT says something like 'EOF from server, retrying...'. Help!

I just wanted to ask the same question again, hopeing someone will answer this time.

---

### Post by patrick295767 on 2006-08-03
> **ubernoob said:**
> Try to go into the directory "library" and run "make" there. If that doesn't fail, you should be able to run the script after that. See my previous answer for an example.
 
(I dont have linux now to check)
You might try to go in the libraries folder & check whether the libwine.so file is present. It should be normally, but we never knwo.
  
:-k

---

### Post by spacepirates on 2006-08-03
libwine.so is NOT present. nothing libwine is. then again i only checked the three root lib folders and the usr lib folders. so... help?

---

### Post by patrick295767 on 2006-08-04
> **spacepirates said:**
> libwine.so is NOT present. nothing libwine is. then again i only checked the three root lib folders and the usr lib folders. so... help?

(I'll try to have a look asap but cant promise when ?
few days ..)

---

### Post by 1stbyte on 2006-08-05
Does one know how to uninstall cvscedega?

---

### Post by patrick295767 on 2006-08-08
> **spacepirates said:**
> libwine.so is NOT present. nothing libwine is. then again i only checked the three root lib folders and the usr lib folders. so... help?

```
find /usr/lib -name "libwine.so"
/usr/lib/transgaming_cedega/winex/lib/libwine.so
/usr/lib/transgaming_cedega/winex/pthread_lib/libwine.so
```
  
I need cvscedega for the knight onine... I instaling nwo the cvscedega on a freshly installed machine. Let's try to see if I get the same error libwine.so msg .. hmm ?

 
 Done !! it's installed.

```
WineCVS.sh - Progress(u) : Green is current

   0 = Uninstall
   1 = Cleanup
   2 = CVS checkout
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Installing launcher script ...
    Packing sourcetree...
All done ... CVS installed

   Installed as: cvscedega
   Config path : <homedir>/.cvscedega

Tue Aug  8 23:55:13 CEST 2006
Installation Done
======================
Type as User: cvscedega

```
  
Maybe try a fresh instaall dapper
  
----
In order to "prepare" the linux machine, from the server install (clean install), I runned this before running the script:
apt-get -f -y install wine
  
or also a slight minimum (useful for me):
```

apt-get update
################ make install !! #############
## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install tcl8.4 
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev

## for building, make ... checkinstall
apt-get install -f -y kdevelop kdevelop3-dev build-essential checkinstall

##### amsn  installation
apt-get -f -y install gcc 
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y install linux-headers-$(uname -r)
apt-get -f -y install build-essential 


## voor vmware
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential 
apt-get -f -y install zenity
apt-get -f -y install linux-tree
apt-get -f -y install g++-3.4
cat /proc/version
ls /usr/bin/gcc*
rm -rf /usr/src/linux
apt-get -f -y install linux-headers-$(uname -r)
ls /usr/bin/gcc*
ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
rm /usr/bin/gccbug
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
CC=/usr/bin/gcc-3.4
export CC
apt-get -f -y install
apt-get -f -y install

######## installing qt3
apt-get -f -y install qt3-dev-tools
apt-get -f -y install qt3-apps-dev
apt-get -f -y install libqt3-headers
apt-get -f -y install qca-dev
apt-get -f -y install libqt3c102-mt
export QTDIR=/usr/share/qt3

##########end ###### make install !! ##############



```
  
I hope that this will help you to make it installed.

GReetings

---

### Post by Darth Lukan on 2006-08-09
I have errors with the script that reference my architecture.  I am running amd64 and the packages return bad arch errors. is there a command that i can use with the script that force install despite differing arch? I tried entering some --help arguments but they all returned errors or just did not appear.

---

### Post by patrick295767 on 2006-08-10
> **Darth Lukan said:**
> I have errors with the script that reference my architecture.  I am running amd64 and the packages return bad arch errors. is there a command that i can use with the script that force install despite differing arch? I tried entering some --help arguments but they all returned errors or just did not appear.
 
to force installing is not recommanded.
Concerning the architecture, dont know much with AMD. 

it shouldnt come from apt-get but maybe the script
bump
try to look more in details about recommandadtion for such architecture.
( It's long time I stop having AMD proc. I wasnt satisfied sorry)

---

### Post by Darth Lukan on 2006-08-10
No worries no rush.  The specific error was in make, I checked the output and log and the issue is that the script is utilizing the 32bit shared libs as opposed to just 64bit native ones.  There is nothing that I can do about it because of the obvious incompatability with the two archs.  I checked transgaming's website and they do not mention support for 64 bit OS's at all, so i am assuming that they do not support it until I am proven otherwise.  Thanks for the quick reply though!

---

### Post by patrick295767 on 2006-08-14
Working with cvscedega :
(For me, faster than with Wine)
(Games are running very well, but you need to configure the guy, and use some command lines sometimes & edit to change cdrom drives, windows versions)
(cd protections with genuine isntall cd are not working sometimes, unfortunately *...* )
It's not soo easy as non-free cedega, which is far far better & easier game playign software for linux. 
  
[I]Starcraft
1st person shooter games
Broodwar
Age of Empire 1
Age of Empire Conqueror
Alice Mc Gee
Grand theft Auto : vice city
Jedi Knight
Jedi knight II 
Dark thieft
...
 
  
Apps are also runnning faster than wine
but the compatibitliy is not soo good as wine
dictionaries
softwares
...[/I]
  

With knightonline, I couldnt make it yet, unfortunately.
For san andreas, gta, I still have to try this:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+GTA+SA&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+GTA+SA&back=HOWTO+INDEX+Wine+Games)

---

### Post by kepos on 2006-08-18
Can someone **PLEASE** help me.
I would really like cedega but script doesn't wotk for me.

when it comes to checkout it says:
EOF from server, retrying...

i see, someone already posted same question,but no response.

anyone? **please**!

---

### Post by mr.champagne on 2006-08-29
yay thx for the script no i can pwn once again
no offense to the linux game developers but i would rather see their stuff in stores than in synaptic

---

### Post by chambo on 2006-09-02
Compiling ...




--------- Error log - file /home/rox/.WineCVS/sources/cvscedega/ErrorLog : ---------
make[1]: se ingresa al directorio `/home/rox/.WineCVS/sources/cvscedega/winex/unicode'
/usr/bin/gcc-3.4 -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT  -o casemap.o casemap.c
En el fichero incluído de ../include/winnt.h:10,
                 de ../include/windef.h:16,
                 de ../include/wine/unicode.h:10,
                 de casemap.c:4:
../include/basetsd.h:153:3: #error Unknown CPU architecture!
En el fichero incluído de ../include/windef.h:16,
                 de ../include/wine/unicode.h:10,
                 de casemap.c:4:
../include/winnt.h:1035:2: #error You need to define a CONTEXT for your CPU
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1038: error: error sintáctico antes del elemento '*'
../include/winnt.h:1038: aviso: el tipo de dato por defecto es `int' en la declaración de `PCONTEXT'
../include/winnt.h:1038: aviso: la definición de datos no tiene tipo o clase de almacenamiento
../include/winnt.h:2073: error: error sintáctico antes de "PCONTEXT"
../include/winnt.h:2073: aviso: no hay punto y coma al final del struct o union
../include/winnt.h:2074: aviso: el tipo de dato por defecto es `int' en la declaración de `EXCEPTION_POINTERS'
../include/winnt.h:2074: aviso: el tipo de dato por defecto es `int' en la declaración de `PEXCEPTION_POINTERS'
../include/winnt.h:2074: aviso: la definición de datos no tiene tipo o clase de almacenamiento
../include/winnt.h:2086: error: error sintáctico antes de "PCONTEXT"
../include/winnt.h:2098: error: error sintáctico antes de "ExceptionInfo"
../include/winnt.h:2101: error: error sintáctico antes de "epointers"
In file included from ../include/winnls.h:5,
                 from ../include/wine/unicode.h:11,
                 from casemap.c:4:
../include/winbase.h:121: error: error sintáctico antes de "LPCONTEXT"
../include/winbase.h:121: aviso: el tipo de dato por defecto es `int' en la declaración de `LPCONTEXT'
../include/winbase.h:121: aviso: la definición de datos no tiene tipo o clase de almacenamiento
../include/winbase.h:123: error: error sintáctico antes de "LPEXCEPTION_POINTERS"
../include/winbase.h:123: aviso: el tipo de dato por defecto es `int' en la declaración de `LPEXCEPTION_POINTERS'
../include/winbase.h:123: aviso: la definición de datos no tiene tipo o clase de almacenamiento
../include/winbase.h:1370: error: error sintáctico antes de "CONTEXT"
../include/winbase.h:1510: aviso: el tipo de dato por defecto es `int' en la declaración de `CONTEXT'
../include/winbase.h:1510: error: error sintáctico antes del elemento '*'
make[1]: *** [casemap.o] Error 1
make[1]: se sale del directorio `/home/rox/.WineCVS/sources/cvscedega/winex/unicode'
make: *** [unicode/libwine_unicode.so] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


sáb sep  2 00:21:54 CLT 2006
Installation Done

](*,)  help me, i don't know that do

---

### Post by patrick295767 on 2007-01-14
The screenshots are back now ... 
also there :[http://patrick295767.pa.funpic.org/cvs.htm](http://patrick295767.pa.funpic.org/cvs.htm)

---

### Post by thestef on 2007-01-23
[http://ubuntuforums.org/showpost.php?p=1327242&postcount=103]("http://ubuntuforums.org/showpost.php?p=1327242&postcount=103")

I have the same problem as Exoor, the scripting problem in line 48.

---

### Post by Preto_X-Ray on 2007-01-26
Hi, I'm pretty new in cegedacvs but I wanna play World of Warcraft and CS 1.6

When I run cedegacvs.sh everything goes fine until stage CVS checkout. 

> 
**EOF from server, retry number 1**
    TIP: A useful Wine resource page:efault x11drv
**EOF from server, retry number 2** bomberman)
    TIP: If you have a WineX related problem you can check theux
    forums on [http://www.transgaming.org/](http://www.transgaming.org/) to a binary enhanced
    TIP: To force all your games to run in a window, uncommentr
    the "Desktop" option in the configuration file.an CVS,
    Look under section [x11drv].for Installshield and copy
    Configuration file will be <Home>/.cvscedega/config info
    It will be created the first time you run cvscedega

Does enyone know other instalation script???

---

### Post by haliphax on 2007-01-30
I don't know if this is useful information to anyone else, but I had to use an outdated (ubuntu 5.10) version of flex (flex 2.5.31-31) in order to get the make to finish without errors.

i ran patrick's script as he instructed. i aborted the installation once the WineCVS script started, and used the following commands to roll back my version of flex:

```
sudo dpkg -r flex flex-old
sudo wget http://security.ubuntu.com/ubuntu/pool/main/f/flex/flex_2.5.31-31ubuntu0.5.10.1_i386.deb
sudo dpkg -i flex_2.5.31-31ubuntu0.5.10.1_i386.deb
sudo sh /root/miniram/WineCVS.sh
```

/root was where i ran the script from to begin with, so /root/miniram was the location that patrick's script had downloaded the WineCVS.sh script to. the installation proceeded as normal. i have yet to test the program itself, but it finally built properly.

this was all extracted from a french website translated with the wonderful, splendiferous babelfish.

also... i am running ubuntu 6.10 (edgy eft) on a P4-based Celeron, using an nVidia GeForce7 7300 something-or-other AGP graphics card.

---

### Post by jrnoyes on 2007-02-01
When I try to get x-window-system-dev
it tells me i cannot get the package because it does not exist
i use ubuntu 6.06 drapper lts
any suggestions?

---

### Post by JayRoe on 2007-02-02
> **thestef said:**
> [http://ubuntuforums.org/showpost.php?p=1327242&postcount=103]("http://ubuntuforums.org/showpost.php?p=1327242&postcount=103")

I have the same problem as Exoor, the scripting problem in line 48.Same here.

---

### Post by patrick295767 on 2007-02-02
Hi guys, 
The script was made working for hoary, breezy, and dapper. It was working well on these distros (also made long time ago/packages changed since). Now, with Etch, that s somethg totally different...I dont have it anymore. I personnally dont like Etch for several reasons (bugs). And  the script needs to be updated !
  
I will try to find some 15 min of time for updating this old script for you guys... 
To be continued
  
Edit:
needs more, its still with gcc3.4 that's damn old :-)

---

### Post by patrick295767 on 2007-02-02
now: 
  
[CODE ### version 2.1
sudo su
cd /tmp
wget http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh
sh easy_cvscedega_patrick_version2.1.sh
[/CODE]

Good Luck !!
CVScedega is not so easy to install anymore, flex-old should be USED ! 
 
The script is now updated for any distro (I use debian) & any type of GCC !

Enjoy 

Sorry that cvscedega profiles are getting less less easy to be installed

-- 
if you mess up and wanna erase the  configure part + profile
beware dangerous: rm -rf /root/.WineCVS/
  
==
I edited / updated the first post of this thread
===
On one machine, I get this error 
[http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2582](http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2582)

---

### Post by Amadeo on 2007-02-07
test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
Wed Feb  7 13:11:56 EST 2007


Just tried it a second ago, won't work. :(

---

### Post by patrick295767 on 2007-02-07
> **Amadeo said:**
> test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
Wed Feb  7 13:11:56 EST 2007


Just tried it a second ago, won't work. :(

There is no "(" line 48. Are you sure you run the right file? So, in order to avoid troubles with that, let's propose this alternative:
```

sudo su
su 
whoami 
## it should be displayed root 
mkdir -p /root/patrickversion2
cd  /root/patrickversion2
wget [http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh](http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh)
wget -N [http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh](http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh)
/bin/bash    /root/patrickversion2/easy_cvscedega_patrick_version2.1.sh

```
## nota: wget with root is not super secured. you can correct it by your own if you'd like and have enough ease with linux to do so.
  
or better secured:
```

cd 
rm -rf easy_cvscedega_patrick_version2.1.sh
wget [http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh](http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh)
wget -N [http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh](http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh)
sudo su
su 
whoami 
## it should be displayed root 
/bin/bash    easy_cvscedega_patrick_version2.1.sh

```
:guitar:

---

### Post by Amadeo on 2007-02-07
I just tried both of these but I end up with the same error.  Everything runs smoothly until the WineCVS.sh part which errors out and ends.  I'm not sure why it's doing this.  I am running Ubuntu 6.10.

---

### Post by patrick295767 on 2007-02-07
> **Amadeo said:**
> I just tried both of these but I end up with the same error.  Everything runs smoothly until the WineCVS.sh part which errors out and ends.  I'm not sure why it's doing this.  I am running Ubuntu 6.10.

Please could you run your script in konsole, or whatever you can do copy-paste, and paste the whole error messages you've got .... Light is at the end of the tunnel... 

> (apt-get install scrot
 $  scrot    
can make very quick screenshots too if you'd need / want) 

---

### Post by Amadeo on 2007-02-07
I have sent you a very large email.  Hopefully that covers all bases. :)

---

### Post by patrick295767 on 2007-02-07
> **Amadeo said:**
> I have sent you a very large email.  Hopefully that covers all bases. :)

Thank for your post. I read your email. I am sorry but my last distro was Dapper and I am very happy that I moved to Debian. Dont ask me why they are having fun with creating bugs and not solving them, or some serious of them. They are the only linux that have corrupted sh for not permitting == anymore. I am not a  great expert but DEBIAN is the most amazing distros I have never used !! It is a really serious distribution, that deserves lot of respect and lot of trust. 

In the script, I made the change for also Ubuntu "Linux" : cough : It was working for all distros but Ubuntu, it  should now for this last distribution. If it is still hanging :

sh WineCVS.sh
or post/pm again me 

I wish you could also profit of this cvscedega !

Enjoy Ubuntu.

---

### Post by BlueSkyDefender on 2007-02-10
I hope this help. I am using Ubuntu 7.04 Feisty Fawn. I am also getting the same error as the others. 
Hummm hope this helps.

[ATTACH]24987[/ATTACH]

---

### Post by TheRealEdwin on 2007-02-10
```
test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
Sat Feb 10 19:24:18 EST 2007
Installation Done

```

:(

---

### Post by old_geekster on 2007-02-10
I just installed cvscedega in Ubuntu 6.10.  It appeared to go very smoothly.  However, it asked me which "gcc" I am using and I didn't have any idea what it is, so I simply hit "Enter" to continue.

What is "gcc" and how do I enter it into the program at this point?

Thanks!

Update:  I ran the script to get the profile, but the screen that you showed in your guide, didn't appear.  I typed the "g" as instructed, but got the message no directory of file found.  Is there a way to delete all that was installed with the script?

---

### Post by honeybear on 2007-02-11
> **old_geekster said:**
> I just installed cvscedega in Ubuntu 6.10.  It appeared to go very smoothly.  However, it asked me which "gcc" I am using and I didn't have any idea what it is, so I simply hit "Enter" to continue.

What is "gcc" and how do I enter it into the program at this point?

Thanks!

Update:  I ran the script to get the profile, but the screen that you showed in your guide, didn't appear.  I typed the "g" as instructed, but got the message no directory of file found.  Is there a way to delete all that was installed with the script?

You used the version 0.1 or 1. He wrote to use the version 2 something:
```
 ### version 2.1
sudo su
su
cd /tmp
wget http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh
sh easy_cvscedega_patrick_version2.1.sh

```
 
I think he made the script compatible with ubuntu. This worked for me. The error message 43 is appearing only due to non stable Ubuntu distro. try: bash easy_cvscedega_patrick_version2.1.sh  ; I just found lot of information in the first post of this thread :-)  
  
if you wanna remove the mess with your profiles, :
```
rm -rf /root/.WineCVS         
```
  
bytheway:
> **TheRealEdwin said:**
> ```
test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
Sat Feb 10 19:24:18 EST 2007
Installation Done

```

:(

you can report the bug to ubuntu if it is not done already
apt-get install reportbug
but forget that they correct it, ubuntu usually dont care or are not able to fix them, that's my experience with openoffice bugs.

---

### Post by burek on 2007-02-11
I get this error message: 
```
-------------------------------------------

Compiling ...




--------- Error log - file /root/.WineCVS/sources/cvscedega/ErrorLog : ---------
./ppl.l:1337: warning: implicit declaration of function ‘max’
./ppl.l:1337: error: ‘ALLOCBLOCKSIZE’ undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1346: warning: conflicting types for ‘macro_add_arg’
./ppl.l:1346: error: static declaration of ‘macro_add_arg’ follows non-static declaration
./ppl.l:493: error: previous implicit declaration of ‘macro_add_arg’ was here
./ppl.l: In function ‘macro_add_arg’:
./ppl.l:1349: error: ‘macexpstackentry_t’ undeclared (first use in this function)
./ppl.l:1349: error: ‘mep’ undeclared (first use in this function)
./ppl.l:1368: error: ‘debuglevel’ undeclared (first use in this function)
./ppl.l:1368: error: ‘DEBUGLEVEL_PPLEX’ undeclared (first use in this function)
./ppl.l:1370: error: ‘input_name’ undeclared (first use in this function)
./ppl.l:1371: error: ‘line_number’ undeclared (first use in this function)
./ppl.l:1378: error: ‘pp_macexp’ undeclared (first use in this function)
./ppl.l:1379: warning: implicit declaration of function ‘push_buffer’
./ppl.l: In function ‘macro_add_expansion’:
./ppl.l:1387: error: ‘macexpstackentry_t’ undeclared (first use in this function)
./ppl.l:1387: error: ‘mep’ undeclared (first use in this function)
./ppl.l:1396: error: ‘debuglevel’ undeclared (first use in this function)
./ppl.l:1396: error: ‘DEBUGLEVEL_PPLEX’ undeclared (first use in this function)
./ppl.l:1398: error: ‘input_name’ undeclared (first use in this function)
./ppl.l:1399: error: ‘line_number’ undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1411: warning: conflicting types for ‘put_buffer’
./ppl.l:1411: error: static declaration of ‘put_buffer’ follows non-static declaration
./ppl.l:476: error: previous implicit declaration of ‘put_buffer’ was here
./ppl.l: In function ‘put_buffer’:
./ppl.l:1415: error: ‘pass_data’ undeclared (first use in this function)
./ppl.l: In function ‘do_include’:
./ppl.l:1439: error: ‘includelogicentry_t’ undeclared (first use in this function)
./ppl.l:1439: error: ‘iep’ undeclared (first use in this function)
./ppl.l:1441: error: ‘includelogiclist’ undeclared (first use in this function)
./ppl.l:1462: warning: implicit declaration of function ‘open_include’
./ppl.l:1462: warning: assignment makes pointer from integer without a cast
./ppl.l:1467: error: ‘seen_junk’ undeclared (first use in this function)
./ppl.l:1468: error: ‘include_state’ undeclared (first use in this function)
./ppl.l:1469: error: ‘include_ppp’ undeclared (first use in this function)
./ppl.l:1470: error: ‘pass_data’ undeclared (first use in this function)
./ppl.l:1473: error: ‘debuglevel’ undeclared (first use in this function)
./ppl.l:1473: error: ‘DEBUGLEVEL_PPMSG’ undeclared (first use in this function)
./ppl.l:1474: error: ‘input_name’ undeclared (first use in this function)
./ppl.l:1474: error: ‘line_number’ undeclared (first use in this function)
./ppl.l:1474: error: ‘include_ifdepth’ undeclared (first use in this function)
./ppl.l: In function ‘push_ignore_state’:
./ppl.l:1488: error: ‘pp_ignore’ undeclared (first use in this function)
make[2]: *** [lex.ppl.o] Error 1
make[2]: Leaving directory `/root/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/root/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS-linuxgamers.sh)


```

---

### Post by Bram77 on 2007-02-11
> **TheRealEdwin said:**
> ```
test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
Sat Feb 10 19:24:18 EST 2007
Installation Done

```

:(

I'm getting the same error.

---

### Post by Breepee on 2007-02-11
CVSCedega hasn;t been updated for the last 2 years, no?

---

### Post by old_geekster on 2007-02-11
> **honeybear said:**
> You used the version 0.1 or 1. He wrote to use the version 2 something:
```
 ### version 2.1
sudo su
su
cd /tmp
wget http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.1.sh
sh easy_cvscedega_patrick_version2.1.sh

```
 
I think he made the script compatible with ubuntu. This worked for me. The error message 43 is appearing only due to non stable Ubuntu distro. try: bash easy_cvscedega_patrick_version2.1.sh  ; I just found lot of information in the first post of this thread :-)  
  
if you wanna remove the mess with your profiles, :
```
rm -rf /root/.WineCVS         
```
  
bytheway:


you can report the bug to ubuntu if it is not done already
apt-get install reportbug
but forget that they correct it, ubuntu usually dont care or are not able to fix them, that's my experience with openoffice bugs.
Thanks, honeybear.

I would have sworn that I used the script that you posted.  It came from the first part of the first post.

I used the method that you posted to remove my goof ups.  So, now I will try again.

Wish me luck!

---

### Post by JulianLx on 2007-02-14
Hi,
I tried your script on Uubuntu 6.10 with Wine 0.9.30 already installed.
When it asked me about my gcc version, I typed 4.1 and after some time and blah, blah, blah I receive the bellow output.


Please download the profile number 1, and 
run this downloaded profile

test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
mié feb 14 23:32:58 IST 2007
Installation Done
====================== 
Type as User: cvscedega
old flex used
root@la-caja:/tmp# cvscedega
bash: cvscedega: orden no encontrada

What´s went wrong?

---

### Post by patrick295767 on 2007-02-15
> **JulianLx said:**
> Hi,
I tried your script on Uubuntu 6.10 with Wine 0.9.30 already installed.
When it asked me about my gcc version, I typed 4.1 and after some time and blah, blah, blah I receive the bellow output.


Please download the profile number 1, and 
run this downloaded profile

test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
mié feb 14 23:32:58 IST 2007
Installation Done
====================== 
Type as User: cvscedega
old flex used
root@la-caja:/tmp# cvscedega
bash: cvscedega: orden no encontrada

What´s went wrong?
  
Your Error message is not a problem from the script but is related to the Ubuntu "politics" quite different than real linux community. Ask Ubuntu developers to make less bugs and have more reliable distro. Install another distro and make the try for us if this error message persists. "==" error message not supported by me.

---

### Post by Mytholody on 2007-02-28
Hey everyone, after trying the script all night and failing, I got it to work at last. Not sure if it was just luck, but decided to go back to the unedited script ([linux gamers.net one]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Cedega%20CVS")). I downloaded it, went to WineCVS's directory, and did a bash WineCVS.sh at the terminal and got to the profile part. From there, just follow patrick295767's walkthrough. BTW, Thank you patrick, made the install a whole lot easier! :)

So good luck everyone, I believe it should work for you. If im totally wrong, just post and stick it in my face hehe because its pretty late and I seem to go on rants that don't make any sense at this time. Anyhow, have fun, its working here!

edit: Btw, not sure if patricks script included the password, but you'll have to enter it when your taking out the CVS if your doing it this way, pw is cvs (if it changes it'll probably say in the terminal).

---

### Post by dea on 2007-03-11
For the error:
test: 43: ==: unexpected operator

Try 'bash WineCVS.sh' instead of 'sh WineCVS.sh'. Works for me :)

---

### Post by FyreBrand on 2007-03-11
> **patrick295767 said:**
> Your Error message is not a problem from the script but is related to the Ubuntu "politics" quite different than real linux community. Ask Ubuntu developers to make less bugs and have more reliable distro. Install another distro and make the try for us if this error message persists. "==" error message not supported by me.You are kidding right?  You're trying to tell me that because you're script is compatible on another distro's package configuration that Ubuntu is buggy?

I have absolutely no problem compiling wine from source on Edgy or Feisty. Maybe it's your script.  It's rude point the finger at Ubuntu developers for not taking into account your script.  Write a better script to take into account gcc versioning.

I'm curious how Ubuntu politics makes your script unusable.

---

### Post by Computer Guru on 2007-04-25
Linux creates so much hate, let's just all move to Windows instead.

(KIDDING!)

---

### Post by patrick295767 on 2007-04-30
> **FyreBrand said:**
> You are kidding right?  You're trying to tell me that because you're script is compatible on another distro's package configuration that Ubuntu is buggy?

I have absolutely no problem compiling wine from source on Edgy or Feisty. Maybe it's your script.  It's rude point the finger at Ubuntu developers for not taking into account your script.  Write a better script to take into account gcc versioning.

I'm curious how Ubuntu politics makes your script unusable.

Try test with == and/or =, I dont understand why with only ubuntu it is not possible and with all other distros, it is:
That s their choice (Ubuntu & sh).
 
Please could you check the origin of this error
```
test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
Sat Feb 10 19:24:18 EST 2007
Installation Done
```

Good evening
 
:guitar:
  
By the way, I just quote from above from Dea:
 >  
For the error:
test: 43: ==: unexpected operator

Try 'bash WineCVS.sh' instead of 'sh WineCVS.sh'. Works for me

Dont tell me Ubuntu is not rather a bit buggy. It is still a good distro for a begin.

---

### Post by Graelb on 2007-05-03
I had the same problem, when i used "bash WineCVS.sh" instead of sh, it went on through to the profile screen.

The problem i'm having is when it gets to the "configure" option on the actual install

Configuring ...




--------- Error log - file /root/.WineCVS/sources/cvscedega/ErrorLog : ---------
/root/.WineCVS/Functions/DefaultProfile: line 628: ./configure: No such file or directory


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Any ideas?

---

### Post by charlieg on 2007-05-03
The title [of this thread] is ironic.  Although this allows Cedega usage for free, it is still a misnomer because you have to pay for pretty much all of the games people will use Cedega for. Therefore it is not "Free Gaming".

---

### Post by mikeym on 2007-05-29
[quote="Graelb"]
I had the same problem, when i used "bash WineCVS.sh" instead of sh, it went on through to the profile screen.

The problem i'm having is when it gets to the "configure" option on the actual install

Configuring ...




--------- Error log - file /root/.WineCVS/sources/cvscedega/ErrorLog : ---------
/root/.WineCVS/Functions/DefaultProfile: line 628: ./configure: No such file or directory


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Any ideas?
[/quote]

Hi,

I'm trying to get system shock 2 working under linux and I can only find references to people having managed that with Cedega so I'm trying to get this working.

By following the origonal script and once it's crashed out with 

```

test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected

```

Running 'sudo bash /root/miniram/WineCVS.sh'. I can get as far as the configuring stage and then I get the same error as Graelb (above). 

I looked the the '.WineCVS/sources/cvscedega/winex/' directory and there is no configure file. Any ideas what's going on?

```

acinclude.m4      documentation   Make.rules.in       scheduler
aclocal.m4        files           memory              server
ANNOUNCE          graphics        misc                setup.sh
AUTHORS           if1632          miscemu             tools
AUTHORS.Wine      include         msdos               tsx11
BUGS              library         objects             unicode
ChangeLog         libs            ole                 VERSION
configure.ac      libtest         port                WARRANTY
console           LICENSE         programs            win32
controls          LICENSE.LGPL    rc                  windows
CVS               LICENSE.ReWind  README              winedefault.reg
debugger          LICENSE.Wine    README.transgaming
DEVELOPERS-HINTS  loader          relay32
dlls              Makefile.in     resources

```

---

### Post by mikeym on 2007-05-30
I would just like to say that this howto seems to be effectively dead. (Correct me if I'm wrong.) There have been too many changes to the system for these scripts to work any more.

The problem I and others had with the DefaultProfile script not finding ./configure is because ./setup has to be run now before configure, but this doesn't help as the CVS won't compile anyway.

The CVS can be got directly from [http://www.transgaming.com/sources.php](http://www.transgaming.com/sources.php) now so I don't know what all the profile business is supposed to be doing. 

I don't even know if the package dependencies are all relevant any more.

So please USE WITH DISCRETION.

---

### Post by sloan2189 on 2007-06-01
Success!

Here's what I remember doing to get cvscedega to work:

1) sudo apt-get install cvs build-essential bison flex-old libasound2-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev autoconf libxt-dev xlibs-dev

2) Now run the script and choose option 0. 

3) Error? Go to /home/<username>/.WineCVS/sources/cvscedega/winex and run ./setup.sh

4) Run the WineCVS script again. 

5) If all goes well, run your games like so: cvscedega game.exe

Step one is a little different from what is listed in the linux-gamers link below.  x-window-system-dev isn't needed  but autoconf is. 

Hope this helps!

Sources of help (besides this thread)

From [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS)

---

### Post by charlieg on 2007-06-01
Slightly off-topic, but as the author of [Free Gamer]("http://freegamer.blogspot.com/"), I find the name of this thread very annoying.  Just because it allows you to run Cedega for free, it does in no way provide FREE gaming.  You still have to PAY for all the commercial titles this enables you to run.

*phew* been wanting to say that for ages.

---

### Post by justin whitaker on 2007-06-01
> **charlieg said:**
> Slightly off-topic, but as the author of [Free Gamer]("http://freegamer.blogspot.com/"), I find the name of this thread very annoying.  Just because it allows you to run Cedega for free, it does in no way provide FREE gaming.  You still have to PAY for all the commercial titles this enables you to run.

*phew* been wanting to say that for ages.

Charlieg, you are assuming that they are actually buying the game.

---

### Post by GasPipe on 2007-06-15
Hi!

I installed CVSCedega with that script succesfully, but when I try to configure profile with that: [http://patrick295767.pa.funpic.org/cvs.htm](http://patrick295767.pa.funpic.org/cvs.htm)

there is no "easy_cvscedega_patrick.sh" file in that directory.

So what I supposed to do?

---

### Post by patrick295767 on 2007-06-17
> **GasPipe said:**
> Hi!

I installed CVSCedega with that script succesfully, but when I try to configure profile with that: [http://patrick295767.pa.funpic.org/cvs.htm](http://patrick295767.pa.funpic.org/cvs.htm)

there is no "easy_cvscedega_patrick.sh" file in that directory.

So what I supposed to do?

"easy_cvscedega_patrick_version2.1.sh" is to be used.  I updated the ftp with the scripts.  (check the first post of this thread)
 
Please report a bug for the sh if you cannot do == with test with Ubuntu. This is not normal
```
apt-get install reportbug sendmail  
reportbug  # then your email , then enter sh


```


Regards

---

### Post by knavex on 2007-06-17
I ran the script and got this message, What should I do. I'm running newest Ubuntu

> WineCVS.sh - Progress(u) : Green is current

   0 = Uninstall
   1 = Cleanup
   2 = CVS checkout
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Compiling ...




--------- Error log - file /home/finny/.WineCVS/sources/cvscedega/ErrorLog : ---------
./ppl.l:1337: warning: implicit declaration of function &#8216;max&#8217;
./ppl.l:1337: error: &#8216;ALLOCBLOCKSIZE&#8217; undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1346: warning: conflicting types for &#8216;macro_add_arg&#8217;
./ppl.l:1346: error: static declaration of &#8216;macro_add_arg&#8217; follows non-static declaration
./ppl.l:493: error: previous implicit declaration of &#8216;macro_add_arg&#8217; was here
./ppl.l: In function &#8216;macro_add_arg&#8217;:
./ppl.l:1349: error: &#8216;macexpstackentry_t&#8217; undeclared (first use in this function)
./ppl.l:1349: error: &#8216;mep&#8217; undeclared (first use in this function)
./ppl.l:1368: error: &#8216;debuglevel&#8217; undeclared (first use in this function)
./ppl.l:1368: error: &#8216;DEBUGLEVEL_PPLEX&#8217; undeclared (first use in this function)
./ppl.l:1370: error: &#8216;input_name&#8217; undeclared (first use in this function)
./ppl.l:1371: error: &#8216;line_number&#8217; undeclared (first use in this function)
./ppl.l:1378: error: &#8216;pp_macexp&#8217; undeclared (first use in this function)
./ppl.l:1379: warning: implicit declaration of function &#8216;push_buffer&#8217;
./ppl.l: In function &#8216;macro_add_expansion&#8217;:
./ppl.l:1387: error: &#8216;macexpstackentry_t&#8217; undeclared (first use in this function)
./ppl.l:1387: error: &#8216;mep&#8217; undeclared (first use in this function)
./ppl.l:1396: error: &#8216;debuglevel&#8217; undeclared (first use in this function)
./ppl.l:1396: error: &#8216;DEBUGLEVEL_PPLEX&#8217; undeclared (first use in this function)
./ppl.l:1398: error: &#8216;input_name&#8217; undeclared (first use in this function)
./ppl.l:1399: error: &#8216;line_number&#8217; undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1411: warning: conflicting types for &#8216;put_buffer&#8217;
./ppl.l:1411: error: static declaration of &#8216;put_buffer&#8217; follows non-static declaration
./ppl.l:476: error: previous implicit declaration of &#8216;put_buffer&#8217; was here
./ppl.l: In function &#8216;put_buffer&#8217;:
./ppl.l:1415: error: &#8216;pass_data&#8217; undeclared (first use in this function)
./ppl.l: In function &#8216;do_include&#8217;:
./ppl.l:1439: error: &#8216;includelogicentry_t&#8217; undeclared (first use in this function)
./ppl.l:1439: error: &#8216;iep&#8217; undeclared (first use in this function)
./ppl.l:1441: error: &#8216;includelogiclist&#8217; undeclared (first use in this function)
./ppl.l:1462: warning: implicit declaration of function &#8216;open_include&#8217;
./ppl.l:1462: warning: assignment makes pointer from integer without a cast
./ppl.l:1467: error: &#8216;seen_junk&#8217; undeclared (first use in this function)
./ppl.l:1468: error: &#8216;include_state&#8217; undeclared (first use in this function)
./ppl.l:1469: error: &#8216;include_ppp&#8217; undeclared (first use in this function)
./ppl.l:1470: error: &#8216;pass_data&#8217; undeclared (first use in this function)
./ppl.l:1473: error: &#8216;debuglevel&#8217; undeclared (first use in this function)
./ppl.l:1473: error: &#8216;DEBUGLEVEL_PPMSG&#8217; undeclared (first use in this function)
./ppl.l:1474: error: &#8216;input_name&#8217; undeclared (first use in this function)
./ppl.l:1474: error: &#8216;line_number&#8217; undeclared (first use in this function)
./ppl.l:1474: error: &#8216;include_ifdepth&#8217; undeclared (first use in this function)
./ppl.l: In function &#8216;push_ignore_state&#8217;:
./ppl.l:1488: error: &#8216;pp_ignore&#8217; undeclared (first use in this function)
make[2]: *** [lex.ppl.o] Error 1
make[2]: Leaving directory `/home/finny/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/finny/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


finny@caketown:~$                                                                      

---

### Post by spooner on 2007-06-30
> **knavex said:**
> I ran the script and got this message, What should I do. I'm running newest Ubuntu

I was having this problem but the solution is found [here ]("http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2582"). 
Once I had removed the massive comments from the top of the two ppl.l files:-
sudo gedit .WineCVS/sources/cvscedega/winex/tools/widl/ppl.l
sudo gedit .WineCVS/sources/cvscedega/winex/tools/wrc/ppl.l 
all seems ok.

---

### Post by patrick295767 on 2007-09-16
Hi,
Small update of the first post of this thread. The little problems are now fixed, and cvscedega can continue being installed.
Regards
 

======== Update of Sept. 2007 ======version 2.2 =================
A new version has been released of easy script cvscedega. To install it, just type this in your console:


> sudo bash
cd /root
apt-get -f -y install flex cvs bison
wget -N [http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.2.sh](http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.2.sh)
sh [http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.2.sh](http://patrick295767.pa.funpic.org/easy_cvscedega_patrick_version2.2.sh)
exit


---

### Post by edemark on 2007-09-18
Hi i got this error at the end:
test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
checking whereis cvscedega ... 
cvscedega:
Installation Done
====================== 
Type as User: cvscedega
old flex was used
This script is not supported anymore
This script is not supported anymore
This script is not supported anymore
This script is not supported anymore
 Cvscedega !!
root@supernova:/root# exit
exit
However as you see the script finishes up. On the other hand I just cannot run cvscedega <-- no command found

Any ideas?

---

### Post by patrick295767 on 2007-09-21
> **edemark said:**
> Hi i got this error at the end:
test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
checking whereis cvscedega ... 
cvscedega:
Installation Done
====================== 
Type as User: cvscedega
old flex was used
This script is not supported anymore
This script is not supported anymore
This script is not supported anymore
This script is not supported anymore
 Cvscedega !!
root@supernova:/root# exit
exit
However as you see the script finishes up. On the other hand I just cannot run cvscedega <-- no command found

Any ideas?

I am sorry but I won't update the script just because Ubuntu is not a clean distro and cannot handle ==. All distro can but Ubuntu. I am not surprised people are getting in  bugs troubles. You should try to learn Debian ; you will not loose your time. 

Best regards,
Nota: == is not accepted by Ubuntu. 
man ssh, you see the email address to write to ... 
change all the == by = or mb. -eq in the script
 
(ah, man, long life to Debian
Btw Ubuntu Automatix is absolutely not supported by Debian.)

---

### Post by g2g591 on 2007-09-28
try using bash WineCVS.sh, then it will work (I hope)

---

### Post by patrick295767 on 2007-09-29
> **g2g591 said:**
> try using bash WineCVS.sh, then it will work (I hope)

The reportbug thing is there too now:
[http://ubuntuforums.org/showthread.php?t=562957](http://ubuntuforums.org/showthread.php?t=562957)
I hope they will be more vigilant with the bugs. That's quite sad for the Debian image to see that bugs remain pretty long with Ubuntu... :(

---

### Post by hikaricore on 2007-09-29
Just let me know if you ever want this thread closed patrick.
I've been watching it sputter back for the dead a few times lol.

---

### Post by patrick295767 on 2007-09-30
> **hikaricore said:**
> Just let me know if you ever want this thread closed patrick.
I've been watching it sputter back for the dead a few times lol.

Well, I recently updated the script and cvscedega can be installed. Installation works quite fine. 
 
Concerning the cvscedega program itself, so, it is nice free alternative but cedega that you pay is by far much better. Ok, you pay. I'd say let's leave the thread open like this, let's look a while how it goes, and in jan 2008 we can re-think about the question. 
It lastly tried, and cvscedega could run several programs that wine was more or less doing its job. Concerning games, well, I have to try ... how good it is now cvscedega... I still think we can play 2years old games. It's free alternative :)

---

### Post by drpepper on 2007-10-28
Hi

I used the latest script, 2.2. And this installed with no problems. However, when i try to run cvscedega from the console i just get command not found. I've looked in /usr/bin and there doesn't seem to be anything cedgea related in there. 

Any ideas? I'm unsure of where to start with this problem or how to remove everything if i can't get it going.

Cheers, Nick

---

### Post by patrick295767 on 2007-11-01
> **drpepper said:**
> Hi

I used the latest script, 2.2. And this installed with no problems. However, when i try to run cvscedega from the console i just get command not found. I've looked in /usr/bin and there doesn't seem to be anything cedgea related in there. 

Any ideas? I'm unsure of where to start with this problem or how to remove everything if i can't get it going.

Cheers, Nick
  
if it is installed the command, will tell you:
```
sudo whereis cvscedega
cvscedega: /usr/bin/cvscedega /usr/lib/cvscedega /usr/X11R6/bin/cvscedega /usr/bin/X11/cvscedega
```

If not, please could you post the installation console output / log ...
thanks

---

### Post by drpepper on 2007-11-05
Hi

Thanks for the reply, I used "sudo whereis cedgea" and this didn't find any installations of cedega. I saw that the script was not compatible with Ubuntu, is this still true?

Kind Regards

Nick

---

### Post by b9anders on 2007-11-23
I am running sidux/debian sid - the script installed just fine, but I am having the same problem in that it can't seem to find the installation...

---

### Post by Sockerdrickan on 2007-11-23
Give me five reasons why this would be better than WINE.

---

### Post by promet on 2008-01-20
For those who fail running WineCVS.sh with the error:

"...unexpected "(" "

Check out the excerpt below. Hopefully will help a little:

[COLOR=Purple]   	Hi! Two little bugs about the WineCVS.sh script:

First, using "sh WineCVS.sh" as pointed in the HOWTO gives an error:

test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected

Use "bash WineCVS.sh" or "./WineCVS.sh" instead.

Second, running the script (with "./WineCVS.sh") and then doing the selection "g -> 1 -> r -> 0" gives the error:

/root/.WineCVS/Functions/DefaultProfile: line 628: ./configure: The file or directory does not exist.

This problem seems to be common (google it), but not yet solved. I have found something about autoconf, but no idea about what to do with. I tried to use [Patrick's method]("http://ubuntuforums.org/showthread.php?t=193814"), but the same happens.

Note: using Ubuntu 7.04 Feisty Fawn[/COLOR]

---

### Post by mattchew on 2008-02-04
You know, I looked into the folder of ~./WineCVS/Functions/ for Defaultprofile
and all I can see on line 628 is this (3rd line is 628 )
> ## Step 3 ## Configure
function CVS_Configure_Default()
{
	if ./configure --prefix=$ConfigurePrefix  $ConfigureOptions >"$ErrorLogFile" 2>&1
	then
		State="4"
	else
		ErrMsgMake
		ExitNow
	fi
}
function CVS_Configure()
{
	CVS_Configure_Default
}

## Step 4 ## Make depend


When I look into the vartiables ConfigurePrefix and ConfigureOptions I find (line 34, the definitions) :

> # NEEDED vars
unset ScriptName          # eg ="cvswinex"
unset CVSroot             # eg =":pserver:cvs@cvs.transgaming.org:/cvsroot"
unset CVSCheckOutDir      # eg ="wine"

# install vars
unset CompileRootDir      # default="$HomeDir/sources/$ScriptName"
unset ErrorLogFile        # default="$CompileRootDir/ErrorLog"
unset ConfigurePrefix     # default="/usr/lib/$ScriptName"
unset ConfigDirName       # default=".$ScriptName"
unset WineExecName        # default="$CVSCheckOutDir"
unset ConfigureOptions    # default=<unset>
unset ConfigureOptions64  # default=<unset>
unset UserOnlyInstall     # default=<unset>
unset OldCVSCheckOutDir   # default=<unset>
unset CVSoptions          # default="-z 3"
unset CVScheckoutOptions  # default=<unset>

Is there a part of the logic that was missing, or are the words mixed up where they should be cvswinex vs WineCVS? How come I don't have a /usr/lib/cvswinex that according to the script, I should be pointing to? (be it as a folder or a .sh or something)? Or something with ./Configure?

---

### Post by LinuxN00b92 on 2008-03-15
Configuring ...




--------- Error log - file /root/.WineCVS/sources/cvscedega/ErrorLog : ---------/root/.WineCVS/Functions/DefaultProfile: line 628: ./configure: No such file or directory


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


This is the error I keep getting, I am currently running Debian if that changes anything. Any help would be greatly appreciated. Thanks in advance.

---

### Post by tyro1981 on 2008-05-13
does the 

sh [http://.](http://.)..

thing work? Not in... um... Ubuntu...

---

### Post by sreekarguddeti on 2008-05-25
I get the same error message... 
################

--------- Error log - file /home/colonel/.WineCVS/sources/cvscedega/ErrorLog : ---------
/home/colonel/.WineCVS/Functions/DefaultProfile: line 628: ./configure: No such file or directory


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Sun May 25 16:41:06 IST 2008
Did you get an error ?
If yes, hit enter ... otherwise press ctrl + c 

./easy_cvscedega_patrick_version2.2.sh: line 171: ./setup.sh: Permission denied
Installing ...

test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected
checking whereis cvscedega ... 
cvscedega:


################
is there any solution for this?

i use ubuntu hardy ... x86_64...

---

### Post by spraff on 2008-09-01
**[SIZE="6"]Solved![/SIZE]**

cd /home/whatever/.WineCVS/sources/cvscedega/winex
autoconf configure.ac > configure
chmod +x configure
cd -
bash WineCVS.sh

This is my first post on these forums and I'm chuffed. Good luck to the rest of you.

(This is with profile 0: cedega_head_userinstall in case that's important.)

---

### Post by Scelestus on 2008-10-18
ok this is the first time I've posted on this site. I've got it down to make but i get this error



--------- Error log - file /home/jon/.WineCVS/sources/cvscedega/ErrorLog : ---------
../include/winbase.h:1805: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1839: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1840: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1841: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1842: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1843: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1844: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1845: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1846: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1847: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1848: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1849: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1850: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1851: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1852: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1853: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1854: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1855: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1900: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1907: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1909: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1916: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1918: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1925: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1927: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1934: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1936: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1940: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1942: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1946: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1948: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1954: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1956: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1962: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1964: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1970: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1972: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1976: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1978: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:1999: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:2004: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:2013: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:2018: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:2023: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:2025: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:2028: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:2030: warning: ‘__stdcall__’ attribute ignored
../include/winbase.h:2032: warning: ‘__stdcall__’ attribute ignored
make[1]: Leaving directory `/home/sowhat/.WineCVS/sources/cvscedega/winex/server'
make: *** [server/libwineserver.so] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


anyone get this error and fixed it?

---

### Post by asdfoo on 2008-10-18
> **Tux0r said:**
> Give me five reasons why this would be better than WINE.

exactly, people should try Wine first.   A lot of programs that Wine can run don't work on cedega.

---

### Post by Scelestus on 2008-10-18
[COLOR="Blue"]Ok I tried manually comfigure and make. I got past configure but when i try to make i get this error[/COLOR]





[email]jon@debian:~/.Wine[/email]CVS/sources/cvscedega/winex$ make
make[1]: Entering directory `/home/jon/.WineCVS/sources/cvscedega/winex/libs/wpp'
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -Wdeclaration-after-statement -D__i386__ -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long"    -D_REENTRANT  -o preproc.o preproc.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -Wdeclaration-after-statement -D__i386__ -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long"    -D_REENTRANT  -o wpp.o wpp.c
bison -y -ppp -d -t ./ppy.y -o ppy.tab.c
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -Wdeclaration-after-statement -D__i386__ -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long"    -D_REENTRANT  -o ppy.tab.o ppy.tab.c
flex -olex.yy.c ./ppl.l
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -Wdeclaration-after-statement -D__i386__ -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long"    -D_REENTRANT  -o lex.yy.o lex.yy.c
rm -f libwpp.a
ar rc libwpp.a  preproc.o wpp.o           ppy.tab.o lex.yy.o
ranlib libwpp.a
make[1]: Leaving directory `/home/jon/.WineCVS/sources/cvscedega/winex/libs/wpp'make[1]: Entering directory `/home/jon/.WineCVS/sources/cvscedega/winex/port'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -Wdeclaration-after-statement -D__i386__ -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long"  -fPIC -D__WINE__ -D_REENTRANT  -o port.o port.c
/tmp/ccja8y1W.s: Assembler messages:
/tmp/ccja8y1W.s:93: Error: suffix or operands invalid for `push'
/tmp/ccja8y1W.s:96: Error: suffix or operands invalid for `pop'
make[1]: *** [port.o] Error 1
make[1]: Leaving directory `/home/jon/.WineCVS/sources/cvscedega/winex/port'
make: *** [port] Error 2
[email]jon@debian:~/.Wine[/email]CVS/sources/cvscedega/winex$ make install
make[1]: Entering directory `/home/jon/.WineCVS/sources/cvscedega/winex/libs/wpp'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jon/.WineCVS/sources/cvscedega/winex/libs/wpp'make[1]: Entering directory `/home/jon/.WineCVS/sources/cvscedega/winex/port'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -Wdeclaration-after-statement -D__i386__ -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long"  -fPIC -D__WINE__ -D_REENTRANT  -o port.o port.c
/tmp/ccudSDuZ.s: Assembler messages:
/tmp/ccudSDuZ.s:93: Error: suffix or operands invalid for `push'
/tmp/ccudSDuZ.s:96: Error: suffix or operands invalid for `pop'
make[1]: *** [port.o] Error 1
make[1]: Leaving directory `/home/jon/.WineCVS/sources/cvscedega/winex/port'
make: *** [port] Error 2
[email]jon@debian:~/.Wine[/email]CVS/sources/cvscedega/winex$

---

### Post by SatNav on 2008-10-29
bump! experiencing the same problem as Scelestus here ^^^

```
make[1]: Entering directory `/home/mark/.WineCVS/sources/cvscedega/winex/port'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -Wdeclaration-after-statement -D__i386__ -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long"  -fPIC -D__WINE__ -D_REENTRANT  -o port.o port.c
port.c: Assembler messages:
port.c:660: Error: suffix or operands invalid for `push'
port.c:663: Error: suffix or operands invalid for `pop'
make[1]: *** [port.o] Error 1
make[1]: Leaving directory `/home/mark/.WineCVS/sources/cvscedega/winex/port'
make: *** [port] Error 2

```

anyone any ideas?

---

### Post by asdfoo on 2008-10-29
> **SatNav said:**
> bump! experiencing the same problem as Scelestus here ^^^

```
make[1]: Entering directory `/home/mark/.WineCVS/sources/cvscedega/winex/port'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -Wdeclaration-after-statement -D__i386__ -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long"  -fPIC -D__WINE__ -D_REENTRANT  -o port.o port.c
port.c: Assembler messages:
port.c:660: Error: suffix or operands invalid for `push'
port.c:663: Error: suffix or operands invalid for `pop'
make[1]: *** [port.o] Error 1
make[1]: Leaving directory `/home/mark/.WineCVS/sources/cvscedega/winex/port'
make: *** [port] Error 2

```

anyone any ideas?

use Wine instead, it's much better.

---

### Post by Scelestus on 2008-11-01
I would use wine if i could. I want to play Everquest but it will not run with regular wine. was going to try winex.sh installer nothing but a headache. lol so much for the open source sector of the world

---

### Post by asdfoo on 2008-11-02
> **Scelestus said:**
> I would use wine if i could. I want to play Everquest but it will not run with regular wine. was going to try winex.sh installer nothing but a headache. lol so much for the open source sector of the world

fair enough.  are you on 64bit?  You might have to include the -m32 flag to gcc if so.  I'm not familiar with what you're building, only regular Wine.

---

