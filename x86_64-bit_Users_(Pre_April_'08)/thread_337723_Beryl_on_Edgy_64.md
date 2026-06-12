---
title: "Beryl on Edgy 64"
date: 2007-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by TheVrolok on 2007-01-13
I've tried using numerous howto's but mostly the following 2:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)
[https://help.ubuntu.com/community/CompositeManager/InstallingBeryl](https://help.ubuntu.com/community/CompositeManager/InstallingBeryl)

And the problem I'm running into is with the Beryl respositories.  I've install xgl easily:

rumble@rumbletop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree
Reading state information... Done
xserver-xgl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But my issue comes with install beryl, bottom line, I can't find repositories that work.  I installed Beryl with not even a small bump in the road last time I did it on my last laptop (32 bit Edgy) so I'm assuming it's a problem with the 64 bit and not something I'm doing wrong (which is such a terrible thing to assume :P).  But here I am, asking what I'm doing wrong :P

I've tried every respository listed in the 2 above howto's and I either get them to be unresolvable (which can happen with mirrors) or, from the main beryl-project site I get:

rumble@rumbletop:~$ sudo apt-get update
Ign cdrom://Kubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/main Translation-en_US
Ign cdrom://Kubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/restricted Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Ign [http://ubunutu.beryl-project.org](http://ubunutu.beryl-project.org) edgy Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Ign [http://ubunutu.beryl-project.org](http://ubunutu.beryl-project.org) edgy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://ubunutu.beryl-project.org](http://ubunutu.beryl-project.org) edgy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Ign [http://ubunutu.beryl-project.org](http://ubunutu.beryl-project.org) edgy/main Packages
Err [http://ubunutu.beryl-project.org](http://ubunutu.beryl-project.org) edgy/main Packages
  404 Not Found
Fetched 4B in 1s (4B/s)
Failed to fetch [http://ubunutu.beryl-project.org/dists/edgy/main/binary-amd64/Packages.gz](http://ubunutu.beryl-project.org/dists/edgy/main/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
rumble@rumbletop:~$                                             

As you can see, I have basically every repository enabled.  For Beryl, I tried, like mentioned, all those listed in the above howto's as well as every compination of:

deb [http://ubunutu.beryl-project.org/](http://ubunutu.beryl-project.org/) edgy main
deb [http://ubunutu.beryl-project.org/](http://ubunutu.beryl-project.org/) edgy main-edgy main-edgy-amd64
deb [http://ubunutu.beryl-project.org/](http://ubunutu.beryl-project.org/) edgy main-edgy-amd64

etc.. etc.. etc..  and with the same result (varying only for the 404 not found main-edgy-amd64 or whatever other things I try to add).  I've tried browsing to the repository with a web browser and aside from "main" there don't seem to be any other areas that exist.  Is this just a restructuring error?  I've noticed .debs that seem to be set for amd64 sitting in the main directory along with all the other packages for beryl-core, beryl-settings, etc.. I was going to try to just grab the .debs for amd64 and dpkg -i them, but I didn't wanna mess things up if the easier, less manual, way, would work.  Any suggestions?  Thanks!

---

### Post by kleeman on 2007-01-13
Its ubuntu not ubunutu Spelling mistake in your repo list...

---

### Post by TheVrolok on 2007-01-13
> **kleeman said:**
> Its ubuntu not ubunutu Spelling mistake in your repo list...

lol, I can't believe I missed that.  I must have looked over my repos for typos a good ten times.  Thanks for lending me your eyes. ;)

Even after the fix, I'm still getting an error (only copied relevant output):

Get:6 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages [5350B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Fetched 5545B in 0s (8345B/s)
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/Release](http://ubuntu.beryl-project.org/dists/edgy/Release)  Unable to find expected entry  main-edgy-amd64/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
rumble@rumbletop:~$

I really don't get it because even if I use the deb [http://ubunutu.beryl-project.org](http://ubunutu.beryl-project.org) edgy main repo I get:

Err [http://ubunutu.beryl-project.org](http://ubunutu.beryl-project.org) edgy/main Packages
  404 Not Found
Fetched 4B in 0s (6B/s)
Failed to fetch [http://ubunutu.beryl-project.org/dists/edgy/main/binary-amd64/Packages.gz](http://ubunutu.beryl-project.org/dists/edgy/main/binary-amd64/Packages.gz)  404 Not Found

But I know [http://ubunutu.beryl-project.org/dists/edgy/main/binary-amd64/Packages.gz](http://ubunutu.beryl-project.org/dists/edgy/main/binary-amd64/Packages.gz) exists because I can browse to it with Konqueror.

---

### Post by kleeman on 2007-01-13
Here's my sources.list line (it works):

 deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

Try backing up yours and then stripping out all your beryl lines and replacing with my line and see what happens....

---

### Post by enzomatrix on 2007-01-18
Bandwidth Limit Exceeded

Seems that the site exceeded the monthly tranfer.

---

### Post by Amelia on 2007-01-18
Is Beryl doable in Dapper? Tried looking, no help found.

---

