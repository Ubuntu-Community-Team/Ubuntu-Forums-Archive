---
title: "Problem instaling wine"
date: 2007-11-06
forum: Wine
---

### Post by jotje on 2007-11-06
ok im kind of new to Linux but i hope to learn fast ^^

im running Ubuntu Gutsy Gibbon (7.10).

im trying to instal the most addictive game WoW ofc and i need to instal wine first, ok sure folowed the steps not so hard but when i try to instal wine i get this error.

-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) but 1.4ubuntu20 is to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
        Depends: libc6-i386 (>= 2.6-1) but 2.3.6-0ubuntu20 is to be installed
E: Broken packages


Does enyone know what i need to do to solve this problem so i can get on with my instalation, or maybe you got a better way to get WoW working (don't know how crossover Works is it easyer/better then wine?)


Greetz jotje

---

### Post by LinuxGuy1234 on 2007-11-06
> **jotje said:**
> ok im kind of new to Linux but i hope to learn fast ^^

im running Ubuntu Gutsy Gibbon (7.10).

im trying to instal the most addictive game WoW ofc and i need to instal wine first, ok sure folowed the steps not so hard but when i try to instal wine i get this error.

-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) but 1.4ubuntu20 is to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
        Depends: libc6-i386 (>= 2.6-1) but 2.3.6-0ubuntu20 is to be installed
E: Broken packages


Does enyone know what i need to do to solve this problem so i can get on with my instalation, or maybe you got a better way to get WoW working (don't know how crossover Works is it easyer/better then wine?)


Greetz jotje

You can try CrossOver Linux:
[http://www.codeweavers.com/]("http://www.codeweavers.com/")

Try for 30 days. $40 is the price to pay if you still want to play WoW.

You can also install it from the SPM too, search for wine and mark for install and install by applying changes! Tada! You now have Wine!

---

### Post by ajgreeny on 2007-11-06
You may need to ensure you have all the repositories needed activated for this.  Go System>Administration>Software sources and make sure universe and multiverse repos are active, then ```
sudo apt-get update
```to download database from the new ones.  You could also add the wine repository itself with the following two lines
```
 sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
    wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
```

---

