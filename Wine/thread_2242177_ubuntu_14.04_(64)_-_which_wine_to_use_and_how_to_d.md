---
title: "ubuntu 14.04 (64) - which wine to use and how to do it + sanity check"
date: 2014-08-31
forum: Wine
---

### Post by xigen on 2014-08-31
I have a copy of MicroSoft Office 2007  home/student and I would like to run it under wine on my Ubuntu 14.04 64 bit system.
** Yes.. I need MS Office because my documents must preserve formatting/fonts/etc.  etc etc. 

Wine is installed via Netflix player

```
meow@MeowBatunde:/usr/share/fonts/truetype/wps$ lsb_release -a; uname -a; dpkg -l | grep -i wine
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty
Linux MeowBatunde 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
ii  netflix-desktop                                       0.8.8~ubuntu14.04.1                                 all          Netflix Desktop provides a convient tool that downloads and installs all of the components necessary to run Netflix under Wine.
ii  pipelight-multi                                       0.2.7.1~ubuntu14.04.1                               amd64        allows usage of Windows NPAPI plugins through Wine
ii  wine-browser-installer                                0.8.8~ubuntu14.04.1                                 all          The Wine Browser Installer provides a tool for multiple packages to provide access to web services that can be run with Mozilla Firefox under Wine.
ii  wine-compholio                                        1.7.24~ubuntu14.04.1                                amd64        The Compholio Edition is a special build of the popular Wine software
ii  wine-compholio-amd64                                  1.7.24~ubuntu14.04.1                                amd64        The Compholio Edition is a special build of the popular Wine software
ii  wine-compholio-i386                                   1.7.24~ubuntu14.04.1                                i386         The Compholio Edition is a special build of the popular Wine software
ii  wine-silverlight5.1-installer                         0.8.8~ubuntu14.04.1                                 all          wine-silverlight5.1-installer provides a convient tool that downloads and installs all of the components necessary to run Silverlight 5.1 under Wine.
meow@MeowBatunde:/usr/share/fonts/truetype/wps$ 
```

I have Ia32 libraries installed:
```
  173  sudo dpkg --add-architecture i386 && sudo apt-get update
  174  sudo apt-get install ia32-libs
  175  sudo -i
  176  cd Downloads/
  177  ls
  178  sudo dpkg -i wps-office_9.1.0.4751~a15_i386.deb 
  179  cd && wget -O kingsoft-office-NoobsLab.deb http://goo.gl/HplIfc
  180  sudo apt-get -y install libc6:i386 libgcc1:i386 gcc-4.6-base:i386 libstdc++6:i386 libx11-6:i386 libglib2.0-0:i386 libfreetype6:i386 libSM6:i386 libXrender1:i386 libfontconfig1:i386 libXext6:i386 libcups2:i386 p11-kit:i386 libcap-ng0:i386 gnome-keyring:i386 libglu1-mesa:i386
```

Here is a website with instructions.  However, I believe the author presumes that I am running a 32 bit install of Ubuntu.

[HTML]http://www.webupd8.org/2011/01/how-to-install-microsoft-office-2007-in.html[/HTML]

Ubuntu 14.04 + office 2007 + wine => am I asking for trouble?
Which wine do I use? 1.3 or the one with Netflix player?
Would one wine (1.3) conflict with (1.7- netflix)?

How would you suggest that I proceede?

---

### Post by adec2 on 2014-08-31
Deleted

---

### Post by adec2 on 2014-08-31
If you are worried about conflicts with wine versions try to use playonlinux that will use a specified wine without conflicting with your existing installation.
For example i run certain programs using the latest wine (1.7.25 as of today) but use playonlinux to play older games that work with older wine versions without needing to mess up winetricks all the time
As for your link you could easily install wine 1.3 into playonlinux and tweak it without affecting your main installation

---

### Post by xigen on 2014-08-31
OK.

I got wine 1.6 running

1) install wine 1.6 (synaptic)
2) take office2007 cd -> put in cd drive --> click on "install.exe" ... and install with wine (1.6)
3) It works ... ish ...   
-- no .docx support
-- needs service packs installed.

Solved for now and I will ask additional questions in a new thread.

---

### Post by mastablasta on 2014-09-01
I installed it using play on Linux. docx support works just fine. the only thing that doesn't work is those graphs images - they can crash it if I remember correctly.

to preserve formatting on all PC it is best to use PDF. it will work no matter what office the person looking it is using.

---

