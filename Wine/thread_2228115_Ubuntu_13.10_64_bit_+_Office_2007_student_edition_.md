---
title: "Ubuntu 13.10 64 bit + Office 2007 student edition 32 bit ==&gt;trouble"
date: 2014-06-05
forum: Wine
---

### Post by xigen on 2014-06-05
Ubuntu 13.10 64 bit 
Office 2007 student edition 32 bit 

I upgraded my hardware and installed the 64 bit verion of Ubuntu 13.10.    Now I am having a very difficult time re-installing 0ffice 2007.

1) Play on Linux
Office 2007 installs and crashes when I try to use Word.
I tried to change the version of wine (1.2.3 -> 1.4)  on both the 64 bit version and 32 bit version.   Word still crashes.

2) Install via Wine
First I removed all previous versions of Wine
I installed wine 1.4
I installed Office 2007   

Office 2007 crashes when I try to run it.

3) 32bit vs. 64 bit wine.  

I tried to make wine run in 32bit mode. 
WINEARCH=win32 WINEPREFIX=~/win32 winecfg 

Office 2007 still crashes upon launch.


Has anyone successfully installed office 2007 under 64bit Ubuntu?  How did you do it?

---

### Post by gdesilva on 2014-06-05
I installed Office 2007 Pro on my Ubuntu Studio 64 bit via Winetricks and so far haven't come across any issues - certainly can create docs, ppt etc. Worth trying to re-install using Winetricks and see how you go.

---

### Post by xigen on 2014-06-06
32 bit vs 64 bit wine prefix issues remain.

meow@meow:~$ locate wineprefix
/home/meow/.PlayOnLinux/wineprefix
/home/meow/.PlayOnLinux/wineprefix/default
meow@meow:~$ WINEARCH=win32 WINEPREFIX=/home/meow/.PlayOnLinux/wineprefix winecfg 
wine: WINEARCH set to win32 but '/home/meow/.PlayOnLinux/wineprefix' is a 64-bit installation.
meow@meow:~$ 

[http://wiki.winehq.org/FAQ#head-8d9263369d4c6d93a7cbacf2415377778c679d32](http://wiki.winehq.org/FAQ#head-8d9263369d4c6d93a7cbacf2415377778c679d32)
7.2. How do I create a 32 bit wineprefix on a 64 bit system?
At present there are some significant bugs that prevent many 32 bit applications from working in a 64 bit wineprefix. To work around this, you can create a new 32 bit wineprefix using the WINEARCH environment variable. In a terminal, type:
WINEARCH=win32 WINEPREFIX=/path/to/wineprefix winecfg 
(use the actual path to the wineprefix), then install your 32 bit application(s) to that wineprefix.
Do not manually create the directory before running that command; Wine must create it. WINEARCH only needs to be set when creating the wineprefix, and the architecture of an existing wineprefix cannot be changed. 


[http://appdb.winehq.org/appview.php?iVersionId=4992](http://appdb.winehq.org/appview.php?iVersionId=4992)
Known issues with wine 1.4 and below 
Known Regressions
(Updated 2012-03-19)
The Wine versions below are known to have regressions that affect the Office 2007 installer. Do not try to install in them:
    1.4-rc1: SP2 & SP3 do not install correctly
    1.3.30
    1.3.21: SP2 does not install correctly
    1.3.16-1.3.17
    1.3.7***
    1.3.2
    1.2.0 and 1.2.1 (Ubuntu and other distro packages compiled with fortify)
    1.1.17 throug*h 1.1.23
    **all versions prior to 1.1.3 *(i*ncludes 1.0.1)

 	
 
HOWTO

*****(Updated 2014-2-12)

*Note: these instructions have been tested and verified to work on the Enterprise, Pro, and Home & Student editions of Office 2007, installing from a cd.

Use the most recent version of Wine known to work for Office 2007 (see list of known bad versions above). In most cases this will be the latest development release. 

Make sure all dependencies of Wine are installed on your system, including winbind. 

Install to a clean wineprefix (no winetricks or other tweaks, no other applications installed), and make sure the Windows version in winecfg is set to XP.

Note: I*f you have 64 bit Wine inst*alled, you must create a 32 bit wineprefix and install Office 2007 to it or the installed programs will not be usable.

Follow the instructions in [http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ) for creating a 32 bit wineprefix, running an installer, and using wineprefixes.

If you are going to install any service packs, install them before setting the override below.

After installing:

    Set riched20 to native, builtin in winecfg to enable Powerpoint to start and selection boxes to display correctly. 
        Do not use winetricks; Office installs its own riched20 to a private directory.
        This override may be set globally if Office is installed to a separate wineprefix (recommended).
        If other applications are installed to the wineprefix (strongly discouraged), either set the override individually for each Office application, or set riched20 to builtin individually for the non-Office applications, as non-Office applications will not be able to find the riched20 installed by Office.

    (Optional) If you want bullets to look the same as they do on Windows, install wingdings.ttf.  Most of the default bullet characters are from this font; if it is not installed on your system, Wine will substitute characters from a font that is installed on your system. (They will work, but will not look the same.)

Guidelines for Submitting Test Reports

    Test in a clean wineprefix, using plain Wine. 
    Specify exactly which edition of Office 2007 you tested (Standard, Pro, etc.). This is crucial--bugs that affect one edition may not affect others.
    Specify exactly what type of install you tested (Typical, Custom, Minimal, etc.)
    Limit your report to the installer only. Reports on the performance of individual apps should be filed under their respective AppDB entries. Problems with running any of the apps should only be mentioned if it is clear that it is due to a problem with the installer.
    If you used any overrides during the install, please list them and explain exactly what problem each override was needed to solve.
    Test reports that do not follow these guidelines will be rejected.

---

### Post by QIII on 2014-06-06
*Moved to **Wine**.*

---

### Post by xigen on 2014-06-07
I have installed wine1.7   due to 32bit v 64 bit issues with wine prior to 1.4
I also upgraded to 14.04.  13.10 had issues with audio and scratchy sounds.

Sooooo....   **How do I install 32bit office 2007 on 64 bit Ubuntu 14.04 using wine 1.7?**

---

### Post by xigen on 2014-06-07
1) install wine 1.7
2) install word under wine 1.7 by inserting the office 2007 student edition disk in my CD drive and navigating to the install.exe
3) Go to menu - all applications -- and click on Word.

Word worked, it prints, and so far so good.

---

