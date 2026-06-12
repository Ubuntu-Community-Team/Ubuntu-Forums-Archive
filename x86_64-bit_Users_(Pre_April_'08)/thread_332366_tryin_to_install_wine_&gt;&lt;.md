---
title: "tryin to install wine &gt;&lt;"
date: 2007-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by kannz on 2007-01-05
um im a linux noob and im tring to install wine but when i try and get the package off synaptic it gives me an error. >< heres a screenie if that helps. 

[IMG]http://i142.photobucket.com/albums/r117/strayhayt/Screenshot.png[/IMG]

---

### Post by tbroderick on 2007-01-06
Check your /etc/apt/sources.list and make sure you are the correct entry for the wine repo.

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

---

### Post by kannz on 2007-01-06
it is the repo i got from the site >< and im pretty sure im using 6.06 isnt edgy 6.10?

---

### Post by tbroderick on 2007-01-06
Can you post your sources.list?

---

### Post by kannz on 2007-01-06
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by tbroderick on 2007-01-06
I'm not sure why it's not working. How about just direct downloading the deb and then use sudo dpkg -i to install.

```

wget -c http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.28~winehq0~ubuntu~6.06-1_i386.deb
sudo dpkg -i wine_0.9.28~winehq0~ubuntu~6.06-1_i386.deb
```

---

### Post by kannz on 2007-01-06
when i did it that way it said this after it was done downloading

dpkg: error processing wine_0.9.28~winehq0~ubuntu~6.06-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 wine_0.9.28~winehq0~ubuntu~6.06-1_i386.deb
is it saying it wont work because im using a amd64 proc? :/

---

