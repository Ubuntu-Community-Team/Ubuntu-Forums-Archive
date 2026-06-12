---
title: "Multiple Wine Installer now Available for Ubuntu !!!"
date: 2008-10-09
forum: Wine
---

### Post by david_kt on 2008-10-09
[COLOR="Red"]Warning: To use multiple wine, you must remove wine from ordinary installation. So, just install any version of wine you want using this installer.[/COLOR]
[B]UPDATE:
- Bug fix: Enable wineprefixcreate for older wine ( 24/11/08 )
- Ensure installing deb package to empty directory ( 1/11/08 )
- Added installation using deb package ( 31/10/08 )
- Workaround to solve Preloader: Warning: failed to reserve range 00000000-60000000 for older wines ( 13/10/08 )
- Remove valgrind and libldap2-dev if older wines fail to compile. ( 13/10/08 ) 
- Previous installer might not work smoothly as I attached the wrong one (work in progress). I have revised to the new one, now completely GUI. You do not need to run in terminal any more, just run it because I have added progress bar GUI for all long processes. ( 11/10/08 )[/B]
=======================================================================================
The bad news, sometimes certain application could run on certain wine version, but could not run on later wine version. Problem start occur if a few application that you want to run needed different wine versions.

Off course you could run regression test and report to wine developer, but in the mean time you have to upgrade/downgrade wine to suit applications you want to run.

Sometimes you are not sure which wine version is suitable for your application, but to try many versions of wine require you to downgrade and upgrade continuously.

**The good news is:**

[COLOR="Red"]Update:
If you want to use downloaded deb package, you do not need to run sudo apt-get build-dep wine. Just make sure you have lzma installed:

```
[COLOR="Red"]sudo apt-get install lzma[/COLOR]
```

It is much faster then compiling from source and require much lesser disc space.

For system other than gnome, you might not have zenity which is use in this script. As such, you will need to install zenity:

```
[COLOR="Red"]sudo apt-get install zenity[/COLOR]
```

[/COLOR]
I just finished making a script to install multiple wine at the same time, and all are installed in your home directory so that it will not mess up your system files

You could install as many wine version as you want with this installer. I have tried it with wine 1.0, 1.1.0 - 1.1.5, all installed at the same time and what you have to do is just to click and click, no command line needed.

This installer also could install older wine versions, and also future wine version by selecting "wine-other" option, I have tried to install wine-0.9.59 using this option and it went well.

What you have to do is:

1. sudo apt-get build-dep wine (you could skip this step if you want to install using deb packages only)
2.  - download the installer attached,
    - extract it, and then
    - double click the extracted file to run,
    - Choose "Run" (you could "Run in terminal" but not necessary) 

If you compile from source, it could take a few hours, depending on how fast your computer is and how many wine versions you choose to install. But if you choose to install from downloaded deb package, it just took a few seconds or minutes.

The installer will do below actions:
1. Downloading wine source codes according to your selection.
2. Extracting, compiling and installing with a minor tweak to suit "multiple wine" situation.
3. It comes with uninstaller, in case you want to uninstall it.

**USAGE**

I have many wine versions now in my computer, but how do I use them? Here is the answer.

There are two ways to use it:
1. Without changing system file,
2. Make a link in system file (a little bit more dangerous but much more convenient to use).
[B]
1. Without changing system file[/B]

1.1 Adding "open with" and changing default wine
Right click on any exe file and choose:

> Properties> Open with > Add > Use a custom command > Browse > navigate to $home/wine-X.X.X (that you have installed) > bin > wine-X.X.X and click "open" button. > click "Add" button.

Repeat the above process until all wine version appear in the "open with" tab.

And to choose the default wine when you double click exe file, select the radio button there as you wish.

1.2. Changing launcher
For application launcher, you have to substitute wine in the "command" entry to "$home/wine-x.x.x/bin/wine-xxx"

Using this method, you have to give full path to launch wine-x.x.x in terminal (i.e. $home/wine-x.x.x/bin/wine-xxx yourprogram.exe)
**2. Make a link in system file (a little bit more dangerous but much more convenient to use)**

First, you have to make a link in your /usr/bin directory:
Open terminal and:

```
cd /usr/bin
```

Next, make a link:

```
sudo ln -s '$home/wine-X.X.X/bin/wine-X.X.X'
```

and key in your password as requested.

1.1 Adding "open with" and changing default wine
Right click on any exe file and choose:

```
Properties> Open with > Add > wine-x.x.x > click "Add" button.
```

Yes, now it available in the application selection. Repeat the above process until all wine versions appear in the "open with" tab.

And to choose the default wine when you double click exe file, select the radio button there as you wish.

1.2. Changing launcher
For application launcher, you have to substitute wine in the "command" entry to wine-x.x.x

Using this method, you could also launch wine-x.x.x from terminal (i.e. wine-x.x.x yourprogram.exe)

If later on you decide to remove certain wine version, you should remove this link as well. To remove it:

```
cd /usr/bin
```

Next, remove the un-needed link:

```
sudo rm wine-X.X.X
```

[U]
**Troubleshooting**[/U]
**1. Older wines fail to compile.**
If you want to install old wines and it fail to compile, remove 2 packages:

```
sudo apt-get remove valgrind libldap2-dev
```

and then run the installer again.
[B]
2. Preloader: Warning: failed to reserve range 00000000-60000000[/B]

[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

Please let me know if you have any questions.

DK

PS: Please do not confuse multiple wine with wineprefix. With this installer you could have multiple wine versions and multiple wineprefix.

---

### Post by X-Legs on 2008-10-09
This is great, thanks!

---

### Post by david_kt on 2008-10-09
> **X-Legs said:**
> This is great, thanks!

Last night I did some experiments, I could use the deb package to install at any location I want, including user home folder. This would save a lot of time as we do not need to compile it anymore. But I am not sure whether wines install using this method will work as good as original ones as I forced install it, but it works.

If you want to give it a try, just let me know and I will create another installer for this purpose. The other advantage is also we do not need to install many packages for compiling (do not need apt-get build-dep wine).

DK

---

### Post by david_kt on 2008-10-11
I have revised the installer, now completely GUI. You do not need to run in terminal any more, just run it because I have added progress bar GUI for all long processes:

- Downloading wine source codes 
- Extracting
- configure
- make depend
- make
- make install
- installing

So, now you know which step the installer is doing. Please let me know if you have difficulty in running the script.

DK

---

### Post by david_kt on 2008-10-13
I tried to install wine 0.9.43 and wine 0.9.46 using the installer but failed. Upon investigation, there are two packages that preventing those wines to be installed i.e. valgrind and libldap2-dev. Removing those 2 packages solves the problem.

DK

---

### Post by Nymz on 2008-10-23
So is the "Making wine..." apart of the process and is it supposed to take quite awhile?

---

### Post by david_kt on 2008-10-23
> **Nymz said:**
> So is the "Making wine..." apart of the process and is it supposed to take quite awhile?

Yes. Depending on your computer's processor and memory, it may take around 30 minutes. Making wine is the longest process.

DK

---

### Post by sephyroff on 2008-10-29
i used sudo apt-get build dep-wine, but it used lots of space. How can i uninstall it? thanks!

---

### Post by david_kt on 2008-10-29
> **sephyroff said:**
> i used sudo apt-get build dep-wine, but it used lots of space. How can i uninstall it? thanks!

Open terminal, copy and paste ALL below command together at the same time, NOT line by line:

```
sudo apt-get remove \
bison \
cvs git-core \
flex \
fontforge \
gcc \
git \
libasound2-dev \
libaudio-dev \
libc6-dev \
libcapi20-3 \
libcapi20-dev \
libcupsys2-dev \
libdbus-1-dev \
libesd0-dev \
libexif-dev \
libexpat1-dev \
libfontconfig1-dev \
libfreetype6-dev \
libgcrypt11-dev \
libgl1-mesa-dev \
libglib1.2-dev \
libglib2.0-dev \
libglu1-mesa-dev \
libgnutls-dev \
libgpg-error-dev \
libgphoto2-2-dev \
libhal-dev \
libice-dev \
libieee1284-3-dev \
libjpeg62-dev \
liblcms1-dev \
libldap2-dev \
libltdl3 \
libltdl3-dev \
liblzo-dev \
libmad0 \
libmad0-dev \
libmng-dev \
libncurses5-dev \
libodbcinstq1c2 \
libogg-dev \
libopencdk10-dev \
libpng12-dev \
libpopt-dev \
libqt3-headers \
libqt3-mt \
libqt3-mt-dev \
libsane-dev \
libsm-dev \
libssl-dev \
libtasn1-3-dev \
libtiff4-dev \
libtiffxx0c2 \
libusb-dev \
libvorbis-dev \
libvorbisfile3 \
libx11-dev \
libxau-dev \
libxcomposite-dev \
libxcursor-dev \
libxdmcp-dev \
libxext-dev \
libxfixes-dev \
libxft-dev \
libxi-dev \
libxinerama-dev \
libxml2-dev \
libxmu-dev \
libxmu-headers \
libxrandr-dev \
libxrender-dev \
libxslt1-dev \
libxt-dev \
libxv-dev \
libxxf86vm-dev \
linux-libc-dev \
m4 \
make \
mesa-common-dev \
odbcinst1debian1 \
qt3-dev-tools \
unixodbc \
unixodbc-dev \
valgrind \
x11proto-composite-dev \
x11proto-core-dev \
x11proto-fixes-dev \
x11proto-input-dev \
x11proto-kb-dev \
x11proto-randr-dev \
x11proto-video-dev \
x11proto-xext-dev \
x11proto-xf86vidmode-dev \
x11proto-xinerama-dev \
x-dev \
xtrans-dev \
zlib1g-dev
```

DK

---

### Post by escapedturkey on 2008-10-30
Love your script!

I mentioned it here:

[http://forum.eeeuser.com/viewtopic.php?id=49335](http://forum.eeeuser.com/viewtopic.php?id=49335)

I'm getting configure errors when installing Wine 0.9.15 manually and with your script. It's missing some kind of dependency, but I'm not sure what to do to fix this. The .deb install works fine. So there must be someway to get it to work. It's the only version that works well with Fallout 1 and 2 via Wine. :)

Running Ubuntu 8.0.4 Hardy Heron.

Can you help, please? :)

---

### Post by david_kt on 2008-10-30
> **escapedturkey said:**
> Love your script!

I mentioned it here:

[http://forum.eeeuser.com/viewtopic.php?id=49335](http://forum.eeeuser.com/viewtopic.php?id=49335)

I'm getting configure errors when installing Wine 0.9.15 manually and with your script. It's missing some kind of dependency, but I'm not sure what to do to fix this. The .deb install works fine. So there must be someway to get it to work. It's the only version that works well with Fallout 1 and 2 via Wine. :)

Running Ubuntu 8.0.4 Hardy Heron.

Can you help, please? :)

Have you removed valgrind and libldap2-dev:
```
sudo apt-get remove valgrind libldap2-dev
```

If not yet, try remove these two packages and run again the installer. I tried a few minutes ago, it works for wine 0.9.15. 
Edit: It succeed until make, I did not continue with make install. But when I continue, make install failed, now I am investigating.

DK

---

### Post by david_kt on 2008-10-30
As very old wine fail to compile properly, I have added an option to install from downloaded deb package to install any version of wine. Be careful when choosing installation directory. f you choose to create new directory, make sure you are in the new directory before pressing ok.

It also save you a lot of time if you choose to install from deb package.

Please see the installer at the first post.

DK

---

### Post by escapedturkey on 2008-10-30
Two questions:

1) This will allow multiple installs even using a .deb?

2) What do you mean by current directory?

Thank you. :)

---

### Post by david_kt on 2008-10-30
> **escapedturkey said:**
> Two questions:

1) This will allow multiple installs even using a .deb?

2) What do you mean by current directory?

Thank you. :)

First of all, please re-download the installer (Multiple_Wine_311008r2.tar.gz), there is a small mistake when renaming the wine executable.

1) Yes, it will install multiple wine using deb package, it is very easy. Just make sure you choose the correct directory to install, preferebly /home/username/wine-x.x.x
For wine naming, you just need to type x.x.x, or may be you want to name it Fall2 (to become wine-Fall2).

2) Could you specify where did I mentioned "current directory"?

---

### Post by escapedturkey on 2008-10-30
"f you choose to create new directory, make sure you are in the new directory before pressing ok."

Was confused about that statement.

Thank you. :)

---

### Post by david_kt on 2008-10-30
> **escapedturkey said:**
> "f you choose to create new directory, make sure you are in the new directory before pressing ok."

Was confused about that statement.

Thank you. :)

That is when you choose to install from deb package, it will ask you 3 things:

1. To locate downloaded deb package
2. To locate installation directory, make sure it is in your home directory and preferable empty directory. You could "create new directory" when choosing it, **make sure you are in the new directory before pressing ok**.
3. The name you want to use for this wine.

That is what I meant, in bold.
DK

---

### Post by escapedturkey on 2008-10-30
Getting an error:

..... etc etc...


tar: ./usr/lib/wine/libglut32.def: Cannot open: No such file or directory
tar: ./usr/lib/wine/libd3d8.def: Cannot open: No such file or directory
tar: ./usr/lib/wine/libd3d9.def: Cannot open: No such file or directory
tar: ./usr/lib/wine/libd3dx8.def: Cannot open: No such file or directory
tar: ./usr/lib/wine/libopengl32.def: Cannot open: No such file or directory
tar: ./usr/lib/wine/libwined3d.def: Cannot open: No such file or directory
tar: ./usr/lib/wine/libddraw.def: Cannot open: No such file or directory
tar: ./usr/lib/wine/libdxerr8.a: Cannot open: No such file or directory
tar: ./usr/lib/wine/libdxerr9.a: Cannot open: No such file or directory
tar: ./usr/lib/wine/libdxguid.a: Cannot open: No such file or directory
tar: ./usr/lib/wine/libstrmiids.a: Cannot open: No such file or directory
tar: ./usr/lib/wine/libuuid.a: Cannot open: No such file or directory
tar: ./usr/lib/wine/libwinecrt0.a: Cannot open: No such file or directory
tar: ./usr/lib/libwine.so.1: Cannot open: No such file or directory
tar: ./usr/lib/libwine_unicode.so.1: Cannot open: No such file or directory
tar: ./usr/lib/mime: Cannot mkdir: No such file or directory
tar: ./usr/lib/mime/packages: Cannot mkdir: No such file or directory
tar: ./usr/lib/mime/packages/wine: Cannot open: No such file or directory
tar: ./usr/bin/wineg++: Cannot create symlink to `winegcc': No such file or directory
tar: ./usr/bin/winecpp: Cannot create symlink to `winegcc': No such file or directory
tar: ./usr/share/man/man1/wineg++.1.gz: Cannot create symlink to `winegcc.1.gz': No such file or directory
tar: Error exit delayed from previous errors
dpkg-deb: subprocess tar returned error exit status 2
Note: command 'dpkg-deb -x /home/escapedturkey/Downloads/wine_0.9.15~winehq0~ubuntu~6.06-1_i386.deb /home/escapedturkey/wine-0.9.15' returned status 2.  Aborting.

---

### Post by escapedturkey on 2008-10-30
Tried it a second time and it worked. Typo on my part?

Thank you for updating your script. You may want to consider sending it to the WineHQ people. It's very useful. :)

---

### Post by david_kt on 2008-10-30
> **escapedturkey said:**
> Tried it a second time and it worked. Typo on my part?

Thank you for updating your script. You may want to consider sending it to the WineHQ people. It's very useful. :)

Hehehe... WineHQ people will laugh at my script you know, it is so simple. They could do much better script.

By the way, could you use wine 0.9.15 now? I have not tested it, I just making the script for you to use.

DK

---

### Post by escapedturkey on 2008-10-30
You may think it's simple, but saves tons of problems for many of us.

It's working great! 

Question: When I run winecfg (from the different version install), where is it storing the information, pertaining to the particular Wine or to all versions?

Example: /home/escapedturkey/wine-0.9.15/usr/bin/wine-0.9.15 winecfg

Hope my question makes sense. :)

---

### Post by david_kt on 2008-10-30
> **escapedturkey said:**
> You may think it's simple, but saves tons of problems for many of us.

It's working great! 

Question: When I run winecfg (from the different version install), where is it storing the information, pertaining to the particular Wine or to all versions?

Example: /home/escapedturkey/wine-0.9.15/usr/bin/wine-0.9.15 winecfg

Hope my question makes sense. :)

First of all, you could not run winecfg that way, but this way:
```
/home/escapedturkey/wine-0.9.15/usr/bin/winecfg
```

Secondly, this winecfg is for all wine versions. If you want to set different setting or different hacking, try wineprefix. As I mentioned in the first post, you could have multiple wine version and multiple wineprefix now.

DK

---

### Post by escapedturkey on 2008-10-30
Edit, ah I see, it works your way. Didn't see the window at first.

Thank you so much for this. It's exactly what is needed. :)

---

### Post by deathpulse on 2008-11-01
I can't seem up gunzip the file?  Is it a broken link?

---

### Post by david_kt on 2008-11-01
> **deathpulse said:**
> I can't seem up gunzip the file?  Is it a broken link?

If you use mouse, just right click on the downloaded file (Multiple_Wine_311008r2.tar) and choose extract here. If you use command line, go to the directory (may be cd Desktop if you download it on desktop) and then:

```

tar -xf Multiple_Wine_311008r2.tar
```

DK

---

### Post by escapedturkey on 2008-11-01
Suggestion:

Have the script by default create a folder and exuctable based on the wine version he/she is installing and make selecting a different directory an option (check mark, confirm, etc.). Reason being if you install this, accidently, in the wrong place it will really mess up your /home permissions. :)

---

### Post by deathpulse on 2008-11-01
I try to right click and select extract here but there is an error that it is not a gzip file?  I think the link is broken?  Its about 30Kb for me?

---

### Post by deathpulse on 2008-11-01
Got it :).  It had a .gz extension on the file - but it is really a .tar file.  Sheesh.

---

### Post by david_kt on 2008-11-01
> **escapedturkey said:**
> Suggestion:

Have the script by default create a folder and exuctable based on the wine version he/she is installing and make selecting a different directory an option (check mark, confirm, etc.). Reason being if you install this, accidently, in the wrong place it will really mess up your /home permissions. :)

Yes, that is true. Still thinking how to make sure the chosen directory is empty but no time yet. I thought I will give a test like ls chosen directory, if it give something than will reject the directory and repeat the "choose install directory process".

If happen to messed up your directory, just do

```
chmod -R 770 to that directory
```

DK

---

### Post by escapedturkey on 2008-11-01
Could do something like -- say the bob is installing Wine 0.18.3 (just an example) -- the program can say:

Automatic install (check mark)

Install will go into /home/bob/wine-0.18.3 for a different directory. If it's a deb, you can still get the Wine version from extrapolation of the name.

Manual Install (check mark):

Please enter the directory you want to install: etc etc.

Just an example. Person can choose either automatic or manual. :)

---

### Post by david_kt on 2008-11-01
> **escapedturkey said:**
> Could do something like -- say the bob is installing Wine 0.18.3 (just an example) -- the program can say:

Automatic install (check mark)

Install will go into /home/bob/wine-0.18.3 for a different directory. If it's a deb, you can still get the Wine version from extrapolation of the name.

Manual Install (check mark):

Please enter the directory you want to install: etc etc.

Just an example. Person can choose either automatic or manual. :)

I have that idea as well, but my skills is limited. I think I should use sed, give me sometime to study more. In the meantime, I will add a script to make sure the chosen directory is empty to avoid trouble. I have found a way, just need to get to my ubuntu box at home.

DK

---

### Post by david_kt on 2008-11-01
I have added a "safety feature" to ensure installation directory is empty for deb package.

I am still studying escapedturkey suggestion to be more flexible on installation directory for compiled wine and also to to add confirmation of installation directory before it continue. If any of you have some suggestion of how to do this, please let me know.

DK

---

### Post by sea_monkey987 on 2008-11-01
great script david_kt!  I tried it and it worked for me the first time!  unfortunately, it didn't work for me the second time.  i had formatted my computer to re-install Intrepid.  after that I followed what you said (notably sudo apt-get build-dep wine), but keep getting a status code 2 from make.  do you know what's wrong?

P.S.  the first time, when your script worked on my comp., i was still using the pre-realease version of Intrepid.  I just reformatted after the official release.  i tried your old script (that i knew worked before) and your latest one.  both return error code 2 from 'make' and 'install'

---

### Post by david_kt on 2008-11-02
> **sea_monkey987 said:**
> great script david_kt!  I tried it and it worked for me the first time!  unfortunately, it didn't work for me the second time.  i had formatted my computer to re-install Intrepid.  after that I followed what you said (notably sudo apt-get build-dep wine), but keep getting a status code 2 from make.  do you know what's wrong?

P.S.  the first time, when your script worked on my comp., i was still using the pre-realease version of Intrepid.  I just reformatted after the official release.  i tried your old script (that i knew worked before) and your latest one.  both return error code 2 from 'make' and 'install'

I will test it soon on intrepid, but in the meant time, why don't you try the deb option. Download the deb file you want to install, and then run the script, choose deb. It do not require build-dep wine to install deb, and much faster (just take a few seconds to install).

DK

---

### Post by david_kt on 2008-11-02
> **sea_monkey987 said:**
> great script david_kt!  I tried it and it worked for me the first time!  unfortunately, it didn't work for me the second time.  i had formatted my computer to re-install Intrepid.  after that I followed what you said (notably sudo apt-get build-dep wine), but keep getting a status code 2 from make.  do you know what's wrong?

P.S.  the first time, when your script worked on my comp., i was still using the pre-realease version of Intrepid.  I just reformatted after the official release.  i tried your old script (that i knew worked before) and your latest one.  both return error code 2 from 'make' and 'install'

Is sudo apt-get build-dep wine run successfully? I have just upgraded to intrepid (but not formatting disc, just upgrade) the script still run without any error. May be you could try below instead of sudo apt-get build-dep wine:

```
sudo apt-get install \
bison \
cvs git-core \
flex \
fontforge \
gcc \
git \
libasound2-dev \
libaudio-dev \
libc6-dev \
libcapi20-3 \
libcapi20-dev \
libcupsys2-dev \
libdbus-1-dev \
libesd0-dev \
libexif-dev \
libexpat1-dev \
libfontconfig1-dev \
libfreetype6-dev \
libgcrypt11-dev \
libgl1-mesa-dev \
libglib1.2-dev \
libglib2.0-dev \
libglu1-mesa-dev \
libgnutls-dev \
libgpg-error-dev \
libgphoto2-2-dev \
libhal-dev \
libice-dev \
libieee1284-3-dev \
libjpeg62-dev \
liblcms1-dev \
libldap2-dev \
libltdl3 \
libltdl3-dev \
liblzo-dev \
libmad0 \
libmad0-dev \
libmng-dev \
libncurses5-dev \
libodbcinstq1c2 \
libogg-dev \
libopencdk10-dev \
libpng12-dev \
libpopt-dev \
libqt3-headers \
libqt3-mt \
libqt3-mt-dev \
libsane-dev \
libsm-dev \
libssl-dev \
libtasn1-3-dev \
libtiff4-dev \
libtiffxx0c2 \
libusb-dev \
libvorbis-dev \
libvorbisfile3 \
libx11-dev \
libxau-dev \
libxcomposite-dev \
libxcursor-dev \
libxdmcp-dev \
libxext-dev \
libxfixes-dev \
libxft-dev \
libxi-dev \
libxinerama-dev \
libxml2-dev \
libxmu-dev \
libxmu-headers \
libxrandr-dev \
libxrender-dev \
libxslt1-dev \
libxt-dev \
libxv-dev \
libxxf86vm-dev \
linux-libc-dev \
m4 \
make \
mesa-common-dev \
odbcinst1debian1 \
qt3-dev-tools \
unixodbc \
unixodbc-dev \
valgrind \
x11proto-composite-dev \
x11proto-core-dev \
x11proto-fixes-dev \
x11proto-input-dev \
x11proto-kb-dev \
x11proto-randr-dev \
x11proto-video-dev \
x11proto-xext-dev \
x11proto-xf86vidmode-dev \
x11proto-xinerama-dev \
x-dev \
xtrans-dev \
zlib1g-dev
```

and then try the script again. But using deb package is much easier and faster.

DK

---

### Post by sea_monkey987 on 2008-11-02
not sure what the problem is.  i got my game working with the latest so i don't need the old wine anymore.  however, for troubleshooting purposes:
         1. I compiled wine version 1.0 using your script and it works
         2. compiling wine version 0.9.49 does not work (status code 2 from make)

I will soon try to install using the deb and tell you what I find.  i see that opening the deb the GDeb shows that a dependency is not met.  won't this be a problem?

---

### Post by david_kt on 2008-11-02
> **sea_monkey987 said:**
> not sure what the problem is.  i got my game working with the latest so i don't need the old wine anymore.  however, for troubleshooting purposes:
         1. I compiled wine version 1.0 using your script and it works
         2. compiling wine version 0.9.49 does not work (status code 2 from make)

I will soon try to install using the deb and tell you what I find.  i see that opening the deb the GDeb shows that a dependency is not met.  won't this be a problem?

Have you tried the troubleshooting section:

```
sudo apt-get remove valgrind libldap2-dev
```

if wine fail to compile?

DK

---

### Post by sea_monkey987 on 2008-11-02
those packages are not installed, so not removed.

---

### Post by escapedturkey on 2008-11-03
> **david_kt said:**
> I have added a "safety feature" to ensure installation directory is empty for deb package.

I am still studying escapedturkey suggestion to be more flexible on installation directory for compiled wine and also to to add confirmation of installation directory before it continue. If any of you have some suggestion of how to do this, please let me know.

DK

Impressive support. Do you take PayPal donations? :)

If it's a problem, I would just have it default to a directory (no option to change) such as /home/username/wine-0.9.15 (could grep to derive version name if a .deb) and the person can always move/copy the folder somewhere else after the installation. Might make it easier for you and the user. :)

By the way: If you try to use winecreateprefix (to make a unique winecfg configuration directory), wine expects a wine binary to be found and your script changes the binary's name. I had to cp wine-version to wine. Just an FYI.

---

### Post by escapedturkey on 2008-11-03
> **sea_monkey987 said:**
> those packages are not installed, so not removed.

To get 0.9.15 installed, I did the following:

You may need the following first:

[http://packages.ubuntu.com/gutsy/i386/libldap2/download](http://packages.ubuntu.com/gutsy/i386/libldap2/download)

If you get the libjack error. Do the following:

sudo apt-get install libjack0.100.0-0
sudo cp /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so

[http://ubuntuforums.org/archive/index.php/t-456002.html](http://ubuntuforums.org/archive/index.php/t-456002.html)

[http://forum.eeeuser.com/viewtopic.php?id=49335](http://forum.eeeuser.com/viewtopic.php?id=49335)

---

### Post by david_kt on 2008-11-03
> **escapedturkey said:**
> Impressive support. Do you take PayPal donations? :)


Wow, thank you very much for the offer. But I do it just for fun, helping other people. If you like to donate, I suggest to give it wine instead, or buy crossover (the sponsor of wine). They are the ones who really do a good job.

> **escapedturkey said:**
> 
If it's a problem, I would just have it default to a directory (no option to change) such as /home/username/wine-0.9.15 (could grep to derive version name if a .deb) and the person can always move/copy the folder somewhere else after the installation. Might make it easier for you and the user. :) 

I have found a way to do it actually, but there is a little problem such as there are wine version with 10 characters and there are also wine version with 11 characters. I am still looking of a way to standardize it i.e. a script to detect whether the wine version is 10 or 11 characters. Worse thing I will just default it to 11 characters so the wine version with 10 characters would have ~ behind e.g. wine_1.1.7~ and the one with 11 characters would have the correct name e.g. wine-0.9.15.

I think it is easy to do such as passing a test if the elevent characters = ~ then it is 10 characters wine version. But I still have no time to do it yet.[/QUOTE]

> **escapedturkey said:**
> 
By the way: If you try to use winecreateprefix (to make a unique winecfg configuration directory), wine expects a wine binary to be found and your script changes the binary's name. I had to cp wine-version to wine. Just an FYI.

While that might be true for older wine, it would not be necessary anymore for newer wine. Wineprefixcreate is deprecated. For newer wine, what you need to do is:

```
mkdir /home/username/.wine_whatever
```

And then you could straightaway use the wine-version such as:
```

env WINEPREFIX="/home/username/.wine_whatever wine-version your_program.exe
```

Anyway I will check whether or not I could create a workaround so that you do not need to rename it wine for older wine. Thanks for your feedback.

DK

---

### Post by SBFC on 2008-11-11
> **david_kt said:**
> 
And then you could straightaway use the wine-version such as:
Code:

env WINEPREFIX="/home/username/.wine_whatever wine-version your_program.exe

Anyway I will check whether or not I could create a workaround so that you do not need to rename it wine for older wine. Thanks for your feedback.

Is this supposed to setup the new wine directory?

---

### Post by david_kt on 2008-11-23
> **SBFC said:**
> Is this supposed to setup the new wine directory?

For newer wine = Yes.

Back to escapedturkey,

I found a workaround to make sure you do not need to rename wine i.e. to make a symlink instead of renaming it. As such, I will edit the script to add symlink instead of renaming and you could use wineprefixcreate again without the need to rename wine binary anymore (I found this workaround long time ago but keep forgotten to update the script).

DK

---

### Post by david_kt on 2008-11-24
I have updated the script to create symlinks instead of renaming the binary as renaming the binary would prevent wineprefixcreate to work, based on escapeturkey feedback.

DK

---

### Post by escapedturkey on 2008-12-05
DK,

Thank you for the fix. Hope you have Happy Holidays! :D

---

### Post by demonstorm on 2008-12-23
Maybe interesting for kubuntu users: i just wanted to install Multiple_Wine and several wine-versions, but when starting the script and then choosing the 'deb' option, nothing happened, the script just ran but didn't do anything. After running it from console i saw there was zenity missing, so i installed it. After that multiple_wine was running and doing its job properly.

Maybe one could add to the first post that kubuntu users should check if zenity is installed. I have a fresh kubuntu 8.10 and it was missing.

---

### Post by sp3ctum on 2009-01-01
Thanks a lot. I managed to install an old version of Wine (0.9.46) and have a much better fps in Warcraft 3 now.
I'll do some more testing later, but just wanted to thank you for the script.

---

### Post by david_kt on 2009-01-01
> **sp3ctum said:**
> Thanks a lot. I managed to install an old version of Wine (0.9.46) and have a much better fps in Warcraft 3 now.
I'll do some more testing later, but just wanted to thank you for the script.

I am glad the script help you. By the way, did you use the deb package or compiling from source?

DK

---

### Post by sp3ctum on 2009-01-03
I used a deb package. The installation was so simple, which is a big bonus to me since I'm new to linux.
Oh and I installed all the old dependencies with deb packages as well. One was especially hard to find. Must be because they're old.

---

### Post by david_kt on 2009-02-18
Recently I need multiple wine myself and encounter problem if some if the wine is installed using the normal method (apt-get, synaptic, or double click on the deb package).

The solution is simple, remove the installed wine, and install any version of wine using this installer.

DK

---

### Post by trlkly on 2009-02-24
While I don't know how you feel about ies4linux, I think you might want to take a play from its playbook.

When it finishes installing, it creates a symlink to the appropriate file in ~/bin (which is added to $PATH if necessary.) I think this would be an excellent option for your script. (If you install from the .deb package, you can just ask what you want to name the link.)

---

### Post by david_kt on 2009-02-24
> **trlkly said:**
> While I don't know how you feel about ies4linux, I think you might want to take a play from its playbook.

When it finishes installing, it creates a symlink to the appropriate file in ~/bin (which is added to $PATH if necessary.) I think this would be an excellent option for your script. (If you install from the .deb package, you can just ask what you want to name the link.)

Thank you for your suggestion. It is not difficult to add that function, but the problem is I do not want user to mess up the system file using the script. To make a symlink to /usr/bin, you have to run the script as root (or with sudo), which is not a good practice for script made by amateur like me.

From my last experiment, we have to remove wine from normal install in order to make multiple wine work. As such, if we in case user make a mistake and choose the default name wine, it would also create problem. So, just a reminder, if you want to make a symlink, make sure you put a custom name for it (e.g. wine_1.1.14) as already pointed out in the script.

Well, I could put a test to refuse default name actually. If many people like to have this function, then I could easily add it. The good point to run it with sudo is you could choose to install multiple wine in /opt directory instead of home directory.

Or may be I would create two scripts, one to run as a user, and the other to run as root.

DK

---

### Post by cristian.palmas on 2009-04-01
Hi DK,

I tried to use your script to install wine 0.9.58 from a deb package I downloaded on my own. Once installed in my home directory under wine-0.9.58, I noticed that there were not in it the fake C and the fake Program Files directories.

Is it OK or I made something wrong?
I only tested your script quickly so no surprise if I made a mistake.

Bye... and thanks for the script

Cristian Palmas

---

### Post by david_kt on 2009-04-01
> **cristian.palmas said:**
> Hi DK,

I tried to use your script to install wine 0.9.58 from a deb package I downloaded on my own. Once installed in my home directory under wine-0.9.58, I noticed that there were not in it the fake C and the fake Program Files directories.

Is it OK or I made something wrong?
I only tested your script quickly so no surprise if I made a mistake.

Bye... and thanks for the script

Cristian Palmas

Yes that is right. Please read how to use it, and let me know if you have difficulties. Please make sure you uninstall the default wine, otherwise it would create a conflict.

DK

---

### Post by cristian.palmas on 2009-04-02
Hi DK,

I've read all of the discussion in this thread.
I'm not sure to have completely understood how to use multiple configurations, so I make an example.

I want to install IES4Linux for my web design job.
So I want to install the 0.9.58 wine version. I use your script to install from the relative .deb package in the directory called "wine-0.9.58" in my home.

After that, I want to install IES4Linux but If I run the installer script I don't know which version of wine it uses. I think It's better to run it when only the 0.9.58 version is present.

For the other applications, after having installed the different versions I need, what is the right procedure?
Suppose I want to install Safari through wine-1.1.17. I think I have to do the following steps:

[LIST=1]
[*] export WINEPREFIX=/home/chris/wine-bottles/Safari

[*] /home/chris/wine-1.1.17/bin/wine-1.1.17 SafariSetup.exe

[*] export WINEPREFIX=/home/chris/wine-1.1.17

[*] /home/chris/wine-1.1.17/bin/winecfg

[*] To run Safari: /home/chris/wine-1.1.17/bin/wine-1.1.17 $HOME/wine-bottles/Safari/Safari.exe
[/LIST]

Is it correct?

---

### Post by david_kt on 2009-04-02
> **cristian.palmas said:**
> 
After that, I want to install IES4Linux but If I run the installer script I don't know which version of wine it uses. I think It's better to run it when only the 0.9.58 version is present.

For the other applications, after having installed the different versions I need, what is the right procedure?
Suppose I want to install Safari through wine-1.1.17. I think I have to do the following steps:

[LIST=1]
[*] export WINEPREFIX=/home/chris/wine-bottles/Safari

[*] /home/chris/wine-1.1.17/bin/wine-1.1.17 SafariSetup.exe

[*] export WINEPREFIX=/home/chris/wine-1.1.17

[*] /home/chris/wine-1.1.17/bin/winecfg

[*] To run Safari: /home/chris/wine-1.1.17/bin/wine-1.1.17 $HOME/wine-bottles/Safari/Safari.exe
[/LIST]

Is it correct?

For IES4Linux I don't know and I have to check how it works first. For other application, this step is not correct:

[*] export WINEPREFIX=/home/chris/wine-1.1.17

You have to keep the WINEPREFIX in the installation directory (i.e. WINEPREFIX=/home/chris/wine-bottles/Safari).

DK

---

### Post by david_kt on 2009-04-02
> **cristian.palmas said:**
> 
I want to install IES4Linux for my web design job.
So I want to install the 0.9.58 wine version. I use your script to install from the relative .deb package in the directory called "wine-0.9.58" in my home.

After that, I want to install IES4Linux but If I run the installer script I don't know which version of wine it uses. I think It's better to run it when only the 0.9.58 version is present.

After I check, IES4Linux use default wine. What you could do is:
1. uninstall the default wine.
2. Open terminal and export wine=/home/chris/wine-1.1.17/usr/bin/wine
3. Run IES4Linux installer
4. Edit IES4Linux launcher, replace wine with /home/chris/wine-1.1.17/usr/bin/wine

I hope that would do it.

DK

---

### Post by cristian.palmas on 2009-04-06
> **david_kt said:**
> After I check, IES4Linux use default wine. What you could do is:
1. uninstall the default wine.
2. Open terminal and export wine=/home/chris/wine-1.1.17/bin/wine
3. Run IES4Linux installer
4. Edit IES4Linux launcher, replace wine with /home/chris/wine-1.1.17/bin/wine

I hope that would do it.

DK

Thanks for the tips.

I now installed wine-0.9.58 anyway is the path correct?
In the folder there are only "etc" and "usr", whereas "bin" is under "usr".

Can I put a symbolic link in ~/bin instead of /usr/bin? I've already the ~/bin in my $PATH

---

### Post by david_kt on 2009-04-06
> **cristian.palmas said:**
> Thanks for the tips.

I now installed wine-0.9.58 anyway is the path correct?
In the folder there are only "etc" and "usr", whereas "bin" is under "usr".

Can I put a symbolic link in ~/bin instead of /usr/bin? I've already the ~/bin in my $PATH

Sorry my mistake, it should be:

2. Open terminal and export wine=/home/chris/wine-0.9.58/usr/bin/wine
4. Edit IES4Linux launcher, replace wine with /home/chris/wine-0.9.58/usr/bin/wine

Please check again the path.

Please do not put any wine in your path. You could put wine-1.1.17 or whatever it is in your path, but not wine, winecfg etc as it would interfere with other wine version.

DK

---

### Post by cristian.palmas on 2009-04-06
> **david_kt said:**
> Sorry my mistake, it should be:

2. Open terminal and export wine=/home/chris/wine-0.9.58/usr/bin/wine


I'm a bit puzzled... Do I have to digit "WINEPREFIX=..." or "wine=..."? I think you meant to write "WINEPREFIX=..."

> 
Please do not put any wine in your path. You could put wine-1.1.17 or whatever it is in your path, but not wine, winecfg etc as it would interfere with other wine version.

DK

Don't worry, I wanted to create symbolink links targeting version executables like wine-0.9.58, wine-1.1.0 and so on...

Bye.

---

### Post by david_kt on 2009-04-06
> **cristian.palmas said:**
> I'm a bit puzzled... Do I have to digit "WINEPREFIX=..." or "wine=..."? I think you meant to write "WINEPREFIX=..."



Don't worry, I wanted to create symbolink links targeting version executables like wine-0.9.58, wine-1.1.0 and so on...

Bye.


Nope,it is correct:

export wine=/home/chris/wine-0.9.58/usr/bin/wine

Because IES4Linux looking for wine and it would stop if there is no wine. Remember you have to uninstall your default wine first.

If you put wine-0.9.58 etc on your path, that should not be a problem.

DK

---

### Post by cristian.palmas on 2009-04-06
Ok.

Now I have a little problem.

I created in ~/bin the symbolic link using the command in your tutorial:

```
sudo ln -s '$home/wine-0.9.58/usr/bin/wine-0.9.58'
```

but when I launch wine-0.9.58 the message is "command not found"...

---

### Post by david_kt on 2009-04-06
> **cristian.palmas said:**
> Ok.

Now I have a little problem.

I created in ~/bin the symbolic link using the command in your tutorial:

```
sudo ln -s '$home/wine-0.9.58/usr/bin/wine-0.9.58'
```

but when I launch wine-0.9.58 the message is "command not found"...

Please open nautilus to ensure that there is a symlink in the /usr/bin.
It is not ~/bin but /usr/bin

DK

---

### Post by cristian.palmas on 2009-04-06
> **david_kt said:**
> Please open nautilus to ensure that there is a symlink in the /usr/bin.
It is not ~/bin but /usr/bin

DK

There is not any symlink in /usr/bin...

---

### Post by cristian.palmas on 2009-04-06
@David

I removed the symlink in ~/bin

I tried to launch IEs4Linux but it failed. I went in the folder where the application launcher was via the terminal, and being there I  wrote in the command line:
```

# export wine=/home/chris/wine-0.9.58/usr/bin/wine
# ./ies4linux

```

It suddenly appears the message that wine wasn't installed... Why?

---

### Post by cristian.palmas on 2009-04-06
@David

Since my ~/bin didn't let the symlink work even if the folder is in $PATH, I opted to put the symlink into /usr/bin

I tested it writing in the command line "wine-0.9.58" and it ran.
Anyway, IEs4Linux keep not to install because it sees that no wine is installed...

I followed your steps but it didn't install.
Maybe it does not work exporting "wine"?

Besides... I don't have any other wine installed.

```

# export wine=/home/chris/wine-0.9.58/usr/bin/wine

```

---

### Post by david_kt on 2009-04-06
> **cristian.palmas said:**
> @David

Since my ~/bin didn't let the symlink work even if the folder is in $PATH, I opted to put the symlink into /usr/bin

I tested it writing in the command line "wine-0.9.58" and it ran.
Anyway, IEs4Linux keep not to install because it sees that no wine is installed...

I followed your steps but it didn't install.
Maybe it does not work exporting "wine"?

Besides... I don't have any other wine installed.

```

# export wine=/home/chris/wine-0.9.58/usr/bin/wine

```
Try to put symlink of /home/chris/wine-0.9.58/usr/bin/wine into /usr/bin.
This time you do not need to do export wine=/home/chris/wine-0.9.58/usr/bin/wine.

Open terminal and try wine, make sure it works. And then tray again IEs4linux.

---

### Post by cristian.palmas on 2009-04-06
> **david_kt said:**
> Try to put symlink of /home/chris/wine-0.9.58/usr/bin/wine into /usr/bin.
This time you do not need to do export wine=/home/chris/wine-0.9.58/usr/bin/wine.

Open terminal and try wine, make sure it works. And then tray again IEs4linux.

Doing as you pointed to, the wine command runs but it says "preloader: Warning: failed to reserve range ..."

This is the problem that you discuss in the first page of this thread. I solved it with Ubuntu 8.10 related instructions in the page linked to.

Now the installer runs.
Thanks...

Cristian Palmas

---

### Post by david_kt on 2009-04-06
> **cristian.palmas said:**
> Doing as you pointed to, the wine command runs but it says "preloader: Warning: failed to reserve range ..."

This is the problem that you discuss in the first page of this thread. I solved it with Ubuntu 8.10 related instructions in the page linked to.

Now the installer runs.
Thanks...

Cristian Palmas

I am glad it finally run. Remember to remove the symlink after that, and change the launcher from wine to /us/bin/wine-0.9.58 or whatever you have.

---

### Post by cristian.palmas on 2009-04-06
> **david_kt said:**
> I am glad it finally run. Remember to remove the symlink after that, and change the launcher from wine to /us/bin/wine-0.9.58 or whatever you have.

I'm a bit confused.
The launcher, for example, of ie6 is a shell script.
Do you mean that in the default application to open with I need to add wine-0.9.58?

By the way, I finally tried to install IEs4Linux under the 1.1.17 version and it worked only in the following way:

- I modified the kommander.sh under ui/kommander in order to strip all incorrect konsole options such as -T, --nomenubar, and so on. I let only --icon and -e options

- To avoid GTK installation bug I ran the program with --no-gui option.

- To make the installer finish the work, I had to create a symlink also for wineprefixcreate

---

### Post by cristian.palmas on 2009-04-06
> **cristian.palmas said:**
> I'm a bit confused.
The launcher, for example, of ie6 is a shell script.
Do you mean that in the default application to open with I need to add wine-0.9.58?

By the way, I finally tried to install IEs4Linux under the 1.1.17 version and it worked only in the following way:

- I modified the kommander.sh under ui/kommander in order to strip all incorrect konsole options such as -T, --nomenubar, and so on. I let only --icon and -e options

- To avoid GTK installation bug I ran the program with --no-gui option.

- To make the installer finish the work, I had to create a symlink also for wineprefixcreate

Well, perhaps I get it...
In every shell script launcher in /home/bin/chris there are lines to launch wine.

I'll try to modify them.

---

### Post by cristian.palmas on 2009-04-06
> **cristian.palmas said:**
> Well, perhaps I get it...
In every shell script launcher in /home/bin/chris there are lines to launch wine.

I'll try to modify them.

It works.
In the ie6 and ie55 script in ~/bin
I modified "wine" into "/home/chris/wine-1.1.17/usr/bin/wine".

---

### Post by david_kt on 2009-04-06
> **cristian.palmas said:**
> It works.
In the ie6 and ie55 script in ~/bin
I modified "wine" into "/home/chris/wine-1.1.17/usr/bin/wine".

Yes, that what I meant. Now you should remove the symlink in /usr/bin (wine and WINEPREFIXCREATE) if you want to use multiple wine.

DK

---

### Post by cristian.palmas on 2009-04-06
> **david_kt said:**
> Yes, that what I meant. Now you should remove the symlink in /usr/bin (wine and WINEPREFIXCREATE) if you want to use multiple wine.

DK

Already done.
I've just installed four versions and now I'm installing Safari, IE7 and IE8 on the basis of some post ago.

---

### Post by cristian.palmas on 2009-04-06
> **cristian.palmas said:**
> Already done.
I've just installed four versions and now I'm installing Safari, IE7 and IE8 on the basis of some post ago.

I installed Safari 3 on my Kubuntu 8.10.
I followed the steps below:
[LIST=1]
[*] From the command line:
```

# export WINEPREFIX=/home/chris/wine-bottles/Safari3

```
[*] Since I created various symlinks to the different versions of wine, I then typed, after have reached the .exe installer folder:
```

# wine-1.1.17 SafariSetup.exe
# /home/chris/wine-1.1.17/usr/bin/winecfg

```
... and set Safari
[*] From the command line, after have reached the executable to launch the browser:
```

# wine-1.1.17 Safari.exe

```
[/LIST]

Even if the installation went smooth, when I try to launch the browser, it doesn't run because there are a lot of errors about libraries not found.

Here is the (very long) output...

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library icuin36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library CoreFoundation.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\Safari.exe") not found                           
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library icuin36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library CoreFoundation.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CFNetwork.dll") not found                        
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\pthreadVC2.dll") not found                              
err:module:import_dll Library pthreadVC2.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CFNetwork.dll") not found                            
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\SQLite3.dll") not found                                 
err:module:import_dll Library SQLite3.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CFNetwork.dll") not found                               
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CFNetwork.dll") not found                               
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CFNetwork.dll") not found                               
err:module:import_dll Library CFNetwork.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\Safari.exe") not found                                
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library icuin36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library CoreFoundation.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                     
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\zlib1.dll") not found                                   
err:module:import_dll Library zlib1.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                              
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                            
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                            
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                            
err:module:import_dll Library CoreGraphics.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\Safari.exe") not found                             
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\WebKit.dll") not found                                  
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library icuin36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library CoreFoundation.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\WebKit.dll") not found                           
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library icuin36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library CoreFoundation.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CFNetwork.dll") not found                        
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\pthreadVC2.dll") not found                              
err:module:import_dll Library pthreadVC2.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CFNetwork.dll") not found                            
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\SQLite3.dll") not found                                 
err:module:import_dll Library SQLite3.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CFNetwork.dll") not found                               
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CFNetwork.dll") not found                               
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CFNetwork.dll") not found                               
err:module:import_dll Library CFNetwork.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\WebKit.dll") not found                                
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library icuin36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library CoreFoundation.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                     
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\zlib1.dll") not found                                   
err:module:import_dll Library zlib1.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                              
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                            
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                            
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                            
err:module:import_dll Library CoreGraphics.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\WebKit.dll") not found                             
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\WebKit.dll") not found                                  
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\WebKit.dll") not found                                  
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\libxml2.dll") not found                                 
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\libxml2.dll") not found                                 
err:module:import_dll Library libxml2.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\WebKit.dll") not found                                  
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library icuin36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\WebKit.dll") not found                                  
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\pthreadVC2.dll") not found                              
err:module:import_dll Library pthreadVC2.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\WebKit.dll") not found                               
err:module:import_dll Library WebKit.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\Safari.exe") not found                                   
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\libxml2.dll") not found                                 
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\libxml2.dll") not found                                 
err:module:import_dll Library libxml2.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\Safari.exe") not found                                  
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"   
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found                                 
err:module:import_dll Library icuin36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found                          
err:module:import_dll Library CoreFoundation.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                     
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\zlib1.dll") not found                                   
err:module:import_dll Library zlib1.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                              
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found                                 
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                            
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                            
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreGraphics.dll") not found                            
err:module:import_dll Library CoreGraphics.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\SafariTheme.dll") not found                        
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuin36.dll") not found
err:module:import_dll Library icuin36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\icuuc36.dll") not found
err:module:import_dll Library icuuc36.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\CoreFoundation.dll") not found
err:module:import_dll Library CoreFoundation.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\SafariTheme.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\SafariTheme.dll") not found
err:module:import_dll Library SafariTheme.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\Safari.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\Safari.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\Safari.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\chris\\wine-bottles\\Safari3\\drive_c\\Programmi\\Safari\\Safari.exe" failed, status c0000135

```

What did I miss? Or did I make something wrong?
All the libraries are in place (even if I didn't find yet the MSVCR80.dll)

---

### Post by cristian.palmas on 2009-04-06
I found the trick.

The browser started from the command line without any problem ONLY AFTER have specified the WINEPREFIX to the folder configuration.

```

# export WINEPREFIX=/home/chris/wine-bottles/Safari3
# wine-1.1.17 Safari.exe

```

I think that it's better to create a script to run it quickly. The link and the menu item don't work.

---

### Post by david_kt on 2009-04-06
> **cristian.palmas said:**
> I found the trick.

The browser started from the command line without any problem ONLY AFTER have specified the WINEPREFIX to the folder configuration.

```

# export WINEPREFIX=/home/chris/wine-bottles/Safari3
# wine-1.1.17 Safari.exe

```

I think that it's better to create a script to run it quickly. The link and the menu item don't work.

You have to edit the link in the menu item, replacing wine with wine-1.1.17:

1. open text editor
2. open file manager and navigate to /home/chris/.local/share/applications/wine/Programs/Safari/Safari
(check the actual path and name for safari)
3. drag and drop safari (actually it has extension .desktop) to text editor.
4. Replace wine with wine-1.1.17
5. save and close the file.
6. Try the menu again.

Or, just make a launcher with this command:
```
env WINEPREFIX="/home/chris/wine-bottles/Safari3" wine-1.1.17 "C:\Program Files\Safari\Safari.exe"

```

Please check the exact path for Safari.exe, I just guess it is in Safari folder.

You could also add from the menu to desktop, and then edit the launcher in the desktop.

Please choose which one you like from above method, all should work so that there is no need to create a script.

DK

---

### Post by cristian.palmas on 2009-04-09
> **david_kt said:**
> You have to edit the link in the menu item, replacing wine with wine-1.1.17:

1. open text editor
2. open file manager and navigate to /home/chris/.local/share/applications/wine/Programs/Safari/Safari
(check the actual path and name for safari)
3. drag and drop safari (actually it has extension .desktop) to text editor.
4. Replace wine with wine-1.1.17
5. save and close the file.
6. Try the menu again.

Or, just make a launcher with this command:
```
env WINEPREFIX="/home/chris/wine-bottles/Safari3" wine-1.1.17 "C:\Program Files\Safari\Safari.exe"

```

Please check the exact path for Safari.exe, I just guess it is in Safari folder.

You could also add from the menu to desktop, and then edit the launcher in the desktop.

Please choose which one you like from above method, all should work so that there is no need to create a script.

DK

Hi David,

thanks for the tips. I prefer the second choice, using "env" and the command for wine.
The problem is that wine throws "Unhandled page fault" for every version of wine I installed (1.1.10 - 1.1.11 - 1.1.14 - 1.1.17).
After a search I found that it can be due to wine version incompatibility with Safari 3.525.21.

It runs smoothly but when Safari search for the address typed in the address bar, it freezes and the terminal shows the page fault errors.

I installed the most recent version for Ubuntu 8.10, wine 1.1.18.
I will try it later...

By the way, I tried to install IE7 using the downloaded exe from Microsoft (well, it's not correct because the license says you must have a legal copy of Windows to use it...).
It gives me a lot of fixme and some minor errors. It installs, it runs, but no menu item is created and, when I type the address, it always says: "Impossible to reach the address ..." even if it is correct.

Do you know about installing IE7?
Well, I can give a shot to the IEs4Linux support for IE7...

---

### Post by david_kt on 2009-04-09
> **cristian.palmas said:**
> 
It runs smoothly but when Safari search for the address typed in the address bar, it freezes and the terminal shows the page fault errors.

Do you know about installing IE7?
Well, I can give a shot to the IEs4Linux support for IE7...

I have not tried Safari, but you could search in winehq:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8248](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8248)

As for IE7, IE4linux beta version support it:

[http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.99.0.1.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.99.0.1.tar.gz) 

Read the instruction here:
[http://www.tatanka.com.br/ies4linux/news/54](http://www.tatanka.com.br/ies4linux/news/54)

But it is beta release.

DK

---

### Post by cristian.palmas on 2009-04-09
> **david_kt said:**
> I have not tried Safari, but you could search in winehq:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8248](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8248)

As for IE7, IE4linux beta version support it:

[http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.99.0.1.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.99.0.1.tar.gz) 

Read the instruction here:
[http://www.tatanka.com.br/ies4linux/news/54](http://www.tatanka.com.br/ies4linux/news/54)

But it is beta release.

DK

Yes, I've already read about IE7 support by IEs4Linux, but it seems that it transform IE6 into IE7. Instead, for my web designs I need both IE6 and IE7.
Since the installation of IE6 and IE5.5 went well, I don't like to mess it up to test if IE7 is added or not.

I don't have enough time to do it.

As far as Safari is concerned, I've already installed it with 1.1.14 version but it didn't work. The tester says that version gave a "gold" result on Ubuntu 8.04 but I have Intrepid (8.10).
Maybe it matters...

---

### Post by NightMKoder on 2009-04-09
This is probably one of the most useful utilities to someone who doesn't want to deal with the terminal. I thought it might be more useful if it also had the ability to apply patches during compilation. (ie to get Fallout 3 to work). 

It is the same exact interface, just make sure you select patch and a wine version (just selecting patch doesn't do anything). You will then get file selection dialogs to pick your patch files. Keep picking patches until you're done, and then just press cancel. Then before compiling your selected version(s) of wine, the patches will be applied.

I haven't tested this very much, so feel free to comment. The diff to the original is also included.

---

### Post by david_kt on 2009-04-09
> **NightMKoder said:**
> This is probably one of the most useful utilities to someone who doesn't want to deal with the terminal. I thought it might be more useful if it also had the ability to apply patches during compilation. (ie to get Fallout 3 to work). .

That is great. That is exactly what I want to do with this script, but somehow I have forgotten (and do not know how to do it yet as well). I will study your script for my personal benefit. And I think a lot of people would love to use it as well, to have any version of wine compiled and patched automatically, have them as many as you want at the same time.

DK

---

### Post by aniruddha on 2009-10-28
I followed all the instructions in your first post to the letter and installed Wine 1.1.19. However, on attempting to run a program from the terminal (by using wine-1.1.19 program.exe) I get the following error:

wine client error:0: version mismatch 392/385.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

What am I missing? Any help? I'm running Ubuntu Jaunty 64bit. I also have wine 1.1.32 installed on my system. Many thanks for your great script, just hope I can get it to work.

---

### Post by david_kt on 2009-10-28
> **aniruddha said:**
> I followed all the instructions in your first post to the letter and installed Wine 1.1.19. However, on attempting to run a program from the terminal (by using wine-1.1.19 program.exe) I get the following error:

wine client error:0: version mismatch 392/385.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

What am I missing? Any help? I'm running Ubuntu Jaunty 64bit. I also have wine 1.1.32 installed on my system. Many thanks for your great script, just hope I can get it to work.

It is probably wine 1.1.32 left something in drive_c/windows/system32.

What you should do is to create a special wineprefix for wine 1.1.19, so as wine 1.1.32 will not disturb that directory. For example:

env WINEPREFIX="$HOME/.wine119" /path/to/wine119/wine setup.exe.

After that, replace wine in the launcher with /path/to/wine119/wine as well.

DK

---

### Post by JohnsShadow on 2009-12-06
hey downloaded your script tryed it out with some wine deb packages i downloaded 

it works great when installing from a deb package, not so much when installing form the directives

one problem when i go to select a program from the open with menu 

all the wine programs are called "wine"...and the wine executible is actually in usr<bin not bin 

and if you want to rename them you gotta change the permissions to the whole folder (which would have been nice if your script would rename the files on extraction )

i also had an idea about an ultimate wine installer (which would install every wine installation to a specific directory naming them appropriately ) in one handy and rather large deb package

FUN QUESTION: do all of the wine instalations save files to the same home/user/.wine/fake_c directatory? will installing new wine's erase old instalations ?

also how do i edit the prefrence for each wine install, well right now i notice that my wine is set as windows 2000 and ive had better experiance emulating as windows XP

---

### Post by JohnsShadow on 2009-12-07
man this is screwed up if you rename wine to wine-1.1.30 or whatever you will break wine-auto, and wine-wine-1.1.30 which are apparently link files

well ive been getting strange errors (that ive never goten before with wine)

and im trying to fix them

EDIT: so the file im spossed to link to (with the open with) is wine-wine-x.x.xx >_< dammit

and WHICH version of the fake c drive has it installed

---

### Post by david_kt on 2009-12-07
> **JohnsShadow said:**
> man this is screwed up if you rename wine to wine-1.1.30 or whatever you will break wine-auto, and wine-wine-1.1.30 which are apparently link files

well ive been getting strange errors (that ive never goten before with wine)

and im trying to fix them

EDIT: so the file im spossed to link to (with the open with) is wine-wine-x.x.xx >_< dammit

You are right. I have updated the script quite sometime ago but forgot to update the instruction.

DK
Edit: I thought I forgot to update the instruction. There is nothing to be updated in the instruction! Please let me know if you still have problem.

---

### Post by david_kt on 2009-12-07
> **JohnsShadow said:**
> 
it works great when installing from a deb package, not so much when installing form the directives

one problem when i go to select a program from the open with menu 

all the wine programs are called "wine"...and the wine executible is actually in usr<bin not bin 

Nope.
It is install in your user directory, not /usr/bin.
You have chance to rename your wine during installation. Well, it is actually not rename, but make a link.

So, you could point it to the link to run the program, to differentiate among many wine version you install.

If you choose to install in different directory, offcourse the old wine will still be there.

DK

---

### Post by JohnsShadow on 2009-12-07
im talking about wine-x.x.xx/usr/bin/wine

im not talking about /usr/bin

and i am haveing a problem a serious problem

im trying to play morrowind (which i have played on wine before)

and im getting errors ive never gotten before

and i want to tell wine to emulate windows xp not 2000

im also haveing a terrible time running no/cd cracks

and i cant edit the .esm dependancies (required for in game moding)

antho i have no idea how you could help with that

---

### Post by david_kt on 2009-12-07
> **JohnsShadow said:**
> im talking about wine-x.x.xx/usr/bin/wine

im not talking about /usr/bin

and i am haveing a problem a serious problem

im trying to play morrowind (which i have played on wine before)

and im getting errors ive never gotten before

and i want to tell wine to emulate windows xp not 2000

im also haveing a terrible time running no/cd cracks

and i cant edit the .esm dependancies (required for in game moding)

antho i have no idea how you could help with that

It is easy. Restart your computer, and do sudo apt-get install wine.

You should be able to use your wine as usual.

DK

---

### Post by JohnsShadow on 2009-12-07
> **david_kt said:**
> It is easy. Restart your computer, and do sudo apt-get install wine.

You should be able to use your wine as usual.

DK

but then all the work ive done for the last 2 days is useless (am i wrong?)

will installing the regular wine screw up compadibility with all the wine's ive installed

can i install new fake wine anfter installing real wine?

---

### Post by david_kt on 2009-12-07
> **JohnsShadow said:**
> but then all the work ive done for the last 2 days is useless (am i wrong?)

will installing the regular wine screw up compadibility with all the wine's ive installed

can i install new fake wine anfter installing real wine?

You still could use the "fake wine" with real wine installed, just need to restart your computer.

Or, instead of restart, you could try below command if you want to switch to different wine version:
```
killall wine
killall wineserver
killall wine-preloader

```

DK

---

### Post by JohnsShadow on 2009-12-07
do you remember the wine configuration wizzard by chance do you remember which file is home to that program?

---

### Post by david_kt on 2009-12-07
> **JohnsShadow said:**
> do you remember the wine configuration wizzard by chance do you remember which file is home to that program?
I don't really understand your question. May be what you mean is wineprefix. Wine configuration is specific to wineprerix.

DK

---

### Post by JohnsShadow on 2009-12-09
i hate to say this but these fake wines fail every game i play i can only get 10-15 minnuites into and the game will crash (and ive tryed every wine version EVER)

dude A for effort but it just isnt working

stuff for a future release
maybe wine has problems because the version of fake wine and the version of the cdrive differ?

well i dont know but somthing major is missing somthing that causes sersious problems

update me when you update your script and i will test it again

if i was better at code i would help but im an artist not a programer

---

### Post by david_kt on 2009-12-09
> **JohnsShadow said:**
> i hate to say this but these fake wines fail every game i play i can only get 10-15 minnuites into and the game will crash (and ive tryed every wine version EVER)

dude A for effort but it just isnt working

stuff for a future release
maybe wine has problems because the version of fake wine and the version of the cdrive differ?

well i dont know but somthing major is missing somthing that causes sersious problems

I doubt it is due to fake wine. To confirm, you could try to install the real wine and see if it could run better.

DK

---

### Post by JohnsShadow on 2009-12-10
actually i did you one better

i installed real wine from deb version 1.1.27 which is the wineDB susgested version for morrowind+expansions im also useing the same version of fake wine so i can help debug 

fake wine: likes to hang at the title screen and crash when loading my save game, will crash when i die, and will not let me axcess the data files (the ingame mod enable/ disable utility) or change them
real wine: has no issues with title screen takes longer to load my save game but hasent crashed, no issues with mods

the only bug i can find that is in both versions is when i go into the fight sequence the game will lag a bit (which has been like that for several versions of wine)

remember when i asked you about the wine configuration?
i found the file in fake wine but it gives me an error saying there is a lack of wine.cfg (which there is one but its not in the same directory)

if there is any mor info i can give i will be happy

ohh i can even link you to the torrent file i downloaded morrowind from
(i actually installed the game from my own copy i simply downloaded a backup so i could mount the iso so i wouldnt need a disk in the drive to play) test it to see the errors for your self

---

### Post by layr on 2011-08-31
I must be doing something wrong.
_First of all - linking doesn't work:_
**1.** Ran the script, installed .deb into home/user/wine-1.3.27
**2.** sudo ln -s /home/user/wine-1.3.27/usr/local/bin/wine /usr/bin/wine-1.3.27
**3.** Tried to execute installer: wine-1.3.27 '/home/user/Downloads/Setup.exe'

Terminal output: */home/laur/wine-1.3.27/usr/local/bin/wine-1.3.27: could not open*

It seems as if the link is incorrect; but it isn't?!

_Secondly, your recommended prefix creating way_
mkdir /home/username/.wine_whatever
	env WINEPREFIX="/home/username/.wine_whatever wine-version your_program.exe
ends up in terminal output: *>*  (nothing happens, no errors either)

---

### Post by david_kt on 2011-08-31
> **layr said:**
> I must be doing something wrong.
_First of all - linking doesn't work:_
**1.** Ran the script, installed .deb into home/user/wine-1.3.27
**2.** sudo ln -s /home/user/wine-1.3.27/usr/local/bin/wine /usr/bin/wine-1.3.27
**3.** Tried to execute installer: wine-1.3.27 '/home/user/Downloads/Setup.exe'

Terminal output: */home/laur/wine-1.3.27/usr/local/bin/wine-1.3.27: could not open*

It seems as if the link is incorrect; but it isn't?!

_Secondly, your recommended prefix creating way_
mkdir /home/username/.wine_whatever
	env WINEPREFIX="/home/username/.wine_whatever wine-version your_program.exe
ends up in terminal output: *>*  (nothing happens, no errors either)


1. Check the file is exist (looks like wrong location, should be'/home/user/wine-1.3.27/bin/wine-1.3.27' instead of /home/user/wine-1.3.27/usr/local/bin/wine /usr/bin/wine-1.3.27)
Please follow the steps properly if you are not sure what you are doing.

2. If wine location is wrong, the second one would not work as well.

DK

---

### Post by layr on 2011-08-31
> **david_kt said:**
> 1. Check the file is exist (looks like wrong location, should be'/home/user/wine-1.3.27/bin/wine-1.3.27' instead of /home/user/wine-1.3.27/usr/local/bin/wine /usr/bin/wine-1.3.27)
Please follow the steps properly if you are not sure what you are doing.

2. If wine location is wrong, the second one would not work as well.

DK
Wow at the response speed:D
I noticed the difference in the paths, but neither of the wine installations had the bin directory in the root (root as in wine-x.x.x) folder. Root had just usr, which again contained local and share.

---

### Post by david_kt on 2011-08-31
> **layr said:**
> Wow at the response speed:D
I noticed the difference in the paths, but neither of the wine installations had the bin directory in the root (root as in wine-x.x.x) folder. Root had just usr, which again contained local and share.

Did you find the executable wine (usr/local/bin/wine for example)?

DK

---

### Post by layr on 2011-08-31
> **david_kt said:**
> Did you find the executable wine (usr/local/bin/wine for example)?

DK
Yes, i linked that to usr/bin/wine-1.2.3 as shown in my first post.

---

### Post by david_kt on 2011-08-31
> **layr said:**
> Yes, i linked that to usr/bin/wine-1.2.3 as shown in my first post.

Is the executable:

/home/user/wine-1.3.27/usr/local/bin/wine

or

/home/user/wine-1.3.27/usr/local/bin/wine-1.3.27

Try to run that file first before calling from the link.

DK

---

### Post by layr on 2011-09-01
> **david_kt said:**
> Is the executable:

/home/user/wine-1.3.27/usr/local/bin/wine

or

/home/user/wine-1.3.27/usr/local/bin/wine-1.3.27

Try to run that file first before calling from the link.

DK

exe file (which installed) is 
/home/user/wine-1.3.27/usr/local/bin/wine

If i created a link into usr/bin as 'wine' instead of 'wine-1.3.27', it worked fine.

---

### Post by kuboode on 2012-01-15
Hi friend; great project; I need you help; I work an project called "ares linux".  the new versions of wine has killed ares linux, because modified and erased drivers as esd, os. I  need to run some wine versions as 1.3.20 or 1.3.24; but my knowledge is low :( you would see the my beta script here: [http://sourceforge.net/projects/areslinux/](http://sourceforge.net/projects/areslinux/) ) it only work in the current version wine, sorry my english es bad :(

---

