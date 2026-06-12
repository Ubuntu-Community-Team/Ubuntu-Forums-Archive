---
title: "question re WINE &amp; PLAYONLINUX"
date: 2018-01-19
forum: Wine
---

### Post by wfriedwaldgmail.c on 2018-01-19
need some input!

am trying to install PLAYONLINUX -

not sure of many things:
which version of PLAYON - "trusty" or "saucy" or whatever
don't know whether or not WINE is a whole separately dealie that has to also be installed separately.

anyhow, here's how the deal went down - the first four lines are the code that the page ([https://www.playonlinux.com/en/download.html](https://www.playonlinux.com/en/download.html)) instructed me to use.

[https://paste.ubuntu.com/26419804/](https://paste.ubuntu.com/26419804/)

grateful for any feedback or suggestions.

thanks!

w - running Ubuntu 17.10

---

### Post by QIII on 2018-01-19
Moved to the Wine sub-forum for better visibility.

---

### Post by Dennis N on 2018-01-19
Why not use the repository version? Type "playonlinux" in the application search box and it will find it and offer to launch Ubuntu Software to install it.

---

### Post by wfriedwaldgmail.c on 2018-01-20
thank you!  I had no idea about such things.

okay, I tried that and this is what I got:

[COLOR=#222222][FONT=arial]Detailed errors from the package manager follow:[/FONT][/COLOR]

[COLOR=#222222][FONT=arial]apt transaction returned result exit-failed[/FONT][/COLOR]


I also tried installing WINE separately, and got the same message:


[COLOR=#222222][FONT=arial]Detailed errors from the package manager follow:[/FONT][/COLOR]

[COLOR=#222222][FONT=arial]apt transaction returned result exit-failed[/FONT][/COLOR]


thanks for this and any further help!

w

---

### Post by mastablasta on 2018-01-22
hmm something is wrong.

try installing using the command line and then copy and post the output here.

to install in CLI open the terminal and paste the following in it:

```
sudo apt-get install playonlinux
```

or 
```

sudo apt-get install wine
```

when asked for password enter your user password (nothing will show up as you enter) and press enter.

if it's not working it should give you the error message. mark it , right click it and select copy to copy the marked contents. the post them here using code tags (the # icon in "go advanced" mode).
that way we can see the error and help you troubleshoot it.

---

### Post by wfriedwaldgmail.c on 2018-01-22
thanks very much for those great specific instructions!

```
will@will-HP-Stream-Notebook-PC-11:~$ sudo apt-get install playonlinux
[sudo] password for will: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  cabextract icoutils libmspack0 libwxbase3.0-0v5 libwxgtk3.0-0v5 p7zip
  p7zip-full python-wxgtk3.0 python-wxversion
Suggested packages:
  libterm-readline-gnu-perl | libterm-readline-perl-perl p7zip-rar wx3.0-doc
The following NEW packages will be installed:
  cabextract icoutils libmspack0 libwxbase3.0-0v5 libwxgtk3.0-0v5 p7zip
  p7zip-full playonlinux python-wxgtk3.0 python-wxversion
0 upgraded, 10 newly installed, 0 to remove and 7 not upgraded.
Need to get 11.9 MB/14.3 MB of archives.
After this operation, 64.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 p7zip amd64 16.02+dfsg-2
  404  Not Found [IP: 91.189.91.23 80]
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 p7zip-full amd64 16.02+dfsg-2
  404  Not Found [IP: 91.189.91.23 80]
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/main amd64 libmspack0 amd64 0.5-1ubuntu0.17.04.1
  404  Not Found [IP: 91.189.91.23 80]
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 icoutils amd64 0.31.2-1
  404  Not Found [IP: 91.189.91.23 80]
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 libwxbase3.0-0v5 amd64 3.0.2+dfsg-4
  404  Not Found [IP: 91.189.91.23 80]
Err:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 libwxgtk3.0-0v5 amd64 3.0.2+dfsg-4
  404  Not Found [IP: 91.189.91.23 80]
Ign:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 python-wxversion all 3.0.2.0+dfsg-4
Err:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 python-wxgtk3.0 amd64 3.0.2.0+dfsg-4
  404  Not Found [IP: 91.189.91.23 80]
Err:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe i386 python-wxversion all 3.0.2.0+dfsg-4
  404  Not Found [IP: 91.189.91.23 80]
Err:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security/main amd64 libmspack0 amd64 0.5-1ubuntu0.17.04.1
  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/p7zip/p7zip_16.02+dfsg-2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/p7zip/p7zip_16.02+dfsg-2_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/p7zip/p7zip-full_16.02+dfsg-2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/p7zip/p7zip-full_16.02+dfsg-2_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libm/libmspack/libmspack0_0.5-1ubuntu0.17.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libm/libmspack/libmspack0_0.5-1ubuntu0.17.04.1_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/i/icoutils/icoutils_0.31.2-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/i/icoutils/icoutils_0.31.2-1_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets3.0/libwxbase3.0-0v5_3.0.2+dfsg-4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets3.0/libwxbase3.0-0v5_3.0.2+dfsg-4_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets3.0/libwxgtk3.0-0v5_3.0.2+dfsg-4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets3.0/libwxgtk3.0-0v5_3.0.2+dfsg-4_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wxpython3.0/python-wxversion_3.0.2.0+dfsg-4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wxpython3.0/python-wxversion_3.0.2.0+dfsg-4_all.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wxpython3.0/python-wxgtk3.0_3.0.2.0+dfsg-4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wxpython3.0/python-wxgtk3.0_3.0.2.0+dfsg-4_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
will@will-HP-Stream-Notebook-PC-11:~$ 
will@will-HP-Stream-Notebook-PC-11:~$ 
will@will-HP-Stream-Notebook-PC-11:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is a virtual package provided by:
  wine-stable 1.8.7-1ubuntu1
  wine-development 2.0-3ubuntu1
You should explicitly select one to install.

E: Package 'wine' has no installation candidate
will@will-HP-Stream-Notebook-PC-11:~$ ^C
will@will-HP-Stream-Notebook-PC-11:~$
```

---

### Post by mastablasta on 2018-01-24
something is wrong with your software sources. 404 means they no longer exist. 

possible solutions:
1. is already mentioned in error report. run:
```
sudo apt-get update
sudo apt-get upgrade
```

2. change the repository server.


you should know that your OS will reach end of life this month, so you should backup the data and upgrade it to 17.10.

if it already reached EoL, you can still upgrade it like this: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by wfriedwaldgmail.c on 2018-01-25
I keep trying!  (by the way, I already upgraded to 17.10, at least I thought I did!)

```
will@will-HP-Stream-Notebook-PC-11:~$ sudo apt-get update
[sudo] password for will: 
Ign:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty InRelease
Ign:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates InRelease              
Ign:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports InRelease            
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty Release                        
  404  Not Found [IP: 91.189.91.23 80]
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates Release                
  404  Not Found [IP: 91.189.91.23 80]
Err:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports Release           
  404  Not Found [IP: 91.189.91.23 80]
Ign:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease
Hit:8 [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty InRelease
Err:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security Release
  404  Not Found [IP: 91.189.88.152 80]
Reading package lists... Done                      
E: The repository 'http://us.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu zesty-backports Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
will@will-HP-Stream-Notebook-PC-11:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
will@will-HP-Stream-Notebook-PC-11:~$ 
```

thanks again!

w

---

### Post by deadflowr on 2018-01-25
> I keep trying! (by the way, I already upgraded to 17.10, at least I thought I did!)
According to your output, no you haven't.
Read howefield's example of how to change sources and upgrade here:
[https://ubuntuforums.org/showthread.php?t=2382832&p=13732693#post13732693]("https://ubuntuforums.org/showthread.php?t=2382832&p=13732693#post13732693")

---

