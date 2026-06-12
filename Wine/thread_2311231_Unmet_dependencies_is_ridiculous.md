---
title: "Unmet dependencies is ridiculous"
date: 2016-01-25
forum: Wine
---

### Post by Gottier on 2016-01-25
I tried to install wine through Ubuntu Software Center, but it says that it has unmet dependencies. So I see that other people recommend PPA, and I installed from there. This was about a week ago. Now when apt-get does it's upgrade, it now says I have unmet dependencies. 

Why is this wine so bad? Is it just really not meant to exist and be **used easily**?

Ubuntu desktop version is 14.04.3 and **always current with updates**. 

-------------------------------------------------------------------------

$ sudo apt-get update
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
[B]The following packages have been kept back:
  wine-devel wine-devel-amd64 wine-devel-i386:i386[/B]
The following packages will be upgraded:
  winehq-devel
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,940 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ppa.launchpad.net/wine/wine-builds/ubuntu/](http://ppa.launchpad.net/wine/wine-builds/ubuntu/) trusty/main winehq-devel amd64 1.9.2~ubuntu14.04.1 [1,940 B]
Fetched 1,940 B in 0s (6,282 B/s)         
(Reading database ... 1041986 files and directories currently installed.)
Preparing to unpack .../winehq-devel_1.9.2~ubuntu14.04.1_amd64.deb ...
Unpacking winehq-devel (1.9.2~ubuntu14.04.1) over (1.9.1~ubuntu14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up winehq-devel (1.9.2~ubuntu14.04.1) ...

-------------------------------------------------------------------------

How can I use wine easily? I just don't want to have to have problems. There really shouldn't be problems!

---

### Post by ian-weisser on 2016-01-26
> **Gottier said:**
> I tried to install wine through Ubuntu Software Center, but it says that it has unmet dependencies.
Unmet dependencies from packages sourced at the Ubuntu repositories is a very, very rare problem.
Usually, such problems are caused by packages from PPAs and other non-Ubuntu sources.

If you happen to reproduce the problem someday using only Ubuntu-sourced packages, please don't detroy it! Let us see it, so we can report the bug in enough detail to fix it permanently.

> **Gottier said:**
>  So I see that other people recommend PPA, and I installed from there.
Unwise. It was unlikely to solve your original problem.
If it did, you got lucky. PPAs sometimes make dependency problems worse.


 > **Gottier said:**
> [B]The following packages have been kept back:
  wine-devel wine-devel-amd64 wine-devel-i386:i386[/B]
 'kept back' is not a dependency problem.
That simply means you must use apt-get dist-upgrade.
WARNING: Using dist-upgrade might introduce dependency problems. Read the proposed changes carefully before hitting 'Y'.

---

