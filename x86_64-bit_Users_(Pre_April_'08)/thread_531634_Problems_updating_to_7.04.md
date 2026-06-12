---
title: "Problems updating to 7.04"
date: 2007-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Shuri on 2007-08-21
I'm trying to update my version of ubuntu to 7.04 through the update manager but it always stops while downloading some files. It gives me this error:

Failed to fetch [http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/drivers/binary-amd64/Packages.gz](http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/drivers/binary-amd64/Packages.gz) 404 Not Found

I'm currently using Ubuntu 6.10 - the Edgy Eft. 
Sorry that I can't give more info :s

---

### Post by Kilz on 2007-08-21
> **Shuri said:**
> I'm trying to update my version of ubuntu to 7.04 through the update manager but it always stops while downloading some files. It gives me this error:

Failed to fetch [http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/drivers/binary-amd64/Packages.gz](http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/drivers/binary-amd64/Packages.gz) 404 Not Found

I'm currently using Ubuntu 6.10 - the Edgy Eft. 
Sorry that I can't give more info :s

The file doesnt exist, clicking on the link should download the file, but you get a 404 file not found error.

---

### Post by John.Michael.Kane on 2007-08-21
> **Shuri said:**
> I'm trying to update my version of ubuntu to 7.04 through the update manager but it always stops while downloading some files. It gives me this error:

Failed to fetch [http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/drivers/binary-amd64/Packages.gz](http://seveas.theplayboymansion.net/seveas/dists/dapper-seveas/drivers/binary-amd64/Packages.gz) 404 Not Found

I'm currently using Ubuntu 6.10 - the Edgy Eft. 
Sorry that I can't give more info :s

Run:
```
gksudo gedit /etc/apt/sources.list 
```

copy paste your sources.list here for review.

---

### Post by Shuri on 2007-08-21
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas drivers
deb-src [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas drivers

Thanks for the quick replies :)

---

### Post by John.Michael.Kane on 2007-08-22
Shuri I have taken your sources.list, and commented out the repo's that are not needed, As well as uncommented the one that are.

Run:
```
gksudo gedit /etc/apt/sources.list 
```

Replace your sources.list with the one below.

The run
```
gksudo aptitude update
```

Then try to distro upgrade as you did before.

```
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas drivers
# deb-src [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas drivers
```

The dapper-seveas drivers I see are for ATI. Having mixed repos is known to cause problems. 

Also when you upgrade to ubuntu 7.04 you should try the driver in the 7.04 repo.

---

### Post by Shuri on 2007-08-23
Thanks for your help, very much apreciate it. My distro update is running fine now :) . I'll be sure to try the new driver when I'm all up to date.

---

