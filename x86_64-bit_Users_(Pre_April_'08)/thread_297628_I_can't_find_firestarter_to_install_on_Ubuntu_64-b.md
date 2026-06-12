---
title: "I can't find firestarter to install on Ubuntu 64-bit"
date: 2006-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by mesh2005 on 2006-11-11
I have two machines, one is 32-bit Ubuntu and the second is 64-Ubuntu. I installed firestarter on the 32-bit machine, I tried to run apt-get install firestarter on the 64-bit machine but I got "couldn't find package"
I checked the universe mirrors too but I couldn't find it too
Why?
Thank you

---

### Post by bruenig on 2006-11-11
> **mesh2005 said:**
> I have two machines, one is 32-bit Ubuntu and the second is 64-Ubuntu. I installed firestarter on the 32-bit machine, I tried to run apt-get install firestarter on the 64-bit machine but I got "couldn't find package"
I checked the universe mirrors too but I couldn't find it too
Why?
Thank you

Are you sure you have universe enabled? If you need to get firestarter and you can't figure out your problem you can download it from the online package thing.
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/f/firestarter/firestarter_1.0.3-1.2ubuntu3_amd64.deb
sudo dpkg -i firestarter_1.0.3-1.2ubuntu3_amd64.deb
```

---

### Post by mesh2005 on 2006-11-11
I can't find many software (e.g. quanta , firestarter , kde-config , ...) for my Ubuntu 64-bit installed on AMD64 Turion?
Here is my /etc/apt/source.list
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by mesh2005 on 2006-11-11
Thank you I found it however I couldn't install it because of dependency. I think I need to get it using apt-get but I don't know why apt-get didn't find it. Here is my /etc/apt/source.list:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by bruenig on 2006-11-11
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

That is the line you should be downloading it from. Maybe there is something wrong with au. I am using us.

Also, you are still using dapper right? Not edgy?

---

### Post by mesh2005 on 2006-11-12
Thank you , it works :) yes I use Dapper 6.06

---

