---
title: "Help!  all my gnome theme text has been replaced by boxes!"
date: 2007-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by the_it on 2007-05-14
So anyways my brother got this new box just the other day.  It's an Intel P4 641 3.2GHz with 1G RAM, an Intel 945G/ICH7 chipset with Intel 950 GMA.  I looked up at my old CD collection and saw that the I still had a 6.06 LTS 64bit edition with me.  We installed that in a snap and didnt have much trouble.  Later on my brother went to work and I started browsing the net.

I quickly encountered the 32/64bit plugins  issue and was going to do nsplugin to compensate, BUT I had the bright idea of upgrading to 7.04 feisty before doing so.  You can guess what happened.

First my apt broke.  Ubuntu-desktop refused to install and no matter what remove, install, upgrade and update combinations I tried there were some broken packages that stayed.  In particular, xfonts-scalable up and died on me.  The postinstall/postrm script kept complaining about mkfontdir failing (as you will see I was unable to write it down).

My rationalization was that upgrading from 606 to 704 was perhaps too big a jump. So I tried bumping it down to edgy.  I replaced all feisty's in my sources.list with edgy's, did an apt-get dist-upgrade and broke my system further >___<.  Somewhere in the apt-upgrade my fonts or themes or something like that must have been deleted.  The thing was, I did a restart after (well actually, it hanged after I restarted gdm)

Basically, I need to know what package I must install/configure to edit the fonts that appear in gnome/gdm.  All text that appears on the widgets, login screens and so on have turned into boxes (unprocessed fonts I guess).  How do I set my gnome-fonts to be normal?

(and yes, I'll still try to upgrade to feisty when I get this right)

---

### Post by the_it on 2007-05-14
Oh man, so little to work on.  Here's my sources.list


> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531)]/ dapper main restricted

---

### Post by RAOF on 2007-05-14
Indeed, you've found that you can't skip versions with a dist-upgrade (you should probably have used the "update-manager", rather than changing the "dapper" to "feisty" in the sources.list, too).

Probably the easiest way to fix this is to just reinstall dapper, then upgrade Dapper->Edgy->Feisty using the instructions here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by the_it on 2007-05-14
I was guessing it would actually be faster to get the feisty installer than to upgrade twice and download essentially 2 distros instead of 1.  So while I'm waiting to see if there's anything I can mess around with on my gnome desktop, I'm also downloading feisty.

But I really do want to know if I can fix my gnome.

---

### Post by RAOF on 2007-05-14
> **the_it said:**
> ...
But I really do want to know if I can fix my gnome.

The answer is quite possibly "no".  You've done a bunch of stuff which is not supported by apt - skipping a version while upgrading, then trying to go back a version, neither of which are supported.

---

### Post by kuja on 2007-05-14
I've ran into the pre/post rm script problems before (in other scenarios), I really do need to find a workaround for that, if one exists :\

---

### Post by the_it on 2007-05-14
my theory was short of editing the cached debs to remove the scripts or make them just return 0, but I don't know deep enough about them to do it.

Anyhows, I just installed feisty using a downloaded iso.  Works great.  I'll be looking for my flash, java and codecs now, preferably over the 64bit browser.

wish me luck (mostly with the java plugin, so far as I have skimmed, there isn't one yet?)

---

