---
title: "Unable to install Wine on Ubuntu 12.04 x64"
date: 2012-10-22
forum: Wine
---

### Post by Noah_Danwell on 2012-10-22
Hello.

I installed Ubuntu 12.04, after installed some soft from Ubuntu Software Center, apt-get and aptitude (i'm choosing what is better, apt-get or aptitude so using them both).

All was fine, but only Flash didn't want to install due broken dependencies. I've used Aptitude Solver and installed flash with downgrade 2 package versions (name of packages don't remember).

Then i tried to install Wine. But faced a unsolvable dependencies problem.

With [COLOR=Blue]**PPA Wine**[/COLOR] version:
> $ sudo aptitude show wine
Package: wine                            
State: not installed
Multi-Arch: foreign
Version: 1.5.15-0ubuntu1
Priority: extra
Section: otherosfs
Maintainer: Scott Ritchie <[EMAIL="scottritchie@ubuntu.com"]scottritchie@ubuntu.com[/EMAIL]>
Architecture: amd64
Uncompressed Size: 21.5 k
Depends: wine1.5
Conflicts: wine
Provides: wine
Provided by: wine, wine1.4, wine1.5
Description: Microsoft Windows Compatibility Layer (meta-package)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine does
 not require Microsoft Windows, however it can use native system dll files in
 place of its own if they are available. 
 
 This meta-package always depends on the default version of Wine.
> $ **sudo apt-get install wine**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ***wine : Depends: wine1.5 but it is not going to be installed***
E: Unable to correct problems, you have held broken packages.
**sudo aptitude install wine**:
[http://pastebin.com/bYNKe3HS](http://pastebin.com/bYNKe3HS)
=====================================================
**[COLOR=Blue]Wine [/COLOR]**from **[COLOR=Blue]standart repos [/COLOR]**gave me output:
> $ sudo aptitude show wine
Package: wine                            
State: not installed
Multi-Arch: foreign
Version: 1.4-0ubuntu4
Priority: extra
Section: universe/otherosfs
Maintainer: Scott Ritchie <[EMAIL="scottritchie@ubuntu.com"]scottritchie@ubuntu.com[/EMAIL]>
Architecture: amd64
Uncompressed Size: 21.5 k
Depends: wine1.4
Conflicts: wine
Provides: wine
Provided by: wine, wine1.4
Description: Microsoft Windows Compatibility Layer (meta-package)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine does
 not require Microsoft Windows, however it can use native system dll files in
 place of its own if they are available. 
 
 This meta-package always depends on the default version of Wine.
Homepage: [http://www.winehq.org/](http://www.winehq.org/)
> $ **sudo apt-get install wine**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ***wine : Depends: wine1.4 but it is not going to be installed***
E: Unable to correct problems, you have held broken packages.[B]
sudo aptitude install wine[/B]:
[http://pastebin.com/ezg8v6Ea](http://pastebin.com/ezg8v6Ea)

My system:
> $ uname -a
Linux blc 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Help me please.

---

### Post by lite1979 on 2012-10-22
It would appear that you have either multiple wine installs conflicting with one another, or traces of old wine installs making it impossible to install a new version of wine.

Please give us the output of the following commands:

which wine
whereis wine
wine --version

If it helps you at all, I'm on 12.04 64-bit, and I've been successful using "sudo apt-get install wine1.5" but before I was able to do this, I had to remove some older versions that I had on my system, including wine 1.3 and wine 1.4. I hope this helps. I'll check back tomorrow.

---

### Post by Noah_Danwell on 2012-10-23
I have no wine installed.

---

### Post by lite1979 on 2012-10-23
Try 'sudo apt-get install wine1.5' and give us the output of that.

---

### Post by Noah_Danwell on 2012-10-24
The same. I tried 1.5, 1.4 or even 1.3 - errors are everywhere.
> $ sudo apt-get install wine1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.15-0ubuntu1)
E: Unable to correct problems, you have held broken packages.


---

### Post by lite1979 on 2012-10-26
Ok. Just to be safe, though, could you give us the output of the three commands I asked you about in my first post? 

which wine
whereis wine
wine --version

Next, I would type "sudo apt-get --purge remove wine" to make sure the files that may have been installed in your last attempt get removed.

Now, try "sudo apt-get build-dep wine"

Tell us which wine it prepares for.

---

### Post by Noah_Danwell on 2012-10-26
> **$ which wine**
**$ whereis wine**
wine:
**$ wine --version**
No command 'wine' found, did you mean:
 Command 'wipe' from package 'wipe' (universe)
 Command 'win' from package 'wily' (universe)
 Command 'wing' from package 'wing' (universe)
 Command 'xine' from package 'xine-ui' (universe)
wine: command not found

> **$ sudo apt-get --purge remove wine**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

> **$** **sudo apt-get build-dep wine**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'wine1.5' as source package instead of 'wine'
The following packages have unmet dependencies:
 libcups2-dev : Depends: libcups2 (= 1.5.3-0ubuntu1) but 1.5.3-0ubuntu4 is to be installed
                Depends: libkrb5-dev but it is not going to be installed
 libdbus-1-dev : Depends: libdbus-1-3 (= 1.4.18-1ubuntu1) but 1.4.18-1ubuntu1.3 is to be installed
 libfontconfig1-dev : Depends: libfontconfig1 (= 2.8.0-3ubuntu9) but 2.8.0-3ubuntu9.1 is to be installed
                      Depends: libexpat1-dev but it is not going to be installed
 libgl1-mesa-dev : Depends: libgl1-mesa-glx (= 8.0.2-0ubuntu3.1) but 8.0.3+8.0.2-0ubuntu3.2 is to be installed
 libglu1-mesa-dev : Depends: libglu1-mesa (= 8.0.2-0ubuntu3.1) but 8.0.3+8.0.2-0ubuntu3.2 is to be installed
 libgphoto2-2-dev : Depends: libgphoto2-2 (= 2.4.13-1ubuntu1) but 2.4.13-1ubuntu1.2 is to be installed
                    Depends: libexif-dev but it is not going to be installed
 libjpeg-dev : Depends: libjpeg8-dev but it is not going to be installed
 libldap2-dev : Depends: libldap-2.4-2 (= 2.4.28-1.1ubuntu4) but 2.4.28-1.1ubuntu4.1 is to be installed
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.2) but 1.0.1-4ubuntu5.5 is to be installed
 libxml2-dev : Depends: libxml2 (= 2.7.8.dfsg-5.1ubuntu4.1) but 2.7.8.dfsg-5.1ubuntu4.2 is to be installed
 libxslt1-dev : Depends: libxslt1.1 (= 1.1.26-8ubuntu1) but 1.1.26-8ubuntu1.2 is to be installed
E: Build-dependencies for wine could not be satisfied.:(

---

### Post by KenSharp on 2012-10-27
Have you done an **apt-get update** recently?

Try removing the ppa and re-adding it with **add-apt-repository ppa:ubuntu-wine/ppa**, run **apt-get update** again and see if that helps.

Also, what does your sources.list look like?

---

### Post by Noah_Danwell on 2012-10-27
> **KenSharp said:**
> Have you done an **apt-get update** recently?
Yes.

> **KenSharp said:**
> Try removing the ppa and re-adding it with **add-apt-repository ppa:ubuntu-wine/ppa**, run **apt-get update** again and see if that helps.
The problem still happens. With PPA output is the same like i gave above.

*Without Wine PPA repo:*
> **$ sudo apt-get install wine**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.> **$ sudo apt-get build-dep wine**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'wine1.4' as source package instead of 'wine'
The following packages have unmet dependencies:
 libcups2-dev : Depends: libcups2 (= 1.5.3-0ubuntu1) but 1.5.3-0ubuntu4 is to be installed
                Depends: libkrb5-dev but it is not going to be installed
 libdbus-1-dev : Depends: libdbus-1-3 (= 1.4.18-1ubuntu1) but 1.4.18-1ubuntu1.3 is to be installed
 libfontconfig1-dev : Depends: libfontconfig1 (= 2.8.0-3ubuntu9) but 2.8.0-3ubuntu9.1 is to be installed
                      Depends: libexpat1-dev but it is not going to be installed
 libgl1-mesa-dev : Depends: libgl1-mesa-glx (= 8.0.2-0ubuntu3.1) but 8.0.3+8.0.2-0ubuntu3.2 is to be installed
 libglu1-mesa-dev : Depends: libglu1-mesa (= 8.0.2-0ubuntu3.1) but 8.0.3+8.0.2-0ubuntu3.2 is to be installed
 libgphoto2-2-dev : Depends: libgphoto2-2 (= 2.4.13-1ubuntu1) but 2.4.13-1ubuntu1.2 is to be installed
                    Depends: libexif-dev but it is not going to be installed
 libjpeg-dev : Depends: libjpeg8-dev but it is not going to be installed
 libldap2-dev : Depends: libldap-2.4-2 (= 2.4.28-1.1ubuntu4) but 2.4.28-1.1ubuntu4.1 is to be installed
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.2) but 1.0.1-4ubuntu5.5 is to be installed
 libxml2-dev : Depends: libxml2 (= 2.7.8.dfsg-5.1ubuntu4.1) but 2.7.8.dfsg-5.1ubuntu4.2 is to be installed
 libxslt1-dev : Depends: libxslt1.1 (= 1.1.26-8ubuntu1) but 1.1.26-8ubuntu1.2 is to be installed
E: Build-dependencies for wine could not be satisfied.> **KenSharp said:**
> Also, what does your sources.list look like?
> # 

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120822.4)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120822.4)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120822.4)]/ precise main restricted

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120822.4)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120822.4)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120822.4)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise main restricted
deb-src [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-updates main restricted
deb-src [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise universe
deb-src [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise universe
deb [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-updates universe
deb-src [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise multiverse
deb-src [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise multiverse
deb [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-updates multiverse
deb-src [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-backports main restricted universe multiverse

deb [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-security main restricted
deb-src [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-security main restricted
deb [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-security universe
deb-src [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-security universe
deb [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-security multiverse
deb-src [http://mirror.corbina.net/ubuntu/](http://mirror.corbina.net/ubuntu/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

# good Java repo
deb [http://www.duinsoft.nl/pkg](http://www.duinsoft.nl/pkg) debs allLast item - "Java repo" doesn't influence, the problem appeared before i added it.

---

### Post by Noah_Danwell on 2012-10-28
It turned out the repository, to which I was attached, has not been updated for several weeks.

I've switched to another and many updates came to me.

Now [aptitude]("http://pastebin.com/pcxhwamb") offers to install both 32- and 64- versions of his dependencies. 
He can not resolve gettext and reports about some "internal errors". It is problem for me?

[apt-get ]("http://pastebin.com/VkHrS28T")feels better himself. Should i accept its offer?

---

### Post by lite1979 on 2012-10-30
You mean should you go ahead and install it? Yes. You can always uninstall it if it doesn't work.

---

### Post by Noah_Danwell on 2012-10-31
It seems wine installed with apt-get is working :)

---

### Post by nabeel2 on 2013-09-22
when I try to install wine, it is giving me below error. plz help me how can I fix this...

[COLOR=#333333][FONT=lucida grande]The following packages have unmet dependencies:wine1.4: PreDepends: dpkg (>= [/FONT][/COLOR][1.15.7.2]("http://1.15.7.2/")[COLOR=#333333][FONT=lucida grande]~) but [/FONT][/COLOR][1.16.1.2]("http://1.16.1.2/")[COLOR=#333333][FONT=lucida grande]ubuntu7.1 is to be installed         Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.4 is to be installed         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1~precise1~ppa4) but 1.4.1-0ubuntu1~precise1~ppa4 is to be installed         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa4) but it is a virtual package

Thank you[/FONT][/COLOR]

---

