---
title: "All of a sudden Pidgin is gone and I can't bring it back."
date: 2008-07-07
forum: x86 64-bit Users
---

### Post by Rock on 2008-07-07
I dual boot XP Pro x64 with Kubuntu 8.04 Hardy Heron because I do work with Adobe CS3 and I boot into Kubuntu after a day of being in Windows to find that Pidgin is gone and when I try to install it again. I get this 
> chris@Chris-PC:~$ sudo apt-get install pidgin
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
  pidgin: Depends: libpurple0 (>= 1:2.4.1-1ubuntu2.1) but it is not going to be installed
          Depends: pidgin-data (< 1:2.4.1-z) but 1:2.4.3-0ubuntu1~hardy1 is to be installed
E: Broken packages

---

### Post by scragar on 2008-07-07
try running:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f pidgin
```
and see if you still get an error.(or where you get an error :P)

---

### Post by lesshaste on 2008-09-16
I have the same problem and that fix doesn't work.   Looks like something has broken in the packaging.

Raphael

---

### Post by brodae on 2008-10-22
This doesn't work for me, either... HELP!

---

