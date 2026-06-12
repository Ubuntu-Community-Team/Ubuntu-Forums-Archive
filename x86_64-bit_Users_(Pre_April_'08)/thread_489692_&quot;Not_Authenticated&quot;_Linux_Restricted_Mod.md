---
title: "&quot;Not Authenticated&quot; Linux Restricted Modules?"
date: 2007-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by NeilBlanchard on 2007-07-01
Greetings,

Both my 64bit and 32bit Feisty machines have some available updates, that when I start to install them, I get a warning about them being "NOT AUTHENTICATED", and "this could allow a malicious individual to damage or take control of your system":

linux-restricted-modules-2.6.20.16-generic
linux-restricted-modules-common

Are these legit?  And if so, why the warning?

---

### Post by praxis22 on 2007-07-01
yes, they are, but it looks like you've either installed a new kernel via synaptic or enabled the extra repositories but not installed the pgp key.

Check your software sources control panel.

---

### Post by Vajra Vrtti on 2007-07-01
That should not happen to a kernel update. Could you post your */etc/apt/sources.list* here?

---

### Post by NeilBlanchard on 2007-07-01
Greetings,

Sure, here's the 64bit machine's:
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by Vajra Vrtti on 2007-07-02
It seems OK. In *System -> Administration -> Software Sources* select the *Authentication* tab and press the *Restore Defaults* button. The refresh the list in the *Update Manager* and see what happens.

---

### Post by NeilBlanchard on 2007-07-02
Hello again,

Here's the 32bit machine's file, which is a FRESH installation, only just a week ago or so:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

I should say that I have already installed the upgrades -- I am trusting that it was the authentication list that was causing this; not illegitimate upgrades.

---

### Post by Vajra Vrtti on 2007-07-02
> I am trusting that it was the authentication list that was causing this; not illegitimate upgrades.

I agree. Your sources.list looks fine. I'm attaching my own authorization list.

---

### Post by mvaniersel on 2007-07-03
I had the exact same problem: NOT AUTHENTICATED on the latest kernel updates. How can this happen all of a sudden? I didn't make any changes to apt sources or authorization lists. Could this be a problem with the ubuntu mirror that I'm using?

---

### Post by dkaddict on 2007-07-05
I have always had warnings about packages that are 'not authenticated'  when installing stuff with Synaptic. I just assumed it was because I had a load of 3rd party sources on my '/etc/apt/sources.list'. I haven't had anything malicious sneak into my machine hitherto so don't really take any notice of these messages. 

Am I being a bit cavalier by ignoring them so? I haven't got that much experience using Ubuntu (10 months) but just can't see how a malicious package in the repos would go unnoticed, and therefore unreported, for long enough for it to get inadvertantly installed by loads of users.  When I was first learning about editing the 'sources.list' file, I recall there being warnings about sources that had dodgy software which could break ones machine on some of the lists of 3rd party repos published on the web. I took heed and didn't add them to my list.

Now I am pretty sure that I have read somewhere on these forums recently that the latest updates of the 2.6.20-16 Restricted Modules package have played havoc with some peoples wireless connections.  As a result, I unchecked the boxes for that and the 2.6.20-16 common package before I installed these latest updates. I had a look at the details of the restricted modles and saw a 'mad wifi' package. Would this wreck my perfectly good existing connection? Also, the other elements which make up this package don't really have anything to do with my set up. I don't need them. Is there any way I can tell my update manager I don't want them so it will stop hassling me when I boot up? Sorry if I have gone on a bit and hijacked this thread. If I have been out of order, tell me so I can ask in the correct place.

Nice one and thanx for any help if it comes my way.

Little more

dk

---

