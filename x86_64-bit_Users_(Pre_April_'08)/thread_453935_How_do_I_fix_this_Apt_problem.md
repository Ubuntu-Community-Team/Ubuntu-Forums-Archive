---
title: "How do I fix this Apt problem?"
date: 2007-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by gaylapdancer on 2007-05-24
Earlier I was trying to get xDVDShrink, and found a program called Automatix2 which would do it for me. To get automatix, I followed instuctions on [this]("http://www.ubuntugeek.com/install-popular-applications-in-ubuntu-feisty-fawn-using-automatix2.html") site. 

I entered the commands:
```

# sudo -i

# password

# echo “deb http://www.getautomatix.com/apt feisty main” | sudo tee -a /etc/apt/sources.list

# wget http://www.getautomatix.com/keys/automatix2.key

# gpg --import automatix2.key

# gpg --export --armor E23C5FC3 | sudo apt-key add -

```
Then did:
```

# sudo apt-get update

```

and got the error:

```
E: Type '“deb' is not known on line 42 in source list /etc/apt/sources.list
```

my sources.list file looks like this:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nz.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nz.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nz.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nz.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://nz.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe #Added by software-properties
“deb http://www.getautomatix.com/apt feisty main”
```

Line 42 is:

```
“deb http://www.getautomatix.com/apt feisty main”
``` 

To fix it do I remove the quotes? or is there something else I need to do? Any help at all is greatly appreciated

---

### Post by NeoLithium on 2007-05-24
Just remove the " surrounding the automatix entry in your sources.list; and then run sudo aptitude update once again. Should clear it up.

---

### Post by ryanVickers on 2007-05-24
When I installed automatix2, I don't remember it being that complicated.  I found this great guide but I don remember the URL.  search for "Seven post-install tips for ubuntu 7.04" at [www.linuxworld.com.au](www.linuxworld.com.au) and somewhere on the page there is a link that takes you to a page for installing it.

---

### Post by gaylapdancer on 2007-05-24
Thanks a heap guys, that fixed it right up. :D

---

### Post by NeoLithium on 2007-05-24
No prob :) Glad it's all working for you.  For additional stuff, you may want to check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  Just because it gives you some detailed instructions regarding installations of programs, etc.  Automatix is good for a quick install, but some users (not all) find that it causes some problems.

---

### Post by gaylapdancer on 2007-05-24
Will do. Thanks Again.

---

