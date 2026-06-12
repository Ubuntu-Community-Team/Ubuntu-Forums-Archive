---
title: "Wine does not run"
date: 2012-03-31
forum: Wine
---

### Post by cscj01 on 2012-03-31
I have Ubuntu 11.10 x64 and Wine 1.4 installed.  When I try to launch a program, I get a message "Starting <program name>", but nothing starts and the message goes away.  If I try to start wine from a terminal, I get the message```
 /usr/bin/wine: No such file or directory
```But wine is in usr/bin.  None of the wine programs in /usr/bin will run , giving me the same message as above.  What's going on here?.

---

### Post by zombifier25 on 2012-03-31
Try reinstalling wine.
```
sudo apt-get install --reinstall wine
```

---

### Post by cscj01 on 2012-03-31
I re-installed.  Same problem.

---

### Post by nothingspecial on 2012-03-31
*Thread moved to **Wine**.*

---

### Post by davidvandoren on 2012-03-31
```
Brief 32/64 bit howto.

Except for Debian & clones, 32bit = /usr/lib, /usr/local/lib, etc
64bit = /usr/lib64
Debian uses /usr/lib32 & /usr/lib respectively.
Wine is usually compiled 32 bit, and needs/uses 32 bit libs, because windows programs in the main are 32 bit
```

I found this here [http://www.linuxquestions.org/questions/linux-software-2/error-when-trying-to-run-wine-usr-bin-wine-no-such-file-or-directory-787683/](http://www.linuxquestions.org/questions/linux-software-2/error-when-trying-to-run-wine-usr-bin-wine-no-such-file-or-directory-787683/)
maybe it helps. 



Open nautilus.
Go to your home directory.
In nautilus; View and show hidden files and folders.
Go to .wine/ drive_c and windows
Right click on the notepad.exe and chose open with other application.
Then choose run a custom command and type wine.
Sometimes, this helps.

---

### Post by davidvandoren on 2012-03-31
```
                                  **Re: /usr/bin/wine: No such file or directory**             
                                                                I was not interpreting this correctly.

In fact, [there was a bug in ia32-libs]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all").

Personally, I've been having trouble getting dpkg to understand  dependency chains since upgrading so it could be that dpkg failed to  notice it needs ia32-libs-multiarch. The other possibility is that the  dependencies haven't been properly implemented in the wine or ia32-libs  packages.

Anyway, the solution is:
     Code:
    ** sudo apt-get install ia32-libs-multiarch:i386 **
I have a feeling this is going to get messy down the line. As it  stands, i now have two 32bit libc6 packages which apparently don't  conflict with each other....

```This one came from here and might help figuring out the problem. 
[http://ubuntuforums.org/showthread.php?t=1846286](http://ubuntuforums.org/showthread.php?t=1846286)

---

### Post by dino99 on 2012-03-31
Latest wine is 1.5.1 and since 1.4 the installation is quite different depending on arch.
Rename your .wine to wineold and create a new installation (you still can copy/paste the progs folder into the new .wine)

add this ppa and update/upgrade first:

[https://launchpad.net/~scottritchie/+archive/build-tests](https://launchpad.net/~scottritchie/+archive/build-tests)

---

### Post by cscj01 on 2012-03-31
> **davidvandoren said:**
> ```
Brief 32/64 bit howto.

Except for Debian & clones, 32bit = /usr/lib, /usr/local/lib, etc
64bit = /usr/lib64
Debian uses /usr/lib32 & /usr/lib respectively.
Wine is usually compiled 32 bit, and needs/uses 32 bit libs, because windows programs in the main are 32 bit
```

I found this here [http://www.linuxquestions.org/questions/linux-software-2/error-when-trying-to-run-wine-usr-bin-wine-no-such-file-or-directory-787683/](http://www.linuxquestions.org/questions/linux-software-2/error-when-trying-to-run-wine-usr-bin-wine-no-such-file-or-directory-787683/)
maybe it helps. 



Open nautilus.
Go to your home directory.
In nautilus; View and show hidden files and folders.
Go to .wine/ drive_c and windows
Right click on the notepad.exe and chose open with other application.
Then choose run a custom command and type wine.
Sometimes, this helps.
I can get to "open with other application."  After that, there is no option to open notepad.exe with a custom command.

If I understand what has been discussed here, Wine is always a 32-bit app.  So if I install any version of Wine and then install ia32-libs-multiarch:i386, Wine should run.  If that is incorrect, please let me know.

As an extra bit of information, I went to Synaptic and marked wine:i386 for installation.  I got the following list of changes required:```
To be removed:

britty
britty-x11
libgd2-xpm
pdl
ubuntu-desktop
unrar
w3m
To be installed:

libasound2:i386
libavahi-client3:i386
libavahi-common3:i386libavahi-client3:i386
libc6:i386
libcomerr2:i386
libcups2:i386
libcupsimage2:i386
libdb5.1:i386
libdbus-1-3:i386
libdrm-intel1:i386
libdrm-nouveau1a:i386
libdrm-radeon1:i386
libdrm2:i386
libexpat1:i386
libffi6:i386
libfontconfig1:i386
libfreetype6:i386
libgcc1:i386
libgcrypt11:i386
libgd2noxpm
libgl1-mesa-dri:i386
libgl1-mesa-glx:i386
libglapi-mesa:i386
.
.
.
```for a total of 75 additions plus the removals.  This seems like a train wreck to do this.  Therefor, I'm hoping I can just install ia32-libs-multiarch:i386 and get things working.  But I'm not sure.  So I would appreciate someone either verfying what I am saying or giving me guidance on how to address this issue.  Thanks for all the comments so far.

---

### Post by cscj01 on 2012-03-31
> **dino99 said:**
> Latest wine is 1.5.1 and since 1.4 the installation is quite different depending on arch.
Rename your .wine to wineold and create a new installation (you still can copy/paste the progs folder into the new .wine)

add this ppa and update/upgrade first:

[https://launchpad.net/~scottritchie/+archive/build-tests](https://launchpad.net/~scottritchie/+archive/build-tests)I added the PPA and entered the following:```
sudo apt-get update
sudo apt-get upgrade
```Wine 1.4 was not listed as a package that would be upgraded.  No Wine was listed in the upgrade list.  So how do I get it installed?

---

### Post by davidvandoren on 2012-04-01
Since nobody else is helping out here and I am running ubuntu 10.04 32 and not Ubuntu 11.10 x64, I sugest you install virtualbox then install the same version Ubuntu 11.10 x64 in it and try out what works. 

This way you won't mess up your system. 

As far as I can tell from another thread a week ago, you'll have to compile it from source.
This is from here [http://www.ashwinraon.com/2012/03/installing-wine-1-5-with-itunes-10-x-support-on-ubuntu-12-0411-1011-04/?wpmp_switcher=desktop](http://www.ashwinraon.com/2012/03/installing-wine-1-5-with-itunes-10-x-support-on-ubuntu-12-0411-1011-04/?wpmp_switcher=desktop)
```
wget http://prdownloads.sourceforge.net/wine/wine-1.5.0.tar.bz2 tar -xjvf wine-1.5.0.tar.bz2 cd wine-1.5.0 sudo apt-get install flex bison qt3-dev-tools qt4-qmake ./configure cd tools ./wineinstall
```

Ubuntu thread is here [http://ubuntuforums.org/showthread.php?t=1945905](http://ubuntuforums.org/showthread.php?t=1945905)

---

### Post by cscj01 on 2012-04-03
I removed my Wine 1.4 installation with Synaptic and installed Wine 1.5 from source.  After having the same problem as before, I removed it.  I then removed any remaining Wine files from /usr/local/ and it's sub-folders, renamed ~/.wine to .wine.bak, and installed Wine 1.2.  Then I installed ia32-libs-multarch:i386.  Now my Wine applications run (mostly).  I'm still having problems with Spotify.  I am considering installing the Linux Spotify app.  So, I will close this thread.

Thanks for those of you who offered suggestions, particularly davidvandoren.

---

### Post by chris_gs on 2012-04-07
Hey,
Just wanted to add. I had the same problem.
Mine has seemed to be fixed by simply installing the ia32-libs-multiarch:i386 module through synaptic (and all the dependencies that it says need to be installed).
Mine seemed to break after I purged the libre-office PPA.
Thanks for the hint.

Cheers,
Chris

---

