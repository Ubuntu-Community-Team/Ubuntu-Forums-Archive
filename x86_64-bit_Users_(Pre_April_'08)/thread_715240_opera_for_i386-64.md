---
title: "opera for i386-64"
date: 2008-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by lynx shadow on 2008-03-04
i'm trying to install 64-bit opera on my notebook, but i get an error message saying "Package libqt3-mt is not installed." where can i get libqt3-mt?

i'm a beginner linux user, whose life is complicated by having a 64-bit notebook, an msi megabook with intel core2 duo.

i'd appreciate this simple piece of info.

thanks

---

### Post by fedex1993 on 2008-03-04
i found this guide [http://my.opera.com/sjosul/blog/installing-opera-on-ubuntu-7-04-64-bit](http://my.opera.com/sjosul/blog/installing-opera-on-ubuntu-7-04-64-bit) and i think it might work for you if your even on 7.10

---

### Post by LaRoza on 2008-03-05
Enable all repositories, and the package manager will most likely find it on its own.

---

### Post by lynx shadow on 2008-03-05
uhhn, thanks. it may sound like a stupid question to you, but how do i "enable all repositories"? i've used windows for so long, and i'm new to linux commands. pls help me. in the meantime, i'll check the linux and ubuntu commands for this.

your response is much appreciated.

---

### Post by LaRoza on 2008-03-05
> **lynx shadow said:**
> uhhn, thanks. it may sound like a stupid question to you, but how do i "enable all repositories"? i've used windows for so long, and i'm new to linux commands. pls help me. in the meantime, i'll check the linux and ubuntu commands for this.

your response is much appreciated.

Open Applications->Add/Remove and select "All Available Applications" from the drop down box in the upper right.

---

### Post by jan quark on 2008-03-05
you can enable the software sources going to

system > administration > software sources

and there checking everything except source code and cd

then reload

and try again to install

---

### Post by lynx shadow on 2008-03-05
thanks for your replies. i tried reloading using the system>administration>software sources feature, but kept getting these messages. (these are only some of the messages, but they're all about "connection refused". what does that mean?

so i don't think i got anything reloaded. i disabled the option saying items are installable from the ubuntu gutsy cdrom.


[I][http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_PH.bz2:](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_PH.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_PH.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_PH.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[/I]
could i also add another question here? i keep getting the following message too, not just for 'kpowersave'.

[I]This application conflicts with other installed software. To install 'kpowersave' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
[/I]

i try the synaptic package manager, but there's nothing that tells me what the conflicting software are so i can uninstall them.

thanks again for the help. i haven't gotten there yet, but at least i'm learning to try new things.

---

### Post by jan quark on 2008-03-06
can ypi please post the result of this terminal command:

```
cat /etc/apt/sources.list
```

---

### Post by lynx shadow on 2008-03-06
here are the results of the command: cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted

that's it. hope you can help me out. i need to start preparing a project plan, and i need openproj for it. i could install openproj in my windows boot, but i'd really like to leave windows and go with ubuntu linux all the way. if i have neglected to mention it, i've installed ubuntu 7.10 gut\sy.

thanks loads

---

### Post by lynx shadow on 2008-03-09
thanks for your advice.

i was finally able to get opera installed on my 64-bit notebook by getting the prerequisite files installed. i was so glad to see the opera icon in my applications menu.

but when i tried to run it, i got the message, "could not connect to proxy server. access denied." but i don't have a proxy server!

even more disturbing, evertime i run opera, after a couple of seconds, it disappears from my screen.

what gives? please help me take the next steps to get opera running.

thanks for your replies.

---

### Post by zubrug on 2008-03-10
Go into your home folder and delete the .opera file and then try again.
If that fails then try a reinstall.

sudo apt-get remove --purge opera

sudo dpkg -i opera'tab'

good luck, opera rocks

---

