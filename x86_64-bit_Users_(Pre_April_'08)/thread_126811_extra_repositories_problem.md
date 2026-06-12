---
title: "extra repositories problem"
date: 2006-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by eXTerminate on 2006-02-07
hi. i was told to ask this question at this part of the forum because i use the amd 64 version of kubuntu.
i'm looking for help with enabling extra repositories in kubuntu 5.10 breezy.
i followed the steps shown in easylinux.info/wiki/Ubuntu . the problem is that i can't get the packadges i want, i get

W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_f ree_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_n on-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

and when i do >
sudo apt-get update
i get :

Failed to fetch [http://packages.freecontrib.org/ubun...64/Packages.gz](http://packages.freecontrib.org/ubun...64/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubun...64/Packages.gz](http://packages.freecontrib.org/ubun...64/Packages.gz) 404 Not Found

my /etc/apt/sources.list looks like this (i used the thing listed in the starter guide):

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.
## You may replace "us" with your country code to get the closest mirror.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 

ideas?
thanks in advance.

---

### Post by gingermark on 2006-02-07
Hey :)

As I (sort of) mentioned in the other thread, I think the problem is that the PLF repository doesn't have any AMD64 packages in it. So, you won't be able to use that repository. My sig gives a reasonable list of official and unofficial repositories, but not many of the unnoffical ones are for AMD64, and legal issues mean that these are usuallty the places to get your codecs.

Obviously I don't have the solution on how to get the packages you're after, but hopefully someone else here will.

---

### Post by gingermark on 2006-02-07
I remember you were interested in the latest version of Firefox - have a look at [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) details how to get DVDs playing among other things, and includes notes about how to do AMD64 things when they differ from the x86 version.

Hope they help.

---

### Post by eXTerminate on 2006-02-13
why does the firefox open the page [www.barnesandnoble.com](www.barnesandnoble.com) each time it starts ?
doesn't matter which page i put to be my homepage firefox always opens barnesandnoble.com. i tried clearing all of my private data, erasing cookies...
whats wrong? i installed the firefox using 

[https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) you gave me?

---

