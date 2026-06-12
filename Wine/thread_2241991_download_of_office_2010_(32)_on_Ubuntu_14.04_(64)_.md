---
title: "download of office 2010 (32) on Ubuntu 14.04 (64) -- is this dumb?"
date: 2014-08-29
forum: Wine
---

### Post by xigen on 2014-08-29
I use office
I use Ubuntu

I would like to use Office 2010 on Ubuntu 14.04 (64).    

Amazon offers a download version...
1) Get a box with a key printed on a card
2) Go to MS and download Office 2010
3) Install w/ key.  (1key-1pc)

Does this work for my system?
Do I need to get the disk of office 2010
Am I about to have a bunch of headaches?
Does office 32 bit work well on Ubuntu 14.04 64 bit?

Thoughts?

---

### Post by slooksterpsv on 2014-08-29
You can see if you can run it under WINE:
[https://appdb.winehq.org/objectManager.php?sClass=version&iId=17336](https://appdb.winehq.org/objectManager.php?sClass=version&iId=17336)

If you want the look of Office 2010/2013 you can also use WPS Office - granted it's beta, but it's awesome. 
[http://wps-community.org/](http://wps-community.org/)

---

### Post by Mark Phelps on 2014-08-30
> Am I about to have a bunch of headaches?
Does office 32 bit work well on Ubuntu 14.04 64 bit?

Answers: Yes, and No.  Office 2010 and newer does not work well in Wine.  There are tricks you can use to get it installed, but the newer "xml" format files simply don't work well -- and those are the default format for Office 2007 and newer.

The WineHQ website links shows the ratings for each of the Office components -- and as you will see, those vary considerably by component.  Plus, some Office-related components, like Outlook, Project, Access (to name a few), simply don't work in Wine.

You should consider trying WPS Office (new name for Kingston Office), as it's claimed to have the best compatibility with MS Office files.

---

### Post by xigen on 2014-08-30
I love the idea of using WPS office - however:
as of 8/28/14 
-- there is not 6 bit version
-- ia32 libraries + --add-architecture i386 .. and I stil cannot install
-- 404 errors when I go to noobslabwps-office_9.1.0.4751~a15_i386.deb
[HTML]
http://wps-community.org/forum/viewtopic.php?f=28&t=66&start=10[/HTML]

```
wps-office-fonts_1.0_all.deb
meow@MeowBatunde:~/Downloads$ sudo dpkg -i wps-office_9.1.0.4751~a15_i386.deb 
(Reading database ... 253627 files and directories currently installed.)
Preparing to unpack wps-office_9.1.0.4751~a15_i386.deb ...
Unpacking wps-office (9.1.0.4751~a15) over (9.1.0.4751~a15) ...
Setting up wps-office (9.1.0.4751~a15) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
meow@MeowBatunde:~/Downloads$ cd && wget -O kingsoft-office-NoobsLab.deb http://goo.gl/HplIfc
--2014-08-30 14:00:57--  http://goo.gl/HplIfc
Resolving goo.gl (goo.gl)... 74.125.239.103, 74.125.239.104, 74.125.239.105, ...
Connecting to goo.gl (goo.gl)|74.125.239.103|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://drive.noobslab.com/apps/kingsoft-office_9.1.0.4244~a12p3_i386.deb [following]
--2014-08-30 14:00:57--  http://drive.noobslab.com/apps/kingsoft-office_9.1.0.4244~a12p3_i386.deb
Resolving drive.noobslab.com (drive.noobslab.com)... 91.196.124.156
Connecting to drive.noobslab.com (drive.noobslab.com)|91.196.124.156|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2014-08-30 14:00:58 ERROR 404: Not Found.
```

---

### Post by xigen on 2014-08-30
I tried this:

[HTML]http://kb.openstudioproject.com/content/ubuntu/install-kingsoft-office-ubuntu-1310-64-bit[/HTML]

```

sudo apt-get -y install libc6:i386 libgcc1:i386 gcc-4.6-base:i386 libstdc++6:i386 libx11-6:i386 libglib2.0-0:i386 libfreetype6:i386 libSM6:i386 libXrender1:i386 libfontconfig1:i386 libXext6:i386 libcups2:i386 p11-kit:i386 libcap-ng0:i386 gnome-keyring:i386 libglu1-mesa:i386

```

it generated some errors -- yet, it looks like it worked...

```
meow@MeowBatunde:~/Downloads$ sudo dpkg -i wps-office_9.1.0.4751~a15_i386.deb 
(Reading database ... 253501 files and directories currently installed.)
Preparing to unpack wps-office_9.1.0.4751~a15_i386.deb ...
Unpacking wps-office (9.1.0.4751~a15) over (9.1.0.4751~a15) ...
Setting up wps-office (9.1.0.4751~a15) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtsp
```

---

### Post by xigen on 2014-08-30
WPS is terrific.   However, it is not MSword.

Funky - font - and - formatting issues.    Ugh!
Specifically text appears larger on WPS and my CV is 3 pages as opposed to 2. 

I wil check the WPS forums and see if there is a simple solution.

---

### Post by mastablasta on 2014-09-01
Word, Excel and PowerPoint 2010 work ok under wine. not great but OK.

you could install a Windows XP under virtualbox just for Office use. unless you use it all the time...

---

