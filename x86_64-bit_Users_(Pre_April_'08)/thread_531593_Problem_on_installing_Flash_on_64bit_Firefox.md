---
title: "Problem on installing Flash on 64bit Firefox"
date: 2007-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by satimis on 2007-08-21
Hi folks,


Ubuntu 7.04 lamp server amd64
Firefox version 2.0.0.6


$ apt-cache policy firefox```

firefox:
  Installed: 2.0.0.6+1-0ubuntu1
  Candidate: 2.0.0.6+1-0ubuntu1
  Version table:
 *** 2.0.0.6+1-0ubuntu1 0
        500 http://security.ubuntu.com feisty-security/main Packages
        100 /var/lib/dpkg/status
     2.0.0.3+1-0ubuntu2 0
        500 http://hk.archive.ubuntu.com feisty/main Packages

```
I suppose this is a 64bit version???


I followed;
6.2 Flash Plugin of following URL:-
[http://www.my-guides.net/en/content/view/26/26/](http://www.my-guides.net/en/content/view/26/26/)

to install Flash.  But I can proceed to install;
nspluginwrapper-0.9.91.4-1.x86_64.rpm
nspluginwrapper-i386-0.9.91.3-1.x86_64.rpm

They are RedHat packages.

However the tarball download on following site;
[http://gwenole.beauchesne.info/en/projects/nspluginwrapper](http://gwenole.beauchesne.info/en/projects/nspluginwrapper)

nspluginwrapper-0.9.91.4.tar.bz2
having no indication of 64bit or 32bit and I can't find the viewer tarball.

Having tried installing "nspluginwrapper-0.9.91.4.tar.bz2" after decompressing it.  But it complained on running "./configure" -```

pre pkg-config not found

```


I further found following thread;
Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64 
[http://ubuntuforums.org/showthread.php?t=202537&highlight=install+flash+64+bit](http://ubuntuforums.org/showthread.php?t=202537&highlight=install+flash+64+bit)

but the steps not so simple as the previous URL

Any advise how to install rpm package on Ubuntu.  TIA



B.R.
satimis

---

### Post by je1117 on 2007-08-22
Just follow the steps carefully on this [page]("http://ubuntuforums.org/showthread.php?t=341727").

Alternative n.1 worked for me. 



Using 32-bit Firefox is lame. I don't know why people use it on their 64-bit machines when there's a perfectly simple alternative.

---

### Post by Kilz on 2007-08-22
> **je1117 said:**
> Just follow the steps carefully on this [page]("http://ubuntuforums.org/showthread.php?t=341727").

Alternative n.1 worked for me. 



Using 32-bit Firefox is lame. I don't know why people use it on their 64-bit machines when there's a perfectly simple alternative.

The reason is that some people need more than Flash. Nspluginwrapper only works with flash. If you need a safe java, the acrobat reader, or other plugins a 32bit Firefox is your best bet. Since Firefox is not optimized to a 64bit processor, you dont lose any performance. What the original poster missed on the page he linked to was the automated setup script that makes short work of installing it.

That said, if you are going to install nspluginwrapper because all you need is flash. [Why not do it the easy way. 10 seconds and its installed.]("http://ubuntuforums.org/showthread.php?t=476924")

---

### Post by satimis on 2007-08-22
Hi folks,


I have Flash installed.


Steps performed as follows;


1)
On
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
Download "install_flash_player_9_linux.tar.gz"

On
[http://gwenole.beauchesne.info/projects/nspluginwrapper/](http://gwenole.beauchesne.info/projects/nspluginwrapper/)
Download;
nspluginwrapper-i386-0.9.91.3-1.x86_64.rpm   
nspluginwrapper-0.9.91.4-1.x86_64.rpm

All 64bit version.


2)
$ sudo apt-get install alien linux32```

....
Setting up html2text (1.3.2a-3) ...
Setting up gettext (0.16.1-1ubuntu2) ...
Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.8) ...
Setting up debhelper (5.0.42ubuntu1) ...
Setting up libbeecrypt6 (4.1.2-6build1) ...
Setting up libneon25 (0.25.5.dfsg-6build1) ...
Setting up librpm4 (4.4.1-14build1) ...
Setting up rpm (4.4.1-14build1) ...
Setting up alien (8.65) ...
Setting up linux32 (1-3) ...

```


$ sudo alien -d nspluginwrapper-0.9.91.4-1.x86_64.rpm```
 
Warning: Skipping conversion of scripts in package nspluginwrapper: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
nspluginwrapper_0.9.91.4-2_amd64.deb generated

```

$ sudo alien -d nspluginwrapper-i386-0.9.91.3-1.x86_64.rpm```
 
nspluginwrapper-i386_0.9.91.3-2_amd64.deb generated

```

$ sudo dpkg -i nspluginwrapper*.deb```

Selecting previously deselected package nspluginwrapper.
(Reading database ... 43497 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.4-2_amd64.deb) ...
Selecting previously deselected package nspluginwrapper-i386.
Unpacking nspluginwrapper-i386 (from nspluginwrapper-i386_0.9.91.3-2_amd64.deb) ...
Setting up nspluginwrapper (0.9.91.4-2) ...
Setting up nspluginwrapper-i386 (0.9.91.3-2) ...

```

$ sudo ln -s /usr/lib/nspluginwrapper/x86_64/npconfig /usr/bin/nspluginwrapper 

$ tar -xzf install_flash_player_9_linux.tar.gz
$ cd install_flash_player_9_linux
$ sudo cp libflashplayer.so /usr/lib64/firefox/plugins/

$ nspluginwrapper -i /usr/lib64/firefox/plugins/libflashplayer.so 

$ nspluginwrapper --list```

/home/satimis/.mozilla/plugins/npwrapper.libflashplayer.so
  Original plugin: /usr/lib64/firefox/plugins/libflashplayer.so
  Wrapper version string: 0.9.91.4

```

Restart Firefox
On Address bar type;
about:plugins```

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

```

Installation of Flash completed.

Now Flash is running on 64bit Firefox


B.R.
satimis

---

### Post by satimis on 2007-08-22
> **je1117 said:**
> Just follow the steps carefully on this [page]("http://ubuntuforums.org/showthread.php?t=341727").

Alternative n.1 worked for me. 
Hi je1117,


On above URL;

[http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)
Did not work.


satimis

---

### Post by satimis on 2007-08-22
> **Kilz said:**
> The reason is that some people need more than Flash. Nspluginwrapper only works with flash. If you need a safe java, the acrobat reader, or other plugins a 32bit Firefox is your best bet. Since Firefox is not optimized to a 64bit processor, you dont lose any performance. What the original poster missed on the page he linked to was the automated setup script that makes short work of installing it.

That said, if you are going to install nspluginwrapper because all you need is flash. [Why not do it the easy way. 10 seconds and its installed.]("http://ubuntuforums.org/showthread.php?t=476924")
Hi Kilz,

Tks for your advice.

I read your posting after having installed Flash.  I'll try it another tiime.


B.R.
satimis

---

### Post by Kilz on 2007-08-22
> **satimis said:**
> Hi Kilz,

Tks for your advice.

I read your posting after having installed Flash.  I'll try it another tiime.


B.R.
satimis

Please be aware that the deb created with alien will be a problem if you later upgrade to Gutsy.

---

### Post by satimis on 2007-08-22
> **Kilz said:**
> Please be aware that the deb created with alien will be a problem if you later upgrade to Gutsy.
Noted and thanks


satimis

---

