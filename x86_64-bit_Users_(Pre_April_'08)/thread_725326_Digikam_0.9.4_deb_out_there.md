---
title: "Digikam 0.9.4 deb out there?"
date: 2008-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Didjit on 2008-03-15
Any one have AMD 64 Digikam 0.9.4 debs they can share? 

Dijdit

---

### Post by zeltak on 2008-03-16
I would also LOVE \\:D/ getting some 64bit debs. i have been trying to compile 0.9.3 for ages with no success and have been looking like crazy for 0.9.3 debs with no success....

any deb files for new digikam versions would be much appreciated!

Zeltak

---

### Post by lui456 on 2008-04-14
Hi there,
are you still interested in a 64bit digikam deb-file?
You can download an [digikam.rpm]("http://rpmfind.net/linux/RPM/mandriva/2008.0/x86_64/media/main/backports/digikam-0.9.3-6mdv2008.0.x86_64.html") and convert it to digikam.deb. 

if it starts with error like: 
digikam: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

just link lib.tiff.so.4 to lib.tiff.so3:
 -cd /usr/lib
 -sudo ln -s libtiff.so.4 libtiff.so.3


lui

---

### Post by Didjit on 2008-04-14
Cool. Tx. I'll give it a shot.

Didjit

---

### Post by freackout on 2008-04-15
> **lui456 said:**
> Hi there,
are you still interested in a 64bit digikam deb-file?
You can download an [digikam.rpm]("http://rpmfind.net/linux/RPM/mandriva/2008.0/x86_64/media/main/backports/digikam-0.9.3-6mdv2008.0.x86_64.html") and convert it to digikam.deb. 

if it starts with error like: 
digikam: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

just link lib.tiff.so.4 to lib.tiff.so3:
 -cd /usr/lib
 -sudo ln -s libtiff.so.4 libtiff.so.3


lui
do look on net for 64 bit sources list for ubunt and add 28000 programmes to your list whats 64 is as is including digikam debs

---

### Post by freackout on 2008-04-15
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
# deb cdrom:[APTonCD for ubuntu gutsy - i386 (2008-03-24 21:21) CD1]/ /
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#######################################################################
# libdvdcss stuff here ie sudo apt-get install libdvdcss2 cos its amd64
# dont forget apt-get update first tommy ok
# deb [http://ftp.debian-unofficial.org/debian/](http://ftp.debian-unofficial.org/debian/) etch main contrib non-free restricted


#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071017)]/ gutsy main restricted

---

### Post by freackout on 2008-04-15
> **zeltak said:**
> I would also LOVE \\:D/ getting some 64bit debs. i have been trying to compile 0.9.3 for ages with no success and have been looking like crazy for 0.9.3 debs with no success....

any deb files for new digikam versions would be much appreciated!

Zeltak

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
# deb cdrom:[APTonCD for ubuntu gutsy - i386 (2008-03-24 21:21) CD1]/ /
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#######################################################################
# libdvdcss stuff here ie sudo apt-get install libdvdcss2 cos its amd64
# dont forget apt-get update first tommy ok
# deb [http://ftp.debian-unofficial.org/debian/](http://ftp.debian-unofficial.org/debian/) etch main contrib non-free restricted


#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071017)]/ gutsy main restricted

---

### Post by Nicram on 2008-04-15
> **Didjit said:**
> Any one have AMD 64 Digikam 0.9.4 debs they can share? 

Dijdit


Just compiled Digikam 0.9.4_beta3, but for i386 architecture only. :(

---

### Post by zeltak on 2008-04-16
Hi Nicram

Any chance for a deb file?


thx

Zeltak

---

### Post by Nicram on 2008-04-16
> **zeltak said:**
> Hi Nicram

Any chance for a deb file?

Zeltak

Sure, here you are [http://www.adrive.com]("http://www.adrive.com/public/0d00cc9d69ed32e6c489c3c97849e2fc5299c23f7dece53096f95592e00516da.html")

---

### Post by zeltak on 2008-04-16
hi again Nicram

Thx for the deb file but i think its for the i386 architecture, is that what you use? i was actually searching for a 64 bit version

thanks anyway!


zeltak

---

### Post by Nicram on 2008-04-16
> **zeltak said:**
> hi again Nicram

Thx for the deb file but i think its for the i386 architecture, is that what you use? i was actually searching for a 64 bit version

thanks anyway!
zeltak

Sorry, I've forgot to mention it. :oops:

Anyway, it works perfectly on my system.

---

### Post by erazz on 2008-04-16
Thanks a million!

Couldn't compile it myself for some strange reason (no error - just didn't make the bin files).   You just saved me hours of sifting through log files  :D

(Hardy beta on i386)

---

### Post by OnlyWhisky on 2008-05-01
Thank you for package but I got exiv2.so not found error. I think ubuntu version of exiv is incompatable with digikam 0.9.4 betas. Can you provide some help? May be exiv package?

---

### Post by Nicram on 2008-05-01
> **OnlyWhisky said:**
>  I got exiv2.so not found error. I think ubuntu version of exiv is incompatable with digikam 0.9.4 betas. Can you provide some help? May be exiv package?

this is Gutsy repo version of exiv
Do you have dev package installed?

---

### Post by OnlyWhisky on 2008-05-01
Hm... 0.16 is current version for hardy heron. Is there a simple way to install 0.15? I tried to add gutsy repo to the list but version 0.15 is not avaliable, may be I did it wrong. [I'm beginner with kubuntu - ex-getnoo user  =) ] Thank you for so fast feedback)

---

### Post by Nicram on 2008-05-01
you can build it by yourself, it's not so hard as it seems

make
./configure
checkinstall

---

### Post by OnlyWhisky on 2008-05-01
I know, I'm gentoo user, it was my daily work) It just takes time to compile and ubuntu gcc seems very slow compared to gentoo gcc (kernel settings, -j2 flag by default, i386 optimisation etc =) ) But I'll try now.

---

### Post by OnlyWhisky on 2008-05-01
Ok, I did it and also I've created deb package for ubuntu hardy heron (-march=pentium4 -O2). If someone needs it I can upload.

---

### Post by andre2p on 2008-05-01
Hello Whisky:

I would like to get your hardy heron deb if possible.

Thanks,
AC

---

### Post by OnlyWhisky on 2008-05-03
> **andre2p said:**
> Hello Whisky:

I would like to get your hardy heron deb if possible.

Thanks,
AC

[http://rapidshare.com/files/112173912/digikam-0.9.4_beta4-1_i386.deb.html](http://rapidshare.com/files/112173912/digikam-0.9.4_beta4-1_i386.deb.html)
here it is.

---

### Post by andre2p on 2008-05-06
Thanks!

---

### Post by Nicram on 2008-06-10
New digikam for i386 Intel. Gutsy.

[digikam-0.9.4 rc-2 i386]("http://www.adrive.com/public/c75d939031186afe3968729df1217a54aa9fdac9fae0917fb1638f7438b4d96a.html")

old one:
[digikam-0.9.4_beta5-1_i386]("http://www.adrive.com/public/dd1af1e6315ce5259bb823e654f3ad7647c9622ab755efac269410848d6adddd.html")

---

### Post by alex2035 on 2008-07-14
Sorry to ask Nicram, but the link for either of this .debs takes forever and doesnt download anything, am I doing something}wrong? thank you

regards
alex

---

### Post by Nicram on 2008-07-14
> **alex2035 said:**
> Sorry to ask Nicram, but the link for either of this .debs takes forever and doesnt download anything, am I doing something}wrong? thank you

regards
alex

Well, I've double checked now and it works perfectly in Firefox, IE6, Opera, so probably it something wrong on your side.

Tal vez algo con la configuracion de tu navegadaor?

---

### Post by alex2035 on 2008-07-14
Ooops,
thanx for the answer, what might be wrong? I have tried with Opera 9.5 and Firefox 3, I have disabled blocking of popups, have Java and every plugin enabled, so?....Have to try again now that I know there is nothing wrong on that side.
Again, thanx
alex

---

### Post by alex2035 on 2008-07-14
Now I am absolutely lost. Have tried again with opera and Firefox. then I went to windows where I tried again with Firefox 3 and IE7, nothing. I have left the browser work for some 10 minutes but nothing, it says "Loading..." and stays forever.
Now I think I have tried with many options, it is strange that all 4 didnt work....what is the link? another page where you download the file, or the file itself? (.html!? dont think so).

Any other place where I could go that you know of?
Thank you
alex

---

### Post by alex2035 on 2008-07-14
@ Nicram
I finally got it, after a long time and about to give up I fired Firefox one more time and it took me to Adrive where it downloaded the .deb without problems. I guess the server was under maintenance or something.
Now I have another problem, Gdebi says that platform is not supported (i386) and rejects the installation, but I know there is a way to "force architecture" to install anyway but I cant remeber how to use it.
Any hint?

Thanx 
alex

---

### Post by Nicram on 2008-07-14
> **alex2035 said:**
> @ Nicram
Now I have another problem, Gdebi says that platform is not supported (i386) and rejects the installation, but I know there is a way to "force architecture" to install anyway but I cant remeber how to use it.
Any hint?
Thanx 
alex

I think it is like
```
 dpkg --install --force-architecture somepackage.deb
```
but it could be dangerous, its better to compile by yourself
./configure
make
make install

---

### Post by Nicram on 2008-07-17
So, at last we have the final version:

[digikam]("http://www.adrive.com/public/9f73dcf7d5481e396e9f2ec0e255a23650503399513b7cd4cc078d67c3f4e2f5.html") for i386 Intel, Gutsy.

old ones:
[digikam-0.9.4 rc-2 i386]("http://www.adrive.com/public/c75d939031186afe3968729df1217a54aa9fdac9fae0917fb1638f7438b4d96a.html")
[digikam-0.9.4_beta5-1_i386]("http://www.adrive.com/public/dd1af1e6315ce5259bb823e654f3ad7647c9622ab755efac269410848d6adddd.html")

---

### Post by mmcmonster on 2008-07-17
> **Nicram said:**
> So, at last we have the final version:

[digikam]("http://www.adrive.com/public/9f73dcf7d5481e396e9f2ec0e255a23650503399513b7cd4cc078d67c3f4e2f5.html") for i386 Intel, Gutsy.

old ones:
[digikam-0.9.4 rc-2 i386]("http://www.adrive.com/public/c75d939031186afe3968729df1217a54aa9fdac9fae0917fb1638f7438b4d96a.html")
[digikam-0.9.4_beta5-1_i386]("http://www.adrive.com/public/dd1af1e6315ce5259bb823e654f3ad7647c9622ab755efac269410848d6adddd.html")

Thanks.

Unfortunately, when I double click on the package, it says that "A later version is already installed."  The version I have installed is 0.9.3, of course. :-(

---

### Post by mmcmonster on 2008-07-17
> :~/Desktop$ sudo dpkg -i digikam_0.9.4-1_i386.deb 
[sudo] password for maimon: 
dpkg - warning: downgrading digikam from 2:0.9.3-2ubuntu1 to 0.9.4-1.
(Reading database ... 163994 files and directories currently installed.)
Preparing to replace digikam 2:0.9.3-2ubuntu1 (using digikam_0.9.4-1_i386.deb) ...
Unpacking replacement digikam ...
Setting up digikam (0.9.4-1) ...
Okay.  Got it to install via the terminal.  It still doesn't work, though. :-(

> :~/Desktop$ digikam
digikam: error while loading shared libraries: libexiv2.so.0: cannot open shared object file: No such file or directory

---

### Post by solracnamrac on 2008-07-17
> **mmcmonster said:**
> Thanks.

Unfortunately, when I double click on the package, it says that "A later version is already installed."  The version I have installed is 0.9.3, of course. :-(

Same thing happening with me too.

---

### Post by Nicram on 2008-07-17
> **mmcmonster said:**
>   Got it to install via the terminal.  It still doesn't work, though. :-(

Hm, for we it works like a charm.
You should remove old version first, and then block new version

Still, I'm wondering why it's happening.

---

### Post by mmcmonster on 2008-07-17
> **Nicram said:**
> Hm, for we it works like a charm.
You should remove old version first, and then block new version

Still, I'm wondering why it's happening.

Still have the problem finding that library.

Maybe the library is in a different path than expected?

---

### Post by mmcmonster on 2008-07-17
Okay.  This fixed it for me:
```
cd /usr/lib
sudo ln -s libexiv2.so.2.1.0 libexiv2.so.0

```

---

