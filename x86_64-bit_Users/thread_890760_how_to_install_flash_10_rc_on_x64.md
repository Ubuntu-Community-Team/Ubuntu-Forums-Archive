---
title: "how to install flash 10 rc on x64 ?"
date: 2008-08-15
forum: x86 64-bit Users
---

### Post by smooth3006 on 2008-08-15
im having problems installing the new adobe flash player 10 rc on ubuntu x64. is there a good guide on how to do this ? would you guys recommend installing flash 10, or should i stick with flash 9 and wait for ubuntu to give the update ?

---

### Post by soxs on 2008-08-15
I think you need the latest nspluginwrapper, compile it with
(requires: sudo apt-get install build-essential checkinstall; apt-get build-dep nspluginwrapper)
cd to the source dir of nspluginwrapper
```
./configure
make
sudo checkinstall
```
Remove any libflashplugin.so files and libflashalternate*.so in /usr/lib/mozilla/plugins/

Install the 10 rc
```

cp /blah/libflashplayer.so /usr/lib/mozilla/plugins/
libfashplayer.so
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

In case anything of the links for nspluginwrapper got messed up, use
```
sudo nspluginwrapper -v -a -u
``` to fix it

---

### Post by Kilz on 2008-08-15
> **soxs said:**
> I think you need the latest nspluginwrapper, compile it with
(requires: sudo apt-get install build-essential checkinstall; apt-get build-dep nspluginwrapper)
cd to the source dir of nspluginwrapper
```
./configure
make
sudo checkinstall
```
Remove any libflashplugin.so files and libflashalternate*.so in /usr/lib/mozilla/plugins/

Install the 10 rc
```

cp /blah/libflashplayer.so /usr/lib/mozilla/plugins/
libfashplayer.so
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

In case anything of the links for nspluginwrapper got messed up, use
```
sudo nspluginwrapper -v -a -u
``` to fix it

The nspluginwrapper in the repositories will work with the flash 10 rc, no need to compile it.

---

### Post by Superkoop on 2008-08-15
You will need to get some new libraries, I used [[COLOR="Blue"]GetLibs[/COLOR]]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") and you will need to get these libs:
```

getlibs -p libnss3-1d
getlibs -p libnspr4-0d
getlibs -p libcurl3
```

Then you could for the most part follow [[COLOR="Blue"]these instructions[/COLOR]]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html"), you would just download ```
http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz
``` in place of the one listed on that page.

---

### Post by rathel on 2008-08-15
I'm trying this, but I keep getting this error:

```
:sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so 
*** NSPlugin Viewer  *** ERROR: libcurl.so.3: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
```

I'm pretty sure I have all libraries installed. Help? Thanks.

---

### Post by soxs on 2008-08-15
> **rathel said:**
> I'm trying this, but I keep getting this error:

```
:sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so 
*** NSPlugin Viewer  *** ERROR: libcurl.so.3: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
```

I'm pretty sure I have all libraries installed. Help? Thanks.

Did you use getlibs so you got the actual 32 bit libraries, NOT the 64bit ones you get when you install the libpackages via apt/aptitude?

---

### Post by rathel on 2008-08-15
> **soxs said:**
> Did you use getlibs so you got the actual 32 bit libraries, NOT the 64bit ones you get when you install the libpackages via apt/aptitude?

Hmm.. I'll try that, thanks for pointing that out. lol

---

### Post by soxs on 2008-08-15
> **rathel said:**
> Hmm.. I'll try that, thanks for pointing that out. lol

Keep in mind you are trying to run a 32 bit binary which expects 32bit libraries... 
Btw. use the thank button if you feel like ;-)

---

### Post by rathel on 2008-08-15
> **soxs said:**
> Keep in mind you are trying to run a 32 bit binary which expects 32bit libraries... 
Btw. use the thank button if you feel like ;-)

Yay, I finally got it working, now lets see if this flash version lasts longer when playing flash videos than the other version that has been giving me trouble.

---

### Post by IntuitiveNipple on 2008-08-16
I've just packaged **flashplugin-nonfree** with the latest Flash player **10.0.0.569 release candidate** for **Gutsy, Hardy** and **Intrepid**. If you install **getlibs** first the package will automatically update the required 32-bit libraries:
```

flashplugin-nonfree (10.0.0.569ubuntu1~ppa1h) hardy; urgency=low

  * New upstream version 10.0.0.569, release candidate 1
  * debian/postinst: Re-wrote script
     - to use variables to make package-update for later releases a case of
       changing just 5 variables
     - to auto-install 32-bit libraries if getlibs is available
  * debian/config: Re-wrote script to use variables
  * debian/template: Added getlibs
  * debian/control: updated Ubuntu Homepage URL
  * debian/copyright: updated

 -- TJ <ubuntu@tjworld.net>  Sat, 16 Aug 2008 20:00:00 +0100

```
It is [available from my PPA](https://launchpad.net/~intuitivenipple/+archive). To add it to your repository list do:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo sh -c "echo 'deb-src http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >>/etc/apt/sources.list.d/intuitivenipple.list"
sudo apt-get update

```

getlibs is available via the forum thread "[getlibs: Automatically solves dependencies for 32-bit programs on 64-bit](http://ubuntuforums.org/showpost.php?p=2849759&postcount=1)".

**[color=red]Update:[/color]** Unfortunately [getlibs has a couple of bugs](http://ubuntuforums.org/showpost.php?p=5606690&postcount=17), one of which causes the *flashplugin-nonfree installation to fail*. I've fixed the bugs and repackaged getlibs and **it is now also available from PPA**. Install my version of getlibs prior to installing my flashplugin-nonfree package and the installation should succeed:

Do:
```

sudo apt-get install  getlibs flashplugin-nonfree

```

**Note:** If you have the hardy-backports repository enabled you'll need to use a **version-specific install** command for flashplugin-nonfree. This isn't my fault - it is because the last *official* Ubuntu flashplugin-nonfree had a version number from the future (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) and so apt will think the **correct version** (10.0.0.569ubuntu1~ppa1h) is too old!

```

$ sudo apt-get install flashplugin-nonfree=10.0.0.569ubuntu1~ppa1h

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 19.8kB of archives.
After this operation, 172kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  flashplugin-nonfree
Install these packages without verification [y/N]? y
Get: 1 http://ppa.launchpad.net hardy/main flashplugin-nonfree 10.0.0.569ubuntu1~ppa1h [19.8kB]
Fetched 19.8kB in 0s (141kB/s)           
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 210776 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.0.569ubuntu1~ppa1h_amd64.deb) ...
Setting up flashplugin-nonfree (10.0.0.569ubuntu1~ppa1h) ...
Downloading...
--00:02:27--  http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz
           => `./flashplayer10_install_linux_081108.tar.gz'
Resolving download.macromedia.com... 88.221.47.191
Connecting to download.macromedia.com|88.221.47.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,035,433 (3.8M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  394.37 KB/s
   50K .......... .......... .......... .......... ..........  2%  590.22 KB/s
  100K .......... .......... .......... .......... ..........  3%  578.88 KB/s

...

 3800K .......... .......... .......... .......... .......... 97%  609.22 KB/s
 3850K .......... .......... .......... .......... .......... 98%  576.61 KB/s
 3900K .......... .......... .......... ..........           100%  602.61 KB/s

00:02:33 (584.27 KB/s) - `./flashplayer10_install_linux_081108.tar.gz' saved [4035433/4035433]

Download done.
Flash Plugin installed.
Installing required 32-bit libraries (libnss3-1d libnspr4-0d libcurl3) ...
The following i386 packages will be installed: libnss3-1d libnspr4-0d libcurl3
Downloading ...
Installing libraries ...
Libraries installed successfully

```

---

### Post by Jim March on 2008-08-17
Any ideas why your install isn't working?

```
jim@crittersudo apt-get install flashplugin-nonfree
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up flashplugin-nonfree (10.0.0.569ubuntu1~ppa1h) ...
Installing from local file /var/cache/flashplugin-nonfree/flashplayer10_install_linux_081108.tar.gz
Flash Plugin installed.
Installing required 32-bit libraries (libnss3-1d libnspr4-0d libcurl3) ...
The following i386 packages will be installed: libnss3-1d libnspr4-0d libcurl3
Downloading ...
Installing libraries ...
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@critter:~$ 
```

Doesn't matter if I purge everything first or not.

---

### Post by soxs on 2008-08-17
> **Jim March said:**
> Any ideas why your install isn't working?

```
jim@crittersudo apt-get install flashplugin-nonfree
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up flashplugin-nonfree (10.0.0.569ubuntu1~ppa1h) ...
Installing from local file /var/cache/flashplugin-nonfree/flashplayer10_install_linux_081108.tar.gz
Flash Plugin installed.
Installing required 32-bit libraries (libnss3-1d libnspr4-0d libcurl3) ...
The following i386 packages will be installed: libnss3-1d libnspr4-0d libcurl3
Downloading ...
Installing libraries ...
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@critter:~$ 
```

Doesn't matter if I purge everything first or not.
get getlibs

---

### Post by Jim March on 2008-08-17
I did.  I just re-installed getlibs and tried it again - no joy, same error.

This is a very standard Hardy 64 install, Dell laptop, Intel 965 video, everything else very normal.

Like help?

---

### Post by soxs on 2008-08-17
Did you allready try:
```
getlibs -p libnss3-1d libnspr4-0d libcurl3
```

---

### Post by Jim March on 2008-08-17
Yup.  Doesn't make sense.

---

### Post by soxs on 2008-08-17
> **Jim March said:**
> Yup.  Doesn't make sense.

I am sorry, I don't get it...

---

### Post by IntuitiveNipple on 2008-08-17
Unfortunately there are **bugs in the getlibs script** that are causing it to return a 'failed' result to the installer which causes that failed flashplugin-nonfree installation.

I've [reported the bug](http://ubuntuforums.org/showpost.php?p=5603461&postcount=203) so hopefully it will be fixed *upstream*.

You can fix it yourself by replacing the current getlibs script with a corrected version. I've built a package with the required patches for **Feisty**, **Gutsy**, **Hardy** and **Intrepid**. It can be installed from my PPA using:
```

$ sudo apt-get install getlibs

```
(Assumes you've already added my PPA to your sources - see my previous post for the details).

Now you can **redo the flashplugin-nonfree installation**:
```

$ sudo apt-get install --reinstall flashplugin-nonfree

```

The version of getlibs in my PPA:
```

getlibs (2.0.7ubuntu1~ppa1h) hardy; urgency=low

  * Initial repository release.
  * Fix: Returning non-zero return code on success
  * Fix: Successful mktemp was calling clean_up_err()

 -- TJ <ubuntu@tjworld.net>  Sun, 17 Aug 2008 12:58:41 +0100

```

---

### Post by sakis on 2008-08-17
It works just fine for me, thanks :)

---

### Post by I am Losted on 2008-08-20
I have this error
```
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; flashplugin-nonfree (10.0.0.569ubuntu1~ppa2h) ...
Installing from local file /var/cache/flashplugin-nonfree/flashplayer10_install_linux_081108.tar.gz
Flash Plugin installed.
Installing required 32-bit libraries (libnss3-1d libidn11 libnspr4-0d libcurl3) ...
The following i386 packages will be installed: libnss3-1d libidn11 libnspr4-0d libcurl3
Downloading ...
Installing libraries ...
Libraries installed successfully
[B]*** NSPlugin Viewer  *** ERROR: libssl3.so: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so[/B]
dpkg: &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1090;&#1100; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088; flashplugin-nonfree (--configure):
 &#1087;&#1086;&#1076;&#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; post-installation script &#1074;&#1086;&#1079;&#1074;&#1088;&#1072;&#1090;&#1080;&#1083; &#1082;&#1086;&#1076; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; 1
&#1055;&#1088;&#1080; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1087;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1080; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080;:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

getlibs 2.0.7ubuntu1~ppa1h installed.

Can you help me? Sorry for my bad english =(

---

### Post by Nehltic on 2008-08-20
> **I am Losted said:**
> I have this error
```
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; flashplugin-nonfree (10.0.0.569ubuntu1~ppa2h) ...
Installing from local file /var/cache/flashplugin-nonfree/flashplayer10_install_linux_081108.tar.gz
Flash Plugin installed.
Installing required 32-bit libraries (libnss3-1d libidn11 libnspr4-0d libcurl3) ...
The following i386 packages will be installed: libnss3-1d libidn11 libnspr4-0d libcurl3
Downloading ...
Installing libraries ...
Libraries installed successfully
[B]*** NSPlugin Viewer  *** ERROR: libssl3.so: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so[/B]
dpkg: &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1090;&#1100; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088; flashplugin-nonfree (--configure):
 &#1087;&#1086;&#1076;&#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; post-installation script &#1074;&#1086;&#1079;&#1074;&#1088;&#1072;&#1090;&#1080;&#1083; &#1082;&#1086;&#1076; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; 1
&#1055;&#1088;&#1080; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1087;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1080; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080;:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

getlibs 2.0.7ubuntu1~ppa1h installed.

Can you help me? Sorry for my bad english =(

I have the same problem. Anyone have any ideas?

---

### Post by rubberglove on 2008-08-21
I was having trouble with getlibs failing on libnss3-1d and libnspr4-0d.
Installing your version didn't help, so I dug a bit deeper. 

The errors I was getting were:
```
libnss3-1d was not found in your repositories
Make sure you have all repositories enabled and updated
```

Looking in the getlibs script, I traced that error to:
```
templink=`apt-cache --no-all-versions show $pack | grep -o -m 1 '[^ ]*\.deb$'`
```

Running that apt-cache command manually with libnss3-1d indeed finds the (installed) package, but wasn't listing the .deb filename anywhere!

WTF, I asked myself... turns out (long story short) that at one point I had added a repo that installed a custom version of those two packages ([https://launchpad.net/~fta/+archive](https://launchpad.net/~fta/+archive)) -- I was probably installing FF3.1, after which point I disable the repository. 

This left me with installed packages that are no longer downloadable. 
To get around it, I (temporarily) modified getlibs to remove the '--no-all-versions' switch (before realizing I should just manually downgrade those two packages to the normal versions).

Which worked great. Unless I'm missing something, the '--no-all-versions' switch shouldn't be necessary in combination with the grep -m 1 switch, since grep will only return the first .deb filename and (I assume) apt-cache show will order the packages by version. I can't say I've really thought that through, though. 

Posting all this in case it's useful for someone...

---

### Post by d4v1dv00 on 2008-08-31
Hi there,

I follow the instructions but given the following output after i ran:

```
sudo apt-get install  getlibs flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
getlibs is already the newest version.
Suggested packages:
  konqueror-nsplugins libflashsupport ttf-xfree86-nonfree xfs
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
Need to get 20.1kB of archives.
After this operation, 12.3kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  flashplugin-nonfree
Install these packages without verification [y/N]? y
Get:1 http://ppa.launchpad.net hardy/main flashplugin-nonfree 10.0.0.569ubuntu1~ppa2h [20.1kB]
Fetched 20.1kB in 1s (10.1kB/s)            
Preconfiguring packages ...
(Reading database ... 228704 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.124.0ubuntu2 (using .../flashplugin-nonfree_10.0.0.569ubuntu1~ppa2h_amd64.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (10.0.0.569ubuntu1~ppa2h) ...
Downloading...
--10:23:02--  http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz
           => `./flashplayer10_install_linux_081108.tar.gz'
Resolving download.macromedia.com... 125.252.235.191
Connecting to download.macromedia.com|125.252.235.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,035,433 (3.8M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   31.08 KB/s
   50K .......... .......... .......... .......... ..........  2%   23.19 KB/s
  100K .......... .......... .......... .......... ..........  3%   36.66 KB/s
  150K .......... .......... .......... .......... ..........  5%   18.49 KB/s
  200K .......... .......... .......... .......... ..........  6%   21.28 KB/s
  250K .......... .......... .......... .......... ..........  7%   26.03 KB/s
  300K .......... .......... .......... .......... ..........  8%   19.90 KB/s
  350K .......... .......... .......... .......... .......... 10%   21.44 KB/s
  400K .......... .......... .......... .......... .......... 11%   29.96 KB/s
  450K .......... .......... .......... .......... .......... 12%   30.65 KB/s
  500K .......... .......... .......... .......... .......... 13%   29.92 KB/s
  550K .......... .......... .......... .......... .......... 15%   30.39 KB/s
  600K .......... .......... .......... .......... .......... 16%   30.61 KB/s
  650K .......... .......... .......... .......... .......... 17%   31.25 KB/s
  700K .......... .......... .......... .......... .......... 19%   20.51 KB/s
  750K .......... .......... .......... .......... .......... 20%   58.01 KB/s
  800K .......... .......... .......... .......... .......... 21%   30.92 KB/s
  850K .......... .......... .......... .......... .......... 22%   30.04 KB/s
  900K .......... .......... .......... .......... .......... 24%   30.55 KB/s
  950K .......... .......... .......... .......... .......... 25%   30.96 KB/s
 1000K .......... .......... .......... .......... .......... 26%   30.01 KB/s
 1050K .......... .......... .......... .......... .......... 27%   31.26 KB/s
 1100K .......... .......... .......... .......... .......... 29%   30.30 KB/s
 1150K .......... .......... .......... .......... .......... 30%   27.02 KB/s
 1200K .......... .......... .......... .......... .......... 31%   30.01 KB/s
 1250K .......... .......... .......... .......... .......... 32%   25.00 KB/s
 1300K .......... .......... .......... .......... .......... 34%   24.98 KB/s
 1350K .......... .......... .......... .......... .......... 35%   28.58 KB/s
 1400K .......... .......... .......... .......... .......... 36%   31.26 KB/s
 1450K .......... .......... .......... .......... .......... 38%   30.31 KB/s
 1500K .......... .......... .......... .......... .......... 39%   31.25 KB/s
 1550K .......... .......... .......... .......... .......... 40%   31.09 KB/s
 1600K .......... .......... .......... .......... .......... 41%   30.96 KB/s
 1650K .......... .......... .......... .......... .......... 43%   21.80 KB/s
 1700K .......... .......... .......... .......... .......... 44%   49.19 KB/s
 1750K .......... .......... .......... .......... .......... 45%   31.19 KB/s
 1800K .......... .......... .......... .......... .......... 46%   30.99 KB/s
 1850K .......... .......... .......... .......... .......... 48%   29.98 KB/s
 1900K .......... .......... .......... .......... .......... 49%   31.22 KB/s
 1950K .......... .......... .......... .......... .......... 50%   31.26 KB/s
 2000K .......... .......... .......... .......... .......... 52%   30.96 KB/s
 2050K .......... .......... .......... .......... .......... 53%   29.71 KB/s
 2100K .......... .......... .......... .......... .......... 54%   30.30 KB/s
 2150K .......... .......... .......... .......... .......... 55%   31.10 KB/s
 2200K .......... .......... .......... .......... .......... 57%   31.60 KB/s
 2250K .......... .......... .......... .......... .......... 58%   29.83 KB/s
 2300K .......... .......... .......... .......... .......... 59%   30.79 KB/s
 2350K .......... .......... .......... .......... .......... 60%   31.06 KB/s
 2400K .......... .......... .......... .......... .......... 62%   27.52 KB/s
 2450K .......... .......... .......... .......... .......... 63%   28.66 KB/s
 2500K .......... .......... .......... .......... .......... 64%   24.72 KB/s
 2550K .......... .......... .......... .......... .......... 65%   28.59 KB/s
 2600K .......... .......... .......... .......... .......... 67%   27.13 KB/s
 2650K .......... .......... .......... .......... .......... 68%   30.18 KB/s
 2700K .......... .......... .......... .......... .......... 69%   30.74 KB/s
 2750K .......... .......... .......... .......... .......... 71%   31.47 KB/s
 2800K .......... .......... .......... .......... .......... 72%   30.55 KB/s
 2850K .......... .......... .......... .......... .......... 73%   30.67 KB/s
 2900K .......... .......... .......... .......... .......... 74%   30.94 KB/s
 2950K .......... .......... .......... .......... .......... 76%   31.20 KB/s
 3000K .......... .......... .......... .......... .......... 77%   30.64 KB/s
 3050K .......... .......... .......... .......... .......... 78%   30.25 KB/s
 3100K .......... .......... .......... .......... .......... 79%   31.66 KB/s
 3150K .......... .......... .......... .......... .......... 81%   31.26 KB/s
 3200K .......... .......... .......... .......... .......... 82%   30.29 KB/s
 3250K .......... .......... .......... .......... .......... 83%   23.62 KB/s
 3300K .......... .......... .......... .......... .......... 85%   44.78 KB/s
 3350K .......... .......... .......... .......... .......... 86%   31.27 KB/s
 3400K .......... .......... .......... .......... .......... 87%   29.68 KB/s
 3450K .......... .......... .......... .......... .......... 88%   31.16 KB/s
 3500K .......... .......... .......... .......... .......... 90%   31.62 KB/s
 3550K .......... .......... .......... .......... .......... 91%   29.78 KB/s
 3600K .......... .......... .......... .......... .......... 92%   23.44 KB/s
 3650K .......... .......... .......... .......... .......... 93%   38.35 KB/s
 3700K .......... .......... .......... .......... .......... 95%   25.05 KB/s
 3750K .......... .......... .......... .......... .......... 96%   24.39 KB/s
 3800K .......... .......... .......... .......... .......... 97%   27.25 KB/s
 3850K .......... .......... .......... .......... .......... 98%   28.76 KB/s
 3900K .......... .......... .......... ..........           100%   30.32 KB/s

10:25:18 (29.03 KB/s) - `./flashplayer10_install_linux_081108.tar.gz' saved [4035433/4035433]

Download done.
Flash Plugin installed.
/var/lib/dpkg/info/flashplugin-nonfree.postinst: 188: dpkg-architecture: not found
*** NSPlugin Viewer  *** ERROR: libcurl.so.3: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by d4v1dv00 on 2008-08-31
> **IntuitiveNipple said:**
> Unfortunately there are **bugs in the getlibs script** that are causing it to return a 'failed' result to the installer which causes that failed flashplugin-nonfree installation.

I've [reported the bug](http://ubuntuforums.org/showpost.php?p=5603461&postcount=203) so hopefully it will be fixed *upstream*.

You can fix it yourself by replacing the current getlibs script with a corrected version. I've built a package with the required patches for **Feisty**, **Gutsy**, **Hardy** and **Intrepid**. It can be installed from my PPA using:
```

$ sudo apt-get install getlibs

```
(Assumes you've already added my PPA to your sources - see my previous post for the details).

Now you can **redo the flashplugin-nonfree installation**:
```

$ sudo apt-get install --reinstall flashplugin-nonfree

```

The version of getlibs in my PPA:
```

getlibs (2.0.7ubuntu1~ppa1h) hardy; urgency=low

  * Initial repository release.
  * Fix: Returning non-zero return code on success
  * Fix: Successful mktemp was calling clean_up_err()

 -- TJ <ubuntu@tjworld.net>  Sun, 17 Aug 2008 12:58:41 +0100

```

Added your repos but cant find 2.0.7, now installed 2.0.6. anything missing for me?

---

### Post by d4v1dv00 on 2008-08-31
now it works for me after i did:

```
getlibs -p libnss3-1d libnspr4-0d libcurl3
```

then did a reinstallation of flash

```
sudo apt-get install --reinstall flashplugin-nonfree
```

---

### Post by Didjit on 2008-09-01
Any way to get this to work with a newer version of nspluginwrapper? I keep getting ```

Flash Plugin installed.
invalid option -n
nspluginwrapper, configuration tool.  Version 1.0.0

   usage: nspluginwrapper [flags] [command [plugin(s)]]

   -h --help               print this message
   -v --verbose            flag: set verbose mode
   -a --auto               flag: set automatic mode for plugins discovery
   -l --list               list plugins currently installed
   -u --update             update plugin(s) currently installed
   -i --install [FILE(S)]  install plugin(s)
   -r --remove [FILE(S)]   remove plugin(s)

dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree


```

I can force to the default version in Hardy, but it seems a few repos out there have an earlier version.

Thanks

Didjit

---

### Post by alexcuervo on 2008-09-08
For Ubuntu 64 bit users there is a 2 click installer for the latest Flash 10 RC at [http://www.queleimporta.com/how-to-install-flash-10-rc-on-ubuntu-64-bits-with-2-clicks/en/]("http://queleimporta.com/how-to-install-flash-10-rc-on-ubuntu-64-bits-with-2-clicks/en/")

---

### Post by peakshysteria on 2008-09-08
Tried it. Didn't work. Removed the grey (flash)boxes and replaced them with the background colour of the site (just like Flashblock actually which seemed nice since Flashblock crashes FF when loading to many tabs or tabs with lots of flash at once). But no flash where possible to play (because flash weren't there at all). When going to sites with flash firefox prompted me to install the latest flash player because it wasn't installed or I had an older version. Clicking the prompt made me choose between three different flash plugins. The first one didn't work at all. The second one: ```
Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r100
``` worked nicely. But the damn grey boxes are back again.

---

### Post by alexcuervo on 2008-09-08
@ peakshysteria

When using the installer for the latest Flash 10 RC at [http://www.queleimporta.com/how-to-install-flash-10-rc-on-ubuntu-64-bits-with-2-clicks/en/](http://www.queleimporta.com/how-to-install-flash-10-rc-on-ubuntu-64-bits-with-2-clicks/en/) 

you have to click YES for every prompt as it is installing many required libraries.

---

### Post by Kilz on 2008-09-08
> **alexcuervo said:**
> @ peakshysteria

When using the installer for the latest Flash 10 RC at 

you have to click YES for every prompt as it is installing many required libraries.

I dont recommend installing scripts from someone new. I dont recommend anyone installing a script that they have not read and understand. That command they ask you to copy and paste in includes a download and a script. Scripts can install alll kinds of things, some of them no good.

---

### Post by alexcuervo on 2008-09-08
> **Kilz said:**
> I dont recommend installing scripts from someone new. I dont recommend anyone installing a script that they have not read and understand. That command they ask you to copy and paste in includes a download and a script. Scripts can install alll kinds of things, some of them no good.

My bad, I should not have said that. Sorry.
All the code for the script is available here for eveyones review.
[http://queleimporta.com/downloads/flash10RC_en.sh](http://queleimporta.com/downloads/flash10RC_en.sh)

---

### Post by Mauriciobc on 2008-09-25
I am getting broken mirrors from Getlibs for libnss3-1d and libnspr4-0d

```
The following i386 packages will be installed: libnss3-1d
Continue [Y/n]? y
Downloading ...
Failed to download file http://ppa.launchpad.net/reacocard-awn/ubuntu/pool/main/n/nss/libnss3-1d_3.12.1~rc2-0ubuntu1~fta1~hardy_i386.deb
The mirrors do not have the requested file or there is no internet connection
No packages to install
The following i386 packages will be installed: libnspr4-0d
Continue [Y/n]? y
Downloading ...
Failed to download file http://ppa.launchpad.net/reacocard-awn/ubuntu/pool/main/n/nspr/libnspr4-0d_4.7.1+1.9-0ubuntu5~fta1~hardy_i386.deb
The mirrors do not have the requested file or there is no internet connection
No packages to install

```

What's happening?

---

### Post by Sef on 2008-09-26
>  	 		**Re: how to install flash 10 rc on x64 ?**
 		I am getting broken mirrors from Getlibs for libnss3-1d and libnspr4-0d

 	Code:
 	The following i386 packages will be installed: libnss3-1d
Continue [Y/n]? y
Downloading ...
Failed to download file [http://ppa.launchpad.net/reacocard-awn/ubuntu/pool/main/n/nss/libnss3-1d_3.12.1~rc2-0ubuntu1~fta1~hardy_i386.deb](http://ppa.launchpad.net/reacocard-awn/ubuntu/pool/main/n/nss/libnss3-1d_3.12.1~rc2-0ubuntu1~fta1~hardy_i386.deb)
The mirrors do not have the requested file or there is no internet connection
No packages to install
The following i386 packages will be installed: libnspr4-0d
Continue [Y/n]? y
Downloading ...
Failed to download file [http://ppa.launchpad.net/reacocard-awn/ubuntu/pool/main/n/nspr/libnspr4-0d_4.7.1+1.9-0ubuntu5~fta1~hardy_i386.deb](http://ppa.launchpad.net/reacocard-awn/ubuntu/pool/main/n/nspr/libnspr4-0d_4.7.1+1.9-0ubuntu5~fta1~hardy_i386.deb)
The mirrors do not have the requested file or there is no internet connection
No packages to install 
What's happening? 	


The site could be down.  I would try again later.

---

### Post by smooth3006 on 2008-10-04
ill just wait to install flash 10 until it's in the repositories or an update.

---

### Post by digitzero on 2008-10-05
> **alexcuervo said:**
> My bad, I should not have said that. Sorry.
All the code for the script is available here for eveyones review.
[http://queleimporta.com/downloads/flash10RC_en.sh](http://queleimporta.com/downloads/flash10RC_en.sh)

Thanks this worked for me.  I was having problems with my 64bit Ubuntu Hardy Heron and Flash.  I'd run a fix, and it seemed like a couple days later it'd be broken again *until* I ran the fix at the above website.

 And yes, you should always view the source code of any script you run on your system.  Here's the code for reference:

```

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# More Super minor updates by Alejandro Cuervo 3[at]cuervo[dot]net
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10 RC"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz
tar zxvf flashplayer10_install_linux_091508.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "Yoy may re-start Firefox now"

```

---

### Post by perky on 2008-10-05
After (and before) installing the script mentioned above to install Flash 10, I am getting a grey box instead of the flash applet.

If anyone else has had this problem, and you have found a fix, please post your solution :)

FYI:
No errors occurred in the script.

Distro:  8.10 64bit

Firefox:  3.03

In about: plugins:
Shockwave Flash
    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r12
MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

cat /etc/adobe/mms.cfg
WindowlessDisable = 1

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/262693](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/262693) < Downgrading to nspluginwrapper_0.9.91.5-2ubuntu2_amd64.deb did not make the problem go away (after restarting FF)

Just for kicks I also edited the script to keep the nspluginwrapper to version 0.9.91.5-2, ran it again, but still no go :/

Prior to running this script, I was using Flash 9, and having the same problem (grey box).

```

ls -al /usr/lib/mozilla/plugins/
total 9804
drwxr-xr-x 2 andy users     4096 2008-10-06 10:24 .
drwxr-xr-x 4 root root      4096 2008-07-02 19:57 ..
lrwxrwxrwx 1 root root        37 2008-10-06 10:24 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rwxr-xr-x 1 root root  10008276 2008-10-06 09:39 libflashplayer.so
lrwxrwxrwx 1 root root        44 2008-09-28 11:35 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root        42 2008-09-28 11:35 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root        44 2008-09-28 11:35 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root        50 2008-09-28 11:35 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root        60 2008-10-06 09:39 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```
```

ls -al /usr/lib/firefox-addons/plugins/
total 12
drwxr-xr-x 2 root root 4096 2008-10-06 10:39 .
drwxr-xr-x 5 root root 4096 2008-07-02 19:55 ..
lrwxrwxrwx 1 root root   60 2008-10-06 10:39 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so


```
Help!  Thanks in advance :)

---

### Post by gwenn on 2008-10-06
no need to do complicated things!
you just unninstall with:    apt-get purge flashplugin     and after that you must enable all restricted repo's,then:      apt-get install flashplugin-nonfree.

---

### Post by perky on 2008-10-06
> **gwenn said:**
> no need to do complicated things!
you just unninstall with:    apt-get purge flashplugin     and after that you must enable all restricted repo's,then:      apt-get install flashplugin-nonfree.

Thanks for the reply, however, I think this is the version I was initially using with a fresh install of Intrepid.

I found it frustratingly slow - FF would randomly freeze for a min or so - hence the exploration of other versions of flash :)

---

### Post by Kilz on 2008-10-06
> **perky said:**
> Thanks for the reply, however, I think this is the version I was initially using with a fresh install of [COLOR="Red"]**Intrepid.**[/COLOR]

I found it frustratingly slow - FF would randomly freeze for a min or so - hence the exploration of other versions of flash :)

This section (the 64bit) is for releases , Intrepid is under Development.Please take this problem to the Intrepid development section. 
I also 100% suggest you FILE A BUG REPORT.

---

### Post by gwenn on 2008-10-06
For me flash works very fine on Intrepid.Intrepind also work very good,and I have a fresh kernel...But flash 10 from the repo must be the best they can tested so...

---

### Post by perky on 2008-10-06
Fixed - it ended up being [_the repository I was using (psyke83)_]("http://ubuntuforums.org/showthread.php?t=866965").

After commenting this out, reloading sources, removing, rm'ing, and reinstalling flashplugin-nonfree, its working again :)

Still buggy, first applet I tested did not make it all the way through without turning into a grey box.

I guess that is normal for betas - at least it is playable now, yay!

Hope this helps anyone else with the same issues using the same repository

---

### Post by perky on 2008-10-06
> **Kilz said:**
> This section (the 64bit) is for releases , Intrepid is under Development.Please take this problem to the Intrepid development section. 
I also 100% suggest you FILE A BUG REPORT.

I could be wrong here, but I don't think it is Intrepid at fault.

Bug report has been submitted to Adobe.

---

### Post by Kilz on 2008-10-06
> **perky said:**
> I could be wrong here, but I don't think it is Intrepid at fault.

Bug report has been submitted to Adobe.

What part of your post is in the wrong section dont you understand?

Second, since you are running a development version you, as a good member of a linux community, should file bug reports to the team working on Intrepid.

---

### Post by perky on 2008-10-06
> **Kilz said:**
> What part of your post is in the wrong section dont you understand?

Second, since you are running a development version you, as a good member of a linux community, should file bug reports to the team working on Intrepid.

Sorry about that, I came across this thread via searching, not browsing  - I will be more mindful when posting problems in future.  (I did not see your first post until after my second post).

Moving along, [_a fix_]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403") already exists on the launchpad, thank-you for guiding me this way :)

I installed a few more 32bit libs mentioned there, and re-installed flashplugin-nonfree.

Not sure if that fixed the random crashes or not, but 5 simultaneous tabs/videos played flawlessly, and have not had any problems since.

---

### Post by simpsonna on 2008-10-09
I've been trying this:

> I think you need the latest nspluginwrapper, compile it with
(requires: sudo apt-get install build-essential checkinstall; apt-get build-dep nspluginwrapper)
cd to the source dir of nspluginwrapper
Code:

./configure
make
sudo checkinstall

Remove any libflashplugin.so files and libflashalternate*.so in /usr/lib/mozilla/plugins/

Install the 10 rc
Code:

cp /blah/libflashplayer.so /usr/lib/mozilla/plugins/
libfashplayer.so
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

In case anything of the links for nspluginwrapper got messed up, use
Code:

sudo nspluginwrapper -v -a -u

to fix it

But I can't get past this:

[PHP]simpsonna@simpsonna-laptop:~$ sudo apt-get install build-essential checkinstall
[sudo] password for simpsonna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
checkinstall is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up b43-fwcutter (1:011-1) ...
Error parsing proxy URL http://:8080/: Invalid host name.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)[/PHP]

---

### Post by mo.reina on 2008-10-10
i tried all sorts of different ways to install flash 10.  finally i just copied the libflashplayer.so file to .mozilla/plugins and voila! seamonkey and FF3 all of a sudden have flash 10.

---

### Post by BoobsLover on 2008-12-04
Hey,

I've installed GetLibs and these :
```

getlibs -p libnss3-1d
getlibs -p libnspr4-0d
getlibs -p libcurl3
```

but when i try to install rc10 i get this error at the end :

```
Download done.
Flash Plugin installed.
/var/lib/dpkg/info/flashplugin-nonfree.postinst: 188: dpkg-architecture: not found
```

Which result in connection problem issues when streaming videos on some sites (on youtube i get &#733;this video is not available ...&#733; error at almost every clip)

I guess i might miss some libs,but i don't know which ones ?

:?: any suggestions ?

---

