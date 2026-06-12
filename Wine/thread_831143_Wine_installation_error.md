---
title: "Wine installation error"
date: 2008-06-16
forum: Wine
---

### Post by spraveenitpro on 2008-06-16
Hi 

While installing wine , i get the below dependency error,
pls let me know how to fix this.

root@praveen:~# [COLOR="DarkRed"]sudo apt-get install wine[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: winbind but it is not going to be installed
[COLOR="DarkRed"]E: Broken packages
root@praveen:~# [/COLOR]

praveen.

---

### Post by cogadh on 2008-06-16
What version of Ubuntu are you using and have you customized your repositories in any way (i.e. added or removed any)?

---

### Post by spraveenitpro on 2008-06-16
I use hardy 8.04 and have the following entries in the souftware sources ;

binary
[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

sources
[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

---

### Post by cogadh on 2008-06-16
What about the rest of your standard software sources, have you altered them in any way? The winbind package is part of the main Ubuntu repository and if you have disabled or altered that in any way, you won't be able to get it. Your /etc/apt/sources.list should probably have all these entires:
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```
If you don't have the universe/multiverse repositories enabled, they may be commented out, but at the very least, all of the main repositories should be there and enabled.

---

