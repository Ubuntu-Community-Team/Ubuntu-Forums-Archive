---
title: "Wine and other repo errors"
date: 2008-07-18
forum: x86 64-bit Users
---

### Post by Hark3n on 2008-07-18
Hi,

Yesterday I decided to install Wine and to my shock found out that the ubuntu repos only has a pre 1.0 release.

I then went over to [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb") and followed the instructions there.

When I run apt-get update i get the following printout:

> Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_ZA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_ZA
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_ZA
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_ZA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/multiverse Translation-en_ZA
Get:2 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_ZA
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages [2802B]
99% [Waiting for headers] [Waiting for headers] [Connecting to ppa.launchpad.net (91.189.90.217)] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
  Sub-process gzip returned an error code (1)
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Get:4 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates Release [58.5kB]
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates Release

Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/main Packages

Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/restricted Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/universe Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy/multiverse Sources
Fetched 2993B in 9s (316B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://za.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-amd64/Packages.gz](http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


This was also when I first noticed that some other repos are also not updating.

Does anyone know what the problem is?

---

### Post by empty_tank on 2008-07-20
i just installed wine 1.0 from the ubuntu repository.  I am using hardy amd64.

Your problem with the repos could be temporary.  Try looking for a faster download server.

---

### Post by Kilz on 2008-07-20
> **Hark3n said:**
> Hi,

Yesterday I decided to install Wine and to my shock found out that the ubuntu repos only has a pre 1.0 release.



You were shocked that the wine package was of an older version? Packages are created by volunteers. Sometimes we have to wait for them to package a newer version, that doesn't mean that the version in the repositories is bad.

---

### Post by Yannick Le Saint kyncani on 2008-07-20
> **Hark3n said:**
> Yesterday I decided to install Wine and to my shock found out that the ubuntu repos only has a pre 1.0 release.

Wine 1.0.0 is available in hardy-updates repository, section universe, in fact, I have it installed :

/home/kyncani/ > apt-cache policy wine
wine:
  Installed: 1.0.0-1ubuntu4~hardy1
  Candidate: 1.0.0-1ubuntu4~hardy1
  Version table:
 *** 1.0.0-1ubuntu4~hardy1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
        100 /var/lib/dpkg/status
     0.9.59-0ubuntu4 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
/home/kyncani/ >

---

